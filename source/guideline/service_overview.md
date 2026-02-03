\pagebreak

# Service Overview {#sec:service_overview}

## General {#sec:service_overview_general}

The design uses SECOM defined APIs. As such, it is important to understand that both the AtoN information provision service and its consumers must be able to function as client and server as understood in the traditional HTTP world. As such from here on when the term service is used, it applies to the on-shore "Provision of AtoN Information to End-Users" service and the consumer is the on-board ship system that is communicating with it. 

This design does not concern itself with how the service instances will communicate with on-board ship systems. The instances of this design may be developed as integrated components directly or as independent microservices that communicate with the onboard ship systems via different integration mechanisms e.g., APIs or by emitting and consuming events.

It should also be noted that all AtoN information provision service instances, the advertised S-125 datasets, as well as the included AtoNs, must support the IALA Maritime Resource Naming (MRN) scheme, as per [@cite:iala-g1143]. Valid MRN identifiers should be made available for each of these entities. The implementation methodology however, falls outside the scope of this service design.

## Service Interfaces {#sec:service_overview_interfaces}

***Reference: IEC 63173-2 SECOM v1.0.0 Clause 5.7 SECOM service interface definitions***

SECOM does not require that all the interfaces defined in the standard must be implemented. Thus, for the purposes of this service and its consumers, only the following interfaces are required:

| Interface | SECOM Reference | Comment |
| --- | --- | --- |
| Get | IEC 63173-2 SECOM v1.0.0 Clause 5.7.5 service interface - Get | This interface is called when the client gets (pulls) data from the service.
| Get By Link | IEC 63173-2 SECOM v1.0.0 Clause 5.7.7 service interface - Get By Link | This interface is called when the client downloads (pulls) large data by reference given from interface Upload Link. |
| Get Summary | IEC 63173-2 SECOM v1.0.0 Clause 5.7.6 service interface - Get Summary | This interface is called when the client gets a summary of available data from the service. The data is retrieved (pulled) using the interface Get. |
| Subscription | IEC 63173-2 SECOM v1.0.0 Clause 5.7.10 service interface - Subscription | This interface is called when the client or server initiates subscription on data from the service. Response is given with interface Upload and Subscription Notification. |
| Remove Subscription | IEC 63173-2 SECOM v1.0.0 Clause 5.7.11 service interface - Remove Subscription | This interface is called when the client or server removes subscription. Response is given with interface Subscription Notification. |
| Subscription Notification | IEC 63173-2 SECOM v1.0.0 Clause 5.7.12 service interface - Subscription Notification | This interface is called as response from Subscription or Remove Subscription. |
| Upload | IEC 63173-2 SECOM v1.0.0 Clause 5.7.2 service interface - Upload | This interface is called when the client uploads (pushes) data to the service. The sender (client) decides the format and protection of the data. |
| Upload Link | IEC 63173-2 SECOM v1.0.0 Clause 5.7.3 service interface - Upload Link | This interface is called when the client uploads (pushes) a reference pointer to large data. The data is downloaded using interface Get By Link. |Z
Acknowledgement | IEC 63173-2 SECOM v1.0.0 Clause 5.7.4 service interface - Acknowledgement | This interface is called as response to Acknowledgement request in Upload. |
| Capability | IEC 63173-2 SECOM v1.0.0 Clause 5.7.13 service interface - Capability | This interface is called when the client asks for the service capabilities. |
| Ping | IEC 63173-2 SECOM v1.0.0 Clause 5.7.14 service interface - Ping | This interface is called when the client checks the availability of the service.
| PublicKey | IEC 63173-2 SECOM v1.0.0 Clause 5.7.16 service interface - PublicKey | This interface is called when the client gets (pulls) the public certificate(s) from the service. |

: AtoN Information Service interfaces {#tbl:aton_info_service_interfaces}

All unused interfaces of SECOM should be implemented to return HTTP 501 as specified in [@cite:iec-63173-2].

There are three components that are of interest from the perspective of the service design:

* The data provider's service has a SECOM-component which supports the SECOM REST APIs defined in the table above. All other components of the service are left to the decisions of the implementing party.
* The data consumer client has a SECOM-component which will accept the incoming connections from the service and store all messages until delivered to the vessel. This interface is typically on a shoreside server as it must be always available and at a reachable address.
* The data consumer client also supports a SECOM client which allows it to make direct SECOM calls to the service without having to proxy all calls via the SECOM-component on shore.

In this service design we will not define the communication between the data provider and the AtoN information SECOM service or between the ship and the ship's shoreside SECOM-component. These are specific for each implementation and depend on the general system architecture and implementation decisions.

## Service Discovery {#sec:service_overview_discovery}

Services implemented according to this design must submit their instance description to a valid service registry that follows the IALA G1129 Maritime Service Registry (MSR) [@cite:iala-g1191] technical specification.

An XML template for the instance description is provided as an annex to this design ANNEX B [@sec:g1128-instance-desc].
