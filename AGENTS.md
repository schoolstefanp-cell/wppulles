# Agent-Instructies - wppulles

## Voor Autonome Agents & Copilot Chat

Dit document geeft agents richtlijnen voor autonoom, effectief en veilig werken aan wppulles.

## Primaire Directieven

### 1. Inspecteer Eerst
- Voordat je wijzigingen maakt, voer eerst een diagnose uit
- Controleer huidige mappenstructuur, bestanden en configuratie
- Lees relevante docs (README, PROJECTSTATUS, OFFLINE_STRATEGIE)
- Begrijp de context voordat je handelt

### 2. Maak Geen Grote Refactors Zonder Plan
- Kleine wijzigingen zijn voorkeur
- Voor grotere wijzigingen: documenteer het plan eerst
- Vraag impliciete confirmatie door het plan duidelijk uit te leggen
- Splits grote taken in kleinere, testbare stappen

### 3. Verwijder Geen Bestanden Zonder Duidelijke Reden
- Bestanden hebben een doel of zullen dat krijgen
- Voor verwijderingen: leg uit waarom
- Twijfel? Laat het staan en documenteer waarom het problematisch is

### 4. Werk Offline-First
- Zorg dat alle oplossingen ook offline werken
- Geen internet-afhankelijkheid zonder duidelijke noodzaak
- Denk aan de werkplaatslaptop: snel, betrouwbaar, zonder WiFi/internet

### 5. Houd Rekening Met Windows & Werkplaatslaptop
- Werkplaatslaptop draait waarschijnlijk Windows
- Pad-scheiders, line endings, karaktercodering: allemaal relevant
- Geen bash-only scripts zonder Windows-equivalent
- Test mentaal: "Kan Stefan dit in de werkplaats gebruiken?"

## Rapportage Checklist

**Na elke taak, rapporteer dit:**

```
## Taakrapport

### 1. Wat gevonden
- [Beschrijf wat je ontdekt hebt]
- [Huidige staat van de repo]
- [Problemen/gaten die je zag]

### 2. Wat aangepast
- [Bestand A: beschrijf wijziging]
- [Bestand B: beschrijf wijziging]
- [Nieuwe mappen/bestanden met doel]

### 3. Hoe getest
- [Hoe je lokaal kunt verifiëren]
- [Wat te checken]
- [Command lines / stappen indien relevant]

### 4. Volgende beste stap
- [Wat logisch volgt]
- [Wat wachten kan op feedback]
- [Mogelijke vervolgstappen]
```

## Werkwijze: Stap voor Stap

### Voor Kleinere Taken (fixes, docs, structuur)
1. Inspecteer relevant deel van repo
2. Maak wijziging(en)
3. Rapporteer (zie checklist boven)
4. Klaar

### Voor Grotere Taken (nieuwe features, refactors)
1. Inspecteer repo grondvest
2. Lees PROJECTSTATUS.md, OFFLINE_STRATEGIE.md
3. Formuleer plan en leg uit
4. Implementeer in stappen
5. Rapporteer per stap
6. Vraag impliciete goedkeuring voordat volgende stap

## Niet-Negotiables

- **Geen secrets committen** → `.env`, API keys, wachtwoorden altijd in `.gitignore`
- **Geen internet-dependencies zonder reden** → Alles offline-first
- **Geen assumptie HP-apparaat** → Stefan werkt voornamelijk vanaf werkplaatslaptop
- **Documentatie is code** → Elke wijziging moet duidelijk zijn

## Communicatie

- Wees duidelijk en expliciet
- Leg aannames uit
- Toon de volledige workflow
- Vraag om feedback bij onduidelijkheden
- Rapporteer volledig, ook missteps

## Twijfels?

Verwijs naar:
- `.github/copilot-instructions.md` – Algemene richtlijnen
- `PROJECTSTATUS.md` – Beslissingen en status
- `OFFLINE_STRATEGIE.md` – Hoe offline werking georganiseerd is
- `README.md` – Projectoverzicht
