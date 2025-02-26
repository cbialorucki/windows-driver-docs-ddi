---
UID: NF:netwakesource.NetWakeSourceGetMediaChangeParameters
title: NetWakeSourceGetMediaChangeParameters function (netwakesource.h)
description: The NetWakeSourceGetMediaChangeParameters function gets parameters for a media change wake source.
tech.root: netvista
ms.date: 04/01/2022
keywords: ["NetWakeSourceGetMediaChangeParameters function"]
ms.keywords: NetWakeSourceGetMediaChangeParameters
req.header: netwakesource.h
req.include-header: netadaptercx.h 
req.target-type: Universal
req.target-min-winverclnt: Windows 10, version 2004
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 2.33 
req.lib: netadaptercxstub.lib
req.dll: 
req.irql: PASSIVE_LEVEL
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
targetos: Windows
ms.custom: Vb
f1_keywords:
 - NetWakeSourceGetMediaChangeParameters
 - netwakesource/NetWakeSourceGetMediaChangeParameters
topic_type:
 - apiref
api_type:
 - LibDef
api_location:
 - netadaptercxstub.lib
api_name:
 - NetWakeSourceGetMediaChangeParameters
---

# NetWakeSourceGetMediaChangeParameters function


## -description

The **NetWakeSourceGetMediaChangeParameters** function gets parameters for a media change wake source.

## -parameters

### -param WakeSource [_In_]

A NETWAKESOURCE object that represents this media change wake source.

### -param Parameters [_Inout_]

A pointer to a driver-allocated and initialized [**NET_WAKE_SOURCE_MEDIA_CHANGE_PARAMETERS**](../netwakesource/ns-netwakesource-_net_wake_source_media_change_parameters.md) structure that receives the media change parameters.


## -remarks

Call [**NET_WAKE_SOURCE_MEDIA_CHANGE_PARAMETERS_INIT**](../netwakesource/nf-netwakesource-net_wake_source_media_change_parameters_init.md) to initialize the [**NET_WAKE_SOURCE_MEDIA_CHANGE_PARAMETERS**](../netwakesource/ns-netwakesource-_net_wake_source_media_change_parameters.md) structure before calling this function.

The client driver must only call **NetWakeSourceGetMediaChangeParameters** during a power transition, typically from its *[EVT_WDF_DEVICE_ARM_WAKE_FROM_SX](../wdfdevice/nc-wdfdevice-evt_wdf_device_arm_wake_from_sx.md)*, *[EVT_WDF_DEVICE_ARM_WAKE_FROM_S0](../wdfdevice/nc-wdfdevice-evt_wdf_device_arm_wake_from_s0.md)*, or *[EVT_NET_DEVICE_PREVIEW_WAKE_SOURCE](../netdevice/nc-netdevice-evt_net_device_preview_wake_source.md)* callback function. Otherwise, the call results in a system bugcheck.

## -see-also

[Configuring power management](/windows-hardware/drivers/netcx/configuring-power-management)

[**NET_WAKE_SOURCE_MEDIA_CHANGE_PARAMETERS**](../netwakesource/ns-netwakesource-_net_wake_source_media_change_parameters.md)

[**NET_WAKE_SOURCE_MEDIA_CHANGE_PARAMETERS_INIT**](../netwakesource/nf-netwakesource-net_wake_source_media_change_parameters_init.md)
