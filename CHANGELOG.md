# Changelog

Notable BioLit AI changes are recorded here. This project follows a simplified [Keep a Changelog](https://keepachangelog.com/en/1.1.0/) structure. Version 2.0 is **in development**, not a verified production release.

## [Unreleased] — v2.0 development (2026-11-01)

### Added (implemented in code; functional testing pending)
- Searchable article library and tag filtering.
- Edit and delete controls for saved articles and evidence reviews.
- DOI metadata lookup using Crossref.
- PDF selectable-text extraction using PDF.js.
- Expanded article editor with abstract, tags, source type, and extracted source text.
- JSON backup import alongside export.
- Optional AI assistant interface for a separately configured HTTPS backend.
- User-facing notices about scientific verification and imported content.

### Changed
- Expanded navigation from the v1.0 research workspace to include Smart Import, Article Editor, and AI Assistant sections.
- Updated record format and local storage handling for v2.0.
- Added code intended to copy existing v1.0 records into v2.0 storage without changing v1.0 data; **migration requires testing**.
- Clarified that study comparisons display saved notes rather than generating independent scientific conclusions.

### Limitations / pending
- No built-in AI model or hosted backend.
- DOI import does not automatically generate scientific methods, findings, or limitations.
- PDF import extracts text but does not automatically populate scientific interpretation fields.
- No OCR for image-only PDFs.
- Browser, mobile, migration, DOI, PDF, and backup tests remain pending.

## [1.0.0] — Initial prototype (2026-11-01)

### Added
- Article library with fictional example records.
- Manual article entry.
- Side-by-side comparison of two distinct articles.
- Evidence review with user-selected assessment and reasoning.
- JSON export of saved records.
- Browser-local record storage.

### Verified during initial manual testing
- Application opened; fictional records loaded.
- Study comparison rendered and rejected selecting the same article twice.
- Evidence reviews saved.
- JSON export completed.

These observations reflect earlier manual testing, not a comprehensive automated test suite.

## Release policy

The `main` branch preserves v1.0 while `v2-development` contains the new prototype. A release tag is optional; do not label v2.0 stable until acceptance tests are completed.
