---
UID: NF:fwpmk.FwpmConnectionDestroyEnumHandle0
tech.root: netvista
title: FwpmConnectionDestroyEnumHandle0
ms.date: 06/04/2024
targetos: Windows
description: The FwpmConnectionDestroyEnumHandle0 function frees a handle returned by FwpmConnectionCreateEnumHandle0.
prerelease: false
req.assembly: 
req.construct-type: function
req.ddi-compliance: 
req.dll: 
req.header: fwpmk.h
req.idl: 
req.include-header: 
req.irql: <= PASSIVE_LEVEL
req.kmdf-ver: 
req.lib: fwpkclnt.lib
req.max-support: 
req.namespace: 
req.redist: 
req.target-min-winverclnt: Available starting with Windows Vista.
req.target-min-winversvr: 
req.target-type: Universal
req.type-library: 
req.umdf-ver: 
req.unicode-ansi: 
topic_type:
 - apiref
api_type:
 - HeaderDef
api_location:
 - fwpmk.h
api_name:
 - FwpmConnectionDestroyEnumHandle0
f1_keywords:
 - FwpmConnectionDestroyEnumHandle0
 - fwpmk/FwpmConnectionDestroyEnumHandle0
dev_langs:
 - c++
helpviewer_keywords:
 - FwpmConnectionDestroyEnumHandle0
---

## -description

The **FwpmConnectionDestroyEnumHandle0** function frees a handle returned by **[FwpmConnectionCreateEnumHandle0](nf-fwpmk-fwpmconnectioncreateenumhandle0.md)**.

## -parameters

### -param engineHandle [in]

Handle for an open session to the filter engine. Call **[FwpmEngineOpen0](nf-fwpmk-fwpmengineopen0.md)** to open a session to the filter engine.

### -param enumHandle [in]

Handle of a connection object enumeration created by a call to **[FwpmProviderContextCreateEnumHandle0](nf-fwpmk-fwpmprovidercontextcreateenumhandle0.md)**.

## -returns

| Return code/value | Description |
| --- | --- |
| **ERROR_SUCCESS**<br>0 | The enumerator was successfully deleted. |
| **FWP_E_\* error code**<br>0x80320001—0x80320039 | A Windows Filtering Platform (WFP) specific error. See [WFP Error Codes](/windows/win32/fwp/wfp-error-codes) for details. |
| **RPC_\* error code**<br>0x80010001—0x80010122 | Failure to communicate with the remote or local firewall engine. |
| **Other NTSTATUS codes** | An error occurred. |

## -remarks

## -see-also

- **[FwpmConnectionCreateEnumHandle0](nf-fwpmk-fwpmconnectioncreateenumhandle0.md)**
- **[FwpmEngineOpen0](nf-fwpmk-fwpmengineopen0.md)**
- **[FwpmProviderContextCreateEnumHandle0](nf-fwpmk-fwpmprovidercontextcreateenumhandle0.md)**
- [WFP Error Codes](/windows/win32/fwp/wfp-error-codes)
