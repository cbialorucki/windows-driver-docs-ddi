---
UID: NS:windot11._DOT11_PROVISION_DISCOVERY_REQUEST_SEND_COMPLETE_PARAMETERS
title: _DOT11_PROVISION_DISCOVERY_REQUEST_SEND_COMPLETE_PARAMETERS (windot11.h)
description: The parameters for a provision discovery request send complete are specified in a DOT11_PROVISION_DISCOVERY_REQUEST_SEND_COMPLETE_PARAMETERS structure.
old-location: netvista\dot11_provision_discovery_request_send_complete_parameters.htm
tech.root: netvista
ms.date: 02/16/2018
keywords: ["DOT11_PROVISION_DISCOVERY_REQUEST_SEND_COMPLETE_PARAMETERS structure"]
ms.keywords: "*PDOT11_PROVISION_DISCOVERY_REQUEST_SEND_COMPLETE_PARAMETERS, DOT11_PROVISION_DISCOVERY_REQUEST_SEND_COMPLETE_PARAMETERS, DOT11_PROVISION_DISCOVERY_REQUEST_SEND_COMPLETE_PARAMETERS structure [Network Drivers Starting with Windows Vista], PDOT11_PROVISION_DISCOVERY_REQUEST_SEND_COMPLETE_PARAMETERS, PDOT11_PROVISION_DISCOVERY_REQUEST_SEND_COMPLETE_PARAMETERS structure pointer [Network Drivers Starting with Windows Vista], _DOT11_PROVISION_DISCOVERY_REQUEST_SEND_COMPLETE_PARAMETERS, netvista.dot11_provision_discovery_request_send_complete_parameters, windot11/DOT11_PROVISION_DISCOVERY_REQUEST_SEND_COMPLETE_PARAMETERS, windot11/PDOT11_PROVISION_DISCOVERY_REQUEST_SEND_COMPLETE_PARAMETERS"
req.header: windot11.h
req.include-header: Windot11.h
req.target-type: Windows
req.target-min-winverclnt: Supported starting with   Windows 8.
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
req.typenames: DOT11_PROVISION_DISCOVERY_REQUEST_SEND_COMPLETE_PARAMETERS, *PDOT11_PROVISION_DISCOVERY_REQUEST_SEND_COMPLETE_PARAMETERS
f1_keywords:
 - _DOT11_PROVISION_DISCOVERY_REQUEST_SEND_COMPLETE_PARAMETERS
 - windot11/_DOT11_PROVISION_DISCOVERY_REQUEST_SEND_COMPLETE_PARAMETERS
 - PDOT11_PROVISION_DISCOVERY_REQUEST_SEND_COMPLETE_PARAMETERS
 - windot11/PDOT11_PROVISION_DISCOVERY_REQUEST_SEND_COMPLETE_PARAMETERS
 - DOT11_PROVISION_DISCOVERY_REQUEST_SEND_COMPLETE_PARAMETERS
 - windot11/DOT11_PROVISION_DISCOVERY_REQUEST_SEND_COMPLETE_PARAMETERS
topic_type:
 - APIRef
 - kbSyntax
api_type:
 - HeaderDef
api_location:
 - Windot11.h
api_name:
 - _DOT11_PROVISION_DISCOVERY_REQUEST_SEND_COMPLETE_PARAMETERS
 - PDOT11_PROVISION_DISCOVERY_REQUEST_SEND_COMPLETE_PARAMETERS
 - DOT11_PROVISION_DISCOVERY_REQUEST_SEND_COMPLETE_PARAMETERS
---

# _DOT11_PROVISION_DISCOVERY_REQUEST_SEND_COMPLETE_PARAMETERS structure


## -description

> [!Important]
> [WiFiCx](/windows-hardware/drivers/netcx/wifi-wdf-class-extension-wificx) is the new Wi-Fi driver model released in Windows 11. We recommend that you use WiFiCx to take advantage of the latest features. The WDI driver model is now in maintenance mode and will only receive high priority fixes.

The parameters for a provision discovery request send complete are specified in a <b>DOT11_PROVISION_DISCOVERY_REQUEST_SEND_COMPLETE_PARAMETERS</b> structure. This structure is sent with an <a href="/windows-hardware/drivers/network/ndis-status-dot11-wfd-provision-discovery-request-send-complete">NDIS_STATUS_DOT11_WFD_PROVISION_DISCOVERY_REQUEST_SEND_COMPLETE</a> indication.

## -struct-fields

### -field Header

The type, revision, and size of the <b>DOT11_PROVISION_DISCOVERY_REQUEST_SEND_COMPLETE_PARAMETERS</b> structure. The required settings for the members of <b>Header</b> are the following.

<table>
<tr>
<th>Member</th>
<th>Setting</th>
</tr>
<tr>
<td><b>Type</b></td>
<td>NDIS_OBJECT_TYPE_DEFAULT</td>
</tr>
<tr>
<td><b>Revision</b></td>
<td>DOT11_PROVISION_DISCOVERY_RESPONSE_SEND_COMPLETE_PARAMETERS_REVISION_1</td>
</tr>
<tr>
<td><b>Size</b></td>
<td>DOT11_SIZEOF_PROVISION_DISCOVERY_RESPONSE_SEND_COMPLETE_PARAMETERS_REVISION_1</td>
</tr>
</table>

### -field PeerDeviceAddress

The Peer-to-Peer (P2P) device address of the Wi-Fi Direct (WFD) device that the provision discovery request was sent to.

### -field ReceiverAddress

The receiver device address used in the provision discovery request.

### -field DialogToken

The dialog token used for the provision discovery request packet. This token must match the token sent with the <a href="/windows-hardware/drivers/network/-oid-dot11-wfd-send-provision-discovery-request">OID_DOT11_WFD_SEND_PROVISION_DISCOVERY_REQUEST</a> request.

### -field Status

The status for the provision discovery request that was sent.

### -field uIEsOffset

The offset, in bytes,  of the array of additional information elements (IEs) that were included in the provision discovery request packet. This offset is from the start of the buffer that contains this structure.

### -field uIEsLength

The length, in bytes, of the array of IEs provided at <b>uIEsOffset</b>.

## -syntax

```cpp
typedef struct _DOT11_PROVISION_DISCOVERY_REQUEST_SEND_COMPLETE_PARAMETERS {
  NDIS_OBJECT_HEADER Header;
  DOT11_MAC_ADDRESS  PeerDeviceAddress;
  DOT11_MAC_ADDRESS  ReceiverAddress;
  DOT11_DIALOG_TOKEN DialogToken;
  NDIS_STATUS        Status;
  ULONG              uIEsOffset;
  ULONG              uIEsLength;
} DOT11_PROVISION_DISCOVERY_REQUEST_SEND_COMPLETE_PARAMETERS, *PDOT11_PROVISION_DISCOVERY_REQUEST_SEND_COMPLETE_PARAMETERS;
```

## -see-also

<a href="/windows-hardware/drivers/network/-oid-dot11-wfd-send-provision-discovery-request">OID_DOT11_WFD_SEND_PROVISION_DISCOVERY_REQUEST</a>



<a href="/windows-hardware/drivers/network/ndis-status-dot11-wfd-provision-discovery-request-send-complete">NDIS_STATUS_DOT11_WFD_PROVISION_DISCOVERY_REQUEST_SEND_COMPLETE</a>

