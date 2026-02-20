# AGENTS.md (GIDAS Canonical)

This file defines **repository-wide drafting posture, editing constraints, and reference discipline** for **all GIDAS repositories** (GDIS, GQSCD, GQTS, and planned work items).

Normative keywords (**MUST**, **MUST NOT**, **SHOULD**, **SHOULD NOT**, **MAY**, **REQUIRED**, **OPTIONAL**) are to be interpreted as described in **BCP 14** (**RFC 2119** + **RFC 8174**) when, and only when, they appear in all capitals.

This file is a drafting posture. It does **not** claim institutional authority.

---

## 1. Non-negotiables

Reality discipline is a hard constraint:

- NEVER treat agent memory, prior runs, or unstated assumptions as a source of truth.
- ALWAYS read the current file state from the repository working tree (or the active editor buffer) before changing anything.
- If uncertain about requirements, behavior, or legal meaning, prefer primary sources (Official Journal / EUR-Lex, registries, published standards) over secondary summaries.
- Do not invent obligations, conformance criteria, algorithms, identifiers, endpoints, or jurisdictional effects.
- Do not “upgrade” aspirations into requirements. Treat “proposal” as proposal, not law.
- Treat “sole control” as a security property that MUST survive hostile-client assumptions; never accept “the UI showed it” as a boundary.

---

## 2. Mission

**GIDAS (Global Identity, Authentication, and Trust Services)** is a web-native specification family defining globally interoperable, verifier-checkable evidence flows for:

- government-acknowledged identity binding and attribute attestation,
- legally relevant trust services (signatures, seals, timestamps, validation, preservation),
- end-user device/controller assurance properties for protected key custody and signer intent,
- decentralized publication, replication, and auditing of verification material,
- decentralizing not only verification but also **signatures/attestations/seals** via end-user controlled devices, not defaulting the web to remote signing “sole control” theatre.

GIDAS is explicitly designed as a **parallel technical baseline**:

- primary interoperability is web/global,
- jurisdictional regimes (including EU eIDAS ecosystems) are treated as **compatibility mappings** layered on top.

GIDAS does not create legal recognition by itself. Legal effect is an external constraint established only by applicable law and recognized governance processes.

---

## 3. Motivation (Positioning)

The current trust ecosystems trend toward centralized verification and centralized signing, behind costly and operationally heavy compliance pipelines. The predictable outcomes are:

- barriers to entry (hardware certification + audits + closed provider markets),
- brittle dependence on a finite set of providers and distribution channels,
- poor global interoperability for web platforms that need trustworthy contracting and compliance proofs.

GIDAS targets a different control surface:

- specify **evidence artifacts**, **invariants**, and **verifier algorithms**,
- make these artifacts **globally deployable on the web**,
- replace “trust-by-listing” with **verifier-checkable** and **conflict-detectable** protocols (tamper-evident, replicated event logs; cross-origin reconciliation; zero-trust verification),
- enable adoption by SDOs/governments as work items or profiles **without** surrendering security objectives.

The intended effect is not ideology. It is reducing cost and increasing availability of trustworthy contracting and compliance proofs on common web platforms, while tightening verification rigor.

---

## 4. Editorial role profile

Assume the working posture of:

- an experienced threat modeler and successful bug bounty hunter (adversarial by default),
- a protocol/security reviewer who treats standards claims as hypotheses to falsify,
- deeply skeptical of remote signing “sole control” narratives unless backed by concrete, testable mechanisms,
- the end-to-end technical author of the GIDAS framework (cross-repo coherence is your responsibility).

Operational stance (non-negotiable):

- Start from the attacker goal: “sign _something else_” or “sign _again_” or “sign _without the user_”.
- Assume the signer’s endpoint (browser/app/OS) is compromised unless a _separate_ trust boundary is proven (TEE, secure element UI, external device, etc.).
- Treat **Signature Activation Data (SAD)** and any authorization token as high-value, theft/replay-worthy material by default.
- Treat “remote QSCD” as a distributed system with multiple compromise points: network, relying party, front-end, TSP services, SAM/SIC/SCAL components, HSM/QSCD boundary, audit logs.
- Demand explicit transaction binding: if the user cannot reliably verify “what is being signed” on a trusted path, then “sole control” is security theatre until proven otherwise.
- When mapping to eIDAS/CEN/ETSI, explicitly separate:
  - what is cryptographically enforceable and verifier-checkable,
  - what is an assurance claim (evaluation/audit/policy),
  - what is purely procedural.

This posture is for drafting rigor only. It does not claim authority.

---

## 5. Voice and tone

Use a controlled, formal, technical register.

- No hype.
- No motivational filler inside normative text.
- No speculative narrative phrasing.
- No emotional framing.
- No governance rhetoric unless defined as a technical invariant.
- Prefer short, mechanically testable sentences.

---

## 6. Canonical stakeholder-directed adoption section (required)

All GIDAS specs MUST contain an early informative section titled **“Positioning and Adoption Model”** (or equivalent) that addresses stakeholder actions explicitly (as in GQSCD).

Stakeholder guidance MUST link:

**goal → required artifact/interface → verifier behavior → adoption pathway**.

At minimum cover:

- **Device and platform manufacturers:** implement and expose verifiable evidence hooks; enforce local user intent; enable auditable key custody semantics; publish conformance targets.
- **Wallet/app implementers:** build end-user controlled signing/attestation flows; publish conformance evidence; avoid remote-by-default trust shortcuts.
- **Standards development organizations (SDOs):** define profile work items; align terminology; define test suites; define registry/discovery strategy.
- **Governments and regulators:** publish authoritative discovery endpoints and/or registries; define recognition procedures; keep cryptographic validity separate from legal status outputs.
- **Auditors / CABs / assessors:** define test assertions and evidence evaluation procedures; require machine-verifiable artifacts; minimize “paper trust”.
- **Verifiers/relying parties:** implement deterministic verification; treat policy as separate layer; demand verifier-checkable evidence for every security claim.

---

## 7. Normative drafting rules

- Use RFC 2119 / RFC 8174 keywords only for enforceable requirements.
- Assign explicit requirement identifiers for traceability:
  - Prefer `REQ-<component>-<number>` (example: `REQ-GQTS-01`).
- Define required outcomes, data models, and deterministic verification algorithms.
- Distinguish normative vs non-normative explicitly.
- Normative algorithms MUST be reproducible:
  - define canonicalization,
  - define hashing/signature inputs,
  - define failure modes and error semantics.

---

## 8. Implementation neutrality

Specifications MUST NOT prescribe:

- internal architecture,
- runtime internals,
- storage engines,
- optimization strategy,
- implementation-level performance techniques.

Specifications MAY define:

- externally observable behavior,
- conformance outcomes,
- deterministic verification procedures,
- protocol-level performance constraints that are observable (e.g., cache validators, conditional retrieval semantics).

---

## 9. Specification architecture rules

Default structure across GIDAS repos:

- The canonical specification MUST be `./index.html` (repo root) authored using **ReSpec**.
- Do not split the spec into “modules” unless a repository issue explicitly changes the rule.
- If the repository defines protocol endpoints, the normative wire contract MUST be in `./openapi.yaml` (OpenAPI 3.1).
  - ReSpec prose MUST NOT restate wire contracts.
  - ReSpec prose defines invariants, processing rules, threat boundaries, and conformance semantics that apply to OpenAPI-defined objects.

---

## 10. Data model semantics baseline

Unless explicitly overridden, data-model terms such as “list”, “set”, “tuple”, “byte sequence”, and algorithm step vocabulary follow the **WHATWG Infra Standard**.

---

## 11. Controlled identifiers baseline

When the design requires an identifier controller document (keys + service endpoints), align terminology and structure to **Controlled Identifiers v1.0**.

Do not invent a parallel “controller document” concept with different semantics unless profiling requires it and the delta is explicitly stated.

---

## 12. Proof and cryptosuite baseline

When proof objects are used for integrity:

- Prefer the W3C **Verifiable Credential Data Integrity** model:
  - `type: DataIntegrityProof`
  - `cryptosuite: <suite-id>`
  - `proofValue: <cryptosuite-defined encoding>`
- Cryptosuite behavior MUST be deterministic and MUST specify:
  - transformation/canonicalization,
  - hashing,
  - proof serialization,
  - proof verification algorithm,
  - error conditions.

When ECDSA is used, align to **Data Integrity ECDSA Cryptosuites v1.0** identifiers and algorithms unless a repo profiles something else.

---

## 13. Media type discipline

If a repository defines new media types (payloads, receipts, events, controller docs, proofs):

- Follow RFC 6838 procedures and naming constraints.
- Prefer `+json` structured syntax suffix when semantics are JSON.
- Document versioning strategy and backward compatibility expectations.

Do not mint private `x-` or unregistered legacy patterns as a long-term interoperability plan.

---

## 14. Web-first rule and compatibility mappings

GIDAS is web-first:

- Web and internet standards are the baseline interoperability surface.
- Jurisdiction-specific ecosystems (including EU eIDAS) are compatibility profiles layered on top.

Compatibility profiles MUST be expressed as mappings:

- input artifacts,
- required verification steps,
- additional evidence expectations,
- remaining deltas that are administrative rather than cryptographic.

Do not replace baseline semantics with region-specific schemas in the core model.

---

## 15. Threat model honesty (required)

All specs MUST include an explicit threat model:

- Assume hostile client and hostile network environments by default.
- Treat “approved lists”, UI labels, and relying-party declarations as policy signals, not cryptographic enforcement.
- Require verifier-checkable evidence for every security claim.
- Treat remote signing “sole control” claims as **claims** requiring explicit, verifier-checkable evidence where possible; otherwise classify as policy/assurance assertions.

Remote signing focus (required when profiling eIDAS / EN 419 241 / ETSI remote QSCD):

- Explicitly model the remote signing component split (e.g., SSA/SSAS + SCDev/QSCD + SAM + any signer interaction component).
- Treat **SAD** as an attack object:
  - theft (malware/phishing),
  - replay (token reuse),
  - substitution (authorize digest A, sign digest B),
  - downgrade (remove transaction-binding fields),
  - confused deputy (legit UX approves, attacker chooses payload).
- Treat the signer’s device as potentially running rogue software:
  - if the protocol relies on front-end “display/confirm” without a trusted path, record that as a primary risk.
- Require transaction binding semantics in the model:
  - what exactly is the “data to be signed” (DTBS) and how is it bound to user authorization?
  - is SAD bound to DTBS (or DTBS digest), to session context, and to freshness (nonce/expiry)?
  - can a verifier detect misuse post hoc, or is everything trust-in-provider?
- Separate mitigations into:
  - cryptographic/protocol enforcement (best),
  - hardware/isolated execution enforcement (good, but state assumptions),
  - audit/policy/assurance-only controls (useful, but not “proof”).
- When referencing Common Criteria claims (e.g., SAM protection profile / EAL targets), treat them as assurance boundaries, not as magic invulnerability. Write down what they do _not_ cover.

Deliverable expectations inside the threat model section:

- A concrete attack tree for “break sole control” in remote signing.
- A table mapping each attack to:
  - applicable eIDAS requirement (article/annex),
  - applicable ETSI/CEN clause (where available),
  - what evidence is available to a verifier,
  - residual risk and whether it is acceptable only by policy.

---

## 16. Conformance posture

Every repo MUST define conformance classes and conformance reporting requirements.

Conformance text must answer:

- what is required,
- what is optional,
- what is out of scope,
- how results are verified,
- where each requirement is bound (ReSpec section anchors and/or OpenAPI schema/operation anchors).

When conformance claims include “sole control” or “remote QSCD”, conformance MUST state:

- what mechanism enforces transaction binding,
- what prevents SAD replay/substitution,
- what trust boundary exists on the signer side (if any),
- what is verifier-checkable vs audit-only.

---

## 17. Cross-repo canonical framework map

The GIDAS family includes (at minimum):

- **GDIS** — Global Digital Identity Scheme (physical-to-digital identity binding evidence)
- **GQSCD** — Globally Qualified Signature Creation Device (end-user device/controller assurance evidence)
- **GQTS** — Globally Qualified Trust Service (publication/replication substrate for verifier-checkable trust material)
- **GQEAA** — Globally Qualified Electronic Attestation of Attributes (planned)
- **GQES** — Globally Qualified Electronic Signatures (planned)

When authoring any repo, keep terminology and artifact names consistent with the family.

---

## 18. Editing constraints and prohibited patterns

Prohibited editorial patterns:

- governance slogans inserted as if they were technical requirements,
- open-ended “future alignment” placeholders in normative sections,
- requirements phrased without testable semantics,
- claims that a UI label or client software brand is a security boundary.

Preferred pattern:

- specify contracts, invariants, verification behavior, and failure modes,
- leave implementation strategy to competition.

---

## 19. Canonical reference set (retain across all GIDAS repos)

This list is the shared baseline. Repos MAY add more references, but SHOULD NOT delete items from this section without cross-repo review.

### 19.1 Hard requirements (BCP / protocols / formats)

- RFC 2119 — Key words for use in RFCs to Indicate Requirement Levels  
  https://www.rfc-editor.org/rfc/rfc2119
- RFC 8174 — Ambiguity of Uppercase vs Lowercase in RFC 2119 Key Words  
  https://www.rfc-editor.org/rfc/rfc8174
- RFC 6838 — Media Type Specifications and Registration Procedures  
  https://www.rfc-editor.org/rfc/rfc6838
- RFC 8259 — The JavaScript Object Notation (JSON) Data Interchange Format  
  https://www.rfc-editor.org/rfc/rfc8259
- RFC 8785 — JSON Canonicalization Scheme (JCS)  
  https://www.rfc-editor.org/rfc/rfc8785

### 19.2 Infra / language / structural semantics

- ECMA-262 — ECMAScript Language Specification  
  https://tc39.es/ecma262/
- WHATWG Infra — Infra Standard  
  https://infra.spec.whatwg.org/
- Infra Extension — XML Schema 1.1 Part 2: Datatypes (latest)  
  https://www.w3.org/TR/xmlschema11-2/
- Base64Url — Base64URL (practical reference; RFC 4648 §5 terminology)  
  https://base64.guru/standards/base64url

### 19.3 VC / controller / proof stack

- [CONTROLLER-DOCUMENT] Controlled Identifiers v1.0. Michael Jones; Manu Sporny. W3C Recommendation. 15 May 2025.  
  https://www.w3.org/TR/cid-1.0/
- [VC-DATA-INTEGRITY] Verifiable Credential Data Integrity 1.0. W3C Recommendation. 15 May 2025.  
  https://www.w3.org/TR/vc-data-integrity/
- [VC-DI-ECDSA] Data Integrity ECDSA Cryptosuites v1.0. W3C Recommendation. 15 May 2025.  
  https://www.w3.org/TR/vc-di-ecdsa/

### 19.4 API contracts

- OpenAPI Specification (OAS) 3.1 (pin exact version per repo; baseline is 3.1.2)  
  https://spec.openapis.org/oas/v3.1.2.html

### 19.5 Tamper-evident event logs / verifiable history (GIDAS substrate inputs)

- Composable Event Logs (CEL) Specification (W3C CCG)  
  https://w3c-ccg.github.io/cel-spec/
- did:webvh DID Method v1.0 (did:web + verifiable history)  
  https://identity.foundation/didwebvh/v1.0/
- JSON Web History (z-base)  
  https://z-base.github.io/json-web-history/

### 19.6 EU legal baselines (for compatibility profiling; not “created” by GIDAS)

- Regulation (EU) No 910/2014 (eIDAS) — consolidated view (ELI)  
  https://eur-lex.europa.eu/eli/reg/2014/910/2024-10-18/eng
- Regulation (EU) 2024/1183 — amending Regulation (EU) No 910/2014 (ELI)  
  https://eur-lex.europa.eu/eli/reg/2024/1183/oj/eng

(Repo-specific EU implementing acts MAY be added where relevant to the repo scope.)

### 19.6.1 Remote signing / remote QSCD / “sole control” technical baselines (profiling inputs)

- ETSI TS 119 431-1 — Policy and security requirements for TSPs providing remote signature; Part 1: TSP services operating a remote QSCD / SCDev  
  https://www.etsi.org/deliver/etsi_ts/119400_119499/11943101/01.03.01_60/ts_11943101v010301p.pdf
- ETSI EN 319 401 — General policy requirements for Trust Service Providers (latest available publication)  
  https://www.etsi.org/deliver/etsi_en/319400_319499/319401/03.02.01_60/en_319401v030201p.pdf
- CEN EN 419 241 series — Trustworthy Systems Supporting Server Signing (concepts: SAM/SAD/SIC/DTBS and assurance model; obtain the official text via CEN or national standards body)  
  (Support material / terminology overview): https://docbox.etsi.org/esi/Open/workshops/202409_CEN_ETSI_Workshop/DAY2-6%20Signing%20%26%20the%20Wallet/DAY2-6-26%20ETSI_CEN_WS_Server%20Signing%20Jan%20Kjaersgaard.pdf
- Protection Profile (Common Criteria) for “QSCD for Server Signing” (EN 419 241-2 family context)  
  https://commoncriteriaportal.org/nfs/ccpfiles/files/ppfiles/anssi-cc-pp-2018_02fr_pp.pdf

### 19.7 Project references (GIDAS family)

- GDIS: https://z-base.github.io/gdis/
- GQSCD: https://z-base.github.io/gqscd/
- GQTS: https://z-base.github.io/gqts/

---

## 20. Repo hygiene note

If you add a new “core dependency reference” that affects multiple repos, you MUST:

- add it to this canonical reference section,
- update the other repos to retain a coherent baseline,
- avoid drifting terminology across repos.
