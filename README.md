# wppulles – Werkplaatsomgeving

**Status:** Eerste opzet  
**Doel:** Offline-first werkplaatsomgeving voor Stefan (automonteur/technisch specialist)

## Over Dit Project

`wppulles` is een werkplaatsprogramma dat Stefan helpt met:
- **Handleidingen** en technische documentatie
- **Voertuiggegevens** en configuraties
- **Kenteken- en klusnotities** (per klant/auto)
- **Logging en audit trails**
- **Lokale offline opslag** – internet niet nodig voor dagelijkse werkzaamheden

## Primaire Regel

> **De werkplaatslaptop is het primaire apparaat.**  
> HP is niet meer beschikbaar.  
> Alles moet offline kunnen werken.

## Projectstructuur

```
wppulles/
├── docs/                    # Projectdocumentatie
├── offline/                 # Offline gegevens & cache
│   ├── handleidingen/       # Handleidingen, technische docs
│   ├── voertuigen/          # Voertuiggegevens
│   └── cache/               # Lokale cache/sync
├── logs/                    # Logbestanden
├── scripts/                 # Utility scripts
├── src/                     # Broncode (toekomstig)
├── .github/
│   └── copilot-instructions.md   # Copilot/Copilot Chat richtlijnen
├── AGENTS.md                # Agent working instructions
├── OFFLINE_STRATEGIE.md     # Offline-first strategie
└── PROJECTSTATUS.md         # Huidige status & beslissingen
```

## Voor Copilot / Copilot Chat

Dit project heeft expliciet richtlijnen voor AI-gestuurde hulp:

1. **`.github/copilot-instructions.md`** – Kernprincipes en werkwijze
2. **`AGENTS.md`** – Voor autonome agents en Copilot Chat
3. **`PROJECTSTATUS.md`** – Huidige stand van zaken

Lees deze eerst voordat je grote wijzigingen maakt.

## Hoe Verder Bouwen

### Korte Termijn
- Mappenstructuur aanvullen met voorbeeld-bestanden
- Offline-strategie verfijnen
- Basisscripts voor Windows toevoegen (bijv. data-exporten, logging)

### Middellange Termijn
- Lokale database (SQLite) voor voertuig-/klusgegevens
- Desktop-applicatie (Electron, Qt of web-local)
- Lokale synchronisatie-mechanisme

### Lange Termijn
- Optionele cloud-sync (als Stefan later wifi heeft)
- API (lokaal draaiend)
- Mobile companion-app (offline-ready)

## Vereisten Checklist

- [x] Offline-first architectuur
- [x] Werkplaatslaptop primair (Windows-gericht)
- [x] HP niet meer beschikbaar
- [x] Geen internet-dependencies standaard
- [x] Duidelijke documentatie voor Copilot
- [ ] Basisdata-structuur (voertuigen, notitiën, logs)
- [ ] Eerste prototype app/CLI
- [ ] Lokale synchronisatie

## Belangrijk

- **Geen secrets** in deze repo (zie `.gitignore`)
- **Alles offline** tenzij expliciet anders nodig
- **Windows-compatible** – Denk aan de werkplaatslaptop
- **Documenteer alles** – Stefan en toekomstige wijzigingen moeten begrijpen wat waar gebeurt

## Contact / Vragen

Verwijs naar:
- `PROJECTSTATUS.md` voor huidige beslissingen
- `OFFLINE_STRATEGIE.md` voor offline-architectuur
- `AGENTS.md` voor Copilot-specifieke richtlijnen
