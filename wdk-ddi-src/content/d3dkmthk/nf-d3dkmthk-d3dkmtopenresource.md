---
UID: NF:d3dkmthk.D3DKMTOpenResource
title: D3DKMTOpenResource function (d3dkmthk.h)
description: The D3DKMTOpenResource function opens a shared resource.
old-location: display\d3dkmtopenresource.htm
ms.date: 05/10/2018
keywords: ["D3DKMTOpenResource function"]
ms.keywords: D3DKMTOpenResource, D3DKMTOpenResource function [Display Devices], OpenGL_Functions_ba035fe1-7970-45fc-a1c3-adddf285abd1.xml, d3dkmthk/D3DKMTOpenResource, display.d3dkmtopenresource
req.header: d3dkmthk.h
req.include-header: D3dkmthk.h
req.target-type: Universal
req.target-min-winverclnt: Windows Vista
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
req.lib: Gdi32.lib
req.dll: Gdi32.dll
req.irql: 
targetos: Windows
tech.root: display
req.typenames: 
f1_keywords:
 - D3DKMTOpenResource
 - d3dkmthk/D3DKMTOpenResource
topic_type:
 - APIRef
 - kbSyntax
api_type:
 - DllExport
api_location:
 - Gdi32.dll
 - API-MS-Win-DX-D3DKmt-l1-1-0.dll
 - API-MS-Win-DX-D3DKmt-l1-1-1.dll
 - API-MS-Win-DX-D3DKMT-L1-1-2.dll
api_name:
 - D3DKMTOpenResource
---

# D3DKMTOpenResource function


## -description

The <b>D3DKMTOpenResource</b> function opens a shared resource.

## -parameters

### -param unnamedParam1

*pData* [in, out]

A pointer to a <a href="/windows-hardware/drivers/ddi/d3dkmthk/ns-d3dkmthk-_d3dkmt_openresource">D3DKMT_OPENRESOURCE</a> structure that contains parameters for opening a shared resource.

## -returns

<b>D3DKMTOpenResource</b> returns one of the following values:

|Return code|Description|
|--- |--- |
|STATUS_SUCCESS|The resource was successfully opened.|
|STATUS_DEVICE_REMOVED|The graphics adapter was stopped or the display device was reset.|
|STATUS_INVALID_PARAMETER|Parameters were validated and determined to be incorrect.|

This function might also return other <a href="/windows-hardware/drivers/kernel/ntstatus-values">NTSTATUS</a> values.

## -see-also

<a href="/windows-hardware/drivers/ddi/d3dkmthk/nf-d3dkmthk-d3dkmtqueryresourceinfo">D3DKMTQueryResourceInfo</a>

<a href="/windows-hardware/drivers/ddi/d3dkmthk/ns-d3dkmthk-_d3dkmt_openresource">D3DKMT_OPENRESOURCE</a>
