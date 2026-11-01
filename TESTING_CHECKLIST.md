# BioLit AI — Testing Checklist

**Target:** v2.0 on `v2-development`  
**Status:** Not yet executed against the deployed v2.0 application  
**Tester:** _To complete_  
**Test date / browser / device:** _To complete_  
**Deployment URL / commit SHA:** _To complete_

Mark each item only after personally verifying it. Record **Pass / Fail / Blocked / Not tested**, observed behavior, and screenshots or console errors for failures. Do not treat a checked box as proof of automated testing.

## A. Repository and deployment

- [ ] `main` still contains the original v1.0 `index.html`.
- [ ] `v2-development` contains the v2.0 `index.html` and documentation files.
- [ ] GitHub Pages is configured to publish `v2-development` from `/(root)`.
- [ ] Deployment succeeds and the page opens over HTTPS.
- [ ] Page title/version visibly identifies v2.0.
- [ ] Browser developer console shows no blocking JavaScript errors.

## B. Navigation and responsive layout

- [ ] All six sections open: Article Library, Smart Import, Article Editor, Compare Studies, Evidence Review, AI Assistant.
- [ ] Layout remains usable on a tablet or phone in portrait and landscape.
- [ ] Forms, buttons, and cards do not overlap or clip important content.
- [ ] Keyboard navigation and form labels are usable where applicable.

## C. Article library and editor

- [ ] Empty library displays a useful message.
- [ ] Fictional demo records load and are clearly labeled as fictional.
- [ ] Create a manual article with a title and save it.
- [ ] Edit that article and confirm the changes persist after reload.
- [ ] Search matches title or author; tag filtering works.
- [ ] Delete a test article; confirmation is shown and record disappears.
- [ ] Missing optional scientific fields are not represented as verified findings.
- [ ] Invalid required form input is rejected.

## D. DOI metadata import

- [ ] Enter a known valid DOI; lookup populates available title, authors, year, source URL, and (when supplied) abstract.
- [ ] DOI URL format (`https://doi.org/...`) also works.
- [ ] Research question, methods, findings, and limitations are **not fabricated** by DOI lookup.
- [ ] Invalid DOI produces a clear error.
- [ ] Unavailable DOI / network failure produces a recoverable error.
- [ ] Imported record can be corrected and saved.

**Suggested real-world test:** use a DOI from a paper you already have access to; compare every populated field with the publisher page. Do not assume Crossref always supplies an abstract.

## E. PDF import

- [ ] Upload a text-based PDF under 15 MB; text extraction completes.
- [ ] Extracted text appears in the editable source-text field.
- [ ] Filename is treated as a provisional title, not verified metadata.
- [ ] No unsupported methods, findings, or limitations are auto-generated.
- [ ] Scanned/image-only PDF produces an understandable failure or empty-text warning.
- [ ] File over 15 MB is rejected.
- [ ] Large document behavior respects first-60-pages and 150,000-character limits.
- [ ] Extraction failure does not erase previously saved articles.

## F. Comparison and evidence review

- [ ] Two different records produce a side-by-side comparison.
- [ ] Selecting the same record twice is rejected.
- [ ] Comparison content matches saved notes without invented conclusions.
- [ ] Save an evidence review with claim, article, assessment, and reasoning.
- [ ] Edit and delete an evidence review.
- [ ] Assessment is clearly labeled as user judgment, not verified scientific fact.
- [ ] Deleting an article handles its linked evidence reviews as described by the interface.

## G. Data storage and backup

- [ ] Saved records persist after refreshing the same site and browser.
- [ ] Export downloads valid JSON containing articles and reviews.
- [ ] Import a previously exported backup and verify record contents.
- [ ] Malformed JSON is rejected without overwriting existing records.
- [ ] Import replacement confirmation appears before overwriting records.
- [ ] Clearing v2 records asks for confirmation.
- [ ] Test whether v1 records migrate on first v2 launch **when both versions share the same browser origin and v1 storage exists**.
- [ ] Confirm migration does not modify the original v1 data.
- [ ] Confirm that switching between local file URLs and GitHub Pages does **not** automatically transfer browser-local data; use JSON backup as needed.

## H. AI assistant (requires backend)

- [ ] Without a configured endpoint, application explains what is missing.
- [ ] Non-HTTPS endpoint is rejected.
- [ ] User must confirm before sending article data to backend.
- [ ] Configured trusted backend receives selected article and task.
- [ ] Valid backend response renders as an **unverified AI draft**.
- [ ] Backend failure / CORS error produces an understandable message.
- [ ] No API keys or secrets appear in frontend source or Git history.

**If no backend exists:** mark backend-dependent tests **Blocked**, not Pass.

## I. Regression and release gate

- [ ] Recheck all v1.0 workflows on v2.0.
- [ ] Verify v1.0 still works on `main`.
- [ ] No critical data-loss, security, or blocking functionality defects remain.
- [ ] README and CHANGELOG match observed behavior.
- [ ] Record known issues and decide whether v2.0 is ready for release.

## Test execution log

| ID | Area | Result | Device / browser | Evidence / issue |
| --- | --- | --- | --- | --- |
| T01 | Deployment | Not tested | — | — |
| T02 | Article library | Not tested | — | — |
| T03 | DOI import | Not tested | — | — |
| T04 | PDF import | Not tested | — | — |
| T05 | Comparison | Not tested | — | — |
| T06 | Evidence review | Not tested | — | — |
| T07 | JSON backup | Not tested | — | — |
| T08 | v1 migration | Not tested | — | — |
| T09 | AI backend | Blocked — backend not configured | — | — |
| T10 | Mobile layout | Not tested | — | — |

## Defect report template

**ID:** BUG-___  
**Severity:** Critical / High / Medium / Low  
**Environment:** Device, OS, browser, deployment URL, commit  
**Steps to reproduce:** 1. … 2. … 3. …  
**Expected result:** …  
**Actual result:** …  
**Evidence:** Screenshot / console error  
**Resolution / retest:** …

## Acceptance criteria

Do not declare v2.0 complete until deployment, article management, comparison, evidence review, and backup tests pass; DOI and PDF capabilities are tested or explicitly documented as limited; and AI functionality is either verified with a secure backend or clearly labeled unavailable. Preserve `main` throughout development.
