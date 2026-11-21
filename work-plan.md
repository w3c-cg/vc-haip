# [DRAFT] Work plan

A proposal for the group's first year. Dates are targets and will be adjusted by the group.

## Phase 0: set up (November 2026 – December 2026)

- Agree the charter and choose Chair(s).
- Set up the repository: README, CONTRIBUTING, LICENSE, issue labels (`use-case`, `requirement`, `profile`, `test`, `liaison`), and a ReSpec skeleton for each deliverable.
- Confirm the name and short name of the Specification (proposed: *High Assurance Profile for W3C Verifiable Credentials*, *VC-HAP*).
- Call for use cases, implementations and candidate input documents.
- Agree a meeting rhythm (proposal: a call every two weeks, minutes posted as GitHub issues).

## Phase 1: use cases, requirements and first draft (January – March 2027)

- **Use Cases and Requirements:** first public draft. Each requirement has an identifier, the role it applies to (issuer, holder/wallet, verifier, vocabulary publisher, registry operator, ecosystem authority) and a test approach.
- **Profile:** first editor's draft covering:
  - securing mechanisms;
  - algorithms;
  - key resolution;
  - status;
  - integrity and loading of contexts and vocabularies.
- **Test suite:** structure, the first positive and negative test vectors, and a runner.
- **Alignment note:** a first comparison with the ETSI TS 119 472 series and OpenID4VC HAIP.
- **EU reference case:** map the profile to EU requirements for attestations of attributes (EAA, QEAA, PuB-EAA). Separate the jurisdiction-neutral core from an EU module.

## Phase 2: complete draft and implementations (April – August 2027)

- **Profile:** complete draft, including protocol bindings, holder binding, selective disclosure, decision records and algorithm agility.
- **Test suite:** tests for every testable requirement.
- **Implementation reports:** at least two independent implementations per conformance class.
- **Other jurisdictions:** invite requirements from trust frameworks outside the EU, and review the core profile against them.
- **Liaison:** exchange with the VC and JSON-LD Working Groups, the OpenID DCP Working Group and ETSI TC ESI on open points, such as format identifiers and qualified attestations secured with Data Integrity.

## Phase 3: report and next steps (September – December 2027)

- Final Community Group Report for the Profile and for Use Cases and Requirements.
- Decide whether to propose the Profile for the W3C Recommendation track.
- Plan the next revision: post-quantum suites once W3C publishes them as Recommendations, and lessons from deployments.

## Ways to contribute now

- **Use cases:** open an issue with the `use-case` label. Describe who relies on the credential, what goes wrong if it is wrong, and what assurance you need.
- **Implementations:** tell us what you build: issuer, wallet, verifier, vocabulary publishing or registry.
- **Input documents:** point to existing analyses, profiles or test suites the group should consider.
