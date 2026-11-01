# BioLit AI

**Guided Biomedical Literature Research Workspace**  
**Current release:** V2.0 — Midterm Prototype (2026-11-01)  
**Status:** Released educational prototype; selected workflows manually tested, with documented limitations

BioLit AI is a browser-based educational research workspace for organizing biomedical literature, comparing studies, and documenting evidence-based scientific judgments. It supports critical reading; it does **not** replace original publications, independently verify scientific claims, or provide medical advice.

**Live application:** https://jessehokj.github.io/BioLit-ai/  
**Repository:** https://github.com/jessehokj/BioLit-ai  
**Releases:** https://github.com/jessehokj/BioLit-ai/releases

## Versions and branches

| Reference | Purpose |
| --- | --- |
| `main` | Current V2.0 midterm prototype; GitHub Pages publishing source |
| `V1.0` release/tag | Preserved original prototype at its historical commit |
| `V2.0` release/tag | Midterm prototype snapshot at its release commit |
| `v2-development` | Historical V2.0 development branch, if retained; merged into `main` |

The V1.0 release preserves its source snapshot; it is **not** the current `main` branch. The V2.0 release is a milestone, not a claim of production readiness. Do not move or overwrite historical release tags when preparing future versions.

## V2.0 capabilities

- **Article Library:** browse, search, filter by tag, edit, and delete saved articles.
- **Smart Import — DOI:** request available publication metadata from Crossref and populate bibliographic fields in the editor.
- **Smart Import — PDF:** extract selectable text using PDF.js and place it in an editable source-text field.
- **Article Editor:** record title, authors, year, DOI/URL, tags, abstract, research question, methods, findings, limitations, and source text.
- **Compare Studies:** display two distinct saved article records side by side; quality depends on the notes stored in each record.
- **Evidence Review:** record a claim, supporting article, assessment, and reasoning as a user-authored judgment.
- **Data portability:** JSON export/import for local backups.
- **AI Research Assistant interface:** request analysis from a separately deployed, trusted HTTPS backend **if one is configured**. No AI model or backend is bundled.
- **V1.0 data migration:** code supports copying legacy records into V2.0 storage when both versions have access to the same browser-origin storage; this is not cross-device synchronization.

These are implemented features/interfaces, **not** claims that every scenario has passed acceptance testing. See [TESTING_CHECKLIST.md](TESTING_CHECKLIST.md).

## Quick start

1. Open the [live application](https://jessehokj.github.io/BioLit-ai/) or open `index.html` in a modern browser.
2. Review the Article Library; use fictional examples only as demonstrations, never as evidence.
3. In **Smart Import**, enter a DOI or select a text-based PDF.
4. Review and correct imported material in **Article Editor**; manually document scientific details not supplied by the import.
5. Save the article, compare it with another saved record, or document an evidence assessment.
6. Export a JSON backup regularly; browser-local records are not automatically synchronized.

### Deployment

GitHub Pages is configured to publish from **`main` → `/(root)`**. The midterm build was reported working from the live site after a successful Pages build and deployment. GitHub Pages is a static host; it does not supply an AI analysis backend or shared database.

## Architecture and dependencies

- **Frontend:** one `index.html` containing HTML, CSS, and vanilla JavaScript; no build step.
- **Storage:** browser `localStorage`, scoped by browser and origin. Data may be lost when browser storage is cleared.
- **DOI lookup:** Crossref public API (`api.crossref.org`), dependent on connectivity, metadata coverage, and API availability.
- **PDF extraction:** PDF.js 3.11.174 loaded from a CDN. Current code limits extraction to PDFs up to 15 MB, the first 60 pages, and 150,000 extracted characters. Network access may be needed for the library.
- **Optional AI integration:** an external HTTPS POST endpoint accepting JSON `{ "task": "...", "article": { ... } }` and returning JSON containing an `analysis` string (and optionally `citations`). A backend would need CORS, access controls, rate limits, and secure secret handling.

## What Smart Import actually does

**DOI lookup** may populate title, authors, year, DOI URL, and abstract if supplied by the metadata provider. It does **not** independently read the full article or derive its research question, methods, findings, or limitations.

**PDF upload** extracts selectable text and may use the file name as a **provisional**, unverified title. Extracted text is placed into the source-text field; it is **not** automatically transformed into a structured scientific analysis. Image-only/scanned PDFs may yield no useful text; tables and reading order can be degraded.

**Compare Studies** compares saved records, not the underlying full texts unless the user has documented relevant content in those records. **AI Assistant** remains an integration interface until a separately configured backend is available.

## Testing and known limitations

Manual screenshots and user testing confirmed live deployment, article saving and deletion, successful DOI metadata retrieval for at least one DOI, and the presence of the main interface sections. Other behaviors have only partial or unrecorded verification. In particular, complete backup restoration, v1 storage integrity, evidence-review end-to-end flow, and backend AI analysis have **not** been established as passing. See [TESTING_CHECKLIST.md](TESTING_CHECKLIST.md) for the evidence-aware status matrix.

Known limitations:

- DOI metadata does not provide complete scientific interpretation.
- PDF import extracts text but does not identify structured findings, methods, or limitations; no OCR.
- Comparisons depend on the completeness and accuracy of saved article notes.
- No operational AI analysis without a trusted backend.
- No accounts, server-side database, cloud sync, or multi-user collaboration.
- Browser-local storage is not shared between local files, the deployed site, devices, or browsers.
- No automatic independent fact-checking, formal risk-of-bias assessment, or validated systematic-review workflow.

## Scientific, security, and privacy safeguards

- Verify every imported field, extracted passage, and AI-generated suggestion against the original paper.
- Fictional demo records must not be cited as scientific evidence.
- Evidence-review verdicts represent user judgment rather than validated conclusions.
- Do not upload confidential or sensitive research to third-party services without authorization.
- Never commit API secrets to the frontend or repository. Article content sent to a configured backend may leave the browser; use only trusted services.
- BioLit AI is an **educational research prototype**, not a clinical decision system.

## Roadmap after the midterm

1. Improve article identification and structured extraction from PDFs, with source-linked evidence and user verification.
2. Implement a secure AI backend for citation-grounded scientific summaries and analyses.
3. Improve comparison workflows, provenance, and evidence quality checks.
4. Expand automated tests, backup/migration validation, accessibility, and responsive design checks.

## Development workflow

Create a new feature or documentation branch from `main`, test changes, and merge via pull request. Keep [CHANGELOG.md](CHANGELOG.md) and [TESTING_CHECKLIST.md](TESTING_CHECKLIST.md) aligned with observed results. Preserve the V1.0 and V2.0 release tags as historical snapshots.

## License

No license has been selected yet. Public repository visibility does not by itself grant reuse rights.
