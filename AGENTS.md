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
  - `md/exams/problems/*.md`: readable exam problems.
  - `md/exams/solutions/*.md`: readable solution proposals.
- `midterms/`: currently out of scope unless explicitly requested.

Agents should read from the `md/` mirror by default. Use PDFs only when checking transcription fidelity, figures, page layout, or other details missing from Markdown.
