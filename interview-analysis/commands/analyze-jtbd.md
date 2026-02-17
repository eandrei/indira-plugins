---
description: Analizează o transcriere de interviu și generează un raport JTBD comprehensiv
argument-hint: "<calea fișierului de transcript>"
---

# Analiză JTBD — Transcriere Interviu

Analizează o transcriere de interviu prin lentila Jobs-To-Be-Done și generează un raport
structurat cu 10 dimensiuni, scorare a încrederii și citate verbatim din transcript.

## Usage

```
/analyze-jtbd <calea fișierului de transcript>
```

Exemple:
- `/analyze-jtbd transcripts/interviu-maria-2024-03.md`
- `/analyze-jtbd interviu-client-1.txt`
- `/analyze-jtbd uploads/transcript-sesiune-discovery.md`

## Workflow

### 1. Citește și Salvează Transcriptul

Citește fișierul de transcript de la calea specificată.

Dacă fișierul nu se află deja în `transcripts/`, salvează o copie acolo:
- Numele fișierului: păstrează numele original
- Fără modificări de conținut — copie exactă

Notează:
- Numele/ID-ul interviewee-ului (dacă e menționat)
- Data interviului (dacă e menționată)
- Domeniul/subiectul principal
- Lungimea aproximativă și structura (ghidat/neghidat, teme principale)

### 2. Extrage Dovezi Brute

**Înainte de orice interpretare**, parcurge transcriptul și colectează citate directe
pentru fiecare dintre cele 10 dimensiuni JTBD. Nu categoriza încă — doar culege.

Pentru fiecare dimensiune, listează intern citatele candidate cu numărul de linie sau
contextul din transcript. Aceasta previne bias-ul de confirmare și asigură că analiza
e ancorată în text, nu în presupuneri.

Identifică și marchează:
- Declarații de Luptă (Struggle) — frustrare, eșec, dificultate cu soluția actuală
- Declarații de Rezultat (Outcome) — cum arată succesul, situația ideală
- Declarații de Progres (Progress) — schimbări deja făcute, decizii de tranziție
- Declarații de Context (Context) — când, unde, în ce situație apare jobul

Folosește skill-ul **jtbd-analysis** pentru ghidul complet de extracție.

### 3. Analizează Fiecare Dimensiune JTBD

Folosind skill-ul **jtbd-analysis**, parcurge sistematic toate 10 dimensiunile:

1. Jobul Principal — aplică testul „De ce?" de 3-5 ori pe jobul declarat
2. Circumstanțele Jobului — când, unde, de ce, frecvență
3. Rezultate Dorite — funcționale, emoționale, sociale (format metric Ulwick)
4. Puncte de Durere — ce eșuează, workaround-uri, severitate
5. Joburi Emoționale și Sociale — cum vor să se simtă, cum vor să fie percepuți
6. Soluții Concurente — directe, indirecte, workaround-uri, non-consum
7. Declanșatoare de Schimbare — Push, Pull, Anxietate, Inerție (Moesta)
8. Semnale de Segment — caracteristici comportamentale și situaționale
9. Oportunități — gap-uri între rezultate dorite și ce livrează soluțiile actuale
10. Citate Cheie — cele mai puternice exprimări verbatim

### 4. Scorează Încrederea

Pentru **fiecare** insight generat, asignează:
- **Ridicată** — 3+ citate directe, explicit, consistent pe tot transcriptul
- **Medie** — 1-2 citate, parțial implicit, o inferență logică necesară
- **Scăzută** — inferit din context, nicio declarație directă, sau menționat ipotetic

Regula: Când ești în dubiu, scorează mai jos.

### 5. Generează și Salvează Raportul

Scrie raportul complet în fișierul:
```
JTBD/<nume-interviewee-sau-data>.md
```

Dacă numele interviewee-ului nu e disponibil, folosește data interviului sau un ID secvențial
(ex: `JTBD/interviu-001.md`).

Folosește exact template-ul de mai jos:

```markdown
# Raport JTBD — [Nume Interviewee sau ID]
**Intervievat:** [Nume/ID sau „Anonim"]
**Data Interviului:** [Data sau „Necunoscută"]
**Fișier Transcript:** [calea fișierului]
**Data Analizei:** [Data de astăzi]

---

## 1. Jobul Principal

> [Statement în format: „Când [situație], vreau să [motivație], astfel încât să pot [rezultat]."]

**Încredere:** [Ridicată / Medie / Scăzută]
**Citate suport:**
- „[Citat verbatim din transcript]"
- „[Citat verbatim din transcript]"

---

## 2. Circumstanțele Jobului

| Dimensiune | Constatare |
|------------|-----------|
| Când | [Situații/declanșatoare] |
| Unde | [Context/mediu] |
| De ce | [Motivație subiacentă] |
| Frecvență | [Cât de des apare jobul] |

**Încredere:** [Ridicată / Medie / Scăzută]
**Citate suport:**
- „[Citat]"

---

## 3. Rezultate Dorite

### Funcționale
- [Rezultat măsurabil — format: Minimizează/Maximizează + metrică + context]
- [Rezultat măsurabil]

### Emoționale
- [Cum vor să se simtă în timpul sau după job]

### Sociale
- [Cum vor să fie percepuți de alții]

**Încredere:** [Ridicată / Medie / Scăzută]
**Citate suport:**
- „[Citat care arată starea dorită]"

---

## 4. Puncte de Durere și Dificultăți

| Punct de Durere | Severitate | Workaround Actual |
|-----------------|------------|-------------------|
| [Durere 1] | [Ridicată/Medie/Scăzută] | [Ce fac în schimb] |
| [Durere 2] | [Ridicată/Medie/Scăzută] | [Ce fac în schimb] |

**Încredere:** [Ridicată / Medie / Scăzută]
**Citate suport:**
- „[Citat cu frustrare sau workaround]"

---

## 5. Joburi Emoționale și Sociale

**Job Emoțional:** Vreau să mă simt [...]
**Job Social:** Vreau ca ceilalți să mă vadă ca [...]

**Încredere:** [Ridicată / Medie / Scăzută]
**Citate suport:**
- „[Citat care relevă emoție sau identitate]"

---

## 6. Soluții Concurente

| Soluție | Tip | De ce o folosesc | Unde eșuează |
|---------|-----|------------------|--------------|
| [Soluție 1] | [Directă/Indirectă/Workaround/Non-consum] | [Motiv] | [Gap] |
| [Soluție 2] | [Directă/Indirectă/Workaround/Non-consum] | [Motiv] | [Gap] |

**Încredere:** [Ridicată / Medie / Scăzută]

---

## 7. Declanșatoare de Schimbare

### Push (departe de situația actuală)
- [Ce frustrare/eșec ar putea provoca schimbarea]

### Pull (spre soluție nouă)
- [Ce ar atrage spre o alternativă]

### Anxietăți (ce îi ține pe loc)
- [Frici sau costuri de tranziție percepute]

### Inerție (obișnuință)
- [Ce familiaritate sau „merge și așa" îl reține]

**Încredere:** [Ridicată / Medie / Scăzută]
**Citate suport:**
- „[Citat despre decizia de schimbare sau refuzul ei]"

---

## 8. Semnale de Segment

**Ipoteză Segment:** [Nume pentru acest tip de utilizator]
**Caracteristici definitorii:**
- [Pattern comportamental]
- [Caracteristică situațională]
- [Semnal de prioritate sau valoare]

**Încredere:** [Ridicată / Medie / Scăzută]
**Notă:** Aceasta este o ipoteză bazată pe un singur interviu. Necesită validare pe minim 5-8 interviuri cu profil similar.

---

## 9. Oportunități

| Oportunitate | Descriere (gap de rezultat) | Puterea Dovezilor |
|--------------|----------------------------|-------------------|
| [Oportunitate 1] | [Ce nu livrează nicio soluție actuală] | [Ridicată/Medie/Scăzută] |
| [Oportunitate 2] | [Ce nu livrează nicio soluție actuală] | [Ridicată/Medie/Scăzută] |

---

## 10. Citate Cheie

> „[Cel mai puternic citat verbatim — pentru jobul principal sau durerea centrală]"
> — Context: [Ce descria în acel moment]

> „[Al doilea citat puternic]"
> — Context: [Ce descria]

> „[Al treilea citat puternic]"
> — Context: [Ce descria]

---

## Sumar Analiză

**Insight-uri cu cea mai mare încredere:**
- [Constatare 1 — Ridicată]
- [Constatare 2 — Ridicată]

**Zone cu dovezi insuficiente:**
- [Dimensiune cu Scăzută — ce ar trebui investigat în continuare]

**Întrebări de Follow-up Recomandate:**
- [Întrebare pentru o zonă de încredere Scăzută]
- [Întrebare pentru a aprofunda un thread promițător]

**Încredere Generală Analiză:** [Ridicată / Medie / Scăzută]
[1-2 propoziții care explică ce a determinat sau limitat încrederea în această analiză]
```

### 6. Sugerează Pași Următori

După prezentarea confirmării că raportul a fost salvat:
- „Vrei să extrag top 3 oportunități pentru o prezentare executivă?"
- „Să generez un ghid de interviuri de follow-up bazat pe zonele cu încredere Scăzută?"
- „Vrei să compar acest raport cu un interviu anterior?"
