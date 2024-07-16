# Peppol

This is an overview page  pointing to my different Peppol solutions.
All of the solutions are Java based, requiring at least Java 11, require Maven to build and are usually deployed to [Maven Central](https://central.sonatype.com/).

Please star the project if you like it :)

# Access Point (AP)

* [phase4](https://github.com/phax/phase4) is a *library* implementing the AS4 protocol and including value added services like SMP client, SBDH wrapping etc.
* [Standalone phase4 for Peppol](https://github.com/phax/phase4-peppol-standalone) is an example implementation of a standalone AP, based on Spring Boot 3.x

* See [phase4 Known Users](https://github.com/phax/phase4/wiki/Known-Users) for a list of known users that agreed to be listed

# Service Metadata Publisher (SMP)

* [phoss SMP](https://github.com/phax/phoss-smp/) is a standalone Peppol SMP server. Provided with different backends to store data. Prebuilt Docker images are available.
* [SMP Client](https://github.com/phax/peppol-commons?tab=readme-ov-file#peppol-smp-client) is a shared component to access an SMP from e.g. an AP (see above)

# Document Validation

* [ph-schematron](https://github.com/phax/ph-schematron/) is a generic Schematron validation *library*. It offers different "engines" to perform the actual validation.
* [phive](https://github.com/phax/phive) is a more advanced validation *library* that deals with different types of validations and includes XML Schema (XSD) and Schematron validation (based on ph-schematron)
* [phive-rules](https://github.com/phax/phive-rules) is a set of collected validation rules to be used with **phive** to validate actual business documents (e.g. Peppol BIS Billing, XRechnung, ...)
* [ddd](https://github.com/phax/ddd) is a library that can be used to determine the VESID of a business document for usage with **phive**

## Users

* [ecosio Document Validator](https://ecosio.com/en/peppol-and-xml-document-validator/) provides a web-based validation to validate documents and is based on **phive** and **phive-rules**
* [Peppol Practical Document Validation](https://peppol.helger.com/public/locale-en_US/menuitem-validation-ws2) provides a SOAP based service to validate business documents and is based on **phive** and **phive-rules**

# Peppol Directory

* [phoss Directory](https://github.com/phax/phoss-directory) is the technical solution powering the Peppol Directory operated by OpenPeppol at https://directory.peppol.eu and https://test-directory.peppol.eu
* [phoss Directory Client](https://github.com/phax/phoss-directory?tab=readme-ov-file#pd-client) is a reusable client for accessing the Peppol Directory. This is mainly needed for SMP servers.

* This is primarily used by OpenPeppol itself, but was used in other eDelivery based EU projects as well

# Peppol Network Reporting

* [peppol-reporting](https://github.com/phax/peppol-reporting) contains the data model for the Transaction Statistics Report (TSR) and End User Statistics Report (EUSR)

# Peppol related components

* [peppol-commons](https://github.com/phax/peppol-commons) is a set of shared and reusable libraries
    * peppol-id-datatypes contains the JAXB generated datatypes for Peppol identifiers
    * peppol-id contains a set of predefined Peppol identifiers (Document Types, Processes, Participant Identifier Schemes and Transport Profiles)
    * peppol-commons a set of generic helper methods support the use of certificates and the trust model
    * peppol-sbdh contains the specific rules to be applied to an SBDH document to comply to the Peppol specifications
    * peppol-sml-client contains a client to access the public APIs of an SML that uses the Peppol SML specification. This is mainly used for SMP servers.
    * peppol-smp-datatypes contains the JAXB generated datatypes for SMP data types
    * peppol-smp-client contains a client to access SMP servers that follow the Peppol SMP specification
    * peppol-directory-businesscard contains the JAXB generated datatypes for the Peppol Business Card
    * peppol-mlr contains supporting methods to easily create a Peppol Message Level Response
* [ph-sbdh](https://github.com/phax/ph-sbdh)  contains the JAXB generated data models for the Standard Business Document Header (SBDH)
* [ph-ubl](https://github.com/phax/ph-ubl) contains the JAXB generated data models for UBL 2.x
* [ph-cii](https://github.com/phax/ph-cii) contains the JAXB generated data models for Cross Industry Invoice (CII)
* [en16931-cii2ubl](https://github.com/phax/en16931-cii2ubl) is a library that allows you to convert CII to UBL (only in that direction) in case you are forced to deal with CII but you don't want to deal with it
* [ph-xsds](https://github.com/phax/ph-xsds/) contains the JAXB generated data models for a bunch of commonly used XML Schemas

