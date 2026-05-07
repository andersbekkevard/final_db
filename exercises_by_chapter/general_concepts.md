# General concepts (multiple choice)

**About:** Cross-cutting topic — *not* a single curriculum chapter. Bundles every multiple-choice question that tests **conceptual / definitional / true-false** claims rather than a chapter-specific algorithm. These are the "what does ACID stand for"-flavoured items: claims that span WAL ↔ steal/force ↔ isolation levels ↔ 2PL flavours ↔ snapshot isolation ↔ catalog ↔ optimizer, where the answer comes from the *meaning* of the concept, not from running an algorithm on a given log/schedule/tree.

**Scope filter (what is *not* here):**
- SQL writing/recognising → see SQL category in `topic_index.md`.
- Relational algebra → see RA category in `topic_index.md`.
- ER / EER diagrams → see ER category in `topic_index.md`.
- FD / Normal forms / Decomposition → see `normalization_theory.md`.
- Algorithmic MC tied to one Part-2 chapter (B+-tree construction/sizing, hash insertion, query block-cost, join cost, sort cost, recoverability classification, conflict-serializability test, 2PL commit-order computation, SI execution computation, ARIES Analysis/Redo/Undo computation on a given log) → see the per-chapter files (`04_…`, `06_…`, …, `18_recovery_aries.md`).

**Exercise types seen on exams:**
- Multi-claim true/false on **WAL, steal vs. no-steal, force vs. no-force** (which combination ARIES uses, what WAL guarantees, whether force/no-steal removes the need for logging).
- Multi-claim true/false on **isolation levels and anomalies** (READ COMMITTED, SERIALIZABLE, phantoms).
- Multi-claim true/false on **snapshot isolation** (concurrent reads, concurrent writes to same item, read-locking under SI, more concurrency than SERIALIZABLE, lost-update / write-skew).
- Multi-claim true/false on **2PL ↔ serializability ↔ conflict-serializability** implications (does 2PL imply serializability, does conflict-serializability imply serializability, is 2PL required for serializability).
- Pick which **2PL flavour** (basic / conservative / strict / rigorous) cannot deadlock — definitional, not a schedule trace.
- Multi-claim true/false on **DPT / Transaction Table / REDO / UNDO / PageLSN semantics** (where does REDO start, where does UNDO end, what does the TT say after Analysis, when is PageLSN updated).
- Cross-cutting "miscellaneous" T/F bundles mixing logging + isolation + catalog + optimizer in one question.

**Total exercises:** 6 — sourced from D2021, D2022, D2023_K. Older papers (D2018–D2020) had no MC questions; D2023, D2024, D2024_K, D2025 had no MC items in this category (their conceptual MC items either fit a single chapter cleanly or are computation-on-a-given-state, see the per-chapter files).

---

## D2021 Problem 3: Miscellaneous (3 %)

Kva for ein påstand er riktig?

**Vel eitt alternativ:**

- [ ] Ei historie kan umogeleg havne i vranglås med "basic" tofaselåsing.
- [ ] Ei historie kan umogeleg havne i vranglås med "konservativ" tofaselåsing.
- [ ] Ei historie kan umogeleg havne i vranglås med "strict" tofaselåsing.
- [ ] Ei historie kan umogeleg havne i vranglås med "rigorous" tofaselåsing.

**Maks poeng:** 3

---

## D2021 Problem 13: Miscellaneous (6 %)

Kva for utsegn er sanne?

**Vel eitt eller fleire alternativ:**

- [ ] Write-Ahead Logging sørger for at data må skrivast før loggen skrivast.
- [ ] Force / No-Steal gjør at ein ikkje treng logging
- [ ] READ COMMITTED gjør at alle samtstundesproblem blir borte.
- [ ] SERIALIZABLE gjør at transaksjonar ikkje merker noe til såkalte "fantomar".
- [ ] SQL dictionary / Catalog brukast for å sjekke reserverte ord i SQL queries.
- [ ] Optimalisatoren velgjer mellom forskjellige utføringsplanar for eit query basert på ein kostnadsmodell.

**Maks poeng:** 6

---

## D2022 Problem 3: Misc (6 %)

Hva er riktig for ARIES?

**Velg ett eller flere alternativer**

- [ ] write-ahead logging
- [ ] force, no-steal
- [ ] force, steal
- [ ] no-force, no-steal
- [ ] no-force, steal
- [ ] no logging

I denne oppgaven får du poeng for hvert riktige svar og trekk for hvert feil svar. Minimum 0 poeng på hele oppgaven.

**Maks poeng:** 6

---

## D2022 Problem 4: Misc (6 %)

Hvilke alternativ er sanne?

**Velg ett eller flere alternativer**

- [ ] Snapshot isloation lar transakjoner lese dataelement som samtidig oppdateres av andre transaksjoner
- [ ] 2PL impliserer serialiserbarhet
- [ ] Snapshot isolation lar to forskjellige transaksjoner skrive til samme dataalement samtidig
- [ ] Hvis du har konfliktserialiserbarhet, har du alltid serialiserbarhet.
- [ ] Hvis du har serialiserbarhet, har du alltid konfliktserialserbarhet
- [ ] Serialiserbarhet krever at vi har 2PL

I denne oppgaven får du poeng for hvert riktige svar og trekk for hvert feil svar. Minimum 0 poeng på hele oppgaven.

**Maks poeng:** 6

---

## D2022 Problem 5: Misc (6 %)

Hvilke alternativ er sanne?

**Velg ett eller flere alternativer**

- [ ] DPT forteller hvor UNDO kan starte
- [ ] REDO starter ved eldste "levende" loggpost, dvs. eldste loggpost blant tapere.
- [ ] Transaksjonstabellen forteller hvem som er vinnere og tapere av transaksjonene etter analysen
- [ ] DPT forteller hvor REDO kan starte
- [ ] UNDO slutter ved eldste "levende" loggpost, dvs. eldste loggpost blant tapere.
- [ ] PageLSN blir alltid oppdatert for alle loggposter ved REDO

I denne oppgaven får du poeng for hvert riktige svar og trekk for hvert feil svar. Minimum 0 poeng på hele oppgaven.

**Maks poeng:** 6

---

## D2023_K Problem 6: SNAPSHOT ISOLATION (6 %)

Hvilke påstander er riktige?

**Velg ett eller flere alternativer**

- [ ] SNAPSHOT ISOLATION tillater at to skrivetransaksjoner skriver samme dataelement samtidig
- [ ] SNAPSHOT ISOLATION fører til at lesetransaksjoner ofte må abortere
- [ ] SNAPSHOT ISOLATION tillater mer samtidighet mellom transaksjoner enn SERIALIZABLE
- [ ] SNAPSHOT ISOLATION tillater at to transaksjoner leser samme dataelement
- [ ] Ingen av de andre alternativene er riktige
- [ ] SNAPSHOT ISOLATION er den metoden som gir mest isolasjon mellom transaksjoner
- [ ] SNAPSHOT ISOLATION lar transaksjoner lese data som er låst av skrivetransaksjoner

**Maks poeng:** 6
