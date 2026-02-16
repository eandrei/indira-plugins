# Indira Customer Care Plugin

Plugin Claude Cowork pentru echipa de customer care a [indira.ro](https://www.indira.ro) — magazin online de bijuterii demi-fine din argint și aur.

## Comenzi

| Comandă | Descriere |
|---------|-----------|
| `/draft-response` | Scrie un răspuns profesional pentru un mesaj de la client |
| `/triage` | Triază și prioritizează un ticket de suport |
| `/research` | Cercetare multi-sursă pe o întrebare sau un topic |
| `/escalate` | Creează un brief de escalare structurat |
| `/kb-article` | Creează sau actualizează un articol în baza de cunoștințe |
| `/agent-improve` | Îmbunătățește baza de cunoștințe pe baza feedback-ului |

## Cum se Folosește

### Răspuns la un Ticket

1. Copiază mesajul clientei din Delight Chat
2. Tastează `/draft-response` și lipește mesajul
3. Revizuiește draft-ul și trimite-l din Delight Chat

### Triaj Rapid

1. Copiază mesajul clientei
2. Tastează `/triage` — primești categorie, prioritate, și răspuns sugerat
3. Dacă vrei răspuns complet: `/draft-response`

### Cercetare

1. Tastează `/research` cu întrebarea clientei
2. Primești un răspuns cu nivel de încredere și surse
3. Dacă e gata de trimis: `/draft-response` cu rezultatele

### Escalare

1. Tastează `/escalate` cu problema și numele clientei
2. Primești un brief structurat cu impact, context, și cerere specifică
3. Trimite brief-ul către management

### Îmbunătățirea Agentului

Dacă un răspuns e greșit sau incomplet:

1. Tastează `/agent-improve` cu explicația a ce a fost greșit
2. Claude va propune o modificare a bazei de cunoștințe
3. Confirmă modificarea
4. Commit-ează în git: `git add . && git commit -m "knowledge: [descriere]"`

## Structura

```
skills/             → Expertiza agentului (cum folosește cunoștințele)
commands/           → Comenzi disponibile
CONNECTORS.md       → Referințe la instrumente conectate
```

> **Notă:** Baza de cunoștințe (`knowledge/`) se află în `workspace/` la nivelul repo-ului. Comenzile și skill-urile referențiază `knowledge/` ca path relativ, rezolvat de Cowork din working directory.

## Skills

| Skill | Descriere |
|-------|-----------|
| response-drafting | Redactare răspunsuri profesionale în română |
| ticket-triage | Categorizare și prioritizare tickete |
| product-knowledge | Expertiză bijuterii — materiale, pietre, îngrijire |
| customer-research | Cercetare multi-sursă cu scor de încredere |
| escalation | Structurare escalări cu impact business |
| knowledge-management | Creare și menținere articole KB |

## Setup

1. Instalează plugin-ul `.plugin` în Claude Desktop Cowork
2. Selectează proiectul "Customer support"
3. **Work in a folder** → selectează directorul `workspace/` din repo
