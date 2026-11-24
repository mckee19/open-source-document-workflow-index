# Open-Source Document Workflow Index

> **Decision:** Use this index to assemble capture, OCR, document management, retrieval, retention, and preservation as explicit stages; skip it if one application is expected to own the entire document lifecycle.
>
> **For:** households, offices, and archivists building searchable governed records  ·  **Not for:** users seeking a simple cloud drive or unwilling to preserve originals and export paths

This is a non-commercial, source-traceable decision guide. It normalizes upstream declarations; it does not claim that repository reachability proves functionality, security, maintenance, or fitness.

**Start here:** [Download the document lifecycle ledger](assets/document-lifecycle-map.csv) — twelve projects, located upstream evidence, and explicit unknowns.

## Choose by workload

- Personal searchable archive: start with Paperless-ngx, Papermerge OSS, or Teedy, then test export and restore.
- Scan at the workstation: NAPS2 captures pages; OCRmyPDF or Tesseract handles OCR, but neither is a records system.
- Governed team workflow: compare Docspell, Mayan EDMS, and OpenDocMan by permissions, metadata, and upgrade burden.
- Institutional repository: DSpace needs its separate frontend and production prerequisites.
- Preservation pipeline: Archivematica creates preservation packages; it is not a daily document inbox.

## Follow a document from scanner to retention

Select one authoritative original. OCR text, transformed PDFs and preservation packages are outputs with different retention duties.

## Capture-to-preservation map

- **Capture and transform** — NAPS2 captures from scanner APIs; Stirling PDF reshapes PDFs; OCRmyPDF and Tesseract add text. These tools produce inputs for a manager rather than owning records.
- **Searchable document managers** — Paperless-ngx, Papermerge OSS, Teedy, and Docspell target searchable operational archives with different metadata and automation models.
- **Governed DMS** — Mayan EDMS and OpenDocMan emphasize users, versions, and workflow; compare authoritative storage and upgrade procedures, not screenshots.
- **Repository and preservation** — DSpace exposes a repository backend plus separate frontend; Archivematica builds preservation packages and depends on companion services.

## Document lifecycle ledger

| Project | Role | Input and capture stage | Record or transformation output | Storage and runtime prerequisites |
|---|---|---|---|---|
| Paperless-ngx | document manager | > Document scanners are typically used to scan sensitive documents like your social insurance number, tax records, invoices, etc. Paperless-ngx should never be … | Paperless-ngx is a document management system that transforms your physical documents into a searchable online archive so you can keep, well, less paper. | The easiest way to deploy paperless is docker compose. The files in the /docker/compose directory are configured to pull the image from the GitHub container reg… |
| Stirling PDF | PDF workbench | Stirling PDF is a powerful, open-source PDF editing platform. Run it as a personal desktop app, in the browser, or deploy it on your own servers with a private … | - Automation & workflows - No-code pipelines direct in UI with APIs to process millions of PDFs. | Unknown in the frozen upstream README |
| OCRmyPDF | OCR pipeline | OCRmyPDF adds an OCR text layer to scanned PDF files, allowing them to be searched or copy-pasted. | OCRmyPDF adds an OCR text layer to scanned PDF files, allowing them to be searched or copy-pasted. | Linux, Windows, macOS and FreeBSD are supported. Docker images are also available, for both x64 and ARM. |
| Tesseract | OCR engine | This package contains an OCR engine - libtesseract and a command line program - tesseract. | Tesseract supports various output formats: plain text, hOCR (HTML), PDF, invisible-text-only PDF, TSV, ALTO and PAGE. | Tesseract was originally developed at Hewlett-Packard Laboratories Bristol UK and at Hewlett-Packard Co, Greeley Colorado USA between 1985 and 1994, with some m… |
| Docspell | document manager | Docspell is a personal document organizer. Or sometimes called a "Document Management System" (DMS). You'll need a scanner to convert your papers into files. Do… | predefined and custom metadata. If your documents are associated with such meta data, you can quickly find them later using the search feature. But adding this … | Unknown in the frozen upstream README |
| Mayan EDMS | enterprise DMS | The most advanced, scalable, and mature open source document management system. | Unknown in the frozen upstream README | Unknown in the frozen upstream README |
| OpenDocMan | traditional DMS | Free PHP Document Management System DMS | Free PHP Document Management System DMS | - Database: MySQL 8+, MariaDB 10.0+ |
| Archivematica | digital preservation pipeline | allows your institution to preserve long-term access to trustworthy, authentic and reliable digital content. Our target users are archivists, librarians, and an… | allows your institution to preserve long-term access to trustworthy, authentic and reliable digital content. Our target users are archivists, librarians, and an… | Issues related to Archivematica, the Storage Service, or any related repository can be filed in the [Issues] repository. |
| Teedy | lightweight DMS | - Import document from email (EML format) - Automatic inbox scanning and importing | - Flexible search engine with suggestions and highlighting - Full text search in all supported files - All Dublin Core metadata - Custom user-defined metadata !… | A preconfigured Docker image is available, including OCR and media conversion tools, listening on port 8080. If no PostgreSQL config is provided, the database i… |
| Papermerge OSS | scanned-document manager | Papermerge OSS (Open Source) is a document management system for scanned documents, with OCR, full-text search, tags, folders, and a desktop-like web UI. | documents, with OCR, full-text search, tags, folders, and a desktop-like web UI. | Want to run Papermerge OSS (Open Source) from source? The development setup (PostgreSQL, environment variables, backend and frontend, running tests, CLI command… |
| NAPS2 | scanner client | Unknown in the frozen upstream README | Unknown in the frozen upstream README | NAPS2.Sdk is a fully-featured scanning library, supporting WIA, TWAIN, SANE, and ESCL scanners on Windows, Mac, and Linux. Read more. |
| DSpace | institutional repository backend | DSpace open source software is a turnkey repository application used by more than 2,000 organizations and institutions worldwide to provide durable access to di… | DSpace open source software is a turnkey repository application used by more than 2,000 organizations and institutions worldwide to provide durable access to di… | Please be aware that, as a Java web application, DSpace requires a database (PostgreSQL) and a servlet container (usually Tomcat) in order to function. More inf… |

Values are short excerpts from the frozen upstream README, not feature-test scores. The CSV retains the located evidence for each cell. “Unknown” means the retrieved document did not establish that axis; it is not a claim that the feature is absent.

## Keep the authority path explicit

A small paper workflow can be NAPS2 → OCRmyPDF → Paperless-ngx. An institution may instead ingest curated objects into DSpace, and pass preservation copies through Archivematica. Never let an OCR output folder and a DMS database both appear authoritative without an explicit retention rule.

## Adoption notes by project

### Paperless-ngx

- **Choose it for:** Households and small offices wanting a searchable archive.
- **License at the frozen source:** [GPL-3.0](https://raw.githubusercontent.com/paperless-ngx/paperless-ngx/4973be8499bc61dc4f791a609d0d31e9ac9ccd41/LICENSE).
- **Adoption test:** Define export, database backup, originals retention, and re-import drills before destroying paper.
- **Source:** [paperless-ngx/paperless-ngx](https://github.com/paperless-ngx/paperless-ngx).

### Stirling PDF

- **Choose it for:** Preparing PDFs before they enter an archive.
- **License at the frozen source:** [MIT outside separately licensed app/proprietary, app/saas, engine and listed frontend subdirectories](https://raw.githubusercontent.com/Stirling-Tools/Stirling-PDF/f5503b8910ad5cec06dd6125d7e96d985a6d1248/LICENSE).
- **Adoption test:** The root MIT grant excludes app/proprietary, app/saas, engine and named frontend modules when present. Locate the operation and its directory license before adoption.
- **Source:** [Stirling-Tools/Stirling-PDF](https://github.com/Stirling-Tools/Stirling-PDF).

### OCRmyPDF

- **Choose it for:** Batch OCR where the PDF remains the artifact.
- **License at the frozen source:** [MPL-2.0](https://raw.githubusercontent.com/ocrmypdf/OCRmyPDF/86a5e723ea2b612e8df4a647056b0ebf3b3c97a5/LICENSE).
- **Adoption test:** OCR accuracy, language packs, signatures, and PDF conformance need sample documents; it does not manage retention.
- **Source:** [ocrmypdf/OCRmyPDF](https://github.com/ocrmypdf/OCRmyPDF).

### Tesseract

- **Choose it for:** Developers who need a low-level OCR component.
- **License at the frozen source:** [Apache-2.0](https://raw.githubusercontent.com/tesseract-ocr/tesseract/2516f31c560e056449b6d9e95e10c6feeb6ad618/LICENSE).
- **Adoption test:** Layout reconstruction, document storage, and workflow are outside its scope; benchmark your scripts and languages.
- **Source:** [tesseract-ocr/tesseract](https://github.com/tesseract-ocr/tesseract).

### Docspell

- **Choose it for:** Households or teams wanting automated intake.
- **License at the frozen source:** [AGPL-3.0](https://raw.githubusercontent.com/eikek/docspell/751b0b834617c1f3d21fb738f4778e444ef316b0/LICENSE.txt).
- **Adoption test:** Verify scanner/mail ingestion, metadata export, database restore, and resource needs with representative volume.
- **Source:** [eikek/docspell](https://github.com/eikek/docspell).

### Mayan EDMS

- **Choose it for:** Organizations needing controlled document processes.
- **License at the frozen source:** [GPL-2.0; trademark rights are separate](https://gitlab.com/mayan-edms/mayan-edms/-/raw/834ffec1b539171390358e60a0406870108514f5/LICENSE).
- **Adoption test:** The GitHub repository is an outdated mirror; use the official GitLab source and test upgrades across all companion services.
- **Source:** [mayan-edms/mayan-edms](https://gitlab.com/mayan-edms/mayan-edms).

### OpenDocMan

- **Choose it for:** Small teams preferring a conventional DMS model.
- **License at the frozen source:** [GPL-2.0](https://raw.githubusercontent.com/opendocman/opendocman/6f29a4714b0cce7d2bcc0aa5d68bb87bb3bd0975/LICENSE.txt).
- **Adoption test:** Test current authentication, migrations, permissions, and export; do not infer modern OCR or preservation features.
- **Source:** [opendocman/opendocman](https://github.com/opendocman/opendocman).

### Archivematica

- **Choose it for:** Archivists planning durable preservation rather than daily filing.
- **License at the frozen source:** [AGPL-3.0](https://raw.githubusercontent.com/artefactual/archivematica/8b715e088c0f6e908ae742805ce696d3ba851de7/LICENSE).
- **Adoption test:** It includes related repositories such as Storage Service; scope infrastructure, format policy, and recovery as one system.
- **Source:** [artefactual/archivematica](https://github.com/artefactual/archivematica).

### Teedy

- **Choose it for:** Individuals and businesses wanting an integrated lightweight archive.
- **License at the frozen source:** [GPL-2.0](https://raw.githubusercontent.com/sismics/docs/5b39c4680b5a107a44d9d38bdf45e8fb6953128f/COPYING).
- **Adoption test:** Upstream says embedded H2 is for testing, latest may be unstable, and the default admin password must be changed.
- **Source:** [sismics/docs](https://github.com/sismics/docs).

### Papermerge OSS

- **Choose it for:** Scanned-document archives needing desktop-like organization.
- **License at the frozen source:** [Apache-2.0](https://raw.githubusercontent.com/papermerge/papermerge-core/831c2e355cf5c841c4587fea19d89e9b46a92b79/LICENSE).
- **Adoption test:** OSS and Papermerge Cloud use separate codebases and may diverge; replace quick-start credentials and test export.
- **Source:** [papermerge/papermerge-core](https://github.com/papermerge/papermerge-core).

### NAPS2

- **Choose it for:** Cross-platform capture before document ingestion.
- **License at the frozen source:** [GPL-2.0-or-later; SDK components include LGPL or MIT terms](https://raw.githubusercontent.com/cyanfish/naps2/07f1fd3667373e7a07dd095e9703a72d588e1a5a/LICENSE).
- **Adoption test:** It is a capture application, not a shared archive; verify scanner drivers, OCR language, and handoff naming.
- **Source:** [cyanfish/naps2](https://github.com/cyanfish/naps2).

### DSpace

- **Choose it for:** Libraries and institutions operating a repository.
- **License at the frozen source:** [BSD-3-Clause](https://raw.githubusercontent.com/DSpace/DSpace/7ad52048c3143f161f6cb8ad93b15243aad3913f/LICENSE).
- **Adoption test:** Upstream says Docker Compose is for development/testing, not production; deploy the separate frontend and follow supported-release docs.
- **Source:** [DSpace/DSpace](https://github.com/DSpace/DSpace).

## Reconcile originals and derived records

1. Ingest a multilingual scan and retain its untouched original.
2. Compare extracted text, metadata and transformed output to the source.
3. Export records and permissions separately from application database state.
4. Rebuild original storage and database together; reconcile the authoritative record.

## What this guide covers

Human documents, OCR and governed records, not code retrieval or newsletter publishing.

## Adjacent guides

- [self-hosted-photo-library-decision-guide](https://github.com/Thomas664951/self-hosted-photo-library-decision-guide) — Use it when the collection is primarily photos and videos with mobile backup, RAW, search, and album needs.
- [self-hosted-read-it-later-landscape](https://github.com/rayrooto/self-hosted-read-it-later-landscape) — Use it when web capture and reading state feed the document preservation workflow.
- [encrypted-backup-tool-selector](https://github.com/Anguianodd/encrypted-backup-tool-selector) — Use it when originals, derivatives, metadata, and indexes need a tested encrypted restore path.

## Located sources and update policy

[`sources.json`](sources.json) binds each cited declaration to a commit, document, exact line range and local snapshot hash. [`assets/projects.json`](assets/projects.json) holds the normalized roles and decision axes. Current HEAD reachability is recorded separately; it is not a maintenance or security assessment. Licensing is version- and directory-specific. Re-read the selected release before adoption.

Run the local evidence and package checks, then opt into public-source reachability:

```bash
python3 scripts/verify_sources.py
python3 scripts/verify_sources.py --online
```

These checks validate source binding, excerpts, hashes, language, the decision asset and nonempty public content. They do not certify feature behavior, migration success or restore success. No popularity score, paid placement or affiliate ranking is used. Restricted-license and historical examples are explicit contrasts, not silently recommended open-source defaults.

If this saved you a decision, star the repo — it is how the next reader finds it.
