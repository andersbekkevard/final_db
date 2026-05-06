# TDT4145 — Final-exam practice index by curriculum chapter

Problems are mapped **cumulatively** to the highest curriculum chapter they touch.
Pre-curriculum topics (ER / SQL / relational algebra / FD / normal forms /
decomposition / non-storage conceptual) live in `topic_index.md`.

Source: 12 final-exam papers (`md/exams/problems/`): D2018, D2018_K, D2019,
D2019_K, D2020, D2021, D2022, D2023, D2023_K, D2024, D2024_K, D2025.

---

## Chapter 1 — DBMS architecture

**About:** Software stack of a SQL DBMS — compiler, optimizer, executor, buffer, log.

**Exercise types seen on exams:** none isolated.

**Practice problems:** none — only ever appears as background context for higher chapters.

---

## Chapter 2 — Database storage

**About:** Where the database lives — files vs. raw partitions, deviceId abstraction, free-space management.

**Exercise types seen on exams:** none isolated.

**Practice problems:** none.

---

## Chapter 3 — Record format

**About:** Layout of a single row — fixed-offset, variable-length record vector, delimiters, column stores.

**Exercise types seen on exams:** none isolated (always rolled into ch. 10/12 sizing).

**Practice problems:** none directly — but the per-record byte counts you assume here drive every B+-tree / heap-file / hash-file sizing problem.

---

## Chapter 4 — Block format

**About:** Block as the unit of I/O — slot directory, RID = (BlockId, slot), records-grow-up + page-directory-grows-down, flip/flop checksums.

**Exercise types seen on exams:**
- Draw / annotate the slotted-page layout for a stated record set: header, records-grow-up region, trailing pointer/slot vector (records-grow-down).

**Practice problems:**
- D2024_K Problem 2 — slotted page with trailing pointer vector (first ever isolated Ch 4 exam exercise).

---

## Chapter 5 — Database buffer

**About:** In-memory block cache with hash index on BlockId; prefetching; force/no-force; steal/no-steal terminology.

**Exercise types seen on exams:** none isolated. Force/steal *as a recovery property* lives in chapter 18.

**Practice problems:** none directly.

---

## Chapter 6 — Heap files

**About:** Unordered records, scan-only access, optionally split full-vs-free linked lists.

**Exercise types seen on exams:**
- Given record size, block size, and 100% fill, count the blocks in the heap file.

**Practice problems:**
- D2023 Problem 7 — heap file: blocks for 10 000 records of 100 B.

---

## Chapter 7 — Static hashing

**About:** `h(K) = K mod N` over fixed `N` blocks, with overflow handling (open / separate / multiple hashing).

**Exercise types seen on exams:**
- Given a hash file with overflow chains, compute the average number of block accesses for a successful lookup.

**Practice problems:**
- D2021 Problem 10 — average block accesses after a sequence of inserts.
- D2023_K Problem 4 — same shape, different inputs.

---

## Chapter 8 — Extendible hashing

**About:** Directory + global/local depth; block split rehashes only its bucket; directory doubles when a full block has local depth = global depth.

**Exercise types seen on exams:**
- Insert a sequence of keys (hash given) into an empty / partial structure; draw global+local depths after each insert.
- Given a partial figure, identify the *first* block that must split and the resulting local depths.
- Given final state, count blocks with a stated local depth.
- Given that global depth went from `g₁` to `g₂`, list possible local depths.
- Pick which of N candidate figures are legal extendible-hash structures.

**Practice problems:**
- D2018_K Problem 5 — insert 7 keys, h(K)=K mod 8.
- D2019 Problem 13 — possible local depths given global depth went 2→5.
- D2019_K Problem 13 — insert 11 keys.
- D2020 Problem 11 — first block to split, resulting local depths.
- D2021 Problem 5 — local-depth value in a given figure.
- D2022 Problem 2 — pick legal extendible-hashing structures.
- D2023 Problem 9 — count blocks with local depth = 3.
- D2024 Problem 2 — count blocks with local depth = 3.

---

## Chapter 9 — Indexing concepts

**About:** Clustered vs. unclustered, primary vs. secondary; uniqueness as an index property; menu of storage alternatives (clustered B+ / heap+B+ / heap / LSM / column / clustered hash).

**Exercise types seen on exams:**
- Choose / explain how to enforce uniqueness on multiple attributes via indexes.

**Practice problems:**
- D2019 Problem 18 — uniqueness on `studno` and `email` via indexes.

---

## Chapter 10 — B+-trees

**About:** Balanced ordered tree with all data at leaves; sideways pointers; split copies key up at leaf and moves key up internally; fill factor 2/3.

**Exercise types seen on exams:**
- Insert a sequence of keys into an empty B+-tree of given fan-out; draw the tree after each split (or just the final state).
- Given a final tree, pick which of several candidate insertion sequences produced it.
- Sizing: given block size, record size, key/RID/BlockId widths, record count, fill factor 2/3, compute leaf-block count.
- Sizing: same setup, compute level-1 block count and total number of levels.
- Given keys 1…N, classify which leaf-block letter (a–e) each key ends up in.

**Practice problems:**
- D2018 Problem 5 — insert 10 keys, show splits.
- D2018_K Problem 6a — clustered B+-tree sizing: blocks per level.
- D2019_K Problem 12 — insert 11 keys.
- D2020 Problem 12 — leaf-block assignment (a–e) for 10 keys.
- D2021 Problem 6 — which insertion sequence yields a given tree.
- D2022 Problem 1 — same shape: which sequence yields the given tree.
- D2023 Problem 8 — clustered B+-tree leaf-block count, fill 2/3.
- D2023_K Problem 2 — insert 10 keys, show splits.
- D2024 Problem 1 — which insertion sequence yields the given tree.
- D2024_K Problem 1 — insert 5 keys; figure fan-out from 1000 B records / 4096 B blocks, then construct.
- D2024_K Problem 3a — clustered B+-tree leaf-block count, 40 000 records of 100 B, fill 2/3.
- D2024_K Problem 3b — unclustered B+-tree leaf-block count on `epost` (25 B).
- D2025 Problem 1 — leaf-block count given record/block size.
- D2025 Problem 2 — level-1 block count.

---

## Chapter 11 — LSM trees

**About:** Memtable + WAL + tiered SSTables, write-optimized; bloom filters per SST; used in RocksDB / BigTable.

**Exercise types seen on exams:** none isolated — LSM only appears in passing in conceptual true/false items filed under ch. 18.

**Practice problems:** none.

---

## Chapter 12 — Queries and storage structures (access paths)

**About:** Block-cost reasoning for a single SELECT against one of {heap, clustered B+, heap + unclustered B+, clustered hash}, under "optimal access path".

**Exercise types seen on exams:**
- Given a clustered B+-tree on a primary key, count blocks for `WHERE pk = c` (typically just tree height).
- Given heap + unclustered B+-tree on a non-key, count blocks for `WHERE attr = c` — including the RID dereferences.
- Range query (`WHERE attr > c`, `attr BETWEEN`) — when does scanning the heap beat following the unclustered index?
- ORDER BY / GROUP BY — does the index avoid a sort?
- `SELECT *` and `SELECT DISTINCT attr` cost.
- Suggest an additional index to speed up a slow query.
- Pick best storage configuration for a stated mixed workload (clustered vs. unclustered B+).
- True/false claims about clustered-B+-tree access costs.

**Practice problems:**
- D2018 Problem 6a — equality on full key (clustered B+).
- D2018 Problem 6b — partial key + filter.
- D2018 Problem 6c — ORDER BY full key.
- D2018 Problem 6d — GROUP BY exno + filter.
- D2018_K Problem 6b — `WHERE regNo=…` with B+-tree on `passId`.
- D2018_K Problem 6c — propose index to speed up the query.
- D2019 Problem 14 — `SELECT * FROM Student`.
- D2019 Problem 15 — equality via hash index.
- D2019 Problem 16 — `WHERE lastname='Hansen'` using unclustered B+.
- D2019 Problem 17 — `SELECT DISTINCT lastname`.
- D2020 Problem 13 — four-part block-cost on Student with two B+-trees.
- D2021 Problem 8 — `WHERE bwid=2001` (clustered B+).
- D2021 Problem 9 — `SELECT * FROM Birdwatcher` (clustered hash).
- D2022 Problem 9 — true/false on clustered-B+-tree block costs.
- D2023 Problem 12 — `WHERE mykey=7` (clustered B+).
- D2023 Problem 13 — `WHERE mykey<7`.
- D2023 Problem 14 — `ORDER BY mykey`.
- D2023_K Problem 3 — `WHERE bwid=2001`.
- D2023_K Problem 5 — `SELECT *` (clustered hash).
- D2024 Problem 8 — best storage choice (clustered vs. unclustered B+) for mixed workload.
- D2024_K Problem 3c — `WHERE studnr=123456` on clustered B+.
- D2024_K Problem 3d — `WHERE epost='hansnils@stud.ntnu.no'` on unclustered B+.
- D2025 Problem 3 — `SELECT EtterNavn WHERE AnsattId=12001`.
- D2025 Problem 4 — `SELECT ForNavn WHERE EtterNavn='Johannessen'`.
- D2025 Problem 5 — `SELECT EtterNavn ORDER BY EtterNavn DESC`.

---

## Chapter 13 — JOIN queries (block-NL)

**About:** Block-nested-loop join cost when joining two heap files with a B-block buffer; smaller table goes outer.

**Exercise types seen on exams:**
- Given two relations of stated block counts and a buffer of B blocks, compute total I/O for block-NL.
- Show that swapping outer/inner changes cost; justify the smaller-outer rule.
- Note simple optimization: if a small predicate fixes one side to one row, you only scan the other side.

**Practice problems:**
- D2018_K Problem 7 — `Passeringer × Kjøretøy`, 32-block buffer.
- D2021 Problem 12 — `Department × Employee`, 8-block buffer.
- D2022 Problem 11 — `Klasse × Student`, 8-block buffer.
- D2023 Problem 10 — `Class × Student`, 7-block buffer.

---

## Chapter 14 — External merge sort

**About:** Initial sort phase (`n_R = ⌈b / n_B⌉` runs), then merge phase with degree `d_M = min(n_B − 1, n_R)` and `⌈log_{d_M}(n_R)⌉` passes; total I/O = read+write per pass.

**Exercise types seen on exams:**
- Given block count `b` and buffer `n_B`, compute number of initial runs, merge degree, number of passes, and total I/O.

**Practice problems:**
- D2023 Problem 11 — 512 blocks, buffer = 5.

---

## Chapter 15 — Introduction to transactions

**About:** ACID properties; the four anomalies (dirty read, dirty write, unrepeatable / read skew, incorrect summary); SQL isolation levels and which anomaly each blocks.

**Exercise types seen on exams:**
- Define / explain ACID (one letter or all four).
- Pick the SQL isolation level that prevents a stated anomaly (e.g. phantom inserts).

**Practice problems:**
- D2018_K Problem 8a — explain the C in ACID.
- D2019_K Problem 15 — explain all four ACID properties.
- D2020 Problem 14 — isolation level to prevent phantom inserts.

---

## Chapter 16 — Transactions and theory (recoverability + serializability)

**About:** Schedules, conflict pairs, recoverable ⊃ ACA ⊃ strict hierarchy, conflict serializability via precedence-graph cycle test.

**Exercise types seen on exams:**
- Given a list of histories (with `r/w/c/a`), classify each as unrecoverable / recoverable / ACA / strict (pick the *strongest* property).
- Given a set of histories, pick the conflict-serializable ones (build the precedence graph, look for cycles).

**Practice problems:**
- D2018 Problem 7 — classify three histories on the recoverability hierarchy.
- D2019_K Problem 16 — classify three histories.
- D2021 Problem 1 — recoverability class of a single history.
- D2021 Problem 2 — recoverability class of a single history.
- D2021 Problem 4 — recoverability class of a single history.
- D2021 Problem 15 — pick the conflict-serializable histories.
- D2022 Problem 7 — pick the conflict-serializable histories.
- D2022 Problem 8 — pick the recoverable histories.
- D2023_K Problem 7 — recoverability class.
- D2023_K Problem 8 — recoverability class.
- D2023_K Problem 9 — recoverability class.
- D2023_K Problem 10 — pick conflict-serializable histories.
- D2024 Problem 9 — pick conflict-serializable histories.
- D2024_K Problem 4 — classify H1/H2/H3 on the recoverability hierarchy.
- D2024_K Problem 5 — pick conflict-serializable histories.
- D2025 Problem 6 — pick conflict-serializable histories.

---

## Chapter 17 — Concurrency control (2PL + MVCC / SI)

**About:** Read/write locks; basic / conservative / strict / rigorous 2PL; deadlock handling; snapshot isolation as alternative to read locks (writers still lock until commit).

**Exercise types seen on exams:**
- Given a sequence `r/w/c/a` of basic operations, annotate the schedule with rigorous-2PL lock/unlock and produce the actual commit order (detect deadlock if it occurs).
- Given a partially populated lock table (has-locks / wants-locks lists), reconstruct the operation sequence that produced it.
- Pick which 2PL flavor cannot deadlock (conservative); pick the correct claim about strict vs. rigorous.
- Snapshot-isolation execution: compute final value of an item under two concurrent transactions where one reads-modifies-writes.
- True/false on SI vs. serializable, write-skew, lost-update under SI.

**Practice problems:**
- D2018 Problem 8 — apply rigorous 2PL to schedule S3.
- D2018_K Problem 8b — rewrite history H1 with rigorous-2PL locks.
- D2019 Problem 19 — 2PL execution + deadlock check.
- D2019 Problem 20 — 2PL execution + deadlock check.
- D2020 Problem 15 — commit order under rigorous 2PL.
- D2021 Problem 3 — which 2PL flavor cannot deadlock.
- D2021 Problem 11 — commit order under rigorous 2PL.
- D2022 Problem 4 — true/false on SI vs. serializability vs. 2PL.
- D2022 Problem 6 — commit order under rigorous 2PL.
- D2023 Problem 15 — find the originating operation sequence from a lock-table figure.
- D2023 Problem 16 — commit order under rigorous 2PL.
- D2023_K Problem 6 — true/false on snapshot isolation.
- D2024 Problem 3 — commit order under rigorous 2PL.
- D2024 Problem 4 — final value of `D` under snapshot isolation.
- D2024_K Problem 6 — rigorous 2PL deadlock: draw lock data structure showing held + wanted locks.
- D2025 Problem 9 — find the originating operation sequence from a lock-table figure.
- D2025 Problem 10 — commit order under rigorous 2PL.

---

## Chapter 18 — Recovery / ARIES

**About:** WAL + force-log-at-commit; transaction table + Dirty Page Table; PageLSN per block; three-phase recovery (Analysis from last checkpoint forward; Redo from oldest recLSN; Undo from end backwards through losers, writing CLRs).

**Exercise types seen on exams:**
- **Analysis:** given a log (LSN, prevLSN, op, page) and the checkpoint TT/DPT, produce the post-Analysis TT and DPT.
- **Redo:** given DPT and per-page PageLSN at start of redo, decide which log records get redone and why; or determine the LSN at which redo scan begins.
- **Undo:** list the CLRs and abort records written during undo for the loser transactions; resulting PageLSN for the affected pages.
- **"Which pages can we be sure were flushed before the crash?"** — reasoning from absence in DPT or `recLSN > LSN`.
- **Conceptual / true-false:** WAL rule, force vs. no-force, steal vs. no-steal, what's in a checkpoint, why redo starts at oldest recLSN, why undo writes CLRs, why durability needs force-log-at-commit.
- **"Why do we need recovery?"** open-ended.

**Practice problems:**
- D2018 Problem 9a — Analysis: TT and DPT after analysis.
- D2018 Problem 9b — Undo: rollback list and CLRs.
- D2018_K Problem 9a — checkpoint contents and use.
- D2018_K Problem 9b — when must data pages be written in ARIES.
- D2019 Problem 21 — Analysis: TT and DPT.
- D2019 Problem 22 — Redo: which records get redone given PageLSN.
- D2019_K Problem 14 — why do we need recovery.
- D2019_K Problem 17 — why ARIES Redo starts at oldest recLSN.
- D2020 Problem 16 — Analysis: TT and DPT.
- D2020 Problem 17 — PageLSN of A,B,C after Redo and after Undo.
- D2021 Problem 7 — DPT after analysis.
- D2021 Problem 13 — true/false: WAL, force, no-steal, isolation, optimizer.
- D2021 Problem 14 — at which LSN must the Redo scan start.
- D2022 Problem 3 — true/false on WAL and force/steal.
- D2022 Problem 5 — true/false on DPT/TT/REDO/UNDO/PageLSN claims.
- D2022 Problem 10 — Redo: which records get redone.
- D2023 Problem 17 — Redo: which records get redone.
- D2023 Problem 18 — Undo: log records generated.
- D2023_K Problem 11 — Analysis: TT and DPT.
- D2023_K Problem 12 — possible PageLSN values entering redo.
- D2024 Problem 5 — Analysis: DPT after analysis.
- D2024 Problem 6 — Undo: log records generated.
- D2024 Problem 7 — which pages can we be sure were flushed.
- D2024_K Problem 7 — Redo: per-update justification given PageLSNs.
- D2024_K Problem 8 — why must Redo come before Undo (conceptual).
- D2025 Problem 7 — Analysis: DPT after analysis.
- D2025 Problem 8 — which pages can we be sure were flushed (with steal hint).

---

## Coverage map

| Ch | Title | # problems |
|---:|---|---:|
| 1  | DBMS architecture | 0 |
| 2  | Database storage | 0 |
| 3  | Record format | 0 |
| 4  | Block format | 1 |
| 5  | Database buffer | 0 |
| 6  | Heap files | 1 |
| 7  | Static hashing | 2 |
| 8  | Extendible hashing | 8 |
| 9  | Indexing concepts | 1 |
| 10 | B+-trees | 14 |
| 11 | LSM trees | 0 |
| 12 | Queries / access paths | 25 |
| 13 | JOIN queries | 4 |
| 14 | External merge sort | 1 |
| 15 | Intro transactions | 3 |
| 16 | Transactions theory | 16 |
| 17 | Concurrency control | 17 |
| 18 | Recovery / ARIES | 27 |
|    | **Total (primary)** | **120** |

Pre-curriculum problems (ER / SQL / RA / FD / NF / decomposition / non-storage conceptual / 0-pt placeholder) — see `topic_index.md`.
