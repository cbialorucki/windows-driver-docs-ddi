---
UID: NC:dispmprt.DXGKDDI_RESET_DEVICE
title: DXGKDDI_RESET_DEVICE (dispmprt.h)
description: The DxgkDdiResetDevice function sets a display adapter to VGA character mode (80 x 50).
old-location: display\dxgkddiresetdevice.htm
tech.root: display
ms.date: 05/10/2018
keywords: ["DXGKDDI_RESET_DEVICE callback function"]
ms.keywords: DXGKDDI_RESET_DEVICE, DXGKDDI_RESET_DEVICE callback, DmFunctions_70e9fe99-65be-47a5-bb9a-fac4e10d3ae9.xml, DxgkDdiResetDevice, DxgkDdiResetDevice callback function [Display Devices], display.dxgkddiresetdevice, dispmprt/DxgkDdiResetDevice
req.header: dispmprt.h
req.include-header: 
req.target-type: Desktop
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
req.lib: 
req.dll: 
req.irql: Any level (see Remarks section)
targetos: Windows
req.typenames: 
f1_keywords:
 - DXGKDDI_RESET_DEVICE
 - dispmprt/DXGKDDI_RESET_DEVICE
topic_type:
 - APIRef
 - kbSyntax
api_type:
 - UserDefined
api_location:
 - dispmprt.h
api_name:
 - DXGKDDI_RESET_DEVICE
---

# DXGKDDI_RESET_DEVICE callback function


## -description

The <i>DxgkDdiResetDevice</i> function sets a display adapter to VGA character mode (80 x 50).

## -parameters

### -param MiniportDeviceContext [in]


A handle to a context block associated with a display adapter. The display miniport driver's <a href="/windows-hardware/drivers/ddi/dispmprt/nc-dispmprt-dxgkddi_add_device">DxgkDdiAddDevice</a> function previously provided this handle to the DirectX graphics kernel subsystem.

## -remarks

The HAL calls this function so it can display information on the screen during hibernation, bug checks, and the like.

<i>DxgkDdiResetDevice</i> can be called at any IRQL, so it must be in nonpageable memory. <i>DxgkDdiResetDevice</i> must not call any code that is in pageable memory and must not manipulate any data that is in pageable memory.

