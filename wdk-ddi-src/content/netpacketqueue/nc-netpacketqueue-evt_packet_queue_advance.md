---
UID: NC:netpacketqueue.EVT_PACKET_QUEUE_ADVANCE
title: EVT_PACKET_QUEUE_ADVANCE (netpacketqueue.h)
description: The EvtPacketQueueAdvance callback function is implemented by the client driver to process transmit or receive packets provided by NetAdapterCx.
tech.root: netvista
ms.date: 04/01/2022
keywords: ["EVT_PACKET_QUEUE_ADVANCE callback function"]
req.header: netpacketqueue.h
req.include-header: netadaptercx.h 
req.target-type: Universal
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 1.27
req.umdf-ver: 2.33 
req.lib: 
req.dll: 
req.irql: <= DISPATCH_LEVEL
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
targetos: Windows
ms.custom: RS5
f1_keywords:
 - EVT_PACKET_QUEUE_ADVANCE
 - netpacketqueue/EVT_PACKET_QUEUE_ADVANCE
topic_type:
 - apiref
api_type:
 - UserDefined
api_location:
 - netpacketqueue.h
api_name:
 - EVT_PACKET_QUEUE_ADVANCE
---

# EVT_PACKET_QUEUE_ADVANCE callback function


## -description

The *EvtPacketQueueAdvance* callback function is implemented by the client driver to process transmit or receive packets provided by NetAdapterCx.

## -parameters

### -param PacketQueue [_In_]

A handle to a packet queue.

## -prototype

```C++
//Declaration

EVT_PACKET_QUEUE_ADVANCE EvtPacketQueueAdvance; 

// Definition

VOID EvtPacketQueueAdvance 
(
	NETPACKETQUEUE PacketQueue
)
{...}

```

## -remarks

Register this callback function in your *EVT_NET_ADAPTER_CREATE_TX(RX)QUEUE* callback. Set the appropriate member of a [**NET_PACKET_QUEUE_CONFIG**](ns-netpacketqueue-_net_packet_queue_config.md) structure when you are initializing the structure with [**NET_PACKET_QUEUE_CONFIG_INIT**](nf-netpacketqueue-net_packet_queue_config_init.md), then call **NetTx(Rx)QueueCreate**.

NetAdapterCx serializes this callback function along with the packet queue's [*EVT_PACKET_QUEUE_CANCEL*](nc-netpacketqueue-evt_packet_queue_cancel.md) and [*EVT_PACKET_QUEUE_SET_NOTIFICATION_ENABLED*](nc-netpacketqueue-evt_packet_queue_set_notification_enabled.md) callback functions.

For more info and a diagram showing the NetAdapterCx data path polling model, see [Transmit and receive queues](/windows-hardware/drivers/netcx/transmit-and-receive-queues). For more info about ring buffer usage, see [Using the ring buffer](/windows-hardware/drivers/netcx/using-the-ring-buffer).

For an example of implementing this callback for a transmit queue, see [Sending network data with net rings](/windows-hardware/drivers/netcx/sending-network-data-with-net-rings). For an example of implementing this callback for a receive queue, see [Receiving network data with net rings](/windows-hardware/drivers/netcx/receiving-network-data-with-net-rings).

## -see-also

[*EVT_NET_ADAPTER_CREATE_RXQUEUE*](../netadapter/nc-netadapter-evt_net_adapter_create_rxqueue.md)

[*EVT_NET_ADAPTER_CREATE_TXQUEUE*](../netadapter/nc-netadapter-evt_net_adapter_create_txqueue.md)

[**NetRxQueueCreate**](../netrxqueue/nf-netrxqueue-netrxqueuecreate.md)

[**NetTxQueueCreate**](../nettxqueue/nf-nettxqueue-nettxqueuecreate.md)

[*EVT_PACKET_QUEUE_START*](nc-netpacketqueue-evt_packet_queue_start.md)

[*EVT_PACKET_QUEUE_SET_NOTIFICATION_ENABLED*](nc-netpacketqueue-evt_packet_queue_set_notification_enabled.md)

[*EVT_PACKET_QUEUE_CANCEL*](nc-netpacketqueue-evt_packet_queue_cancel.md)

[*EVT_PACKET_QUEUE_STOP*](nc-netpacketqueue-evt_packet_queue_stop.md)
