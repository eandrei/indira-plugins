---
description: Cercetare multi-sursă pe o întrebare de la client sau un topic
argument-hint: "<întrebarea sau topicul>"
---

# Research — Indira

> Dacă vezi placeholder-e necunoscute, verifică [CONNECTORS.md](../CONNECTORS.md).

Cercetare multi-sursă pe o întrebare de la client, un topic legat de produse, sau o investigare de comandă. Sintetizează rezultatele din toate sursele disponibile cu atribuire clară.

## Usage

```
/research <întrebarea sau topicul>
```

Exemple:
- `/research Ce pietre naturale avem disponibile pentru inele?`
- `/research Politica de retur pentru bijuterii personalizate`
- `/research Clienta întreabă dacă argintul placat cu aur se poate replaca`
- `/research Care e diferența între rodiu și placarea cu aur?`

## Workflow

### 1. Identifică Tipul de Cercetare

- **Întrebare client**: Ceva ce clienta a întrebat și trebuie un răspuns (ex: „Pot purta inelul la piscină?")
- **Investigare problemă**: Background pe o problemă raportată (ex: „A mai fost raportată oxidare la colecția Essentials?")
- **Context comandă**: Istoric cu un client specific (ex: „Ce am discutat cu Maria ultima dată?")
- **Cercetare topic**: Topic general relevant (ex: „Cum se îngrijesc opale?")

### 2. Caută în Surse

Caută în ordinea priorității, adaptând la ce e disponibil:

**Tier 1 — Baza de Cunoștințe (încredere maximă):**
- `knowledge/` — politici, produse, procese, brand voice
- Catalog Shopify — produse, prețuri, disponibilitate

**Tier 2 — Context Operațional:**
- ~~platformă suport — tickete anterioare, răspunsuri la întrebări similare
- ~~e-commerce — detalii comenzi, istoric

**Tier 3 — Surse Externe:**
- Site indira.ro — pagini produs, informații publice
- Căutare web — documentație pietre, materiale, best practices

### 3. Sintetizează Rezultatele

```
## Cercetare: [Întrebare/Topic]

### Răspuns
[Răspuns direct — începe cu concluzia]

**Încredere:** [Ridicată / Medie / Scăzută]
[Ce determină nivelul de încredere]

### Surse Consultate
- [Sursa 1]: [Ce spune]
- [Sursa 2]: [Ce spune]

### Context și Nuanțe
[Mențiuni, cazuri speciale, condiții]

### Lacune
- [Ce nu s-a putut confirma]
- [Ce necesită verificare]

### Recomandare
- [Dacă e gata de trimis la client]
- [Pași de verificare necesari]
- [Cine trebuie consultat]
```

### 4. Surse Insuficiente

Dacă nu găsești răspunsul:
- Fă căutare web pe topic
- Întreabă utilizatorul pentru context intern
- Fii transparent cu limitările
- Sugerează cine ar putea ști răspunsul

### 5. Knowledge Capture

După cercetare, sugerează capturarea cunoștințelor:
- „Să salvez aceste informații în baza de cunoștințe?"
- „Să creez un FAQ din această cercetare?"
- „Asta ar merita documentat — vrei să folosesc /kb-article?"
