# Interview Analysis Plugin

Plugin pentru analiza transcrierilor de interviuri prin framework-ul JTBD (Jobs-To-Be-Done).
Extrage joburi ale clienților, rezultate dorite, puncte de durere, soluții concurente și
oportunități de inovație din date calitative brute.

## Comenzi

| Comandă | Descriere |
|---------|-----------|
| `/analyze-jtbd` | Analizează o transcriere de interviu și generează un raport JTBD comprehensiv |

## Cum să Folosești

### Fluxul de lucru

1. **Încarcă transcriptul** în contextul proiectului Claude
2. **Rulează comanda** cu calea fișierului:
   ```
   /analyze-jtbd transcripts/interviu-client.md
   ```
3. **Raportul se salvează automat** în folderul `JTBD/`
4. **Transcriptul se copiază** în folderul `transcripts/` dacă nu e deja acolo

### Structura de Foldere

```
interview-analysis/
├── transcripts/    ← transcrierile încărcate
└── JTBD/          ← rapoartele generate
```

### Formatul Raportului

Fiecare raport acoperă 10 dimensiuni JTBD:

1. **Jobul Principal** — motivația de bază în format „Când... vreau să... astfel încât..."
2. **Circumstanțele Jobului** — când, unde, de ce, frecvență
3. **Rezultate Dorite** — funcționale, emoționale, sociale (cu metrici)
4. **Puncte de Durere** — ce eșuează, workaround-uri, severitate
5. **Joburi Emoționale și Sociale** — cum vor să se simtă și să fie percepuți
6. **Soluții Concurente** — directe, indirecte, workaround-uri, non-consum
7. **Declanșatoare de Schimbare** — Push, Pull, Anxietate, Inerție (modelul Moesta)
8. **Semnale de Segment** — ipoteză de tip de utilizator bazată pe comportament
9. **Oportunități** — gap-uri de rezultat unde nicio soluție nu performează bine
10. **Citate Cheie** — cele mai puternice exprimări verbatim din transcript

Fiecare insight include un nivel de **încredere** (Ridicată/Medie/Scăzută) bazat pe
cantitatea și calitatea dovezilor din transcript.

## Skill

| Skill | Descriere |
|-------|-----------|
| jtbd-analysis | Expert la nivel Bob Moesta în extragerea JTBD din transcrieri, cu scoring de încredere și ghid complet de analiză |

## Metodologie

Analiza combină:
- **Switch Interview** (Bob Moesta) — cele patru forțe ale progresului
- **Outcome-Driven Innovation** (Tony Ulwick) — rezultate ca metrici măsurabile
- Scoring onest de încredere — niciun insight fără dovezi explicite
