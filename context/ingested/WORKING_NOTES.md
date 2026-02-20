# Context Working Notes

Date: 2026-02-20

## Ingestion Outputs

- File index and metadata: `context/ingested/context-index.json`
- Auto-generated digest: `context/ingested/CONTEXT_INGESTED.md`
- Full extracted text for PDF sources:
  - `context/ingested/CCPART1V3.1R5.txt`
  - `context/ingested/CCPART2V3.1R5.txt`
  - `context/ingested/CCPART3V3.1R5.txt`
  - `context/ingested/CEMV3.1R5.txt`

## Source Status

- Ingested successfully: CC portal pages, CC/CEM PDFs, ETSI page, EUR-Lex eIDAS page, GQSCD ideas page, CEN/CENELEC search pages.
- ISO pages (`context/iso-15408-1-72891.html`, `context/iso-15408-2-72892.html`, `context/iso-15408-3-72893.html`) contain Cloudflare challenge pages, not the final ISO content.

## High-Value Anchors

### eIDAS (Regulation (EU) No 910/2014)

From `context/eur-lex-CELEX-32014R0910.html`:

- Definition of qualified electronic signature: line 7417
- Definition of qualified electronic signature creation device (QSCD): line 7613
- Article 29 (QSCD requirements, Annex II linkage): lines 9683-9689
- Article 30 (QSCD certification): lines 9693-9698
- Article 31 (publication of certified QSCD list): lines 9740-9748
- Recital mention of ISO 15408 as an important tool for QSCD security certification: line 6811

### Common Criteria Part 1 (conceptual framework)

From `context/ingested/CCPART1V3.1R5.txt`:

- TOE concept and representations: lines 85-87
- Protection Profile section: lines 111-117
- Security Target specification section: line 129
- ST/TOE evaluation results: lines 126 and 128
- Glossary-style definitions include:
  - evaluation assurance level (EAL): lines 455-457
  - Protection Profile: lines 531-535

### Common Criteria Part 3 (assurance components / EALs)

From `context/ingested/CCPART3V3.1R5.txt`:

- Assurance class structure: lines 88-89
- EAL structure and EAL1-EAL7 overview: lines 94 and 111-117
- ASE classes (ST evaluation): lines 143-149
- ADV classes (development): lines 151-158
- AGD classes (guidance): lines 161-162
- ALC classes (lifecycle support): lines 164-165

### CEM (evaluation methodology)

From `context/ingested/CEMV3.1R5.txt`:

- Evaluator verdict model and terminology: lines 88, 391, 413-415
- Work units model and mapping: lines 417-420
- Evaluation activities by assurance classes: lines 441-444
- Evidence handling emphasis: lines 378-379 and 462-465

### GQSCD ideas page

From `context/gqscd-ideas.html`:

- Requirement namespace pattern `REQ-GQSCD-##`: lines 299-304
- QSCD definition wording aligned to Annex II outcome framing: lines 377-379
- Sole control definition anchor: lines 385-388
- Deterministic verifier-style error codes (`ERR-GQSCD-*`): lines 604-626

## Practical Use

- For legal/QSCD mapping work, start from eIDAS anchors above and map to Annex II outcomes.
- For evaluation and conformance structure, use Part 1 (PP/ST/TOE) + Part 3 (assurance classes/EALs) + CEM (work units and verdicts).
- For repo drafting style and requirement structure, align with the existing GQSCD requirement and error-code pattern.

## Samsung/Knox Additions (2026-02-20)

- Added source files:
  - `context/samsung-galaxy-s25-ultra.html`
  - `context/samsung-knox-mobile-security-whitepaper.html`
  - `context/samsung-knox-vault.html`
  - `context/samsung-knox-tima-keystore.html`
- Added snippets in `context/ingested/` for all four pages.
- Added metadata entries to `context/ingested/context-index.json` and regenerated `context/ingested/CONTEXT_INGESTED.md`.

## Samsung/Android/BSI Additions (2026-02-20)

- Added source files:
  - `context/samsung-news-s25-series-true-ai-companion.html`
  - `context/android-security-key-attestation.html`
  - `context/bsi-pp-0084.html`
- Added snippets in `context/ingested/` for all three pages.
- Added metadata entries to `context/ingested/context-index.json` and regenerated `context/ingested/CONTEXT_INGESTED.md`.

