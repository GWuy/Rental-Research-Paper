# Rental property management research paper

Working IEEE conference paper: **Design and Evaluation of an Event-Driven Microservices Architecture for a Rental Property Management System**.

This is a collaborative research draft, not a report of completed implementation or experiments. It describes a proposed Java Spring Boot microservices design using PostgreSQL, Apache Kafka, an API gateway, Eureka, OpenFeign, transactional outbox publication, and idempotent consumers. The named system specification, **Đặc tả Hệ thống Microservices – Quản lý Cho thuê Phòng(2).docx**, was not present in this workspace during initialization. Service responsibilities and infrastructure details must be checked against that document and the actual implementation before the paper makes factual claims.

## Project structure

| Path | Purpose | Owner |
| --- | --- | --- |
| main.tex | IEEEtran setup, title, authors, section imports | Shared; review required |
| references.bib | Verified bibliography entries | Shared; review required |
| sections/abstract.tex | Abstract | Duong |
| sections/introduction.tex | I. Introduction | Duong |
| sections/related_work.tex | II. Related Work | Duong |
| tables/related_work.tex | Table I: related-work comparison | Duong |
| sections/system_architecture.tex | III. System Architecture and Security | Huy |
| tables/services.tex | Table II: service responsibilities and logical data ownership | Huy |
| sections/event_driven_design.tex | IV. Event-Driven Design and Infrastructure | Duy |
| tables/events.tex | Table III: candidate event topics and publishers | Duy |
| sections/evaluation.tex | V. Experimental Evaluation | Hoang |
| sections/discussion.tex | VI. Discussion and Limitations | Hoang |
| sections/conclusion.tex | VII. Conclusion and Future Work | Hoang |
| tables/experiments.tex | Table IV: experimental scenarios | Hoang |
| figures/README.md | Diagram and plot requirements | Shared reference |
| experiments/README.md | Experimental protocol and data rules | Hoang |

The eventual writing targets are **1,700–1,900 words** for Duong's files, **1,700–1,900** for Huy's, **1,400–1,600** for Duy's, and **1,700–1,900** for Hoang's. These are completion targets, not reasons to add repetitive filler. The current files are starter material.

## Build

Install a TeX distribution with IEEEtran, BibTeX, pdfLaTeX, and latexmk (for example, TeX Live or MiKTeX). From the project root:

```powershell
latexmk -pdf -interaction=nonstopmode -halt-on-error main.tex
```

The output is `main.pdf`. For a clean rebuild, use `latexmk -C` before the command above. The document uses the IEEE conference class, two columns, numbered citations, and BibTeX with the IEEEtran style. Set `\draftmodefalse` in `main.tex` only after all TODOs are resolved. The author affiliations are placeholders. There is intentionally no table of contents.

If latexmk is unavailable but pdfLaTeX and BibTeX are installed, run pdfLaTeX once, BibTeX once, then pdfLaTeX twice. Do not treat a static check as a successful compilation.

## Git collaboration

Recommended branches: `paper/duong`, `paper/huy`, `paper/duy`, and `paper/hoang`. This workspace is not currently a Git repository; initialize or connect one when the team is ready. No branch, commit, merge, or push is performed by this template.

Each author edits only assigned files. Open a pull request into the agreed integration branch with a short change summary, the source of each factual claim, a build result, and a note on unresolved TODOs. Request review from the owner of any affected section. Changes to `main.tex` or `references.bib` require team review before merge. Keep table and figure labels stable when editing cross-references. Resolve conflicts in source files rather than generated PDF or auxiliary files.

## Writing and evidence rules

Write academic English and preserve the required section structure. Separate design intentions from implemented facts. Cite only sources whose authors, title, publisher or venue, and year have been checked. Add a BibTeX entry before using a citation key; never invent a DOI or URL. The bibliography currently contains only the two foundational books supplied in the task. Duong should add verified rental-domain and empirical studies before claiming a research gap. Do not present the comparison table as experimental evidence.

Replace every TODO with evidence or remove the unsupported claim. Check the unavailable system specification before finalizing actor roles, service boundaries, API contracts, database schemas, Kafka topic names, gateway and CI/CD configuration, and diagrams. Use a consistent terminology for proposed, implemented, and measured elements. Keep the paper focused on design rationale, consistency, access control, and evaluation rather than a list of CRUD endpoints.

## Experimental data requirements

Hoang's scenarios cover API throughput and latency, Kafka event processing, duplicate handling, service failure recovery, and transactional outbox recovery. Record environment and source revision, workloads and seed data, warm-up and measurement intervals, repetitions, fault-injection points, raw logs and traces, analysis scripts, and unsuccessful trials. Report denominators, sample counts, latency percentiles, error rates, and run-to-run variation. Store non-sensitive raw artifacts under `experiments/` using a documented directory layout, but avoid committing secrets, personal data, or large generated outputs. No benchmark number should appear in the paper until it can be reproduced from retained data.
