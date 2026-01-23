\pagebreak

# Technology Introduction {#sec:tech_intro}

## General {#sec:tech_intro_general}

This design template realizes the service specification [@cite:iala-aton_info_service_spec] using SECOM as defined in IEC 63173-2 [@cite:iec-63173-2].

The services conforming to this design must be implemented with REST APIs using HTTPS with TLS protection to encrypt all communication in transit.

## Service Technology and Service Transportation Protocol {#sec:tech_intro_service_tansport_protocol}

***Reference: IEC 63173-2 SECOM v1.0.0 Clause 5.3 Service Technology***

The technology (architectural style) chosen is REST (REpresentational State Transfer) upon HTTP/1.1 (RFC 7231).

## Security {#sec:tech_intro_security}

### Communication Channel Security {#sec:tech_intro_security_comm}

***Reference: IEC 63173-2 SECOM v1.0.0 Clause 6 SECOM communication channel security***

The channel security between the SECOM REST service and a consumer are 

* HTTP/1.1 according to RFC-7231
* HTTPS over TLS according to RFC-2818

Valid versions of TLS for this version of service design template are

* TLS version 1.2 and 1.3 (RFC-8446) 

X.509 Certificates are used in the TLS according to RFC 5280 and RFC 2459.

Certificates shall be verified with OCSP and/or CRL methods.

### Data Protection {#sec:tech_intro_security_data_protection}

***Reference: IEC 63173-2 SECOM v1.0.0 Clause 4.3.4 SECOM data protection***

***Reference: IHO S-100 ed5.2.0 Part 15 Data Protection Scheme***

The data is mandatory to be signed by the sender to enable data authentication and integrity check by the receiver.

The data can optionally be encrypted by the sender, and the sender is responsible for exchanging the encryption key with the receiver.

While sending standalone S-421 documents without the additional metadata of datasets or exchange sets is preferred, if datasets or exchange sets are used the data (one or more data files) can optionally be packaged and compressed before being signed and sent.

### Data Signature {#sec:tech_intro_security_data_sign}

***Reference: IEC 63173-2 SECOM v1.0.0 Clause 7.3 Data authentication and signing***

***Reference: IHO S-100 ed5.2.0 Part 15-8 Data Authentication***

***Reference: NIST Digital Signature Standard (DSS–FIPS Publication 186***

The algorithm for signing data must be ECDSA-384-SHA2.

The signature is transported in HEX.

### Data Encryption {#sec:tech_intro_security_data_encryption}

***Reference: IEC 63173-2 SECOM v1.0.0 Clause 7.4 Data encryption***

***Reference: IHO S-100 ed5.2.0 Part 15-6 Data Encryption***

The encryption algorithm for encryption is AES and CBC mode.

The symmetric encryption key can be exchanged by different means, including using the SECOM REST API to exchange the encryption key.
