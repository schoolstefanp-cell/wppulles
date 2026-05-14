# Copilot Instructions - wppulles Werkplaatsomgeving

## Projectdoel
Dit project is een **offline-first werkplaatsomgeving** voor Stefan, automonteur/technisch specialist. De werkplaats moet maximaal onafhankelijk van internet kunnen functioneren.

## Kernprincipes

### 1. Offline-First Benadering
- **Werkplaatslaptop is het primaire apparaat** – HP is niet meer beschikbaar
- Alle kritieke informatie moet lokaal beschikbaar zijn
- Internetconnectie is uitzondering, niet standaard
- Synchronisatie kan later, offline werking nu

### 2. Voorzichtige, Incrementele Wijzigingen
- Maak kleine, veilige stappen
- Inspecteer de repository eerst voordat je grote wijzigingen doet
- Test elke wijziging in de context van offline gebruik
- Bij twijfel: kies de kleinste wijziging die direct bruikbaar is

### 3. Geen Internetafhankelijkheid
- Voeg geen afhankelijkheden toe die internet vereisen
- Als internet nodig is, moet dit duidelijk gedocumenteerd zijn
- Voorkeur voor lokale opslag, lokale tools, offline-geschikte frameworks

### 4. Veiligheid & Geheimen
- **NOOIT** API keys, wachtwoorden, of secrets committen
- `.env` en `.gitignore` altijd consequent hanteren
- Instructies geven hoe geheimen lokaal ingesteld kunnen worden (zonder ze te committen)

### 5. Documentatie & Transparantie
- Altijd uitleggen **wat** is aangepast en **waarom**
- Duidelijke stappen beschrijven hoe wijzigingen getest/gebruikt moeten worden
- Geen "magische" veranderingen – alles moet logisch en navolgbaar zijn

## Voor Copilot Chat & Agents

### Voor Elke Taak
1. **Inspecteer eerst** – Bekijk de huidige structuur en bestanden
2. **Plan voordat je bouwt** – Geen grote refactors zonder duidelijk plan
3. **Werk offline** – Zorg dat oplossingen ook offline werken
4. **Test in context** – Denk aan de werkplaatslaptop als eindgebruiker
5. **Rapporteer** – Zie onderstaande checklist

### Checklist per Taak
- [ ] Wat heb ik gevonden/gediagnosticeerd?
- [ ] Welke bestanden heb ik aangemaakt/aangepast?
- [ ] Hoe kun je dit lokaal testen?
- [ ] Wat is de volgende beste stap?

## Projectstructuur Richtlijnen

```
wppulles/
├── docs/                    # Documentatie
├── offline/                 # Offline gegevens & cache
│   ├── handleidingen/       # Handleidingen, PDF's, technische docs
│   ├── voertuigen/          # Voertuiggegevens, configuratie
│   └── cache/               # Lokale cache
├── logs/                    # Logbestanden
├── scripts/                 # Utility scripts
├── src/                     # Broncode (indien van toepassing)
├── .gitignore               # Git ignore
├── .github/copilot-instructions.md   # Deze file
├── README.md                # Project overzicht
├── AGENTS.md                # Agent-specifieke instructies
├── OFFLINE_STRATEGIE.md     # Offline strategie
└── PROJECTSTATUS.md         # Projectstatus & beslissingen
```

## Wat Mag & Wat Niet

### ✅ Mag
- Mappenstructuur aanmaken en documenteren
- Richtlijnen schrijven voor offline gebruik
- Kleine bug fixes en verbeteringen
- Documentatie aanvullen
- `.gitignore` beheren

### ❌ Mag Niet
- Grote refactors zonder plan
- Bestanden verwijderen zonder duidelijke reden
- Internet-afhankelijke dependencies toevoegen
- Geheimen/API keys committen
- Assumptie dat HP nog beschikbaar is

## Vragen?
Verwijs naar `PROJECTSTATUS.md`, `AGENTS.md`, en `OFFLINE_STRATEGIE.md` voor meer context.
