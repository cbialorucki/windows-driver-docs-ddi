---
UID: NF:d3dkmthk.D3DKMTCheckOcclusion
title: D3DKMTCheckOcclusion function (d3dkmthk.h)
description: The D3DKMTCheckOcclusion function verifies whether the client area of a graphics window is occluded.
old-location: display\d3dkmtcheckocclusion.htm
ms.date: 02/23/2022
keywords: ["D3DKMTCheckOcclusion function"]
ms.keywords: D3DKMTCheckOcclusion, D3DKMTCheckOcclusion callback function [Display Devices], OpenGL_Functions_a73b8485-971d-47a7-bc42-77bd709c5a74.xml, PFND3DKMT_CHECKOCCLUSION, PFND3DKMT_CHECKOCCLUSION callback, d3dkmthk/D3DKMTCheckOcclusion, display.d3dkmtcheckocclusion
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
 - D3DKMTCheckOcclusion
 - d3dkmthk/D3DKMTCheckOcclusion
topic_type:
 - APIRef
 - kbSyntax
api_type:
 - DllExport
api_location:
 - Gdi32.dll
api_name:
 - D3DKMTCheckOcclusion
---

# D3DKMTCheckOcclusion function

## -description

The **D3DKMTCheckOcclusion** function verifies whether the client area of a window is occluded.

## -parameters

### -param unnamedParam1 [in]

A pointer to a [D3DKMT_CHECKOCCLUSION](ns-d3dkmthk-_d3dkmt_checkocclusion.md) structure that describes parameters for checking occlusion.

## -returns

**D3DKMTCheckOcclusion** returns one of the following values:

| Return code | Description |
|--|--|
| STATUS_SUCCESS | The client area of the window is not occluded. |
| STATUS_GRAPHICS_PRESENT_OCCLUDED | The client area of the window is occluded. |
| STATUS_INVALID_PARAMETER | Parameters were validated and determined to be incorrect. |

This function might also return other **NTSTATUS** values.

## -remarks

The handle to the window that is checked for occlusion must be valid. A window is not occluded if a part of its client area lies on an unowned video present network (VidPn) source, if its client area is an empty rectangular area (RECT), or if desktop composition is running.

## -see-also

[D3DKMT_CHECKOCCLUSION](ns-d3dkmthk-_d3dkmt_checkocclusion.md)
