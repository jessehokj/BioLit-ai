# BioLit AI

**Guided Biomedical Literature Research Workspace**  
**Current development version:** v2.0 prototype  
**Status:** Implementation committed; end-to-end testing pending

BioLit AI is an educational browser-based research workspace for organizing biomedical literature, comparing studies, and documenting evidence-based scientific judgments. It is designed to support critical reading, **not** replace reading original publications or independently verify scientific claims.

## Versions and branches

| Branch | Purpose |
| --- | --- |
| `main` | Preserved v1.0 prototype |
| `v2-development` | Active v2.0 development and testing |

Do not merge `v2-development` into `main` until acceptance tests are complete. A GitHub release tag is optional.

## v2.0 capabilities

The current `index.html` includes interfaces and code for:

- **Article library:** browse, search, filter by tag, edit, and delete records.
- **Smart import by DOI:** request publication metadata from Crossref and populate available bibliographic fields.
- **PDF text extraction:** extract selectable text from uploaded PDFs with PDF.js and place it in an editable article record.
- **Article editor:** record abstract, research question, methodology, findings, limitations, tags, and source text.
- **Study comparison:** display two different saved articles side by side.
- **Evidence review:** save a claim, supporting article, assessment, and reasoning.
- **Data portability:** export/import JSON backups.
- **Optional AI assistant:** send a selected article to a separately deployed, trusted HTTPS backend and display its response as an **unverified draft**.

**Implemented in source code does not mean independently tested.** See [TESTING_CHECKLIST.md](TESTING_CHECKLIST.md) for verification steps.

## Quick start

1. Open `index.html` in a modern browser, or deploy the `v2-development` branch using GitHub Pages.
2. Choose **Load fictional examples** to try the article library and comparison workflow.
3. Use **Smart Import** to enter a DOI or upload a text-based PDF.
4. Inspect and correct all imported fields in **Article Editor** before saving.
5. Export a JSON backup to preserve your work.

### GitHub Pages (development preview)

Repository **Settings → Pages → Build and deployment → Deploy from a branch**, then choose `v2-development` and `/(root)`. This publishes a preview of v2.0 without merging the code into `main`. The Pages URL is expected to be `https://jessehokj.github.io/BioLit-ai/` after successful deployment. GitHub Pages normally serves one selected publishing branch per site.

## Architecture and dependencies

- **Frontend:** single-file HTML, CSS, and vanilla JavaScript; no build step.
- **Local data:** browser `localStorage`; storage is specific to the browser and origin. Export backups regularly.
- **DOI metadata:** Crossref public API (`api.crossref.org`); internet access and API availability required.
- **PDF processing:** PDF.js 3.11.174 loaded from a CDN; internet access is needed to load the library. Extraction is limited in the current code to PDFs up to 15 MB, the first 60 pages, and 150,000 characters of extracted text.
- **AI:** no bundled model or built-in backend. The interface expects an HTTPS POST endpoint accepting `{ "task": "...", "article": { ... } }` and returning JSON with an `analysis` string (optional `citations` array). Backend must implement appropriate CORS, security, authentication, and rate limits.

## What smart import does—and does not do

**DOI lookup** fills available title, authors, publication year, DOI URL, and abstract metadata. It does **not** infer methods, results, or limitations. **PDF upload** extracts text and uses the filename as a provisional title; it does **not** automatically interpret the study or fill scientific analysis fields. Scanned/image-only PDFs may not work. Automated scientific field extraction is a potential future enhancement, not a verified v2.0 feature.

## Scientific and privacy safeguards

- Treat imported bibliographic details, PDF text, and AI output as material to verify against the original publication.
- Demo articles are fictional and cannot support biological conclusions.
- Evidence-review verdicts reflect user judgment, not independent scientific validation.
- Avoid uploading sensitive or confidential research to third-party services without permission.
- The AI assistant asks for confirmation before sending selected article content to the configured endpoint. Never place secret API keys in `index.html` or commit them to GitHub.
- This prototype is **not** medical advice or a validated systematic-review tool.

## Known limitations

- No accounts, cloud sync, multi-user collaboration, or server-side database.
- Data can be lost if browser storage is cleared or a different origin/device is used.
- No OCR for scanned PDFs; PDF extraction can lose layout and tables.
- No independent scientific fact-checking or automatic quality scoring.
- No live AI analysis until a secure backend is deployed and configured.
- Current implementation and migration behavior require browser testing before release.

## Development workflow

Keep v1.0 on `main`. Commit and test changes on `v2-development`, record results in [TESTING_CHECKLIST.md](TESTING_CHECKLIST.md), and describe changes in [CHANGELOG.md](CHANGELOG.md). Only consider merging once critical tests pass.

## License

No license has been selected yet. A public GitHub repository is viewable, but public visibility alone does not grant reuse rights.
