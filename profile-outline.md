# [STRAWMAN] Profile outline

A proposed table of contents for the group's Specification, for discussion only. It shows how the scope in the draft charter could be organised. It contains no requirements yet; every section is open. Once the group agrees a structure, the outline becomes a ReSpec editor's draft.

**Working title:** High Assurance Profile for W3C Verifiable Credentials Data Model 2.0. The short name is to be decided.

## 1. Introduction

- 1.1 Purpose: a small, testable set of choices for high-assurance use of VCDM 2.0
- 1.2 Relationship to VCDM 2.0, Data Integrity, VC-JOSE-COSE and Bitstring Status List
- 1.3 Relationship to other profiles (for example OpenID4VC HAIP and the ETSI TS 119 472 series)
- 1.4 The EU as reference case; a jurisdiction-neutral core and jurisdiction modules

## 2. Conformance

- 2.1 Conformance classes:
  - issuer;
  - holder/wallet;
  - verifier;
  - publisher of contexts, vocabularies and schemas;
  - registry or distribution operator;
  - ecosystem or governance authority.
- 2.2 Core requirements and optional modules
- 2.3 Conformance claims: what a claim states and how it is tested

## 3. Terminology

Terms from VCDM 2.0, eIDAS 2.0 (EAA, QEAA, PuB-EAA) and this profile (for example "high assurance").

## 4. Data model and serialisation

- 4.1 Required and restricted VCDM 2.0 properties
- 4.2 JSON-LD processing rules
- 4.3 Other serialisations (for example CBOR-LD for compact carriers and YAML-LD for authoring), and how they relate to JSON-LD

## 5. Securing mechanisms

- 5.1 Data Integrity: cryptosuites and parameters
- 5.2 VC-JOSE-COSE: media types and parameters
- 5.3 Selective disclosure
- 5.4 Mandatory-to-implement choices

## 6. Algorithms and cryptographic agility

- 6.1 Baseline algorithms
- 6.2 Algorithm policy and downgrade protection
- 6.3 Transition to post-quantum signatures

## 7. Meaning: contexts, vocabularies and schemas

- 7.1 Identifying and versioning contexts, vocabularies and schemas
- 7.2 Integrity protection and loading rules
- 7.3 Publication, update and withdrawal
- 7.4 Processing limits

## 8. Assurance levels in mixed evidence graphs

- 8.1 Levels: qualified (Q: QEAA, PuB-EAA), signed evidence (E), unsigned (U), no attributable source (⊥)
- 8.2 Assigning a level from the verifier's own validation, never from a label inside a credential
- 8.3 No elevation: wrapping, re-signing, merging or presenting never raises a level
- 8.4 Provenance per statement in merged graphs: issuer, meaning, version, authority, level
- 8.5 Policy: minimum level per fact or authority relationship; unsigned data never satisfies a requirement for signed evidence

Background: *Proofs over Statements in Verifiable Evidence Graphs for the European Business Wallet*, v1.3, §4.2 and Figure 2.

## 9. Issuers, keys and holders

- 9.1 Issuer identification and key resolution (X.509 and decentralized identifiers)
- 9.2 Issuer authorisation per credential type
- 9.3 Holder binding

## 10. Credential status

- 10.1 Status mechanisms and parameters
- 10.2 Freshness, and handling of unavailable status

## 11. Verification

- 11.1 Verification procedure, step by step
- 11.2 Outcomes: valid, invalid, unknown
- 11.3 Decision records for later review

## 12. Protocol bindings

- 12.1 OpenID for Verifiable Credential Issuance
- 12.2 OpenID for Verifiable Presentations and the Digital Credentials API
- 12.3 W3C VC API

## 13. Jurisdiction modules

- 13.1 EU module: EAA, QEAA and PuB-EAA as W3C Verifiable Credentials; trusted lists; alignment with ETSI TS 119 472
- 13.2 Template for modules from other jurisdictions

## 14. Security considerations

## 15. Privacy considerations

## 16. Test suite

How tests are organised, numbered and run; positive and negative tests.

## Appendices

- A. Examples
- B. Mapping to the ETSI TS 119 472 series
- C. Comparison with OpenID4VC HAIP
- D. Use cases (with a link to the Use Cases and Requirements report)

## Open questions

1. Is this the right granularity, or should some sections become separate documents?
2. Should protocol bindings (§12) live in this Specification or in separate notes?
3. Which jurisdiction modules beyond the EU should we plan for?
