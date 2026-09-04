# Peppol Open Source Suite

This is an overview page  pointing to my different Peppol solutions.
All of the solutions are Java based, require Maven to build and are usually deployed to [Maven Central](https://central.sonatype.com/).
The current versions require at least Java 17 - [phoss-ap](https://github.com/phax/phoss-ap) requires Java 21.

Please star the project if you like it :)

**New to Peppol?** See [usage.md](usage.md) for a quick orientation by four-corner role (C1 / C2 / C3 / C4) — which projects to use where.

# Access Point (AP)

* [phoss-ap](https://github.com/phax/phoss-ap) A standalone Peppol Access Point (AP) based on [phase4](https://github.com/phax/phase4) and Spring Boot 4.x. Ships with a Docker Compose setup and supports PostgreSQL, MySQL and DB2 as backends
* [phase4](https://github.com/phax/phase4) is a *library* implementing the AS4 protocol and including value added services like SMP client, SBDH wrapping etc.
* [peppol-ap-support](https://github.com/phax/peppol-ap-support/) is a library with Access Point support functions. It is a separate project so that it can leverage other projects like `peppol-commons` and `peppol-reporting`

* See [phase4 Known Users](https://github.com/phax/phase4/wiki/Known-Users) for a list of known users that agreed to be listed

## Legacy solutions

* [Standalone phase4 for Peppol](https://github.com/phax/phase4-peppol-standalone) is an example implementation of a standalone AP, based on Spring Boot 4.x - recommended to use phoss-ap instead

# Service Metadata Publisher (SMP)

* [phoss SMP](https://github.com/phax/phoss-smp/) is a standalone Peppol SMP server. Used by more than 50% of all production SMPs. Ships with different backends to store data. Pre-built Docker images are available.
* [SMP Client](https://github.com/phax/peppol-commons?tab=readme-ov-file#peppol-smp-client) is a shared component to access an SMP from e.g. an AP (see above)
* [Standalone SMP Client](https://github.com/Helger-IT/smp-query-webapp) is a standalone Peppol SMP client available as pre-built Docker image if you don't want to use the Java code. It offers a JSON response instead.
* [smp-mate](https://github.com/phax/smp-mate) is a maintenance tool to bulk-provision participants in a Peppol SMP (documentation in German)

# Document Validation

* [phorm](https://github.com/phax/phorm) A standalone Validation REST service using ph-schematron, phive, phive-rules and ddd together
* [ddd](https://github.com/phax/ddd) is a library that can be used to determine the VESID of a business document for usage with **phive** (links to the VESIDs from `phive-rules`)
* [phive](https://github.com/phax/phive) is a more advanced validation *library* that deals with different types of validations and includes XML Schema (XSD) and Schematron validation (based on `ph-schematron`)
* [phive-rules](https://github.com/phax/phive-rules) is a set of collected validation rules to be used with **phive** to validate actual business documents (e.g. Peppol BIS Billing, XRechnung, ...) (based on `phive`)
* [phive-rules-foundations](https://github.com/phax/phive-rules-foundations) contains the foundational, rarely changing rule sets that other rule sets build upon - the pure structural (XSD only) validation of UBL, CII, ebInterface, Facturae, fatturaPA, Finvoice, KSeF, OSA and TEAPPS. It was split out of `phive-rules` in 2026 so it can be versioned and released independently
* [phive-rules-shared](https://github.com/phax/phive-rules-shared) contains the registration SPI and the helper classes shared by all `phive-rules` modules
* [phive-binary](https://github.com/phax/phive-binary) is a `phive`-inspired validation *library* for binary file formats — validates files by extension or MIME type (used for non-XML attachments in e-invoicing contexts)
* [ph-schematron](https://github.com/phax/ph-schematron/) is a generic Schematron validation *library*. It offers different "engines" to perform the actual validation.
* [ph-diver](https://github.com/phax/ph-diver) provides the "Digitally Versioned Resources" layer that **phive** uses to address and resolve rule sets by their VESID

## Users

* [ecosio Document Validator](https://ecosio.com/en/peppol-and-xml-document-validator/) provides a web-based validation to validate documents and is based on **phive** and **phive-rules**
* [Peppol Practical Document Validation](https://peppol.helger.com/public/locale-en_US/menuitem-validation-ws2) provides a SOAP based service to validate business documents and is based on **phive** and **phive-rules**

# Document Visualization

* [en16931-visualization](https://github.com/phax/en16931-visualization) is a collected overview of existing Open Source solutions that visualize EN 16931 based invoices (stylesheets, tools and services, grouped by document format). It is a curated list, not a library

# Peppol Directory

* [phoss Directory](https://github.com/phax/phoss-directory) is the technical solution powering the Peppol Directory operated by OpenPeppol at https://directory.peppol.eu and https://test-directory.peppol.eu
* [phoss Directory Client](https://github.com/phax/phoss-directory?tab=readme-ov-file#pd-client) is a reusable client for accessing the Peppol Directory. This is mainly needed for SMP servers.

* This is primarily used by OpenPeppol itself, but was used in other eDelivery based EU projects as well

# Peppol Network Reporting

* [peppol-reporting](https://github.com/phax/peppol-reporting) contains the data model for the Transaction Statistics Report (TSR) and End User Statistics Report (EUSR)

# Peppol Country specific components

* [peppol-sk](https://github.com/phax/peppol-sk) contains specific support elements for Slovakia (SK)
* [peppol-om](https://github.com/phax/peppol-om) contains specific support elements for Oman (OM)
* [peppol-uae](https://github.com/phax/peppol-uae) contains specific support elements for United Arab Emirates (UAE)
* [peppol-vida](https://github.com/phax/peppol-vida) contains specific support elements for the Peppol ViDA pilot

# AI integration

* [phoss-peppol-mcp](https://github.com/phax/phoss-peppol-mcp) is a Peppol MCP (Model Context Protocol) server that exposes Peppol Network capabilities as tools to AI models such as Claude

# Peppol related components

* [ph-xsds](https://github.com/phax/ph-xsds) contains the JAXB generated data models for a bunch of commonly used XML Schemas
* [ph-sbdh](https://github.com/phax/ph-sbdh) contains the JAXB generated data models for the Standard Business Document Header (SBDH)
* [ph-xhe](https://github.com/phax/ph-xhe) contains the data model for the OASIS Exchange Header Envelope (XHE) - the envelope used by DBNAlliance instead of the SBDH
* [ph-genericode](https://github.com/phax/ph-genericode) reads and writes OASIS Genericode and CVA files - the format in which the Peppol code lists are published (used by `peppol-commons`)
* [ph-ubl](https://github.com/phax/ph-ubl) contains the JAXB generated data models for UBL 2.x
* [ph-cii](https://github.com/phax/ph-cii) contains the JAXB generated data models for Cross Industry Invoice (CII)
* [peppol-commons](https://github.com/phax/peppol-commons) is a set of shared and reusable libraries
    * peppol-id-datatypes contains the JAXB generated datatypes for Peppol identifiers
    * peppol-id contains a set of predefined Peppol identifiers (Document Types, Processes, Participant Identifier Schemes and Transport Profiles)
    * peppol-id-checks contains checks and derivations on top of the `peppol-id` data structures (separate module, because it needs dependencies that `peppol-id` deliberately avoids)
    * peppol-commons a set of generic helper methods support the use of certificates and the trust model
    * peppol-sbdh contains the specific rules to be applied to an SBDH document to comply to the Peppol specifications (based on `ph-sbdh`)
    * peppol-testfiles contains UBL and SBDH test files for use in different scenarios
    * peppol-sml-client contains a client to access the public APIs of an SML that uses the Peppol SML specification. This is mainly used for SMP servers.
    * peppol-smp-datatypes contains the JAXB generated datatypes for SMP data types
    * peppol-smp-client contains a client to access SMP servers that follow the Peppol SMP specification
    * peppol-directory-businesscard contains the JAXB generated datatypes for the Peppol Business Card
    * peppol-mlr contains supporting methods to easily create a Peppol Message Level Response (based on `ph-ubl`)
    * peppol-mls contains supporting methods to read and write a Peppol Message Level Status (MLS) document (based on `ph-ubl`)
    * dbnalliance-commons and dbnalliance-xhe contain the shared components and the header handling for DBNAlliance - the DBNAlliance counterpart of `peppol-sbdh` (based on `ph-xhe`)
    * hredelivery-commons contains the shared components for the Croatian (HR) eDelivery / eRacun network
* [en16931-cii2ubl](https://github.com/phax/en16931-cii2ubl) is a library that allows you to convert CII to UBL (only in that direction) in case you are forced to deal with CII but you don't want to deal with it (based on `ph-ubl` and `ph-cii`)
* [en16931-ubl2cii](https://github.com/phax/en16931-ubl2cii) is a library that allows you to convert UBL to CII (only in that direction) (based on `ph-ubl` and `ph-cii`)
* [en16931-purifier](https://github.com/phax/en16931-purifier) is a library that removes everything from an EN 16931 invoice that is not part of the core message and writes an XML Schema valid document in the same syntax - input syntax is output syntax, so this is not a converter (based on `ph-ubl` and `ph-cii`)

# Websites and shared UI

* [peppol-practical](https://github.com/phax/peppol-practical) is the source code of the [peppol.helger.com](https://peppol.helger.com) website that also hosts the document validation service mentioned above
* [peppol-shared-ui](https://github.com/phax/peppol-shared-ui) contains the UI and web application components shared between the Peppol related websites

# Other eInvoicing related components

* [kaltblut](https://github.com/phax/kaltblut) is a library that supports the identification, verification and extraction of XML data from hybrid ZUGFeRD and Factur-X invoices
* [ph-redact](https://github.com/phax/ph-redact) is an XSLT based anonymizer for eInvoices - it replaces all sensitive and personally identifiable data but keeps the document structure, the monetary values and the tax information intact. Format detection and SBDH / XHE unwrapping is done with `ddd`. A CLI is included
* [ph-ebinterface](https://github.com/phax/ph-ebinterface) is a library for reading and writing Austrian ebInterface 3.0 up to 6.1 documents
* [ph-fatturapa](https://github.com/phax/ph-fatturapa) is a library for reading and writing Italian fatturaPA invoices
* [erechnung.gv.at-webservice-client](https://github.com/phax/erechnung.gv.at-webservice-client) contains the Webservice clients for ER>B - the national Austrian invoicing solution (not affiliated with BRZ)

---

My personal [Coding Styleguide](https://github.com/phax/meta/blob/master/CodingStyleguide.md) |
It is appreciated if you star the GitHub project if you like it.

