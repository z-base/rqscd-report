“Publishable” depends on what you’re claiming.

Publishable as an informative public draft (blog-style security analysis / design note, clearly non-normative, not a certification claim)

RQ-SCD report: Yes, if it’s explicitly framed as a threat-model / design argument for remote QSCD flows and it anchors the regulatory + standards baseline in current primary references (not vendor blogs). In 2026, that baseline should at least reflect eIDAS as amended by Regulation (EU) 2024/1183 (remote QSCD management becomes a qualified trust service category) and the current ETSI remote-QSCD policy spec TS 119 431-1 v1.3.1 (2024-12), plus the remote signing protocol spec TS 119 432.

LQ-SCD report: Yes, if it’s clearly a “mapping / feasibility” note and not implying the device is a QSCD. For local QSCD security assessment “what standards apply” the Commission Implementing Decision (EU) 2016/650 is still a key reference point, and you’ll want to align with the more recent EUCC state-of-the-art guidance on QSCD certification as well.

Publishable as an audit-grade evaluation (something you’d hand to a CAB, regulator, or expect to survive adversarial review)

RQ-SCD report: Not yet (likely) unless it has (a) a complete, testable threat model with explicit attacker classes and assumptions; (b) “court-verifiable” evidence requirements specified as concrete artifacts and verification procedures (not just “logs exist”); and (c) citations that are mostly primary/authoritative (EUR-Lex, ETSI PDFs, official PP repos / certification portals), with version pinning. For wallet/QES context, the EUDI ARF requirements explicitly point to ETSI TS 119 431-1/432 and SCAL2 alignment with EN 419 241-1—so readers will expect you to line up against that style of requirement language and traceability.

LQ-SCD report: Not yet (likely) unless it cleanly separates (1) what a local QSCD is legally (certified and listed) from (2) what a platform could potentially satisfy technically. Audit-grade also means your PP references are verifiable and current; for SSCD PP material, relying on maintained PP pages (e.g., SOG-IS SSCD PP parts) is far stronger than “random PDF somewhere.”

The practical litmus test:

If your docs say “this is an unofficial draft / not a legal finding / not a certification claim” and stick to defensible “could / would require / subject to certification” language: publishable as public research notes.

If either doc claims or strongly implies compliance/certification without a fully traceable evidence trail and mostly primary citations: not publishable as an evaluation (you’ll get shredded by anyone who’s done CC/QSCD work).

One extra gotcha that affects both: make sure any referenced specs are pinned by exact identifier + version/date (e.g., TS 119 431-1 v1.3.1 (2024-12)), because those documents do change and eIDAS2 shifted the ground under remote QSCD management.
