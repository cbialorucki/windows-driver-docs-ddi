---
UID: NF:netadapter.NetAdapterGetNetLuid
title: NetAdapterGetNetLuid function (netadapter.h)
description: Retrieves the NET_LUID that is assigned to a network adapter.
tech.root: netvista
ms.date: 03/30/2022
keywords: ["NetAdapterGetNetLuid function"]
ms.keywords: NetAdapterGetNetLuid
req.header: netadapter.h
req.include-header: netadaptercx.h
req.target-type: Universal
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 1.21
req.umdf-ver: 2.33 
req.lib: 
req.dll: 
req.irql: PASSIVE_LEVEL
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.alt-api: 
req.alt-loc: 
req.typenames: NetAdapterGetNetLuid
targetos: Windows
f1_keywords:
 - NetAdapterGetNetLuid
 - netadapter/NetAdapterGetNetLuid
topic_type:
 - apiref
api_type:
 - HeaderDef
api_location:
 - netadapter.h
api_name:
 - NetAdapterGetNetLuid
---

# NetAdapterGetNetLuid function


## -description

Retrieves the NET_LUID that is assigned to a network adapter.

## -parameters

### -param Adapter [_In_]

The network adapter object that the client created in a prior call to [NetAdapterCreate](nf-netadapter-netadaptercreate.md).

## -returns

Returns the NET_LUID for the specified NETADAPTER object.

## -remarks

## -see-also

[NET_LUID](/windows/win32/api/ifdef/ns-ifdef-net_luid_lh)
