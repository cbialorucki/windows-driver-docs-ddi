---
UID: NF:fwpmk.FwpmProviderGetByKey0
tech.root: netvista
title: FwpmProviderGetByKey0
ms.date: 06/14/2024
targetos: Windows
description: The FwpmProviderGetByKey0 function retrieves a provider.
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
 - FwpmProviderGetByKey0
f1_keywords:
 - FwpmProviderGetByKey0
 - fwpmk/FwpmProviderGetByKey0
dev_langs:
 - c++
helpviewer_keywords:
 - FwpmProviderGetByKey0
---

## -description

The **FwpmProviderGetByKey0** function retrieves a provider.

## -parameters

### -param engineHandle [in]

Handle for an open session to the filter engine. Call **[FwpmEngineOpen0](nf-fwpmk-fwpmengineopen0.md)** to open a session to the filter engine.

### -param key [in]

A runtime identifier for the desired object. This is the same GUID that was specified when the application called **[FwpmProviderAdd0](nf-fwpmk-fwpmprovideradd0.md)**.

### -param provider [out]

The provider information.

## -returns

| Return code/value | Description |
|---|---|
| **ERROR_SUCCESS**<br>0 | The provider was retrieved successfully. |
| **FWP_E_\* error code**<br>0x80320001—0x80320039 | A Windows Filtering Platform (WFP) specific error. See [WFP Error Codes](/windows/win32/fwp/wfp-error-codes) for details. |
| **RPC_\* error code**<br>0x80010001—0x80010122 | Failure to communicate with the remote or local firewall engine. |
| **Other NTSTATUS codes** | An error occurred. |

## -remarks

The caller must free the returned object by a call to **[FwpmFreeMemory0](nf-fwpmk-fwpmfreememory0.md)**.

The caller needs [FWPM_ACTRL_READ](/windows/desktop/FWP/access-right-identifiers) access to the provider. See [Access Control](/windows/desktop/FWP/access-control) for more information.

**FwpmProviderGetByKey0** is a specific implementation of **FwpmProviderGetByKey**. See [WFP Version-Independent Names and Targeting Specific Versions of Windows](/windows/desktop/FWP/wfp-version-independent-names-and-targeting-specific-versions-of-windows) for more information.

## -see-also

- **[FwpmEngineOpen0](nf-fwpmk-fwpmengineopen0.md)**
- **[FwpmProviderAdd0](nf-fwpmk-fwpmprovideradd0.md)**
- **[FwpmFreeMemory0](nf-fwpmk-fwpmfreememory0.md)**
- [FWPM_ACTRL_READ](/windows/desktop/FWP/access-right-identifiers)
- [FWPM_PROVIDER0](/windows/desktop/api/fwpmtypes/ns-fwpmtypes-fwpm_provider0)
- [WFP Error Codes](/windows/win32/fwp/wfp-error-codes)
- [Access Control](/windows/desktop/FWP/access-control)
- [WFP Version-Independent Names and Targeting Specific Versions of Windows](/windows/desktop/FWP/wfp-version-independent-names-and-targeting-specific-versions-of-windows)
