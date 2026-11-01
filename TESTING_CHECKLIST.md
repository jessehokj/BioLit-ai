# BioLit AI — V2.0 Testing Checklist and Evidence Log

**Target:** V2.0 midterm prototype, merged into `main` and deployed via GitHub Pages  
**Release date:** 2026-11-01  
**Status:** Selected manual tests performed; full acceptance suite **not completed**  
**Tester:** Repository owner (reported screenshots and observations)  
**Environment:** Mobile browser screenshots, Android tablet/phone-class device; exact browser version not recorded  
**Deployment:** https://jessehokj.github.io/BioLit-ai/  
**Release:** `V2.0`  
**Commit:** Merge commit shown in prior GitHub screenshot (`6561571`); confirm full SHA in repository before using it as an immutable test identifier.

## Status conventions

- **Pass:** specific behavior visibly demonstrated or explicitly confirmed.
- **Partial:** part of a workflow demonstrated; remaining acceptance criteria not established.
- **Blocked:** cannot complete without an external dependency.
- **Not tested:** no reliable execution evidence available.
- **Fail:** a tested requirement demonstrably failed; record steps and evidence.

Statuses below are based on the screenshots and observations reported during the V2.0 midterm workflow, **not** a new automated test run. Do not convert Partial/Not tested to Pass without retesting.

## A. Repository and deployment

- [x] `main` contains V2.0 after successful pull-request merge. **Pass**
- [x] V1.0 is preserved by its `V1.0` release/tag. **Pass** (historical snapshot, not current `main`)
- [x] V2.0 release/tag created. **Pass**
- [x] GitHub Pages deploys from `main` and `/(root)`; deployment workflow succeeded. **Pass**
- [x] Live site opened and user reported it working. **Pass**
- [ ] No blocking JavaScript errors in browser console. **Not tested**

## B. Navigation and responsive layout

- [x] Screenshots show all six navigation sections available. **Pass** (visibility/navigation demonstrated)
- [ ] Each section's complete functionality verified. **Partial**
- [ ] Portrait and landscape layout across multiple screen sizes. **Partial** (mobile screenshots only)
- [ ] No clipping/overlap across supported viewports. **Not tested systematically**
- [ ] Keyboard navigation, labels, and accessibility checks. **Not tested**

## C. Article library and editor

- [x] Saved article records displayed in library. **Pass**
- [x] Article saved successfully; confirmation message shown. **Pass**
- [x] Delete function worked, as explicitly reported. **Pass**
- [ ] Search and tag filter behavior. **Not independently verified**
- [ ] Edit existing record and confirm persistence after reload. **Not independently verified**
- [ ] Empty-library message, invalid input, and optional field handling. **Not tested**
- [ ] Records persist after a browser restart. **Not tested**

## D. DOI metadata import

- [x] DOI lookup populated bibliographic fields and an available abstract in the editor. **Pass for tested DOI**
- [x] DOI URL input worked for at least one example. **Pass**
- [x] No invented methodology, findings, or limitations appeared in the imported draft. **Pass for observed example**
- [x] Invalid DOI generated an error message in a screenshot. **Pass for observed invalid input**
- [ ] Unavailable DOI, provider outage, and network error handling. **Not fully tested**
- [ ] Bibliographic fields systematically cross-checked against original publisher page. **Not recorded**

**Known limitation:** Crossref metadata is bibliographic; it does not automatically supply a complete research analysis.

## E. PDF import

- [x] PDF extraction placed text in the extracted source-text field, per user observation. **Pass for basic text extraction**
- [x] Provisional title derived from filename, per user observation. **Observed limitation**
- [ ] Structured extraction of article title, question, methods, findings, and limitations. **Not implemented; not a V2.0 passing requirement**
- [ ] Image-only/scanned PDF behavior. **Not tested**
- [ ] Files above 15 MB rejected. **Not tested**
- [ ] First-60-pages and 150,000-character limits enforced. **Not tested**
- [ ] Extraction failures preserve saved records. **Not tested**

**Known limitation:** PDF import copies selectable text, not a validated scientific summary; it can misidentify the article title when the filename differs from the title.

## F. Comparison and evidence review

- [x] Two different saved articles could be selected in the comparison interface. **Pass for selection**
- [ ] Generated comparison output accurately displays both records. **Not fully evidenced by screenshots**
- [ ] Same-article selection rejected in V2.0. **Not retested** (previously observed in V1.0)
- [ ] Comparison derives substantive analysis directly from DOI/PDF. **Not implemented; comparison depends on saved notes**
- [ ] Create, edit, and delete evidence review in V2.0. **Not fully verified**
- [ ] Deleting a linked article handles evidence reviews safely. **Not tested**

## G. Storage, backup, and migration

- [x] Library displayed records marked as V1 migrated. **Pass for visible migration outcome**
- [ ] V1 original storage remains byte-for-byte unchanged. **Not independently verified**
- [ ] JSON export contains complete valid records. **Not retested in V2.0**
- [ ] JSON import restores exported records correctly. **Not tested**
- [ ] Malformed JSON rejected without data loss. **Not tested**
- [ ] Replacement/clear confirmations work. **Not tested**
- [ ] Local-file origin and GitHub Pages storage remain separate. **Expected browser behavior; not a demonstrated migration test**

**Safety note:** Export a JSON backup before any destructive testing or storage migration.

## H. AI assistant

- [x] AI Assistant configuration interface displayed. **Pass for interface visibility**
- [ ] No-endpoint, invalid endpoint, and error-message handling. **Not tested**
- [ ] Confirm before transmitting article data. **Not tested**
- [ ] External backend accepts article/task request and returns an analysis. **Blocked — no backend configured**
- [ ] AI output is displayed as unverified draft with citations if provided. **Blocked — no backend configured**
- [ ] Backend CORS/authentication/rate-limit and secret-handling checks. **Blocked — no backend configured**

**Important:** An AI Assistant UI is **not** evidence of operational AI analysis.

## I. Regression and release acceptance

- [x] V1.0 release snapshot preserved. **Pass**
- [x] V2.0 merged into `main` and deployed. **Pass**
- [x] V2.0 midterm release published. **Pass**
- [ ] Complete V1.0 workflow retested using the `V1.0` release source. **Not recorded**
- [ ] All critical data-loss/security tests passed. **Not established**
- [ ] All functional acceptance criteria passed. **Not established**
- [x] Known DOI, PDF, comparison, and AI limitations documented. **Pass (documentation)**

**Release decision:** V2.0 was accepted as the **functional midterm prototype**, not as a production-ready or fully validated scientific analysis system. Outstanding tests remain open for the next development cycle.

## Test execution log

| ID | Area | Status | Evidence / observation | Next verification |
| --- | --- | --- | --- | --- |
| T01 | Deployment | Pass | Successful Pages workflow and live-site confirmation | Capture deployment SHA and URL screenshot |
| T02 | Article library | Partial | Saved records visible; save and delete observed | Search, filter, edit, persistence |
| T03 | DOI import | Partial | DOI metadata and abstract populated; invalid DOI message shown | Cross-check against publisher; network failures |
| T04 | PDF import | Partial | Text extraction observed; filename used as provisional title | Edge cases, size limits, OCR warning |
| T05 | Comparison | Partial | Two records selected; full generated output not shown | Compare saved notes and same-article validation |
| T06 | Evidence review | Not tested | No complete V2.0 workflow evidence supplied | Create/edit/delete and linked-record behavior |
| T07 | JSON backup | Not tested | V2.0 round-trip not documented | Export/import and corrupt-file tests |
| T08 | V1 migration | Partial | V1-migrated labels visible | Verify original V1 storage remains intact |
| T09 | AI backend | Blocked | No backend configured | Secure integration and response/error tests |
| T10 | Responsive layout | Partial | Mobile screenshots show usable screens | Portrait/landscape and accessibility audit |

## Defect report template

**ID:** BUG-___  
**Severity:** Critical / High / Medium / Low  
**Environment:** Device, OS, browser, deployment URL, commit  
**Steps to reproduce:** 1. … 2. … 3. …  
**Expected result:** …  
**Actual result:** …  
**Evidence:** Screenshot / console error  
**Resolution / retest:** …

## Next-cycle acceptance gate

Before claiming a fully validated V2.0 workflow or shipping an expanded version: test data persistence, backup round-trip, migration integrity, evidence review, comparison rendering, DOI/PDF edge cases, and accessibility. AI features must remain explicitly unavailable until a secure backend is deployed and tested. Preserve both release tags throughout subsequent development.
