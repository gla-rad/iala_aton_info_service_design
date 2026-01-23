# Introduction {#sec:introduction}

This document specifies the design of the "Provision of AtoN Information to End-Users" service according to the technical service specification [@cite:iala-aton_info_service_spec] using the IEC SECOM [@cite:iec-63173-2] standard as the transport mechanism for route exchange. This one of the core technical service included in the "MS-2 - Aids to Navigation" maritime service, as this was defined by IMO [@cite:imo-msc-1-circ1610-rev1-2024].

This document was produced as part of the work of IALA ARM committee task group on development of technical service specifications for the provision of AtoN Information. The document is structured according to the IALA Guideline G1128 The Specification of e-Navigation Technical Services [@cite:iala-g1128] and is based on the SECOM template found therein [@cite:iala-g1128-annex-d]


## Purpose of this Guideline {#sec:introduction_purpose}

The purpose of this document is to define a service design using SECOM for the "Provision of AtoN Information to End-Users" service defined in the technical service specification [@cite:iala-aton_info_service_spec]. This is done by using SECOM and the S-125 XML representation as defined in the specification. It defines the actual way the interactions and logical interfaces defined in the specification are to be implemented. It also describes how the requirements for authentication etc are to be implemented. 

It describes the actual requirements for both ship and shore side systems in order to support the AtoN information provision as defined in the specification.

Note that this design will undergo changes between versions 1.0 and 2.0 as the SECOM and S-125 standard should be updated during that transition period and the design will be changed to reflect the latest changes. Some of the anticipated changes to SECOM and S-125 have already been included in this design and as such this design may not be fully compatible with SECOM 1.0 and S-125 1.0.


## Intended Readership {#sec:introduction_intended_readership}

This Service Design is intended to be read by service architects, system engineers and developers in charge of designing and developing an instance of the route exchange service.

### Inputs from Other Sources {#sec:introduction_other_sources}

This service design follows the requirements, use cases and dynamic behaviour outlined in [@cite:iala-aton_info_service_spec]. The interfaces, parameters and logic of the API is compliant with IEC 63173-2 SECOM and borrows much of its content from there.

“The authors thank the International Electrotechnical Commission (IEC) for permission to reproduce Information from its International Standards. All such extracts are copyright of IEC, Geneva, Switzerland. All rights reserved. Further information on the IEC is available from `www.iec.ch`. IEC has no responsibility for the placement and context in which the extracts and contents are reproduced by the author, nor is IEC in any way responsible for the other content or accuracy therein.”.
