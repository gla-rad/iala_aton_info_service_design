\pagebreak

# Annex B. G1128 Instance Description XML Template {#sec:g1128-instance-desc}

```xml
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
<serviceInstance
  xmlns="http://iala-aism.org/g1128/v1.6/ServiceInstanceSchema.xsd"
  xmlns:ns2="http://iala-aism.org/g1128/v1.6/ServiceSpecificationSchema.xsd">
    <id>urn:mrn:mcp:service:mcc:grad:instance:aton-service</id>
    <version>0.0.1</version>
    <name>Test AtoN Service</name>
    <status>provisional</status>
    <description>An example of a G1128 instance description XML</description>
    <keywords>aton service g1128 example</keywords>
    <endpoint>https://localhost:8443/api/secom</endpoint>
    <serviceType>other:atonservice</serviceType>
    <requiresAuthorization>true</requiresAuthorization>
    <offersServiceLevel>
        <availability>0.0</availability>
        <name>Development</name>
        <description>This service implementation is under active development, 0% availability is guaranteed.</description>
    </offersServiceLevel>
    <coversAreas>
        <coversArea>
            <name>Example</name>
            <description>Description on the example area</description>
            <geometryAsWKT>POLYGON ((0.0 0.0, 0.0 1.1, 1.1 1,1, 1.1 0.0 ))</geometryAsWKT>
        </coversArea>
    </coversAreas>
    <implementsServiceDesign>
        <id>urn:mrn:iala:si:atonservice:0.0.1</id>
        <version>0.0.0</version>
    </implementsServiceDesign>
    <producedBy>
        <ns2:id>urn:mrn:iala</ns2:id>
        <ns2:name>IALA</ns2:name>
        <ns2:description>International Organization of Marine Aids to Navigation</ns2:description>
        <ns2:contactInfo>https://www.iala.int/</ns2:contactInfo>
        <ns2:isCommercial>false</ns2:isCommercial>
    </producedBy>
    <providedBy>
        <ns2:id>urn:mrn:iala</ns2:id>
        <ns2:name>IALA</ns2:name>
        <ns2:description>International Organization of Marine Aids to Navigation</ns2:description>
        <ns2:contactInfo>https://www.iala.int/</ns2:contactInfo>
        <ns2:isCommercial>false</ns2:isCommercial>
    </providedBy>
</serviceInstance>
```