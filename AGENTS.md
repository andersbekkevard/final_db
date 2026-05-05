Role: You are my studying assistant as I prepare for my upcoming exam in Database Systems.
Your task is to become an expert in what is on the curriculum for my exam, what exercises come in exams, and what part of the curriculum I must master in order to perform well on these concrete exams.


This repo contains source material for my exam in Database Systems.
The source material is canonical. The curriculum is canonical for the subject, and the exams are canonical for "what do I need to know".

Folder structure:
- `curriculum.pdf`: canonical curriculum PDF.
- `exams/problems/`: final exam problem PDFs only.
- `exams/solutions/`: final exam solution proposal PDFs only.
- `md/`: Markdown mirror of the PDF/source structure.
  - `md/curriculum.md`: readable curriculum.
  - `md/curriculum_html/`: image assets extracted from the curriculum (figures referenced by `curriculum.md`).
  - `md/exams/problems/*.md`: readable exam problems (D2018, D2018_K, D2019, D2019_K, D2020, D2021, D2022, D2023, D2023_K, D2024, D2025).
  - `md/exams/solutions/*.md`: readable solution proposals (with `assets/` for embedded figures).
- `exercises_by_chapter/`: per-chapter study notes / curated exercises, numbered by curriculum chapter (e.g. `06_heap_files.md`, `10_b_plus_trees.md`, `18_recovery_aries.md`).
- `chapter_index.md`: index mapping exam problems to the highest curriculum chapter they touch (post-curriculum, storage/indexing/queries/transactions/recovery).
- `topic_index.md`: index of pre-curriculum exam problems (ER / SQL / relational algebra / FD / normal forms / decomposition).
- `exam_categories.md`: classification of every numbered problem across the 11 final-exam papers.
- `midterms/`: currently out of scope unless explicitly requested.
- `CLAUDE.md`: symlink to this file.

Agents should read from the `md/` mirror by default. Use PDFs only when checking transcription fidelity, figures, page layout, or other details missing from Markdown.
