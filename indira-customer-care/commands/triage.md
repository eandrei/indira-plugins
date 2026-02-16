---
description: Triază și prioritizează un ticket de suport
argument-hint: "<textul ticketului>"
---

# Triage — Indira

> Dacă vezi placeholder-e necunoscute, verifică [CONNECTORS.md](../CONNECTORS.md).

Categorizează, prioritizează și sugerează un răspuns inițial pentru un ticket de suport Indira.

## Usage

```
/triage <textul ticketului sau mesajul clientei>
```

Exemple:
- `/triage Clienta spune că inelul primit e oxidat și vrea banii înapoi`
- `/triage „Am comandat mărimea 7 dar am primit 6, ce fac?"`
- `/triage Întrebare despre disponibilitate colier cu safir`
- `/triage Clientă care a trimis 3 mesaje fără răspuns`

## Workflow

### 1. Analizează Ticketul

Citește mesajul și extrage:

- **Problema principală**: Ce experimentează clienta concret?
- **Simptome**: Ce comportament sau eroare descrie?
- **Context client**: Cine e? Detalii comandă, istoric?
- **Semnale de urgență**: E blocată? Menționează ANPC? De câte ori a scris?
- **Stare emoțională**: Frustrată, confuză, neutră, escaladează?

### 2. Categorizează și Prioritizează

Folosind taxonomia și framework-ul de prioritizare din skill-ul **ticket-triage**:

- Asignează o **categorie primară** și opțional una secundară
- Asignează o **prioritate** (P1-P4) pe baza impactului și urgenței
- Identifică **routing-ul** recomandat

### 3. Verifică Duplicatele

Înainte de a ruta:

- **~~platformă suport**: Caută tickete similare deschise sau recent rezolvate
- **Baza de cunoștințe**: Verifică problemele cunoscute sau documentația existentă

### 4. Generează Triajul

```
## Triaj: [Rezumat într-o linie]

**Categorie:** [Primară] / [Secundară dacă e cazul]
**Prioritate:** [P1-P4] — [Justificare scurtă]

### Rezumat
[2-3 propoziții despre ce experimentează clienta]

### Detalii
- **Clientă:** [Nume/cont dacă e cunoscut]
- **Impact:** [Cine și ce e afectat]
- **Workaround:** [Disponibil / Indisponibil / Necunoscut]
- **Tickete similare:** [Link-uri dacă s-au găsit]

### Routing
**Direcționează către:** [Răspuns direct / Senior / Management]
**De ce:** [Raționament scurt]

### Răspuns Sugerat
[Draft de prim răspuns — recunoaște problema, setează așteptări,
oferă workaround dacă e disponibil. Folosește brand voice Indira.]

### Note Interne
- [Context suplimentar pentru agentul care preia]
- [Ce trebuie verificat în Shopify / Delight Chat]
- [Trigger-e de escalare de urmărit]
```

### 5. Sugerează Pași Următori

După prezentarea triajului:
- „Vrei să scriu un răspuns complet? Folosește /draft-response"
- „Trebuie escaladat? Folosește /escalate"
- „Vrei mai mult context? Folosește /research"
