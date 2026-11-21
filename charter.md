# [DRAFT] High Assurance Profile for W3C VCDM 2.0 Community Group Charter

This charter is a proposal for discussion. Please send feedback as GitHub issues in this repository.

- **This charter:** https://github.com/w3c-cg/vc-haip/blob/main/charter.md
- **Start date:** on approval by the group (proposed: January 2027)
- **Last modified:** see the GitHub history

## Goals

Verifiable credentials are moving into uses where a wrong decision is expensive or hard to undo: qualified attestations of attributes, business registers, product passports, supply chains, and automated decisions by software agents, industrial AI and robots. These uses need fewer options and stronger guarantees than a general data model provides.

The group develops a **high-assurance profile of the W3C Verifiable Credentials specifications**: the Verifiable Credentials Data Model (VCDM 2.1 once it is a Recommendation, staying compatible with 2.0 deployments in the meantime) together with the related specifications it relies on, such as Verifiable Credential Data Integrity and its cryptosuites, Securing Verifiable Credentials using JOSE and COSE, Bitstring Status List and Controlled Identifiers. The Profile is a cross-section of this suite: a small, testable set of choices and requirements that issuers, wallets, verifiers and the publishers of credential vocabularies can implement. The aim is a verifiable evidence layer that people and machines can rely on. It is anchored in the eIDAS trust framework and works with comparable frameworks elsewhere.

### Objectives

1. **Fewer options, same specifications.** Profile the VC specifications rather than extend them. Choose securing mechanisms, algorithms, key resolution, holder binding and status mechanisms that are mandatory to implement.
2. **Trustworthy meaning.** Make the documents that give a credential its meaning (contexts, vocabularies, schemas) verifiable: identified, integrity-protected, versioned and loaded under clear rules, so that two verifiers reach the same reading of the same credential.
3. **Regulatory alignment.** Work with existing trust frameworks, using the EU as the reference case: qualified and non-qualified attestations of attributes under eIDAS 2.0 (ETSI TS 119 472 series), trusted lists and the European Business Wallet. Keep the core usable in other jurisdictions (see below).
4. **Interoperable exchange.** Define how profiled credentials travel over existing issuance and presentation protocols, without defining new protocols.
5. **Evidence for automated decisions.** Define what a relying party, human or machine, records so that a decision based on a credential can be explained and checked later.
6. **Long-term readiness.** Provide for long-lived credentials, including algorithm agility and a transition path to post-quantum signatures.
7. **Testability.** Every normative requirement is backed by an open test, including negative tests for known attacks, wherever a test is possible.

## Why the group starts with the European Union as its reference case

The European Union is the first jurisdiction to give verifiable attestations of attributes a detailed legal framework. That framework is backed by technical standards and by wallets for citizens and, as proposed, for businesses:

- **eIDAS 2.0.** Regulation (EU) 2024/1183 amends the eIDAS Regulation (EU) No 910/2014. It introduces the European Digital Identity Wallet and makes the electronic attestation of attributes a trust service with defined legal effects. Qualified attestations and attestations from public bodies responsible for authentic sources have the same legal effect as lawfully issued paper attestations and are recognised across Member States (Article 45b).
- **European Business Wallet.** The European Commission has proposed a business wallet for companies and public bodies. It would let them exchange attestations and documents with legal effect, for example for business registration, company representation, tax, trade and supply chains.
- **Technical standards.** ETSI TS 119 472-1 already specifies how an attestation of attributes, including a qualified one, is built with the W3C Verifiable Credentials Data Model 2.0, alongside other formats. Parts 2 and 3 of the series cover presentation and issuance.
- **Legal compliance.** In these settings an organisation must be able to show that a credential it relied on met the legal requirements, and that its decision followed from it. That needs more than a valid signature.

These requirements are among the most demanding for verifiable credentials today, so the group uses the EU as its **reference case**. Qualified attestations of attributes expressed as W3C Verifiable Credentials ("qualified verifiable credentials") are the benchmark for high assurance in this group.

We expect comparable trust models to emerge in other jurisdictions soon. The group therefore works so that the profile can be used outside the EU:

- **Core and modules.** The core profile is independent of any jurisdiction. EU-specific rules (qualified status, EU trusted lists, ETSI formats) sit in a separate EU module, and other jurisdictions can add modules of their own.
- **Recognition by role.** Trust anchors and authorities are described by their role (for example, "a recognised list of trusted issuers"), not by a single legal instrument.
- **Open to others.** Participants from other jurisdictions are invited to bring their requirements, and the group will review the core against them.

### Terms used in this charter

- **Attestation of attributes (EAA).** Under eIDAS 2.0, an *electronic attestation of attributes* is an attestation in electronic form that allows attributes to be authenticated. An attribute is a characteristic, quality, right or permission of a natural or legal person or of an object. A verifiable credential that states, for example, a company's registration, a person's power of representation or a product's properties is an attestation of attributes.
- **Qualified (QEAA).** A *qualified electronic attestation of attributes* is issued by a qualified trust service provider and meets the requirements of Annex V of eIDAS 2.0. *Qualified* is a legal status. A trust service provider receives it from a national supervisory body after an independent conformity assessment, and it then appears on that Member State's trusted list. A qualified attestation carries the provider's qualified electronic signature or seal.
- **Public-body attestation (PuB-EAA).** An attestation issued by, or on behalf of, a public sector body responsible for an authentic source, such as a business register (Article 45f and Annex VII of eIDAS 2.0). In legal effect it is equivalent to a qualified attestation.
- **High assurance.** In this charter, high confidence that a verifier's result is correct and can be explained and checked later. It covers:
  - who issued the credential, and whether they were authorised to issue it;
  - that it is unchanged and still valid;
  - that the verifier reads its content with the meaning the issuer intended;
  - that the decision can be reproduced as evidence.

  The term is used in the profile's own sense. It is distinct from, though compatible with, the eIDAS assurance levels for electronic identification means (low, substantial, high).
- **Legal compliance.** Meeting the legal requirements that apply to issuing and relying on a credential: eIDAS and its implementing acts, data protection law, and sector rules such as those for product passports or anti-money-laundering checks. The profile supports compliance by making requirements explicit and testable. It does not by itself establish legal recognition, which remains with the competent authorities (see Out of Scope).

## Scope of Work

- A profile of the VC specifications (VCDM 2.1, compatible with 2.0, and the related specifications named under Goals) covering:
  - securing mechanisms (Data Integrity and VC-JOSE-COSE) and their parameters;
  - algorithms and cryptographic agility;
  - issuer identification, issuer authorisation and key resolution;
  - holder binding and selective disclosure;
  - credential status;
  - rules for the integrity, versioning and loading of contexts, vocabularies and schemas;
  - serialisation rules (JSON-LD, and where needed CBOR-LD and YAML-LD);
  - records of verification decisions.
- An EU module for qualified and public-body attestations of attributes, and room for modules for other jurisdictions.
- Bindings of the profile to existing protocols, for example OpenID for Verifiable Credential Issuance and Presentations, the Digital Credentials API, and the W3C VC API.
- Conformance classes for issuers, holders/wallets, verifiers, vocabulary publishers and registry operators.
- Use cases and requirements; a conformance test suite.

## Out of Scope

- Changes to the VC data model, and the standardisation of new securing mechanisms or cryptographic primitives. The group may describe experimental securing mechanisms (for example, approaches that authenticate a credential before any JSON-LD processing) in non-normative notes, test cases and worked examples, and may incubate them as separate draft specifications, distinct from the Profile, for later submission to a W3C Working Group.
- New issuance or presentation protocols.
- Credential formats other than W3C VCDM (for example SD-JWT VC and ISO mdoc), except for informative comparison.
- Legal recognition, accreditation or certification decisions, which belong to the relevant authorities.

## Deliverables

### Specifications

- **High Assurance Profile for W3C Verifiable Credentials** (working title). It profiles VCDM 2.1 and the related specifications named under Goals. Proposed short name: *VC-HAP*, which cannot be confused with OpenID's High Assurance Interoperability Profile (HAIP). The group confirms the name and short name early; the group's own name stays unchanged.
- **Experimental securing mechanisms** (optional): separate draft specifications, distinct from the Profile, incubated for later submission to a W3C Working Group. They are not part of the Profile's conformance requirements.

### Non-Normative Reports

- **Use Cases and Requirements.**
- **Alignment notes** with related specifications, for example the ETSI TS 119 472 series and OpenID4VC HAIP.
- **Notes on experimental securing mechanisms**, non-normative, with test cases and worked examples.

The group may produce other Community Group Reports within the scope of this charter that are not Specifications, such as use cases, requirements, or white papers.

### Test Suites and Other Software

The group MAY produce test suites to support the Specifications. Please see the GitHub LICENSE file for test suite contribution licensing information.

## Dependencies or Liaisons

- **W3C:**
  - Verifiable Credentials Working Group;
  - JSON-LD Working Group;
  - Credentials Community Group;
  - Federated Identity Working Group (Digital Credentials API).
- **OpenID Foundation:** Digital Credentials Protocols Working Group.
- **ETSI:** TC ESI (Electronic Signatures and Trust Infrastructures).
- **IETF:** working groups on JOSE/COSE, OAuth and SCITT, where relevant.
- **European projects and programmes:** large-scale pilots on the EU Digital Identity Wallet and the European Business Wallet, and comparable programmes elsewhere.

The group may propose its Specification for standardisation in a W3C Working Group.

## Community and Business Group Process

The group operates under the Community and Business Group Process. Terms in this Charter that conflict with those of the Community and Business Group Process are void.

As with other Community Groups, W3C seeks organizational licensing commitments under the W3C Community Contributor License Agreement (CLA). When people request to participate without representing their organization's legal interests, W3C will in general approve those requests for this group with the following understanding: W3C will seek and expect an organizational commitment under the CLA starting with the individual's first request to make a contribution to a group Deliverable. The section on Contribution Mechanics describes how W3C expects to monitor these contribution requests.

The W3C Code of Conduct and W3C Antitrust and competition policy apply to participation in this group.

## Work Limited to Charter Scope

The group will not publish Specifications on topics other than those listed under Specifications above. See below for how to modify the charter.

## Contribution Mechanics

Substantive Contributions to Specifications can only be made by Community Group Participants who have agreed to the W3C Community Contributor License Agreement (CLA).

Reports other than Specifications published by this group should use the W3C Software and Document License where possible.

Community Group participants agree to make all contributions in the GitHub repo the group is using for the particular document. This may be in the form of a pull request (preferred), by raising an issue, or by adding a comment to an existing issue.

All GitHub repositories attached to the Community Group must contain a copy of the CONTRIBUTING and LICENSE files.

## Transparency

The group will conduct all of its technical work in public. If the group uses GitHub, all technical work will occur in its GitHub repositories (and not in mailing list discussions). This is to ensure contributions can be tracked through a software tool.

Meetings may be restricted to Community Group participants, but a public summary or minutes must be posted to the group's public mailing list, or to a GitHub issue if the group uses GitHub.

## Decision Process

This group will seek to make decisions where there is consensus. Proposals are discussed in GitHub issues. Where consensus is not clear, the Chairs may run a Call for Consensus of at least seven days. Decisions are recorded in GitHub issues.

If substantial disagreement remains and the group needs to decide an issue to make progress, the Chairs will choose an alternative that had substantial support, after a vote of participants if necessary. Individuals who disagree with the choice are strongly encouraged to take ownership of their objection by taking ownership of an alternative fork. This is explicitly allowed (and preferred to blocking progress) to let implementation experience inform which spec is ultimately chosen by the group to move ahead with.

Any decisions reached at any meeting are tentative and should be recorded in a GitHub issue. Any group participant may object to a decision reached at an online or in-person meeting within 7 days of publication of the decision, provided that they include clear technical reasons for their objection. The Chairs will facilitate discussion to try to resolve the objection according to this decision process.

It is the Chairs' responsibility to ensure that the decision process is fair, respects the consensus of the CG, and does not unreasonably favor or discriminate against any group participant or their employer.

## Chair Selection

Participants in this group choose their Chair(s) and can replace their Chair(s) at any time using whatever means they prefer. However, if 5 participants, no two from the same organization, call for an election, the group must use the election process described in the W3C Community Group charter template, consulting the Community Development Lead on election operations.

## Amendments to this Charter

The group can decide to work on a proposed amended charter, editing the text using the Decision Process described above. The decision on whether to adopt the amended charter is made by conducting a 30-day vote on the proposed new charter. The new charter, if approved, takes effect on either the proposed date in the charter itself, or 7 days after the result of the election is announced, whichever is later. A new charter must receive 2/3 of the votes cast in the approval vote to pass. The group may make simple corrections to the charter, such as deliverable dates, by the simpler group decision process rather than this charter amendment process. The group will use the amendment process for any substantive changes to the goals, scope, deliverables, decision process or rules for amending the charter.
