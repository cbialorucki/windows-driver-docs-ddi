---
UID: NI:ntifs.IOCTL_REDIR_QUERY_PATH
title: IOCTL_REDIR_QUERY_PATH (ntifs.h)
description: Learn more about the IOCTL_REDIR_QUERY_PATH control code.
tech.root: ifsk
ms.date: 06/21/2024
keywords: ["IOCTL_REDIR_QUERY_PATH IOCTL"]
ms.keywords: IOCTL_REDIR_QUERY_PATH, IOCTL_REDIR_QUERY_PATH control, IOCTL_REDIR_QUERY_PATH control code [Installable File System Drivers], ifsk.ioctl_redir_query_path, ioctl_ref_f46fa4a1-0546-4d70-8490-7a233a2e743f.xml, ntifs/IOCTL_REDIR_QUERY_PATH
req.header: ntifs.h
req.include-header: Ntifs.h
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: 
targetos: Windows
req.typenames: 
f1_keywords:
 - IOCTL_REDIR_QUERY_PATH
 - ntifs/IOCTL_REDIR_QUERY_PATH
topic_type:
 - APIRef
 - kbSyntax
api_type:
 - HeaderDef
api_location:
 - ntifs.h
api_name:
 - IOCTL_REDIR_QUERY_PATH
---

# IOCTL_REDIR_QUERY_PATH IOCTL

## -description

The **IOCTL_REDIR_QUERY_PATH** control code is sent by the multiple UNC provider (MUP) to network redirectors to determine which provider can handle a specific UNC path in a name-based operation, typically an IRP_MJ_CREATE request. This request is referred to as "prefix resolution."

MUP is a kernel-mode component responsible for channeling all remote file system accesses that use a UNC name to a network redirector (the UNC provider) capable of handling the remote file system requests. MUP is involved when a UNC path is used as illustrated by the following example that could be executed from a command line:

``` command
notepad \\server\public\readme.txt
```

MUP is not involved during an operation that creates a mapped drive letter (the "NET USE" command, for example). This operation is handled by the multiple provider router (MPR) and a user-mode WNet provider DLL for the network redirector. However, a user-mode WNet provider DLL might communicate directly with a kernel-mode network redirector driver during this operation.

On Windows Server 2003, Windows XP, and Windows 2000, remote file operations that are performed on a mapped drive that does not represent a Distributed File System (DFS) drive don't go through MUP. These operations go directly to the network provider that handled the drive letter mapping.

For network redirectors that conform to the Windows Vista redirector model, MUP is involved even when a mapped network drive is used. File operations performed on the mapped drive go through MUP to the network redirector. Note that in this case, MUP simply passes the operation to the network redirector that is involved.

The **IOCTL_REDIR_QUERY_PATH** control code is sent to network redirectors that have registered with MUP as Universal Naming Convention (UNC) providers by calling [**FsRtlRegisterUncProvider**](nf-ntifs-_fsrtl_advanced_fcb_header-fsrtlregisteruncprovider.md). There can be multiple UNC providers registered with MUP.

The prefix resolution operation serves two purposes:

* The name-based operation that resulted in the prefix resolution is routed to the provider that claims the prefix. If successful, MUP ensures that subsequent handle-based operations (IRP_MJ_READ and IRP_MJ_WRITE, for example) go to the same provider completely bypassing MUP.

* The provider and the prefix that it claimed are entered in a prefix cache that is maintained by MUP. For subsequent name-based operations, MUP uses this prefix cache to determine whether a provider has already claimed a prefix before MUP attempts to perform a prefix resolution. Each entry in this prefix cache is subject to a timeout (referred to as TTL) once it is added to the cache. An entry is thrown away after this timeout expires, at which point of time, MUP will perform prefix resolution again for this prefix on a subsequent name-based operation.

## -ioctlparameters

### -ioctl-major-code

IOCTL_REDIR_QUERY_PATH

### -input-buffer

**IrpSp->Parameters.DeviceIoControl.Type3InputBuffer** is set to a [**QUERY_PATH_REQUEST**](ns-ntifs-query_path_request.md) data structure that contains the request.

### -input-buffer-length

Length of the input buffer, in bytes, which must be at least ```sizeof(QUERY_PATH_REQUEST)```.

### -output-buffer

**IRP->UserBuffer** is set to a [**QUERY_PATH_RESPONSE**](ns-ntifs-query_path_response.md) data structure that contains the response.

### -output-buffer-length

Length of the output buffer, in bytes, which must be at least ```sizeof(QUERY_PATH_RESPONSE)```.

### -in-out-buffer

n/a

### -inout-buffer-length

n/a

### -status-block

The **Status** member is set to STATUS_SUCCESS on success if the \\\server\share prefix name is recognized or to an appropriate NTSTATUS value, such as one of the following:  

| Status code | Meaning |
| ---------- | ------- |
| STATUS_BAD_NETWORK_NAME | The specified share name cannot be found on the remote server. The machine name (\\\server, for example) is valid, but the specified share name cannot be found on the remote server. |
| STATUS_BAD_NETWORK_PATH | The network path cannot be located. The machine name (\\\server, for example) is not valid or the network redirector cannot resolve the machine name (using whatever name resolution mechanisms are available). |
| STATUS_INSUFFICIENT_RESOURCES | There were insufficient resources available to allocate memory for buffers. |
| STATUS_INVALID_DEVICE_REQUEST | An IOCTL_REDIR_QUERY_PATH_EX request should only come from MUP and the **RequestorMode** member of the IRP structure should always be **KernelMode**. This error code is returned if the requester mode of the calling thread was not **KernelMode**. |
| STATUS_INVALID_PARAMETER | The **PathNameLength** member in the [**QUERY_PATH_REQUEST**](ns-ntifs-query_path_request.md) structure exceeds the maximum allowable length, UNICODE_STRING_MAX_BYTES, for a Unicode string. |
| STATUS_LOGON_FAILURE or STATUS_ACCESS_DENIED | If the prefix resolution operation failed due to invalid or incorrect credentials, the provider should return the exact error code returned by the remote server; these error codes must not be translated to STATUS_BAD_NETWORK_NAME or STATUS_BAD_NETWORK_PATH. Error codes like STATUS_LOGON_FAILURE and STATUS_ACCESS_DENIED serve as a feedback mechanism to the user and indicate the requirement to use appropriate credentials. These error codes are also used in certain cases to prompt the user automatically for credentials. Without these error codes, the user might assume that the machine is not accessible. |

If the network redirector is unable to resolve a prefix, it must return an NTSTATUS code that closely matches the intended semantics from the above list of recommended NTSTATUS codes. A network redirector must not return the actual encountered error (STATUS_CONNECTION_REFUSED, for example) directly to MUP if the NTSTATUS code is not from the above list.

## -remarks

Network redirectors should only honor kernel-mode senders of this IOCTL, by verifying that **Irp->RequestorMode** is **KernelMode**.

Note that IOCTL_REDIR_QUERY_PATH is a METHOD_NEITHER IOCTL. This means that the input and output buffers might not be at the same address. A common mistake by UNC providers is to assume that the input buffer and the output buffer are the same and to use the input buffer pointer to provide the response.

When a UNC provider receives an IOCTL_REDIR_QUERY_PATH request, it has to determine whether it can handle the UNC path specified in the **FilePathName** member of the [**QUERY_PATH_REQUEST**](ns-ntifs-query_path_request.md) structure. If so, it has to update the **LengthAccepted** member of the [**QUERY_PATH_RESPONSE**](ns-ntifs-query_path_response.md) structure with the length, in bytes, of the prefix it has claimed and complete the IRP with STATUS_SUCCESS. If the provider cannot handle the UNC path specified, it must fail the IOCTL_REDIR_QUERY_PATH request with an appropriate NTSTATUS error code and must not update the **LengthAccepted** member of the **QUERY_PATH_RESPONSE** structure. Providers must not modify any of the other members or the **FilePathName** string under any condition.

The length of the prefix claimed by the provider depends on an individual UNC provider. Most providers usually claim the \\\\*servername*\\*sharename* part of a path of the form \\\\*servername*\\*sharename*\\*path*. For example, if a provider claimed \\\\*server*\\*public*  given a path \\\\*server*\\*public*\\*dir1*\\*dir2*, all name-based operations for the prefix \\\\*server*\\*public* (\\\\*server*\\*public*\\*file1*, for example) will be routed to that provider automatically without any prefix resolution because the prefix is already in the prefix cache. However, a path with the prefix \\\\*server*\\*marketing*\\*presentation* will go through prefix resolution.

If a network redirector claims a server name (\\\\*server*, for example), all requests for shares on this server will go to this network redirector. This behavior is only acceptable if there is no possibility of another share on the same server being accessed by a different network redirector. For example, a network redirector that claims \\\\*server* of a UNC path will prevent access by other network redirectors to other shares on this server (WebDAV access to \\\\*server*\\*web*, for example).

For more information, see the following articles:

* [Support for UNC Naming and MUP](/windows-hardware/drivers/ifs/support-for-unc-naming-and-mup)

* [MUP Changes in Microsoft Windows Vista](/windows-hardware/drivers/ifs/mup-changes-in-microsoft-windows-vista)

## -see-also

[**FsRtlDeregisterUncProvider**](nf-ntifs-fsrtlderegisteruncprovider.md)

[**FsRtlRegisterUncProvider**](nf-ntifs-_fsrtl_advanced_fcb_header-fsrtlregisteruncprovider.md)

[**FsRtlRegisterUncProviderEx**](nf-ntifs-_fsrtl_advanced_fcb_header-fsrtlregisteruncproviderex.md)

[**IOCTL_REDIR_QUERY_PATH_EX**](ni-ntifs-ioctl_redir_query_path_ex.md)
