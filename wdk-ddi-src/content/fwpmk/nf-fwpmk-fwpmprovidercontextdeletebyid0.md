---
UID: NF:fwpmk.FwpmProviderContextDeleteById0
tech.root: netvista
title: FwpmProviderContextDeleteById0
ms.date: 06/12/2024
targetos: Windows
description: The FwpmProviderContextDeleteById0 function removes a provider context from the system.
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
 - FwpmProviderContextDeleteById0
f1_keywords:
 - FwpmProviderContextDeleteById0
 - fwpmk/FwpmProviderContextDeleteById0
dev_langs:
 - c++
helpviewer_keywords:
 - FwpmProviderContextDeleteById0
---

## -description

The **FwpmProviderContextDeleteById0** function removes a provider context from the system.

## -parameters

### -param engineHandle [in]

Handle for an open session to the filter engine. Call **[FwpmEngineOpen0](nf-fwpmk-fwpmengineopen0.md)** to open a session to the filter engine.

### -param id [in]

A runtime identifier for the object being removed from the system. This is the runtime identifier that was received from the system when the application called **[FwpmProviderContextAdd0](nf-fwpmk-fwpmprovidercontextadd0.md)** for this object.

## -returns

| Return code/value | Description |
|---|---|
| **ERROR_SUCCESS**<br>0 | The provider context was successfully deleted. |
| **FWP_E_\* error code**<br>0x80320001—0x80320039 | A Windows Filtering Platform (WFP) specific error. See [WFP Error Codes](/windows/win32/fwp/wfp-error-codes) for details. |
| **RPC_\* error code**<br>0x80010001—0x80010122 | Failure to communicate with the remote or local firewall engine. |
| **Other NTSTATUS codes** | An error occurred. |

## -remarks

This function cannot be called from within a read-only transaction, it fails with **FWP_E_INCOMPATIBLE_TXN**. See [Object Management](/windows/desktop/FWP/object-management) for more information about transactions.

This function can be called within a dynamic session if the corresponding object was added during the same session. If this function is called for an object that was added during a different dynamic session, it will fail with **FWP_E_WRONG_SESSION**. If this function is called for an object that was not added during a dynamic session, it fails with **FWP_E_DYNAMIC_SESSION_IN_PROGRESS**.

The caller needs [DELETE](/windows/desktop/SecAuthZ/standard-access-rights) access to the provider context. See [Access Control](/windows/desktop/FWP/access-control) for more information.

**FwpmProviderContextDeleteById0** is a specific implementation of **FwpmProviderContextDeleteById**. See [WFP Version-Independent Names and Targeting Specific Versions of Windows](/windows/desktop/FWP/wfp-version-independent-names-and-targeting-specific-versions-of-windows) for more information.

## -see-also

- **[FwpmEngineOpen0](nf-fwpmk-fwpmengineopen0.md)**
- **[FwpmProviderContextAdd0](nf-fwpmk-fwpmprovidercontextadd0.md)**
- [DELETE](/windows/desktop/SecAuthZ/standard-access-rights)
- [WFP Error Codes](/windows/win32/fwp/wfp-error-codes)
- [Object Management](/windows/desktop/FWP/object-management)
- [Access Control](/windows/desktop/FWP/access-control)
- [WFP Version-Independent Names and Targeting Specific Versions of Windows](/windows/desktop/FWP/wfp-version-independent-names-and-targeting-specific-versions-of-windows)
