# Topic — Multiple-choice SQL questions

**About:** Topical (not curriculum-chapter) sheet. Multiple-choice questions whose subject is SQL semantics itself: equivalence between `SELECT` formulations, `JOIN` flavours (equi / natural / cross), `NOT IN` vs `NOT EXISTS`, NULL handling, what a query returns, how to express a stated requirement. Questions where SQL is only the wrapper for a block-cost / I/O / access-path problem are filed in [`12_queries_access_paths.md`](12_queries_access_paths.md), not here.

**Exercise types seen on exams:**
- Given a baseline `SELECT` and 2–3 alternative formulations (one of which may be a relational-algebra tree), pick which alternatives *always* produce the same result. Watch for: `cross join` vs equijoin, `natural join` matching the wrong attribute, equivalent RA trees.
- Given a natural-language requirement ("BIDs used in 2023 but not in 2024"), pick which `SELECT` formulations are correct. Test cases: same row-set in both years, rows with NULL FKs, `BRYear = 2023 AND BRYear <> 2024` (impossible filter), correlated `NOT EXISTS` without binding the outer row.
- Multi-select form ("Velg ett eller flere alternativer") — more than one option can be correct, and "None of the other alternatives" is itself a possible correct answer.

**Scope note:** Only two of the 12 final-exam papers (D2023 and D2024) contain genuine MCQ-format SQL-semantics problems. D2018–D2020 had no MCQ format at all (free-form era). D2021–D2025 use MCQ heavily, but most SQL-bearing problems on those papers are access-path / block-cost questions whose answer options are integers, not SQL — those live in chapter 12. Free-form "write the query" SQL problems live elsewhere (most exams have one).

**Total exercises:** 2 — sourced from D2023, D2024.

**Cross-references:**
- Free-form SQL-writing problems: see exam_categories.md cat. 4 ("SQL `SELECT` queries", 13 problems) and cat. 5 ("SQL DML / DDL", 4 problems).
- SQL-as-window-dressing for block-cost MCQs: [`12_queries_access_paths.md`](12_queries_access_paths.md).

---

## D2023 Problem 4: SQL and Relational algebra (5 %)

Vi har tabellene:

```sql
Photo(ID, Title, PhotographerID)
-- PhotographerID is a foreign key against the Photographer table. Can have NULL value
Photographer(ID, Name)
```

Gitt spørringen:

```sql
select Photographer.ID, count(Photo.ID)
from Photo join Photographer on (Photo.PhotographerID = Photographer.ID)
group by Photographer.ID
```

Vi har tre andre spørringer:

**A:**

```sql
select Photographer.ID, count(Photo.ID)
from Photo cross join Photographer
group by Photographer.ID
```

**B:**

```sql
select Photographer.ID, count(Photo.ID)
from Photo natural join Photographer
group by Photographer.ID
```

**C:** (relasjonsalgebra-tre)

```
        π Photographer.ID, count(Photo.ID)
                    │
                    │   (aggregate F: group by Photographer.ID, count(Photo.ID))
                    │
            ⋈  Photographer.ID = PhotographerID
           ╱ ╲
   Photographer  Photo
```

Hvilke av disse spørringene vil alltid gi samme resultat som den oppgitte spørringen?

**Velg ett eller flere alternativer:**

- [ ] C
- [ ] B
- [ ] A
- [ ] Ingen av de andre alternativene

**Maks poeng:** 5

**Watch for:** `natural join` joins on attributes with the *same name* — here that's `ID`, not `PhotographerID`, so B is wrong. `cross join` produces the cartesian product (no predicate), so A is wrong. C is the same equijoin redrawn as RA, so it always matches.

---

## D2024 Problem 11: SQL (5%)

Bruk denne databasen med informasjon om sykler (eng: bike), syklister (eng: cyclist) og sykkelturer (eng: bike ride):

```text
Bike(BID, Name, Brand, ProdYear)

Cyclist(CID, Name, BirthYear)

BikeRide(BRID, BID, CID, BRDay, BRMonth, BRYear, StartTime, Duration, Length)
```

- BID is a foreign key referencing the Bike table. BID cannot have the NULL value
- CID is a foreign key referencing the Cyclist table. CID cannot have the NULL value

Vi ønsker å finne BID for sykler som er brukt til minst en sykkeltur i 2023, men som ikke er brukt til noen sykkeltur i 2024.

Hvilke av disse SQL-spørringene vil gi det ønskede resultatet?

### Alternativer

**A**

```sql
select distinct BID
from BikeRide AS BR
where BRYear = 2023
  and not exists (select * from BikeRide
                  where BRYear = 2024)
```

**B**

```sql
select distinct BID
from Bike
where BID in (select BID from BikeRide
              where BRYear = 2023)
  and BID not in (select BID from BikeRide
                  where BRYear = 2024)
```

**C**

```sql
select distinct BID
from BikeRide
where BRYear = 2023
  and BRYear <> 2024
```

**D**

```sql
select distinct BID
from Bike natural join BikeRide
where BRYear = 2023
  and BID not in (select BID from BikeRide
                  where BRYear = 2024)
```

**Velg ett eller flere alternativer**

- [ ] C
- [ ] B
- [ ] D
- [ ] None of the other alternatives
- [ ] A

**Maks poeng:** 5

**Watch for:** A's `NOT EXISTS` subquery is uncorrelated — it kills *all* output as soon as any 2024 ride exists anywhere. C is logically broken: a single row cannot have `BRYear = 2023 AND BRYear <> 2024` simultaneously satisfy "the bike was ridden in 2023 and not in 2024" — that needs two passes, not one row. B and D both express the requirement correctly via `NOT IN` against a subquery of 2024 rides.
