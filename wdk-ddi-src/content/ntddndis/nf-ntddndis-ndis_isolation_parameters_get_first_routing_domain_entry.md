---
UID: NF:ntddndis.NDIS_ISOLATION_PARAMETERS_GET_FIRST_ROUTING_DOMAIN_ENTRY
title: NDIS_ISOLATION_PARAMETERS_GET_FIRST_ROUTING_DOMAIN_ENTRY macro (ntddndis.h)
description: The NDIS_ISOLATION_PARAMETERS_GET_FIRST_ROUTING_DOMAIN_ENTRY macro is used to access the first NDIS_ROUTING_DOMAIN_ENTRY that is specified by an NDIS_ISOLATION_PARAMETERS structure.
tech.root: netvista
ms.date: 04/17/2018
keywords: ["NDIS_ISOLATION_PARAMETERS_GET_FIRST_ROUTING_DOMAIN_ENTRY macro"]
ms.keywords: NDIS_ISOLATION_PARAMETERS_GET_FIRST_ROUTING_DOMAIN_ENTRY
req.header: ntddndis.h
req.include-header: ndis.h
req.target-type: Desktop
req.target-min-winverclnt: Supported in NDIS 6.40 and later.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.lib: 
req.dll: 
req.irql: 
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
targetos: Windows
returns-override: true
f1_keywords:
 - NDIS_ISOLATION_PARAMETERS_GET_FIRST_ROUTING_DOMAIN_ENTRY
 - ntddndis/NDIS_ISOLATION_PARAMETERS_GET_FIRST_ROUTING_DOMAIN_ENTRY
topic_type:
 - apiref
api_type:
 - HeaderDef
api_location:
 - ntddndis.h
api_name:
 - NDIS_ISOLATION_PARAMETERS_GET_FIRST_ROUTING_DOMAIN_ENTRY
---

# NDIS_ISOLATION_PARAMETERS_GET_FIRST_ROUTING_DOMAIN_ENTRY macro


## -description

The **NDIS_ISOLATION_PARAMETERS_GET_FIRST_ROUTING_DOMAIN_ENTRY** macro is used to access the first [**NDIS_ROUTING_DOMAIN_ENTRY**](ns-ntddndis-_ndis_routing_domain_entry.md) that is specified by an [**NDIS_ISOLATION_PARAMETERS**](ns-ntddndis-_ndis_isolation_parameters.md) structure.

## -parameters

### -param _MultiTenancyInfo_

A pointer to an **NDIS_ISOLATION_PARAMETERS** structure.

## -returns

The **NDIS_ISOLATION_PARAMETERS_GET_FIRST_ROUTING_DOMAIN_ENTRY** macro returns a pointer to the first [**NDIS_ROUTING_DOMAIN_ENTRY**](ns-ntddndis-_ndis_routing_domain_entry.md) element in the array.

## -remarks

## -see-also

[**NDIS_ISOLATION_PARAMETERS**](ns-ntddndis-_ndis_isolation_parameters.md)

[**NDIS_ROUTING_DOMAIN_ENTRY**](ns-ntddndis-_ndis_routing_domain_entry.md)

