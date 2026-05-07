# Normalization theory

**About:** Cross-cutting topic — *not* a single curriculum chapter. Bundles all material on
normal forms (1NF/2NF/3NF/BCNF/4NF), functional dependencies (FDs), multivalued dependencies
(MVDs), keys / superkeys / candidate keys, attribute closure `X+`, and decomposition with
lossless-join and FD-preservation guarantees.

**Exercise types seen on exams:**
- FD reasoning over a populated tabellforekomst — infer missing values consistent with F (e.g. `A→B`, `CD→B`).
- Construct a tabellforekomst for `R(A,B,C,D)` that violates a stated FD set.
- Armstrong derivation — prove a new FD (e.g. `WY→Z, X→Y ⊢ WX→Z`).
- MVD reasoning — given two MVDs, list which tuples must exist in any legal instance.
- Find all candidate keys / superkeys of R given F; bound the maximum number of legal tuples.
- Define attribute closure `X+` and give an algorithm.
- State the highest NF (1NF / 2NF / 3NF / BCNF / 4NF) satisfied and justify.
- Decompose a non-BCNF schema into BCNF (or 3NF) and prove attribute-preservation, FD-preservation, and lossless-join.
- Test whether a given decomposition is lossless and/or FD-preserving (chase or inspection).
- Conceptual: define 3NF, list three drawbacks of non-BCNF schemas, when *not* to normalize fully, why every relation has at least one key, distinguish key vs. superkey.

**Total exercises:** 30 — sourced from D2018, D2018_K, D2019, D2019_K, D2020, D2023, D2024, D2024_K, D2025.

---

## D2018 Problem 3a (4 %)

I friidrettsøvelsen lengdehopp får hver utøver et antall forsøk (attempt) på å hoppe lengst mulig. Hver utøver er identifisert ved et unikt startnummer. For hvert forsøk blir det registrert hvor mye medvind (wind) hopperen hadde og hvor langt det ble hoppet. Under er vist et eksempel på en tabellforekomst for en lengdehopp-konkurranse.

| StartNumber | Attempt | Length | Wind |
| --- | --- | --- | --- |
| 1 | 1 | 3,10 | 1,5 |
| 2 | 1 | 3,10 | 2,0 |
| 1 | 2 | 3,20 | 2,5 |
| 2 | 2 | 3,30 | 2,5 |

Ut fra denne tabellforekomsten er det mulig at Wind -> Attempt kan være en restriksjon for tabellen. Forklar hvorfor det er mulig. Er det rimelig å anta at denne funksjonelle avhengigheten gjelder i den aktuelle miniverdenen? Formuler med ord hvilken restriksjon som i så fall ville gjelde.

**Maks poeng:** 4

---

## D2018 Problem 3b (4 %)

Gitt R(A, B, C, D). Lag en tabellforekomst for R som bryter med både

```text
CD -> A
```

og

```text
B -> D
```

Du må begrunne svaret ditt.

**Maks poeng:** 4

---

## D2018 Problem 3c (4 %)

Gitt WY -> Z og X -> Y. Vis at også WX -> Z må gjelde. Du må begrunne svaret ditt.

**Maks poeng:** 4

---

## D2018 Problem 3d (4 %)

Gitt R(A, B, C, D) der BC som markert er nøkkel for tabellen. Vil R alltid kunne dekomponeres tapsløst (lossless) i tabellene R1(AB), R2(BC) og R3(CD)? Du må begrunne svaret ditt.

**Maks poeng:** 4

---

## D2018_K Problem 4a: Normalisering (5 %)

Anta `R = {A, B, C, D}` og `F = {A -> B; BC -> D; D -> A}`. Under er vist en tabellforekomst for R. Gitt at tabellforekomsten skal være gyldig, hvilke verdier kan X, Y og Z ha?

| A | B | C | D |
| - | - | - | - |
| X | 2 | 4 | 6 |
| 2 | 2 | 2 | 4 |
| 1 | 1 | 1 | 2 |
| 1 | Y | 3 | 5 |
| 3 | 2 | 5 | Z |

**Skriv ditt svar her**

**Maks poeng:** 5

---

## D2018_K Problem 4b: Normalisering (5 %)

Definer begrepet kandidatnøkkel. Finn alle kandidatnøkler for tabellen `R = {A, B, C, D}` når `F = {A -> B; BC -> D; D -> A}` gjelder.

**Skriv ditt svar her**

**Maks poeng:** 5

---

## D2018_K Problem 4c: Normalisering (5 %)

Gitt `R = {A, B, C, D}` og `F = {A -> B; BC -> D; D -> A}`. Forutsett at R er på første normalform. Hva er den høyeste normalformen som er oppfylt av R? Svaret må begrunnes.

**Skriv ditt svar her**

**Maks poeng:** 5

---

## D2018_K Problem 4d: Normalisering (5 %)

Forklar hva som menes med tillukningen (`X+`) til en mengde attributter (`X`). Lag en algoritme for å finne `X+`.

**Skriv ditt svar her**

**Maks poeng:** 5

---

## D2019 Problem 7: Nøkler (2 %)

Tabeller (relasjoner) vil alltid ha minst en nøkkel. Forklar hvorfor det er slik.

**Maks poeng:** 2

---

## D2019 Problem 8: Nøkkel og supernøkkel (2 %)

Forklar hva som skiller begrepene nøkkel og supernøkkel.

**Maks poeng:** 2

---

## D2019 Problem 9: Funksjonelle avhengigheter (5 %)

Anta at en tabell dekomponeres i to deltabeller. Forklar hva det vil si at en slik dekomponering ikke har bevaring av funksjonelle avhengigheter. Lag et eksempel på en slik dekomponering og diskuter konsekvensene av at dekomponeringen ikke har bevaring av funksjonelle avhengigheter.

**Maks poeng:** 5

---

## D2019 Problem 10: Normalisering (5 %)

Anta at alle restriksjoner kan uttrykkes ved funksjonelle avhengigheter. Ta utgangspunkt i en tabell som er på første normalform (1NF), men ikke på andre normalform (2NF).

Gjør rede for ulemper som kan følge av at tabellen ikke er på Boyce-Codd normalform (BCNF). Årsakene til disse ulempene kan deles i tre klasser, beskriv disse tre klassene.

**Maks poeng:** 5

---

## D2019_K Problem 8 (4 %)

Gitt R(A, B, C, D) og F = { A -> B; C -> D }. Finn alle supernøkler i R.

Skriv ditt svar her...

**Maks poeng:** 4

---

## D2019_K Problem 9 (4 %)

Gi en definisjon av tredje normalform (3NF).

Skriv ditt svar her...

**Maks poeng:** 4

---

## D2019_K Problem 10 (4 %)

Anta at en tabell dekomponeres i to deltabeller. Forklar hva det vil si at en slik dekomponering ikke har tapsløst-join-egenskapen. Lag et eksempel på en slik dekomponering og diskuter konsekvensene av at dekomponeringen ikke har tapsløst-join-egenskapen.

Skriv ditt svar her...

**Maks poeng:** 4

---

## D2019_K Problem 11 (4 %)

I noen situasjoner kan det være hensiktsmessig ikke å normalisere så langt som teoretisk mulig. Hva kan være grunner til ikke å normalisere så langt som mulig? Gi et eksempel på en situasjon og en tabell der du mener det kan være riktig ikke å bringe tabellen opp på en høyere normalform.

Skriv ditt svar her...

**Maks poeng:** 4

---

## D2020 Problem 7 (6 %)

Oppgaven består av tre deloppgaver som teller like mye.

**Oppgave a:**  
Lag et originalt eksempel på en tabell som er på andre normalform (2NF), men ikke på tredje normalform (3NF). Forklar hvorfor det er slik.

I denne oppgaven skal du ikke kopiere et eksempel fra en annen kilde, det vil gi null uttelling.

**Oppgave b:**  
Grei ut om problemene som kan oppstå på grunn av at tabellen du foreslår i deloppgave a ikke er på tredje normalform.

**Oppgave c:**  
Vis hvordan tabellen du foreslår i deloppgave a kan splittes opp slik at vi oppnår tredje normalform. Forklar hvorfor forslaget ditt er en god løsning.

**Maks poeng:** 6

---

## D2020 Problem 8 (3 %)

Ta utgangspunkt i en tabell R(A, B, C, D, E). Attributtene (A-E) er alle definert over en datatype med heltallene fra og med 1 til og med 10.

Hva er det maksimale antall rader som kan finnes i en tabellforekomst av R? Hvilken primærnøkkel vil R ha i dette tilfellet? Du må begrunne svarene.

**Maks poeng:** 3

---

## D2020 Problem 9 (2 %)

Ta utgangspunkt i en tabell R(A, B, C, D, E). Attributtene (A-E) er alle definert over en datatype med heltallene fra og med 1 til og med 10.

Anta at den funksjonelle avhengigheten C->BD gjelder for R. Hva er primærnøkkelen i dette tilfellet? Hvor mange rader kan det maksimalt være i en tabellforekomst av R? Du må begrunne svarene.

**Maks poeng:** 2

---

## D2020 Problem 10 (4 %)

Ta utgangspunkt i tabellen Bil(modell, drivstoff, fremdrift). Et eksempel på en tabellforekomst er vist under.

| Model | Fuel   | Drive |
| ----- | ------ | ----- |
| RAV4  | Petrol | 2WD   |
| RAV4  | Petrol | 4WD   |
| RAV4  | Diesel | 2WD   |
| RAV4  | Diesel | 4WD   |

Tabellen er på Boyce-Codd normalform siden det ikke er noen ikke-trivielle funksjonelle avhengigheter som gjelder for tabellen. Hvilke forutsetninger om miniverdenen må vi gjøre for at tabellen Bil skal være på fjerde normalform (4NF)? Du må begrunne svaret.

**Maks poeng:** 4

---

## D2023 Problem 1: Normalization (3 %)

Gitt R(A,B,C,D,E) og F = {BC → A; D → C}.

Velg de alternativene som er kandidatnøkler (candidate keys) i R.

**Velg ett eller flere alternativer:**

- [ ] BDE
- [ ] BCE
- [ ] BE
- [ ] BC
- [ ] Ingen av de andre alternativene
- [ ] DE
- [ ] BD

**Maks poeng:** 3

---

## D2023 Problem 2: Normalization (3 %)

Gitt R(A,B,C,D,E,F) og G = {C → ABD; D → CEF}.

Anta at R er på 1. normalform (1NF). Velg alle normalformer som R oppfyller.

**Velg ett eller flere alternativer:**

- [ ] Tredje normalform (3NF)
- [ ] Boyce-Codd normalform (BCNF)
- [ ] Andre normalform (2NF)
- [ ] Fjerde normalform (4NF)
- [ ] Ingen av de andre alternativene (1NF er høyeste)

**Maks poeng:** 3

---

## D2023 Problem 3: Normalization (3 %)

Gitt R(A,B,C,D,E,F) som dekomponeres i R1(A,B,C) og R2(D,E,F). De avhengighetene som gjelder er G = {C → AB; D → EF}.

Har denne dekomponeringen tapsløst-join-egenskapen (lossless join)?

**Velg ett eller flere alternativer:**

- [ ] Nei, join av R1 og R2 kan generere tupler som ikke er i R
- [ ] Ja, fordi C er primærnøkkel i R1 og D er primærnøkkel i R2
- [ ] Ja, fordi C ->> AB vil gjelde i R1 og D ->> EF vil gjelde i R2
- [ ] Ja, fordi alle rader i R1 vil kombineres med alle rader i R2

**Maks poeng:** 3

---

## D2024 Problem 12: Functional Dependencies (3 %)

Vi har A->B og CD->B, og følgende gyldige tabellforekomst:

| A | B | C | D |
| - | - | - | - |
| 1 | 1 | 1 | 1 |
| 3 | X | 1 | 1 |
| 2 | 3 | 1 | Y |
| 2 | 3 | 2 | 2 |

Hvilke påstander er riktige?

**Velg ett eller flere alternativer**

- [ ] X <> 1
- [ ] Y <> 1
- [ ] Y = 1
- [ ] X = 1

**Maks poeng:** 3

---

## D2024 Problem 13: Normal Forms (4 %)

Vi har R(A, B, C, D, E) og F = { BC->A; C->D; D->C; CD->E }. R oppfyller første normalform (1NF).

Hvilken normalform er den høyeste normalformen som oppfylles av R?

**Velg ett alternativ:**

- [ ] 2NF
- [ ] 3NF
- [ ] BCNF
- [ ] 1NF

**Maks poeng:** 4

---

## D2024 Problem 14: Normalization (4 %)

Vi har R(A, B, C, D, E) og F = { A->B; DE->C }. R oppfyller første normalform (1NF).

R dekomponeres i R1(A, B) og R2(C, D, E). Hvilke påstander stemmer om denne dekomponeringen?

**Velg ett eller flere alternativer**

- [ ] The decomposation has the attribute preservation property
- [ ] The decompocition preserves functional dependencies
- [ ] R1 and R2 satiesfies Boyce-Codd normal form (BCNF)
- [ ] The decomposition has the lossless join property
- [ ] None of the other alternatives are correct

**Maks poeng:** 4

---

## D2024_K Problem 11: Normalization (10 %)

Bruk tabellen:

```text
friidrettResultat(UtøverID, Arena, Dato, Øvelse, Resultat, Navn, Alder, Sted)
```

Vi vet at:

- UtøverID, Arena, Dato og Øvelse (sammen) er primærnøkkel for tabellen.
- Tabellen oppfyller første normalform (1NF)
- Den funksjonelle avhengigheten (UtøverID -> Navn, Alder) gjelder
- Den funksjonelle avhengigheten (Arena -> Sted) gjelder

Tabellen skal dekomponeres i deltabeller slik at alle deltabellene oppfyller Boyce-Codd-normalform (BCNF) og dekomponeringen har attributt-bevaring, bevaring av funksjonelle avhengigheter og tapsløst-join-egenskapen. Du <u>må</u> forklare hvorfor løsningen din er riktig.

**Skriv ditt svar her**

**Maks poeng:** 10

---

## D2024_K Problem 12: MVD (5 %)

Bruk tabellen:

```text
passersammen(Kamera, Objektiv, Blits)
```

der vi har MVD-ene Kamera ->> Objektiv og Kamera ->> Blits.

Vi vet at kameraet xt-1 kan bruke objektivet 23 mm og objektivet 50 mm, og blitsen ef-42.
Kameraet xt-5 kan bruke objektivet 23 mm og objektivet 35 mm, og blitsene ef-42 og ef-60.

Hvilke av følgende rader (tuppler) må finnes i alle forekomster av passersammen-tabellen?

**Velg ett eller flere alternativer**

- [ ] (xt-1, 23 mm, ef-60)
- [ ] (xt-1, 50 mm, ef-42)
- [ ] Ingen av de andre alternativene
- [ ] (xt-1, 50 mm, ef-60)
- [ ] (xt-1, 23 mm, ef-42)
- [ ] (xt-5, 35 mm, ef-42)
- [ ] (xt-5, 50 mm, ef-60)
- [ ] (xt-5, 23 mm, ef-60)
- [ ] (xt-5, 50 mm, ef-42)
- [ ] (xt-5, 23 mm, ef-42)
- [ ] (xt-5, 35 mm, ef-60)
- [ ] (xt-1, 35 mm, ef-42)
- [ ] (xt-1, 35 mm, ef-60)

**Maks poeng:** 5

---

## D2025 Problem 11: Normalization (4 %)

Vi har tabellen

```text
Geography(CountryCode, CountryName, Population, Continent)
```

der

```text
F = { CountryCode -> CountryName; CountryName -> CountryCode, Population, Continent }
```

Anta at tabellen er på første normalform (1NF). Finn den høyeste av disse normalformene som oppfylles av tabellen.

**Velg ett alternativ:**

- [ ] 3NF
- [ ] BCNF
- [ ] 1NF
- [ ] 2NF

**Maks poeng:** 4

---

## D2025 Problem 12: Normalization (8 %)

Vi har tabellen

```text
Exam(StudentNo, StudentName, CourseNo, CourseName, ExamNo, ExamDay, ExamMonth, ExamYear, Grade)
```

der

```text
F = {
  StudentNo -> StudentName;
  CourseNo -> CourseName;
  ExamNo -> CourseNo;
  ExamNo -> ExamDay, ExamMonth, ExamYear;
  StudentNo, ExamNo -> Grade
}
```

Anta at tabellen er på første normalform (1NF). Du skal splitte opp tabellen (eng: decompose) slik at alle deltabellene er på Boyce-Codd normalform (BCNF), og vi har attributtbevaring, bevaring av funksjonelle avhengigheter og tapsløst-join egenskapen. Du må begrunne at løsningen din har disse egenskapene. Forklaringen vektlegges like mye som forslaget på deltabeller.

Svaret kan skrives på papir, enten helt eller delvis.

**Skriv ditt svar her**

**Maks poeng:** 8
