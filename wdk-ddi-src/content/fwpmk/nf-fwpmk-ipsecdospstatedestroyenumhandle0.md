---
UID: NF:fwpmk.IPsecDospStateDestroyEnumHandle0
tech.root: netvista
title: IPsecDospStateDestroyEnumHandle0
ms.date: 06/20/2024
targetos: Windows
description: The IPsecDospStateDestroyEnumHandle0 function frees a handle returned by IPsecDospStateCreateEnumHandle0.
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
 - IPsecDospStateDestroyEnumHandle0
f1_keywords:
 - IPsecDospStateDestroyEnumHandle0
 - fwpmk/IPsecDospStateDestroyEnumHandle0
dev_langs:
 - c++
helpviewer_keywords:
 - IPsecDospStateDestroyEnumHandle0
---

## -description

The **IPsecDospStateDestroyEnumHandle0** function frees a handle returned by **[IPsecDospStateCreateEnumHandle0](nf-fwpmk-ipsecdospstatecreateenumhandle0.md)**.

## -parameters

### -param engineHandle [in]

Handle for an open session to the filter engine. Call **[FwpmEngineOpen0](nf-fwpmk-fwpmengineopen0.md)** to open a session to the filter engine.

### -param enumHandle [in, out]

Handle of the enumeration to destroy. Previously created by a call to **[IPsecDospStateCreateEnumHandle0](nf-fwpmk-ipsecdospstatecreateenumhandle0.md)**.

## -returns

| Return code/value | Description |
|---|---|
| **ERROR_SUCCESS**<br>0 | The enumeration was deleted successfully. |
| **FWP_E_\* error code**<br>0x80320001—0x80320039 | A Windows Filtering Platform (WFP) specific error. See [WFP Error Codes](/windows/win32/fwp/wfp-error-codes) for details. |
| **RPC_\* error code**<br>0x80010001—0x80010122 | Failure to communicate with the remote or local firewall engine. |
| **Other NTSTATUS codes** | An error occurred. |

## -remarks

**IPsecDospStateDestroyEnumHandle0** is a specific implementation of **IPsecDospStateDestroyEnumHandle**. See[WFP Version-Independent Names and Targeting Specific Versions of Windows](/windows/desktop/FWP/wfp-version-independent-names-and-targeting-specific-versions-of-windows) for more information.

## -see-also

- **[IPsecDospStateCreateEnumHandle0](nf-fwpmk-ipsecdospstatecreateenumhandle0.md)**
- **[FwpmEngineOpen0](nf-fwpmk-fwpmengineopen0.md)**
- **[IPsecDospStateCreateEnumHandle0](nf-fwpmk-ipsecdospstatecreateenumhandle0.md)**
- [WFP Error Codes](/windows/win32/fwp/wfp-error-codes)
- [WFP Version-Independent Names and Targeting Specific Versions of Windows](/windows/desktop/FWP/wfp-version-independent-names-and-targeting-specific-versions-of-windows)
