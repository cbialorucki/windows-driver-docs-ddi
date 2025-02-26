---
UID: NF:nettxqueue.NetTxQueueNotifyMoreCompletedPacketsAvailable
title: NetTxQueueNotifyMoreCompletedPacketsAvailable function (nettxqueue.h)
description: The client driver calls NetTxQueueNotifyMoreCompletedPacketsAvailable to resume queue operations after NetAdapterCx calls the client's EVT_TXQUEUE_SET_NOTIFICATION_ENABLED event callback routine.
tech.root: netvista
ms.date: 04/01/2022
keywords: ["NetTxQueueNotifyMoreCompletedPacketsAvailable function"]
ms.keywords: NetTxQueueNotifyMoreCompletedPacketsAvailable
req.header: nettxqueue.h
req.include-header: netadaptercx.h
req.target-type: Universal
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 1.27
req.umdf-ver: 2.33 
req.lib: 
req.dll: 
req.irql: <= HIGH_LEVEL
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.alt-api: 
req.alt-loc: 
targetos: Windows
f1_keywords:
 - NetTxQueueNotifyMoreCompletedPacketsAvailable
 - nettxqueue/NetTxQueueNotifyMoreCompletedPacketsAvailable
topic_type:
 - apiref
api_type:
 - HeaderDef
api_location:
 - nettxqueue.h
api_name:
 - NetTxQueueNotifyMoreCompletedPacketsAvailable
---

# NetTxQueueNotifyMoreCompletedPacketsAvailable function


## -description

The client driver calls **NetTxQueueNotifyMoreCompletedPacketsAvailable** to resume queue operations after NetAdapterCx calls the client's [*EVT_PACKET_QUEUE_SET_NOTIFICATION_ENABLED*](../netpacketqueue/nc-netpacketqueue-evt_packet_queue_set_notification_enabled.md) event callback routine.

## -parameters

### -param PacketQueue [_In_]

A handle to a net transmit queue.

## -remarks

This function should only be called when polling is disabled.

After NetAdapterCx calls a client driver's [*EVT_PACKET_QUEUE_SET_NOTIFICATION_ENABLED*](../netpacketqueue/nc-netpacketqueue-evt_packet_queue_set_notification_enabled.md) event callback routine with *NotificationEnabled* set to **TRUE**, the client enables the queue's hardware interrupt. When the device generates a hardware interrupt, the client typically calls **NetTxQueueNotifyMoreCompletedPacketsAvailable** from its *[EVT_WDF_INTERRUPT_DPC](../wdfinterrupt/nc-wdfinterrupt-evt_wdf_interrupt_dpc.md) callback function, after it completes a pending [NET_PACKET](../packet/ns-packet-_net_packet.md) in the transmit queue's [**NET_RING**](../ring/ns-ring-_net_ring.md).

The client should only call **NetTxQueueNotifyMoreCompletedPacketsAvailable** once per enabling of the notification. If the most recent call to [*EVT_PACKET_QUEUE_SET_NOTIFICATION_ENABLED*](../netpacketqueue/nc-netpacketqueue-evt_packet_queue_set_notification_enabled.md) has *NotificationEnabled* set to **FALSE**, the client should avoid invoking **NetTxQueueNotifyMoreCompletedPacketsAvailable**. Because NetAdapterCx invokes *EVT_PACKET_QUEUE_SET_NOTIFICATION_ENABLED* repeatedly, the client may miss a few cases and call **NetTxQueueNotifyMoreCompletedPacketsAvailable** when *NotificationEnabled* is set to **FALSE**. In these cases, the call will be a no-op.

## -see-also

[*EVT_PACKET_QUEUE_ADVANCE*](../netpacketqueue/nc-netpacketqueue-evt_packet_queue_advance.md)

[*EVT_PACKET_QUEUE_SET_NOTIFICATION_ENABLED*](../netpacketqueue/nc-netpacketqueue-evt_packet_queue_set_notification_enabled.md)

