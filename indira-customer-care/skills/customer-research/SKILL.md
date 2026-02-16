---
name: customer-research
description: >
  Research customer questions by searching across knowledge base, Shopify, and available sources,
  then synthesize a confidence-scored answer. Use when a customer asks a question you need to
  investigate, when building background on a customer situation, or when you need order context.
---

# Indira Customer Research

Expert la cercetarea multi-sursă pentru a răspunde la întrebările clienților, investiga contextul comenzilor, și construi o înțelegere completă a situației clientei. Prioritizează sursele autoritare, sintetizează informațiile, și comunică clar nivelul de încredere.

## Research Process

### Pas 1: Înțelege Întrebarea

Înainte de a căuta, clarifică ce cauți:
- E o întrebare factuală cu un răspuns definitiv? (ex: „Ce materiale aveți?")
- E o întrebare contextuală? (ex: „Ce s-a întâmplat cu comanda mea?")
- E o întrebare exploratorie? (ex: „Ce bijuterie recomandați pentru un cadou?")
- Cine e audiența răspunsului? (clienta direct, coleg intern)

### Pas 2: Planifică Strategia de Căutare

| Tip Întrebare | Surse Prioritare |
|---------------|-----------------|
| Produs / material | `knowledge/products/`, catalog Shopify |
| Politică (retur, livrare) | `knowledge/policies/` |
| Comandă specifică | ~~platformă suport (Delight Chat), ~~e-commerce (Shopify) |
| Proces intern | `knowledge/processes/` |
| Recomandare | `knowledge/products/collections.md`, site-ul indira.ro |

### Pas 3: Execută Căutarea Sistematic

Caută sursele în ordinea priorității. Nu te opri la primul rezultat — verifică încrucișat.

### Pas 4: Sintetizează și Validează

Combină rezultatele, verifică contradicțiile, evaluează încrederea generală.

### Pas 5: Prezintă cu Atribuire

Citează întotdeauna sursele și menționează nivelul de încredere.

## Source Prioritization

### Tier 1 — Baza de Cunoștințe Internă (Încredere Maximă)
- **Fișiere knowledge/**: Politici, produse, procese, brand voice
- **Catalog Shopify**: Produse, prețuri, disponibilitate, descrieri

Nivel încredere: **Ridicat** (verifică dacă informația e actuală)

### Tier 2 — Context Operațional
- **Delight Chat**: Istoric conversații, tickete anterioare
- **Shopify Admin**: Detalii comandă, status livrare, istoric plăți

Nivel încredere: **Mediu-Ridicat** (poate fi incomplet)

### Tier 3 — Surse Externe
- **Site indira.ro**: Pagini produs, colecții, informații publice
- **Social media Indira**: Anunțuri, promoții, comunicări publice

Nivel încredere: **Mediu** (informația de pe site poate fi mai actualizată decât baza de cunoștințe)

### Tier 4 — Inferență
- **Situații similare**: Cum au fost rezolvate întrebări asemănătoare
- **Bune practici**: Standarde din industria bijuteriilor

Nivel încredere: **Scăzut** (semnalează clar că e inferență, nu fapt)

## Confidence Levels

Asignează și comunică ÎNTOTDEAUNA un nivel de încredere:

**Încredere Ridicată:**
- Răspuns confirmat de baza de cunoștințe sau Shopify
- Informație actuală și verificată
- „Conform bazei noastre de cunoștințe, [răspuns]."

**Încredere Medie:**
- Răspuns găsit într-o singură sursă fără confirmare
- Informația ar putea fi ușor depășită
- „Din informațiile disponibile, [răspuns], dar recomand verificarea cu [sursă]."

**Încredere Scăzută:**
- Răspuns dedus din informații conexe
- Surse contradictorii
- „Nu am găsit un răspuns definitiv. Pe baza [context], estimarea mea e [răspuns], dar trebuie verificat înainte de a comunica clientei."

**Nu Pot Determina:**
- Nicio informație relevantă găsită
- „Nu am găsit informații despre asta. Recomand verificarea cu [persoană/sursă]."

## Handling Contradictions

Când sursele nu corespund:
1. Notează contradicția explicit
2. Identifică sursa mai autoritară sau mai recentă
3. Prezintă ambele perspective
4. Recomandă cum se rezolvă discrepanța
5. Pentru client: folosește răspunsul cel mai conservator până la clarificare

## Synthesis Structure

```
## Cercetare: [Întrebare/Topic]

### Răspuns
[Răspuns direct — începe cu concluzia]

**Încredere:** [Ridicată / Medie / Scăzută]
[Ce determină nivelul de încredere]

### Surse Consultate
- [Sursa 1]: [Ce spune]
- [Sursa 2]: [Ce spune — confirmă sau adaugă nuanță]

### Mențiuni
- [Limitări sau condiții]
- [Ce ar putea schimba răspunsul în contexte specifice]

### Recomandare
- [Dacă e gata de trimis la client]
- [Pași de verificare necesari]
```

## When to Escalate vs. Answer Directly

### Răspunde Direct Când:
- Baza de cunoștințe adresează clar întrebarea
- E o întrebare factuală despre produs, material, mărime
- Politica de retur/livrare e documentată
- Ai răspuns la întrebări similare cu succes

### Escaladează Când:
- Întrebarea implică prețuri speciale sau reduceri nestandardizate
- Întrebare despre garanție pentru cazuri neobișnuite
- Cerere de despăgubire dincolo de politica standard
- Întrebare legală sau GDPR specifică
- Informație contradictorii în surse
- Clienta e un cont de risc (reclamație în derulare)

## Using This Skill

1. Începe ÎNTOTDEAUNA prin a clarifica ce cauți exact
2. Caută sistematic — nu sări peste surse chiar dacă crezi că știi răspunsul
3. Verifică încrucișat între surse
4. Fii transparent cu nivelul de încredere — nu prezenta incertitudinea ca fapt
5. Când ai dubii dacă să trimiți la client, verifică mai întâi
6. Documentează cercetarea pentru beneficiul echipei
7. Dacă cercetarea relevă o lacună în baza de cunoștințe, semnalează-o pentru documentare
