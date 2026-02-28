---
title: "feat: Setup CEO workspace cu mono-repo plugin marketplace"
type: feat
date: 2026-02-28
---

# CEO Workspace Setup

## Overview

Reorganizare `indira-plugins/` ca mono-repo dual: plugin marketplace partajabil + CEO workspace personal. CLAUDE.md la root funcționează ca agent CEO cu routing către plugin-uri specializate.

## Brainstorm

Decizia completă: `docs/brainstorms/2026-02-28-ceo-workspace-brainstorm.md`

## Proposed Solution

5 pași concreți, în ordine:

### Pas 1: Actualizare `.gitignore`

Adaugă fișierele personale care nu trebuie partajate.

**Fișier:** `.gitignore`

```gitignore
# Personal context (nu se partajează)
about-me.md
working-style.md

# OS
.DS_Store

# Working files
workspace/drafts/*
workspace/tickets/*
workspace/research/*
!workspace/drafts/.gitkeep
!workspace/tickets/.gitkeep
!workspace/research/.gitkeep
```

### Pas 2: Creare `CLAUDE.md` la root (Agent CEO)

Acest fișier e core-ul workspace-ului. E citit automat de Claude în orice sesiune deschisă în `indira-plugins/`.

**Fișier:** `CLAUDE.md`

Conținut:

```markdown
# Indira CEO Workspace

## Cine sunt

Citește `about-me.md` pentru context complet.

## Cum lucrez

Citește `working-style.md` pentru preferințe de comunicare și output.

## Brand

Citește `brand-voice.md` pentru tonul și stilul brandului Indira.

## Plugin-uri disponibile

| Plugin | Director | Ce face |
|--------|----------|---------|
| Customer Care | `indira-customer-care/` | Răspunde la mesaje, triază tickete, cercetează, îmbunătățește KB |
| Interview Analysis | `interview-analysis/` | Analizează transcrieri JTBD |

## Routing

Când primesc un task:
1. Dacă e mesaj de la clientă → deschide `indira-customer-care/` și folosește comenzile de acolo
2. Dacă e transcriere de interviu → deschide `interview-analysis/` și folosește `/analyze-jtbd`
3. Altfel → lucrează direct din workspace/

## Conectori

- **Shopify** (Prism MCP): lookup clienți/comenzi pe `indira-bijuterii.myshopify.com`
- **Shopify** (Shop MCP): căutare produse, coș
- **Google Analytics**: trafic și conversii
- **Chrome**: browsing, tracking parcele

## Convenții

- Limba cu mine: română
- Fișiere tehnice: engleză
- Documente business: română cu diacritice
- Fii concis, nu repeta ce am zis
- Întreabă înainte de a presupune
- Salvează fișierele gata de folosit, nu le descrie doar
```

### Pas 3: Rezolvare duplicat `brand-voice.md`

**Problema:** `brand-voice.md` există la root ȘI în `indira-customer-care/knowledge/brand-voice.md`. Trebuie o singură sursă de adevăr.

**Soluție:** Păstrează `brand-voice.md` la root (e business context, nu personal). În `indira-customer-care/CLAUDE.md` actualizează referința:

```
Detalii complete în `../brand-voice.md` — citește-l ÎNTOTDEAUNA înainte de a redacta un răspuns.
```

Apoi șterge `indira-customer-care/knowledge/brand-voice.md` duplicatul, și în loc pune o referință:

```markdown
# Brand Voice

Vezi `../../brand-voice.md` — sursa principală de adevăr pentru vocea brandului.
```

### Pas 4: Curățare `workspace/`

`workspace/` la root devine CEO working area. Deja are structura potrivită:

```
workspace/
├── drafts/          ← draft-uri în lucru
├── research/        ← cercetări salvate
├── tickets/         ← note per ticket
└── knowledge/       ← duplicat cu indira-customer-care/knowledge
```

**Acțiune:** `workspace/knowledge/` e un duplicat al `indira-customer-care/knowledge/`. Șterge-l — nu are sens să existe în două locuri. Knowledge-ul aparține plugin-ului customer-care.

### Pas 5: Actualizare `README.md`

Actualizează README-ul pentru a reflecta noua structură dual (marketplace + workspace):

```markdown
# Indira Plugins

Plugin-uri și workspace pentru [indira.ro](https://www.indira.ro).

## Setup

### Cu Claude Cowork
1. **Work in a folder** → selectează `indira-plugins/` (CEO workspace)
2. Sau selectează un plugin specific (ex: `indira-customer-care/`)

### Plugin-uri disponibile
| Plugin | Descriere |
|--------|-----------|
| indira-customer-care | Customer care agent — răspunsuri, triaj, cercetare |
| interview-analysis | Analiza interviuri JTBD |

## Structura

[structura actualizată]
```

## Acceptance Criteria

- [x] `.gitignore` exclude `about-me.md` și `working-style.md`
- [x] `CLAUDE.md` la root conține routing, context personal (prin referință), și lista de plugin-uri
- [x] `brand-voice.md` la root (general) + customer-care își păstrează propria versiune completă
- [x] `workspace/knowledge/` duplicat e eliminat
- [x] README reflectă noua structură
- [ ] Plugin-urile existente continuă să funcționeze independent (testat cu Cowork pe `indira-customer-care/`)

## Ce NU facem acum

- Nu creăm plugin-uri noi (marketing, operations, strategy) — se fac la nevoie
- Nu configurăm Google Workspace MCP — se face separat când e nevoie
- Nu adăugăm comenzi CEO (/daily-briefing etc.) — se fac după ce workspace-ul e stabil
