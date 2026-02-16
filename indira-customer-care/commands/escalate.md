---
description: Creează un brief de escalare structurat pentru management sau echipe externe
argument-hint: "<problema> [numele clientei]"
---

# Escalate — Indira

> Dacă vezi placeholder-e necunoscute, verifică [CONNECTORS.md](../CONNECTORS.md).

Împachetează o problemă de suport într-un brief de escalare structurat pentru management, curier, sau furnizor. Adună context, evaluează impactul business, și identifică destinatarul potrivit.

## Usage

```
/escalate <descrierea problemei> [numele clientei]
```

Exemple:
- `/escalate Colet pierdut, clienta Maria a comandat acum 2 săptămâni și nu a primit nimic`
- `/escalate Clientă fidelă amenință cu ANPC după retur refuzat`
- `/escalate 3 clienți au raportat aceeași problemă cu cerceii din colecția Birthstone`
- `/escalate Eroare plată — bani debitat dar comanda nu apare`

## Workflow

### 1. Înțelege Problema

Analizează și determină:
- **Ce e stricat / ce e necesar**: Problema tehnică, de proces, sau de politică
- **Cine e afectat**: Client(ă) specifică, segment, sau mai mulți
- **De cât timp**: Când a început? De cât timp așteaptă clienta?
- **Ce s-a încercat**: Troubleshooting sau workaround-uri
- **De ce acum**: Ce face situația să necesite atenție dincolo de suport normal

Folosește criteriile „When to Escalate" din skill-ul **escalation** pentru a confirma că escalarea e justificată.

### 2. Adună Context

Trage împreună informațiile relevante din sursele disponibile:
- **~~platformă suport**: Tickete legate, timeline comunicări
- **~~e-commerce**: Detalii comandă, status livrare, istoric plăți
- **Baza de cunoștințe**: Probleme cunoscute, politici relevante

### 3. Evaluează Impactul Business

Cuantifică:
- **Client**: Nou vs. fidel? Valoare totală comenzi?
- **Financiar**: Ce sumă e în joc?
- **Reputațional**: Risc review negativ? ANPC?
- **Pattern**: Caz izolat sau pattern?
- **Urgență**: Termen care se apropie?

### 4. Determină Destinatarul

Folosind tier-urile de escalare din skill-ul **escalation**: Senior Suport, Management, Curier, Furnizor, sau Urgentă.

### 5. Generează Brief-ul de Escalare

```
## ESCALARE: [Rezumat într-o linie]

**Severitate:** [Critică / Ridicată / Medie]
**Către:** [Management / Curier / Furnizor]
**Raportat de:** [Numele tău]
**Data:** [Data de azi]

### Impact
- **Client afectat:** [Cine și istoric]
- **Problemă:** [Ce nu funcționează]
- **Valoare:** [Sumă dacă e relevant]
- **Timp în așteptare:** [De cât timp]

### Descrierea Problemei
[3-5 propoziții clare și concise]

### Ce S-a Încercat
1. [Acțiune] → [Rezultat]
2. [Acțiune] → [Rezultat]

### Comunicarea cu Clienta
- **Ultimul update:** [Data — ce s-a comunicat]
- **Așteptarea clientei:** [Ce așteaptă și până când]
- **Risc escalare:** [Va contacta ANPC? Review negativ?]

### Ce E Necesar
- [Cerere specifică]
- **Termen:** [Până când]

### Context Suplimentar
- [Tickete, fotografii, link-uri]
```

### 6. Oferă Pași Următori

După generarea escalării:
- „Vrei să trimit un update clientei între timp?"
- „Să setez un reminder de follow-up?"
- „Să pregătesc un răspuns pentru client cu statusul curent?"
