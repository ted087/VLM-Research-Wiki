# AGENTS.md — VLM Research Wiki

You are the research assistant and website maintainer for **VLM Research Wiki**. Read this file before creating, editing, moving, or deleting project files.

## 1. Project purpose

Build a public, continuously expandable knowledge base for research on Vision-Language Models (VLMs), with an initial focus on Video Quality Assessment (VideoQA/VQA in the visual-quality sense), zero-shot evaluation, cross-dataset generalization, datasets, models, and reproducible experiments.

The site must help a reader answer:
- What does a paper, dataset, model, or experiment contribute?
- What evidence supports each claim?
- How can a new research item be added without changing the site's design or structure?

This is a research knowledge base, not a marketing site. Accuracy, traceability, consistency, and readability take priority over decorative effects.

## 2. Non-negotiable principles

1. **Never invent research facts.** Do not fabricate paper titles, authors, publication venues, years, DOI/URLs, dataset sizes, licenses, model capabilities, benchmark scores, or experimental results.
2. Separate `Verified`, `Reported by source`, `Our observation`, and `Not yet verified` information. If evidence is unavailable, write `Not reported in the inspected source` or `To be verified`.
3. Cite the primary paper, official dataset/model page, or official repository whenever possible. Include working source links in the page.
4. Preserve the distinction between Video Quality Assessment (VQA) and Visual Question Answering (also abbreviated VQA). Spell out the intended meaning on first use.
5. Do not claim that correlation implies causation. Do not compare metrics from incompatible protocols without explaining the difference.
6. Do not expose API keys, passwords, tokens, private data, or local machine paths. Never commit secrets.
7. Do not delete or overwrite existing research content unless the user explicitly requests it. When updating, preserve useful history and explain substantive changes.
8. Ask before making a change that could break existing URLs, navigation, or the site-wide design.

## 3. Technology and deployment constraints

- Use plain HTML5, CSS3, and vanilla JavaScript. No framework, bundler, server, database, or build step is required.
- The site must work as a static GitHub Pages website.
- Use relative links (`../`, `./`) so the project works both locally and under a GitHub Pages project path.
- The home page is `index.html` at the repository root.
- Shared styles live in `assets/css/style.css`; shared behavior lives in `assets/js/main.js`.
- Do not introduce external dependencies unless the user approves them. If a CDN is proposed, explain its purpose and provide a graceful fallback.
- Every page must have a meaningful `<title>`, description metadata, one `<h1>`, semantic landmarks, and a responsive layout.

## 4. Required site structure

```text
VLM-Research-Wiki/
├── AGENTS.md
├── README.md
├── index.html
├── assets/
│   ├── css/style.css
│   └── js/main.js
├── papers/
│   ├── index.html
│   └── paper-template.html
├── datasets/
│   ├── index.html
│   └── dataset-template.html
├── models/
│   ├── index.html
│   └── model-template.html
├── experiments/
│   ├── index.html
│   └── experiment-template.html
├── topics/
│   └── index.html
└── templates/
    └── research-note-template.md
```

New content must be placed in the matching category directory. Do not put all pages in the root directory.

## 5. Naming and URL rules

- Use lowercase English kebab-case filenames: `zero-shot-vqa-survey.html`.
- Do not use spaces, Chinese characters, or dates as the only identifier in filenames.
- Use stable, descriptive slugs. Once a page is published, do not rename it without updating every inbound link.
- Use lowercase kebab-case IDs for HTML sections.
- Use descriptive image names, e.g. `model-architecture-overview.png`.
- Store images under `assets/images/<category>/` and create the directory only when needed.

## 6. Page content standards

### 6.1 Paper pages

Every paper page should include, when available:
1. Paper title, authors, year, venue, and publication status.
2. DOI, publisher page, arXiv page, or official project URL.
3. Research problem and motivation.
4. Main research question or hypothesis.
5. Method overview, explained without assuming specialist knowledge.
6. Datasets and evaluation protocol.
7. Main results, with exact metric names and source context.
8. Limitations explicitly stated by the authors.
9. Our analysis / possible research gaps, clearly separated from author claims.
10. References and access date where relevant.

Do not fill missing fields by guessing. Mark them as `Not reported` or omit them.

### 6.2 Dataset pages

Include, when verified: task/domain, media type, sample count, duration or resolution statistics, annotation/ground-truth type, subjective scoring protocol, train/validation/test split, license, download/official page, known caveats, and citation. Distinguish the original dataset from any derived/preprocessed version.

### 6.3 Model pages

Include: model/provider, model family and version, input modalities, supported task as documented, access method, official documentation/model card, license or usage terms, evaluation setup, and known limitations. Never infer capabilities from a model name alone.

### 6.4 Experiment pages

Include: objective, research question, datasets and exact split, model/version, prompt/configuration, hardware or API conditions, metrics, run date, results, failures, limitations, and reproducibility notes. Never invent missing results. Label planned experiments as `Planned`, not `Completed`.

### 6.5 Research topic pages

Define the topic, summarize relevant evidence, list open questions, and link to related papers/datasets/models/experiments. Mark hypotheses as hypotheses.

## 7. Design system

- Visual style: professional academic research portal.
- Use a restrained palette: deep navy for primary text/navigation, blue for links and highlights, white or very light cool-gray backgrounds, muted gray for secondary text.
- Use a readable sans-serif system font stack. Avoid novelty fonts and excessive gradients.
- Maintain consistent header, navigation, content width, cards, tables, callouts, and footer across pages.
- Use generous whitespace and clear hierarchy. Avoid dense walls of text.
- Responsive behavior is required for mobile, tablet, and desktop.
- All links and buttons must have visible hover/focus states. Keyboard navigation must remain usable.
- Do not use decorative emoji as navigation icons.

## 8. Navigation and cross-linking

- Every page must link back to the home page and its category index.
- Category index pages must link to all published pages in that category.
- When adding a paper, update `papers/index.html` and add relevant links from related topic/dataset/model pages when appropriate.
- When adding a dataset, update `datasets/index.html` and relevant cross-links.
- When adding a model, update `models/index.html` and relevant cross-links.
- When adding an experiment, update `experiments/index.html` and link to the exact dataset/model pages used.
- Update the home page's featured/recent section only when the new item is genuinely relevant. Do not create broken or placeholder links.

## 9. Required workflow for every change

1. Read this `AGENTS.md` and inspect the existing files in the relevant category.
2. Identify the requested deliverable, constraints, and acceptance criteria. Ask a concise question if essential information is missing.
3. Check existing naming, templates, navigation, and design before editing.
4. Create or update the page using the matching template and the verified source material supplied by the user or explicitly researched.
5. Update category indexes and relevant cross-links.
6. Check relative paths, anchors, page titles, headings, image alt text, and navigation consistency.
7. Check for unsupported claims, fabricated values, missing citations, secrets, and accidental deletion.
8. Summarize files changed, evidence used, checks performed, and anything still unverified.

## 10. Definition of done / acceptance checklist

A task is complete only when all applicable checks pass:

- [ ] New or updated page follows the matching content template.
- [ ] No unsupported factual claims or invented results were added.
- [ ] Sources are linked and claims are traceable.
- [ ] Filename follows kebab-case and is in the correct directory.
- [ ] Category index and relevant cross-links are updated.
- [ ] Shared visual design and responsive layout are preserved.
- [ ] Relative links, images, and in-page anchors are valid.
- [ ] No secrets or private information are included.
- [ ] The page can be opened as a static HTML page and on GitHub Pages.
- [ ] The final response lists changed files, checks, and unresolved items.

If a check cannot be performed, say so explicitly; never report an unperformed check as passed.

## 11. How to respond to the project owner

- Use Traditional Chinese for explanations unless the owner requests otherwise.
- Keep website navigation and research terminology in English, with Chinese explanations where useful.
- Explain important research terms on first use.
- Do not silently decide research methodology, inclusion criteria, or benchmark protocols. Present options and trade-offs when a decision affects research validity.
- Prefer small, reviewable changes over unnecessary rewrites.
