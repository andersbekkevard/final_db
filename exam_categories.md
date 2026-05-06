# TDT4145 — Exam Question Categories

Classification of every numbered problem across the 12 final-exam papers in
`exams/problems/` (D2018, D2018_K, D2019, D2019_K, D2020, D2021, D2022, D2023,
D2023_K, D2024, D2024_K, D2025).

Each `##`-level numbered problem in the markdown mirror counts as one exercise.
Multi-letter sub-problems that appear as separate `##` headers (e.g. D2018
2a/2b/2c/…) are counted separately. **Total exercises classified: 206.**

---

## Summary tally

| #  | Category                                          | Count |
|----|---------------------------------------------------|------:|
| 1  | ER/EER modeling (design from prose)               | 10 |
| 2  | ER → relational mapping                           | 8  |
| 3  | ER critique (errors in given diagram)             | 2  |
| 4  | SQL `SELECT` queries                              | 13 |
| 5  | SQL DML / DDL                                     | 4  |
| 6  | Relational algebra                                | 9  |
| 7  | Functional dependencies & keys                    | 12 |
| 8  | Normal-form determination                         | 5  |
| 9  | Normalization decomposition                       | 3  |
| 10 | Decomposition properties (lossless / FD pres.)    | 5  |
| 11 | B+-trees (construction & sizing)                  | 14 |
| 12 | Hashing (extendible & static)                     | 12 |
| 13 | Index access paths / query block-cost             | 24 |
| 14 | Join algorithm cost                               | 4  |
| 15 | External sorting                                  | 1  |
| 16 | Storage layout — heap files & block format        | 2  |
| 17 | Conflict serializability                          | 6  |
| 18 | Recoverability classification                     | 10 |
| 19 | Two-phase locking (2PL)                           | 14 |
| 20 | Isolation levels / snapshot isolation             | 4  |
| 21 | ARIES — Analysis phase                            | 9  |
| 22 | ARIES — Redo phase                                | 7  |
| 23 | ARIES — Undo phase                                | 3  |
| 24 | ARIES — conceptual / true-false                   | 6  |
| 25 | Conceptual / theory short-answer                  | 11 |
| 26 | Comment placeholder (0 pts, end of paper)         | 7  |
|    | **Oneoffs (unclassified)**                        | 1  |
|    | **Total**                                         |**206**|

---

## Category definitions

### 1. ER/EER modeling (design from prose) — 10
Given a natural-language description of a domain, draw an EER diagram
(entities, relationships, cardinalities, weak/identifying, specialization,
categories). Highest-weighted single problem on most papers.
*Example:* D2025 #14 — design an EER for "Eksperter i Team" with cohorts,
villages, groups, learning-assistants and graders.

Members: D2018 #1, D2018_K #1, D2019 #1, D2019_K #2, D2021 #16, D2022 #12,
D2023 #6, D2023_K #1, D2024 #15, D2025 #14.

### 2. ER → relational mapping — 8
Translate a given EER (often with specialization, weak entities,
multi-valued attributes) into a relational schema with PKs/FKs, justifying
each table choice. The reverse direction (relational → ER) is filed here too.
*Example:* D2019 #6 — convert athletics-results EER with disjoint
specialization (Throw/Jump/Run) into tables.

Members: D2018 #2a, D2018_K #2, D2018_K #3a, D2019 #6, D2019_K #3, D2020 #2,
D2023 #5, D2024_K #13.

### 3. ER critique — 2
Given a flawed ER/EER diagram for a stated domain, list and explain the
modelling errors.
*Example:* D2020 #1 — find errors in the proposed VLDB-conference paper
review schema.

Members: D2018 #4, D2020 #1.

### 4. SQL `SELECT` queries — 13
Write or recognize an SQL `SELECT` against a given schema. Includes joins,
aggregation, `NOT EXISTS`, sub-queries, ordering.
*Example:* D2020 #5 — find the dates with zero hospitalizations in
Trondheim using `NOT EXISTS`.

Members: D2018 #2b, D2018 #2c, D2018_K #3b, D2018_K #3c, D2018_K #3e, D2019 #3,
D2019 #4, D2019_K #5, D2019_K #6, D2020 #4, D2020 #5, D2024 #11, D2024_K #10.

### 5. SQL DML / DDL — 4
Statements that change schema or data: `INSERT`, `UPDATE`, `CREATE TABLE`
(including constraints).
*Example:* D2019 #5 — `CREATE TABLE ExamResults` with PK/FK and check
constraints.

Members: D2018 #2d, D2019 #5, D2019_K #7, D2020 #6.

### 6. Relational algebra — 9
Express a query as a relational-algebra expression or tree, or read a given
RA expression and explain it / verify equivalence with SQL.
*Example:* D2025 #13 — RA graph for "cities in Nordland with ≥10 000
inhabitants, sorted descending by population".

Members: D2018 #2e, D2018_K #3d, D2019 #2, D2019_K #4, D2020 #3, D2023 #4,
D2024 #10, D2024_K #9, D2025 #13.

### 7. Functional dependencies & keys — 12
Reasoning about FDs (and MVDs for 4NF-related items): derive new FDs
(Armstrong), compute attribute closure `X+`, find candidate / superkeys,
infer missing tuple values from F, or upper-bound the number of legal
tuples.
*Example:* D2018 #3c — prove `WX → Z` from `WY → Z` and `X → Y`.

Members: D2018 #3a, D2018 #3b, D2018 #3c, D2018_K #4a, D2018_K #4b, D2018_K #4d,
D2019_K #8, D2020 #8, D2020 #9, D2023 #1, D2024 #12, D2024_K #12.

### 8. Normal-form determination — 5
Given a schema and its FDs (or MVDs for 4NF), state the highest normal form
(1NF/2NF/3NF/BCNF/4NF) the schema satisfies and justify.
*Example:* D2025 #11 — `Geography(CountryCode, CountryName, Population,
Continent)` with `CountryCode → CountryName; CountryName → CountryCode,
Population, Continent`: highest NF?

Members: D2018_K #4c, D2020 #10, D2023 #2, D2024 #13, D2025 #11.

### 9. Normalization decomposition — 3
Decompose a non-BCNF schema into BCNF (or 3NF) sub-tables and prove the
decomposition is attribute-preserving, FD-preserving, and lossless-join.
*Example:* D2025 #12 — decompose
`Exam(StudentNo, StudentName, CourseNo, CourseName, ExamNo, ExamDay,
ExamMonth, ExamYear, Grade)` into BCNF, with proof.

Members: D2020 #7, D2024_K #11, D2025 #12.

### 10. Decomposition properties (lossless-join / FD preservation) — 5
Given a candidate decomposition, decide whether it is lossless and/or
FD-preserving (often via the chase or by inspection), or explain the
concept with an example.
*Example:* D2018 #3d — does decomposing `R(ABCD)` (key `BC`) into
`R1(AB), R2(BC), R3(CD)` preserve the join?

Members: D2018 #3d, D2019 #9, D2019_K #10, D2023 #3, D2024 #14.

### 11. B+-trees (construction & sizing) — 14
Two flavours, both filed here:
(a) Insert a sequence of keys into a B+-tree of given fan-out, drawing the
state after each split (or recognising which insertion sequence produced a
given final tree).
(b) Given block size, key/RID/BlockId widths, record count and fill factor,
compute the number of blocks at level 0 / level 1 / etc.
*Example:* D2025 #1 — clustered B+-tree, 20 200 records of 120 B, 4 KB
blocks, 2/3 fill: how many leaf blocks?

Members: D2018 #5, D2018_K #6a, D2019_K #12, D2020 #12, D2021 #6, D2022 #1,
D2023 #8, D2023_K #2, D2024 #1, D2024_K #1, D2024_K #3a, D2024_K #3b,
D2025 #1, D2025 #2.

### 12. Hashing (extendible & static) — 12
Either step through extendible-hashing inserts (track global / local depth,
splits) or compute block-access cost on a static-hash file (with overflow).
*Example:* D2020 #11 — given an extendible-hash directory, identify the
first block that must split and the resulting local depths.

Members: D2018_K #5, D2019 #13, D2019_K #13, D2020 #11, D2021 #5,
D2021 #9, D2021 #10, D2022 #2, D2023 #9, D2023_K #4, D2023_K #5, D2024 #2.

### 13. Index access paths / query block-cost — 24
Given an `Ansatt`/`Student`/`By` table with a clustered B+-tree on one key
and an unclustered B+-tree (or hash) on another, count blocks accessed for
a specific SQL query under "optimal execution". Single biggest category.
*Example:* D2025 #4 — optimal block count for
`SELECT ForNavn FROM Ansatt WHERE EtterNavn='Johannessen'`.

Members: D2018 #6a, D2018 #6b, D2018 #6c, D2018 #6d, D2018_K #6b,
D2018_K #6c, D2019 #14, D2019 #15, D2019 #16, D2019 #17, D2019 #18,
D2020 #13, D2021 #8, D2022 #9, D2023 #12, D2023 #13, D2023 #14,
D2023_K #3, D2024 #8, D2024_K #3c, D2024_K #3d, D2025 #3, D2025 #4, D2025 #5.

### 14. Join algorithm cost — 4
Given two relations of stated block size and a buffer of B blocks, compute
I/O cost of a join — almost always block-nested-loop.
*Example:* D2022 #11 — block-NL-join with an 8-block buffer.

Members: D2018_K #7, D2021 #12, D2022 #11, D2023 #10.

### 15. External sorting — 1
External merge-sort I/O accounting given record count and buffer size.

Members: D2023 #11.

### 16. Storage layout — heap files & block format — 2
Compute # blocks in a heap file given record/block sizes and 100% fill,
*or* draw / annotate the slotted-page layout (records-grow-up region with
a trailing pointer / slot vector growing down) for a stated record set.

Members: D2023 #7, D2024_K #2.

### 17. Conflict serializability — 6
Given a set of histories (interleaved `r/w` operations), select the
conflict-serializable ones (precedence-graph cycle test).
*Example:* D2025 #6 — five histories, pick the conflict-serializable
ones.

Members: D2021 #15, D2022 #7, D2023_K #10, D2024 #9, D2024_K #5, D2025 #6.

### 18. Recoverability classification — 10
Classify a history along the hierarchy *unrecoverable / recoverable / ACA
/ strict* (or pick which property holds).
*Example:* D2018 #7 — three histories, classify each.

Members: D2018 #7, D2019_K #16, D2021 #1, D2021 #2, D2021 #4, D2022 #8,
D2023_K #7, D2023_K #8, D2023_K #9, D2024_K #4.

### 19. Two-phase locking (2PL) — 14
Three sub-flavours, all filed here:
(a) Add lock/unlock operations under rigorous 2PL to a given schedule.
(b) Determine the commit order produced by feeding a sequence into rigorous
2PL (and whether deadlock occurs).
(c) Reconstruct which operation sequence produced a given lock-table state.
*Example:* D2025 #10 — given
`r1(X); r2(X); w1(X); r3(Y); c1; w2(Y); c2; r3(Z); c3;`, what is the
commit order under rigorous 2PL?

Members: D2018 #8, D2018_K #8b, D2019 #19, D2019 #20, D2020 #15, D2021 #3,
D2021 #11, D2022 #6, D2023 #15, D2023 #16, D2024 #3, D2024_K #6, D2025 #9,
D2025 #10.

### 20. Isolation levels / snapshot isolation — 4
Pick the right SQL isolation level for a stated anomaly, or compute the
final value of an item under MVCC / snapshot isolation, or evaluate
true/false claims about SI vs. serializable.
*Example:* D2024 #4 — compute final `D` under snapshot isolation with
two concurrent transactions.

Members: D2020 #14, D2022 #4, D2023_K #6, D2024 #4.

### 21. ARIES — Analysis phase — 9
Given a log (LSN, prevLSN, op, page) plus an initial transaction-table /
DPT at the checkpoint, produce the post-Analysis transaction-table and
DPT, *or* answer "which pages can we be sure were written before the
crash?".
*Example:* D2025 #7 — DPT after analysis given the log of T1/T2/T3.

Members: D2018 #9a, D2019 #21, D2020 #16, D2021 #7, D2023_K #11, D2024 #5,
D2024 #7, D2025 #7, D2025 #8.

### 22. ARIES — Redo phase — 7
Given DPT and per-page PageLSN, decide which log entries must be redone,
or where the redo scan begins, or compute new PageLSN values.
*Example:* D2023 #17 — which log entries require redo given the DPT?

Members: D2019 #22, D2020 #17, D2021 #14, D2022 #10, D2023 #17, D2023_K #12,
D2024_K #7.

### 23. ARIES — Undo phase — 3
Determine which loser transactions are rolled back and which CLRs / abort
records appear in the log.
*Example:* D2024 #6 — list the CLRs and abort records written during
undo.

Members: D2018 #9b, D2023 #18, D2024 #6.

### 24. ARIES — conceptual / true-false — 6
Multi-select / explain-style claims about WAL, force / no-force, steal /
no-steal, checkpoint contents, why redo starts at the oldest recLSN, etc.
*Example:* D2022 #3 — pick the correct statements about WAL and the
steal/force policy.

Members: D2018_K #9a, D2018_K #9b, D2019_K #17, D2022 #3, D2022 #5,
D2024_K #8.

### 25. Conceptual / theory short-answer — 11
Define a term ("miniworld", superkey vs. candidate key, ACID properties,
recovery motivation, three problems with non-BCNF schemas, when EER
categories are appropriate, etc.) or pick true claims about
WAL / MVCC / catalog. Distinguished from category 24 in that the topic is
*not* ARIES.
*Example:* D2019_K #15 — explain atomicity, consistency, isolation,
durability.

Members: D2018_K #8a, D2019 #7, D2019 #8, D2019 #10, D2019 #11,
D2019_K #1, D2019_K #9, D2019_K #11, D2019_K #14, D2019_K #15, D2021 #13.

### 26. Comment placeholder (0 pts) — 7
Final "if anything is unclear write to sensor here" 0-point box used by
papers since 2021. Listed so the count balances; nothing to study.

Members: D2021 #17, D2022 #13, D2023 #19, D2023_K #13, D2024 #16, D2024_K #14,
D2025 #15.

---

## Oneoffs (unclassified)

Exercises that did not fit any recurring category:

- **D2019 #12 — Forekomstdiagram (instance diagram).** Given populated
  rows for `book / author / publisher / genre`, draw the corresponding
  *instance* of an ER diagram (entity occurrences and relationship
  links). Tests ER semantics through population, distinct from designing
  a schema (cat. 1) or critiquing one (cat. 3).
