# TDT4145 — Pre-curriculum exam problems

Problems on topics not in `md/curriculum.md` (storage / indexes / queries /
transactions / recovery). These cover material you've already mastered —
listings only, no exercise-type elaboration. For storage/transaction problems
see `chapter_index.md`.

---

## ER / EER modeling

Includes: design from prose, ER critique, ER → relational mapping, instance / forekomst diagrams, EER-category questions.

- D2018 Problem 1 — football-league ER.
- D2018 Problem 2a — book/author/genre relational schema → ER.
- D2018 Problem 4 — find errors in Course/Student/ExercisePackage ER.
- D2018_K Problem 1 — Lotto-game ER.
- D2018_K Problem 2 — Photo/Photographer EER (with category) → relations.
- D2018_K Problem 3 — currency-rates relational schema → ER.
- D2019 Problem 1 — study-program / course / LUB ER.
- D2019 Problem 6 — athletics EER (Throw/Jump/Run subtypes) → relations.
- D2019 Problem 11 — when are EER categories appropriate.
- D2019 Problem 12 — instance diagram for book/author/genre ER.
- D2019_K Problem 2 — Norwegian-counties/POI tourism ER.
- D2019_K Problem 3 — Person/Project/Timesheet relational schema → ER.
- D2020 Problem 1 — find errors in VLDB review / programcommittee ER.
- D2020 Problem 2 — EER (specialization, multivalued attributes) → relations.
- D2021 Problem 16 — national-vaccination ER.
- D2022 Problem 12 — police speed-camera ER.
- D2023 Problem 5 — Vehicle/Truck/Bus EER → relational schema.
- D2023 Problem 6 — comic-strip ER.
- D2023_K Problem 1 — buy/sell second-hand marketplace EER.
- D2024 Problem 15 — Utra building / energy ER.
- D2025 Problem 14 — "Eksperter i Team" course ER.

---

## SQL (SELECT, DML, DDL)

Includes: `SELECT` with joins / aggregation / `NOT EXISTS` / sub-queries / ordering, `INSERT`, `UPDATE`, `CREATE TABLE` with constraints. Pure SQL/RA equivalence-checking problems also live here.

- D2018 Problem 2b — `SELECT` genres containing 'fantasy'.
- D2018 Problem 2c — `SELECT` count of books per publisher.
- D2018 Problem 2d — `INSERT` Kim Leine.
- D2018_K Problem 4 — countries using Euro.
- D2018_K Problem 5 — min/max/avg currency rate per code in 2017.
- D2018_K Problem 7 — months where SEK > NOK every day.
- D2019 Problem 3 — count exam results per year for TDT4145.
- D2019 Problem 4 — courses with exam but no A grade.
- D2019 Problem 5 — `CREATE TABLE ExamResults` with PK/FK and CHECK.
- D2019_K Problem 5 — total hours on NTNU-Campus.
- D2019_K Problem 6 — per-project person count and total hours (incl. zero).
- D2019_K Problem 7 — `UPDATE` increase hourly rate by 10% for 'Bowim'.
- D2020 Problem 4 — count municipalities per county.
- D2020 Problem 5 — dates with zero hospitalized in Trondheim (`NOT EXISTS`).
- D2020 Problem 6 — `INSERT` statements for 6 April 2020 data.
- D2023 Problem 4 — equivalence of SQL/RA queries (cross/natural/inner joins).
- D2024 Problem 11 — choose correct SQL queries (`NOT IN`, `EXISTS`).

---

## Relational algebra

Includes: write an RA expression / tree, read a given RA expression and explain it, fill blanks in an RA query.

- D2018 Problem 2e — co-authors of Linn Ullmann.
- D2018_K Problem 6 — explain information need of given RA query.
- D2019 Problem 2 — students with grade A in TDT4145.
- D2019_K Problem 4 — persons allocated to NTNU-Campus.
- D2020 Problem 3 — fill in 6 boxes (A–F) of RA query (Corona DB).
- D2024 Problem 10 — choose correct RA expressions.
- D2025 Problem 13 — Nordland cities ≥ 10 000 inhabitants, sorted desc.

---

## Functional dependencies & keys

Includes: derive FDs (Armstrong), compute attribute closure `X+`, find candidate / superkeys, infer missing tuple values from F, upper-bound number of legal tuples.

- D2018 Problem 3a — FD reasoning on long-jump table (Wind→Attempt).
- D2018 Problem 3b — construct R(A,B,C,D) instance violating CD→A and B→D.
- D2018 Problem 3c — Armstrong: derive WX→Z from WY→Z, X→Y.
- D2018_K Problem 8 — find X,Y,Z values consistent with A→B; BC→D; D→A.
- D2018_K Problem 9 — define candidate key, find all candidate keys.
- D2018_K Problem 11 — define attribute closure X+ and give algorithm.
- D2019 Problem 9 — FDs on schema / explain reasoning.
- D2019_K Problem 8 — all superkeys of R given F={A→B; C→D}.
- D2020 Problem 8 — max rows in R(A..E) over int 1–10; primary key.
- D2020 Problem 9 — primary key and max rows given C→BD.
- D2023 Problem 1 — candidate keys for R given F={BC→A; D→C}.
- D2024 Problem 12 — FD reasoning: X, Y values given A→B, CD→B.

---

## Normal-form determination

Includes: state the highest NF (1NF/2NF/3NF/BCNF/4NF) the schema satisfies and justify; conceptual NF questions.

- D2018_K Problem 10 — highest NF of R given F.
- D2019 Problem 10 — drawbacks when not in BCNF (three classes).
- D2019_K Problem 9 — define 3NF.
- D2019_K Problem 11 — when not to normalize fully; example.
- D2020 Problem 7 — original example of 2NF-but-not-3NF + decompose.
- D2020 Problem 10 — assumption needed for 4NF on Bil(model,fuel,drive).
- D2023 Problem 2 — highest NF of R given F={C→ABD; D→CEF}.
- D2024 Problem 13 — highest NF of R given F={BC→A; C→D; D→C; CD→E}.
- D2025 Problem 11 — highest NF of `Geography(CountryCode,…)`.

---

## Decomposition (lossless / FD-preservation)

Includes: BCNF / 3NF decomposition with proof; lossless-join / FD-preserving check by chase or inspection.

- D2018 Problem 3d — lossless decomposition of R(A,B,C,D) into R1/R2/R3.
- D2019 Problem 9 — explain non-FD-preserving decomposition with example. *(also tagged FD)*
- D2019_K Problem 10 — explain non-lossless decomposition with example.
- D2023 Problem 3 — does R(A..F) → R1(A,B,C), R2(D,E,F) preserve the join.
- D2024 Problem 14 — properties of decomposition R(A..E) → R1(A,B), R2(C,D,E).
- D2025 Problem 12 — decompose `Exam` table to BCNF (preserving FDs, lossless).

---

## Conceptual short-answer (non-storage)

Definition / motivation questions on relational concepts, not on the storage curriculum.

- D2019 Problem 7 — why every relation has at least one key.
- D2019 Problem 8 — distinguish key vs. superkey.
- D2019_K Problem 1 — define 5 of 8 concepts (miniworld, schema, FD, …).

---

## 0-point comments box

Final "if anything is unclear, write to the sensor here" box. Listed for completeness — nothing to study.

- D2021 Problem 17.
- D2022 Problem 13.
- D2023 Problem 19.
- D2023_K Problem 13.
- D2024 Problem 16.
- D2025 Problem 15.

---

## Topic counts

| Topic | # problems |
|---|---:|
| ER / EER modeling | 21 |
| SQL | 17 |
| Relational algebra | 7 |
| Functional dependencies | 12 |
| Normal-form determination | 9 |
| Decomposition | 6 |
| Conceptual short-answer | 3 |
| 0-pt placeholder | 6 |
| **Total** | **81** |

(Total primary 109 + total here 81 = 190; note D2019 Problem 9 appears under both FD and Decomposition since the agent flagged both readings.)
