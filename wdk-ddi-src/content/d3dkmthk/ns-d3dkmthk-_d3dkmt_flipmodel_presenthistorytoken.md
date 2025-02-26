---
UID: NS:d3dkmthk._D3DKMT_FLIPMODEL_PRESENTHISTORYTOKEN
title: D3DKMT_FLIPMODEL_PRESENTHISTORYTOKEN (d3dkmthk.h)
description: Learn more about the D3DKMT_FLIPMODEL_PRESENTHISTORYTOKEN structure.
ms.date: 04/10/2024
keywords: ["D3DKMT_FLIPMODEL_PRESENTHISTORYTOKEN structure"]
ms.keywords: D3DKMT_FLIPMODEL_PRESENTHISTORYTOKEN, D3DKMT_FLIPMODEL_PRESENTHISTORYTOKEN structure [Display Devices], OpenGL_Structs_819c22ef-0bae-476a-9cbc-0169cd7fc82f.xml, _D3DKMT_FLIPMODEL_PRESENTHISTORYTOKEN, d3dkmthk/D3DKMT_FLIPMODEL_PRESENTHISTORYTOKEN, display.d3dkmt_flipmodel_presenthistorytoken
req.header: d3dkmthk.h
req.include-header: D3dkmthk.h
req.target-type: Windows
req.target-min-winverclnt: Windows 7
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
tech.root: display
req.typenames: D3DKMT_FLIPMODEL_PRESENTHISTORYTOKEN
f1_keywords:
 - _D3DKMT_FLIPMODEL_PRESENTHISTORYTOKEN
 - d3dkmthk/_D3DKMT_FLIPMODEL_PRESENTHISTORYTOKEN
 - D3DKMT_FLIPMODEL_PRESENTHISTORYTOKEN
 - d3dkmthk/D3DKMT_FLIPMODEL_PRESENTHISTORYTOKEN
topic_type:
 - APIRef
 - kbSyntax
api_type:
 - HeaderDef
api_location:
 - d3dkmthk.h
api_name:
 - _D3DKMT_FLIPMODEL_PRESENTHISTORYTOKEN
 - D3DKMT_FLIPMODEL_PRESENTHISTORYTOKEN
---

# D3DKMT_FLIPMODEL_PRESENTHISTORYTOKEN structure

## -description

The **D3DKMT_FLIPMODEL_PRESENTHISTORYTOKEN** structure identifies a flip present-history operation.

## -struct-fields

### -field FenceValue

[in] A 64-bit value that specifies the fence value that is used for the flip.

### -field hLogicalSurface

[in] A 64-bit value that specifies the handle to a logical surface.

### -field dxgContext

The DirectX graphics context.

### -field VidPnSourceId

The zero-based identification number of the video present source in a path of a video present network (VidPN) topology that the monitor is connected to.

### -field SwapChainIndex

[in] The index of the surface in the swap chain that is used for the flip.

### -field PresentLimitSemaphoreId

[in] A 64-bit value that identifies the present-limit semaphore.

### -field FlipInterval

[in] A [**D3DDDI_FLIPINTERVAL_TYPE**](../d3dukmdt/ne-d3dukmdt-d3dddi_flipinterval_type.md)-typed value that indicates the flip interval (that is, if the flip occurs after zero, one, two, three, or four vertical syncs).

### -field Flags

[in] A [**D3DKMT_FLIPMODEL_PRESENTHISTORYTOKENFLAGS**](ns-d3dkmthk-_d3dkmt_flipmodel_presenthistorytokenflags.md) structure that identifies, in bit-field flags, attributes of a flip present-history operation.

### -field hCompSurf

This member is reserved and should be set to zero.

Supported starting with Windows 8.

### -field compSurfLuid

LUID for the composition surface.

### -field confirmationCookie

Confirmation cookie.

### -field CompositionSyncKey

This member is reserved and should be set to zero.

Supported starting with Windows 8.

### -field RemainingTokens

This member is reserved and should be set to zero.

Supported starting with Windows 8.

### -field ScrollRect

This member is reserved and should be set to zero.

Supported starting with Windows 8.

### -field ScrollOffset

This member is reserved and should be set to zero.

Supported starting with Windows 8.

### -field PresentCount

This member is reserved and should be set to zero.

Supported starting with Windows 8.

### -field RevealColor[4]

This member is reserved and should be set to zero.

Supported starting with Windows 8.

### -field Rotation

This member is reserved and should be set to zero.

Supported starting with Windows 8.

### -field ScatterBlts

This member is reserved and should be set to zero.

Supported starting with Windows 8.

### -field hSyncObject

This member is reserved and should be set to zero.

Supported starting with Windows 8.

### -field InkCookie

Cookie for token's ink.

### -field SourceRect

The source rectangle.

### -field DestWidth

The destination width.

### -field DestHeight

The destination height.

### -field TargetRect

The target rectangle.

### -field Transform[6]

Transformation matrix.

### -field CustomDuration

Custom duration of the transition.

### -field CustomDurationFlipInterval

Custom interval of the transition.

### -field PlaneIndex

Index of the plane.

### -field ColorSpace

The color space of the data.

### -field DirtyRegions

[in] A [**D3DKMT_DIRTYREGIONS**](ns-d3dkmthk-_d3dkmt_dirtyregions.md) structure that identifies the active rectangles (dirty regions) of the flip surface.

### -field HDRMetaDataHDR10

### -field HDRMetaDataHDR10Plus

### -field HDRMetaDataType

## -see-also

[**D3DKMT_FLIPMODEL_PRESENTHISTORYTOKENFLAGS**](ns-d3dkmthk-_d3dkmt_flipmodel_presenthistorytokenflags.md)

[**D3DDDI_FLIPINTERVAL_TYPE**](..\d3dukmdt\ne-d3dukmdt-d3dddi_flipinterval_type.md)

[**D3DKMT_PRESENTHISTORYTOKEN**](ns-d3dkmthk-_d3dkmt_presenthistorytoken.md)

[**D3DKMT_DIRTYREGIONS**](ns-d3dkmthk-_d3dkmt_dirtyregions.md)
