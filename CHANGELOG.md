# Changelog

Notable BioLit AI changes are recorded here using a simplified [Keep a Changelog](https://keepachangelog.com/en/1.1.0/) format. Release entries document project milestones, **not** certification of scientific or production readiness.

## [Unreleased]

### Planned / under consideration
- Structured, source-linked scientific information extraction from full-text PDFs.
- Secure AI analysis backend and citation-grounded outputs.
- Better study comparison, evidence provenance, and verification workflows.
- More comprehensive automated and cross-device testing.

## [2.0.0] — 2026-11-01 — Midterm Prototype

**GitHub release:** `V2.0`  
**Deployment:** https://jessehokj.github.io/BioLit-ai/  
**Status:** Accepted functional midterm prototype with known limitations.

### Added
- Searchable article library with tag filtering and edit/delete controls.
- Smart DOI import using Crossref publication metadata.
- PDF selectable-text extraction using PDF.js.
- Expanded article editor with abstract, research question, methods, findings, limitations, tags, source type, and extracted text.
- JSON backup import alongside export.
- Optional AI Research Assistant interface for a separately deployed HTTPS analysis backend.
- Scientific-verification and privacy notices.
- Documentation and test plan (`README.md`, `CHANGELOG.md`, `TESTING_CHECKLIST.md`).

### Changed
- Expanded the V1.0 workflow into six sections: Article Library, Smart Import, Article Editor, Compare Studies, Evidence Review, and AI Assistant.
- Updated article records and local storage handling for V2.0.
- Added migration logic intended to copy V1.0 records into V2.0 storage without modifying the original V1.0 records.
- Clarified that study comparison displays saved notes, not independently generated scientific synthesis.
- Merged `v2-development` into `main` through the midterm pull request; deployed V2.0 from `main` using GitHub Pages.
- Preserved the original V1.0 prototype as a separate GitHub release/tag.

### Observed testing and release validation
- GitHub Pages build and deployment completed successfully; the live website was reported working.
- Article saving and deletion were observed in manual tests.
- DOI metadata lookup populated bibliographic fields for a tested DOI.
- PDF text extraction populated the extracted source-text field, but not structured scientific interpretation fields.
- Comparison article selection and the AI interface were demonstrated; full end-to-end validation of every workflow was not documented.

### Known limitations / unverified cases
- DOI lookup does not infer methods, findings, or limitations.
- PDF extraction may use a filename as a provisional title and does not turn extracted text into structured study analysis; scanned PDFs require OCR not included here.
- Comparisons depend on the quality of saved records.
- AI analysis requires an external secure backend; none was configured during reported tests.
- Browser-local storage has no cloud sync or cross-device persistence.
- Complete JSON backup restoration, migration integrity, evidence-review regression, accessibility, and cross-device acceptance testing are not yet fully evidenced. See [TESTING_CHECKLIST.md](TESTING_CHECKLIST.md).

## [1.0.0] — 2026-11-01 — Original Prototype

**GitHub release:** `V1.0` (historical source snapshot)

### Added
- Article library with fictional example records.
- Manual article entry.
- Side-by-side comparison of two distinct saved articles.
- Evidence review with user-selected assessment and reasoning.
- JSON export of saved records.
- Browser-local record storage.

### Earlier manual observations
- Application opened and fictional records loaded.
- Study comparison rendered and rejected choosing the same article twice.
- Evidence reviews saved.
- JSON export completed.

These observations were not a comprehensive automated test suite.

## Release and branch policy

`main` now contains the released V2.0 midterm prototype. `v2-development` was merged and may remain as a historical branch. The V1.0 and V2.0 tags preserve their respective release commits. Future changes should be made on separate branches and merged after testing; do not rewrite historical release tags.
