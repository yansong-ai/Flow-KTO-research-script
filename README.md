# Flow-KTO Paper Workspace

This repository contains the working manuscript and PaperSpine planning,
evidence, and review artifacts for:

> Flow-KTO: Learning Flow-Based Robot Policies from Unary Feedback

## Current Scope

The paper is being written section by section. The current authoritative
manuscript source is the Introduction:

- `drafts/introduction.tex`: Introduction body.
- `drafts/introduction_preview.tex`: standalone preview entry point.
- `drafts/references.bib`: bibliography used by the preview.
- `drafts/introduction_preview.pdf`: compiled preview for review.

Planning and evidence records live at the repository root. In particular,
`section_blueprints.md`, `writing_rationale_matrix.md`, `evidence_bank.md`, and
`claim_register.md` define the current writing and claim boundaries.

## Build The Introduction

Install a TeX distribution with `latexmk`, `pdflatex`, and BibTeX, then run:

```bash
cd drafts
latexmk -pdf -interaction=nonstopmode -halt-on-error introduction_preview.tex
```

Clean reproducible LaTeX intermediates with:

```bash
cd drafts
latexmk -c introduction_preview.tex
```

PDF previews are versioned because they are review artifacts. LaTeX auxiliary
files and local editor caches are ignored.

## Multi-Machine Notes

`paper_spine_config.json` and several inventory files record absolute source
paths from the workstation that created them. These paths are provenance, not
bundled dependencies. Update the local configuration when running PaperSpine on
another machine, and avoid committing changes that only rewrite workstation
paths.

The cited source PDFs are not copied into this repository. Their identities and
locations are recorded in `reference_materials/source_index.md` and the research
artifacts. Provision those source materials separately on each workstation when
the PaperSpine research workflow needs to re-read them.
