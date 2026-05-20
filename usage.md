# Where to use what — Peppol four-corner model

Peppol exchange follows a four-corner model:

* **C1** — the *Sender* (the business that creates the document, e.g. a supplier's ERP issuing an invoice)
* **C2** — the *Sending Access Point* (technical sender, transmits on C1's behalf)
* **C3** — the *Receiving Access Point* (technical receiver, receives on C4's behalf)
* **C4** — the *Receiver* (the business that processes the document, e.g. a buyer's accounting system)

C2 and C3 are typically operated by service providers and run the same software in opposite directions. C1 and C4 are end-user applications.

Below, projects are mapped to the corner where you will most likely use them. Some libraries (validation, data models, identifiers) appear at more than one corner.

## C1 — Sender (creating outbound documents)

Build a valid business document, choose Peppol identifiers, validate before handing off to C2, convert formats when needed.

* [**ph-ubl**](https://github.com/phax/ph-ubl) — UBL 2.x data model to build the invoice / order / credit note
* [**ph-cii**](https://github.com/phax/ph-cii) — CII data model if you have to produce CII instead of UBL
* [**peppol-commons**](https://github.com/phax/peppol-commons) ([`peppol-id`](https://github.com/phax/peppol-commons?tab=readme-ov-file#peppol-id)) — predefined Peppol identifiers (Document Types, Processes, Participant Identifier Schemes)
* [**phive**](https://github.com/phax/phive) + [**phive-rules**](https://github.com/phax/phive-rules) + [**ddd**](https://github.com/phax/ddd) — validate the document before handing it to C2 ([`ddd`](https://github.com/phax/ddd) resolves the VESID for [`phive`](https://github.com/phax/phive))
* [**en16931-cii2ubl**](https://github.com/phax/en16931-cii2ubl) / [**en16931-ubl2cii**](https://github.com/phax/en16931-ubl2cii) — convert between CII and UBL when the back-office format differs from what you must send

## C2 — Sending Access Point (outbound transmission)

Wrap the document in an SBDH, look up the receiver in an SMP, transmit via AS4, validate at the boundary, generate the required network reports.

* [**phoss-ap**](https://github.com/phax/phoss-ap) — turnkey Spring Boot Access Point (handles both C2 and C3)
* [**phase4**](https://github.com/phax/phase4) — AS4 protocol library (the engine inside [`phoss-ap`](https://github.com/phax/phoss-ap))
* [**peppol-ap-support**](https://github.com/phax/peppol-ap-support/) — AP-side helper functions
* [**peppol-commons**](https://github.com/phax/peppol-commons) ([`peppol-sbdh`](https://github.com/phax/peppol-commons?tab=readme-ov-file#peppol-sbdh), [`peppol-smp-client`](https://github.com/phax/peppol-commons?tab=readme-ov-file#peppol-smp-client), [`peppol-id`](https://github.com/phax/peppol-commons?tab=readme-ov-file#peppol-id)) — SBDH wrapping, SMP lookup of C3, identifiers
* [**peppol-reporting**](https://github.com/phax/peppol-reporting) — TSR / EUSR data model for the mandatory OpenPeppol network reports
* [**phive**](https://github.com/phax/phive) + [**phive-rules**](https://github.com/phax/phive-rules) — boundary validation before sending

## C3 — Receiving Access Point (inbound transmission)

Publish your endpoint in an SMP, receive via AS4, verify the signature and trust chain, unwrap the SBDH, validate, generate a Message Level Response, generate the required network reports.

* [**phoss SMP**](https://github.com/phax/phoss-smp/) — operate an SMP server to publish the C3 endpoint that senders look up (receive-side only)
* [**smp-mate**](https://github.com/phax/smp-mate) — maintenance tool to bulk-provision participants in your SMP (German documentation)
* [**phoss-ap**](https://github.com/phax/phoss-ap) — same Access Point software as at C2
* [**phase4**](https://github.com/phax/phase4) — same AS4 library as at C2
* [**peppol-ap-support**](https://github.com/phax/peppol-ap-support/) — same helpers as at C2
* [**peppol-commons**](https://github.com/phax/peppol-commons) ([`peppol-sbdh`](https://github.com/phax/peppol-commons?tab=readme-ov-file#peppol-sbdh), [`peppol-mlr`](https://github.com/phax/peppol-commons?tab=readme-ov-file#peppol-mlr), [`peppol-id`](https://github.com/phax/peppol-commons?tab=readme-ov-file#peppol-id)) — SBDH unwrapping, Message Level Response generation
* [**peppol-reporting**](https://github.com/phax/peppol-reporting) — TSR / EUSR generation
* [**phive**](https://github.com/phax/phive) + [**phive-rules**](https://github.com/phax/phive-rules) — inbound validation; or run [**phorm**](https://github.com/phax/phorm) as a standalone validation REST service that C3 calls

## C4 — Receiver (processing inbound documents)

Parse the received document, re-validate, convert it to whatever format your back-office prefers.

* [**ph-ubl**](https://github.com/phax/ph-ubl) — parse UBL documents
* [**ph-cii**](https://github.com/phax/ph-cii) — parse CII documents
* [**phive**](https://github.com/phax/phive) + [**phive-rules**](https://github.com/phax/phive-rules) — re-validate the received document inside your application
* [**en16931-cii2ubl**](https://github.com/phax/en16931-cii2ubl) / [**en16931-ubl2cii**](https://github.com/phax/en16931-ubl2cii) — convert into the format your back-office prefers
* [**kaltblut**](https://github.com/phax/kaltblut) — extract embedded XML from hybrid ZUGFeRD / Factur-X PDF invoices (useful when such invoices arrive alongside Peppol traffic)

## Outside the corners — network infrastructure

These do not belong to a single corner. They support the Peppol network operated by OpenPeppol and the SMP service providers.

* [**smp-query-webapp**](https://github.com/Helger-IT/smp-query-webapp) — standalone SMP query service (pre-built Docker image)
* [**phoss Directory**](https://github.com/phax/phoss-directory) — operate a Peppol Directory server
* [**phoss Directory Client**](https://github.com/phax/phoss-directory?tab=readme-ov-file#pd-client) — query the Peppol Directory (used by SMPs and any participant)
* [**peppol-commons**](https://github.com/phax/peppol-commons) ([`peppol-sml-client`](https://github.com/phax/peppol-commons?tab=readme-ov-file#peppol-sml-client)) — access the Service Metadata Locator (used by SMP servers when registering)
* [**phoss-peppol-mcp**](https://github.com/phax/phoss-peppol-mcp) — MCP (Model Context Protocol) server exposing Peppol Network capabilities as tools to AI models such as Claude

## Country-specific add-ons

These augment whichever corner handles that country's specific rules — usually C2/C3 for transport peculiarities and C1/C4 for document-content rules.

* [**peppol-sk**](https://github.com/phax/peppol-sk) — Slovakia (SK)
* [**peppol-om**](https://github.com/phax/peppol-om) — Oman (OM)
* [**peppol-uae**](https://github.com/phax/peppol-uae) — United Arab Emirates (UAE)
* [**peppol-vida**](https://github.com/phax/peppol-vida) — Peppol ViDA pilot
