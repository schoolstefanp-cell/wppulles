# Offline-Strategie – wppulles

## Doel
Dit document beschrijft hoe `wppulles` offline kan werken en welke informatie lokaal beschikbaar moet zijn.

## Kritieke Gegevens (Offline Beschikbaar)

### 1. Handleidingen & Technische Documentatie
- **Waar:** `offline/handleidingen/`
- **Inhoud:** PDF's, TXT's, markdown-docs van autofabrikanten
- **Gebruik:** Stefan raadpleegt dit zonder internet
- **Format:** PDF, Markdown, gekrompen images waar mogelijk
- **Bijv.:** 
  - `handleidingen/Ford/Focus/2020/ownersmanaual.pdf`
  - `handleidingen/Ford/Focus/2020/technical-specs.md`

### 2. Voertuiggegevens
- **Waar:** `offline/voertuigen/`
- **Inhoud:** Configuraties, specs, onderhoudsschema's per voertuig
- **Gebruik:** Snelle lookup van spec's, herkenning
- **Format:** JSON, YAML of SQLite-database
- **Bijv.:**
  - `voertuigen/Ford_Focus_2020.json` (specs)
  - `voertuigen/Mercedes_C200_2018.json` (specs)

### 3. Kenteken- en Klusnotities
- **Waar:** `offline/klusgegevens/` (toekomstig, onder `offline/`)
- **Inhoud:** Lokaal opgeslagen notities per voertuig/klant
- **Gebruik:** Stefan schrijft hier zijn notities op
- **Format:** JSON, SQLite, of tekstbestanden
- **Bijv.:**
  - `klusgegevens/2024-05-14_FORD_ABC123.txt`
  - Database: `klusgegevens.db`

### 4. Logs & Audit Trails
- **Waar:** `logs/`
- **Inhoud:** Alle activiteiten, wijzigingen, fouten
- **Gebruik:** Later terugkijken wat Stefan gedaan heeft
- **Format:** Structured logs (JSON, CSV)
- **Bijv.:**
  - `logs/2024-05-14_werkplaats.log`
  - `logs/2024-05-14_reparaties.log`

### 5. Cache & Temporaire Gegevens
- **Waar:** `offline/cache/`
- **Inhoud:** Gesynchroniseerde kopieën, thumbnails, indices
- **Gebruik:** Snel openen van veelgebruikte gegevens
- **Lifecycle:** Mag gewist worden zonder data-verlies
- **Bijv.:**
  - `cache/voertuigen_index.json`
  - `cache/handleidingen_thumbnails/`

## Voorgestelde Opslagstructuur

```
offline/
├── handleidingen/
│   ├── Ford/
│   │   ├── Focus/
│   │   │   ├── 2020/
│   │   │   │   ├── owners_manual.pdf
│   │   │   │   ├── technical_specs.md
│   │   │   │   └── maintenance_schedule.txt
│   │   │   └── 2021/
│   │   └── Mondeo/
│   ├── Mercedes/
│   ├── Volkswagen/
│   └── _index.json  (metadata: merk, model, jaar, filepath)
│
├── voertuigen/
│   ├── database.db  (SQLite: alle voertuigdata)
│   │   Tables: vehicles, specs, maintenance_history
│   │
│   └── exports/
│       ├── Ford_Focus_2020.json
│       ├── Mercedes_C200_2018.json
│       └── ...
│
├── klusgegevens/  (toekomstig)
│   ├── database.db  (SQLite: klus-notitiën, klanten)
│   │   Tables: klanten, voertuigen_per_klant, klussen, notities
│   │
│   └── exports/
│       ├── 2024-05-14_FORD_ABC123.txt
│       └── ...
│
└── cache/
    ├── voertuigen_index.json
    ├── handleidingen_search_index.json
    ├── thumbnails/
    └── sync_metadata.json
```

## Hoe Internetafhankelijkheid Wordt Vermeden

### ✅ Best Practices
1. **Lokale databases** – SQLite ipv. cloud
2. **Offline-first data** – Alles standaard lokaal, sync optioneel
3. **Geen API calls nodig** – Alle gegevens lokaal beschikbaar
4. **Lokale tools** – Desktop app, CLI of web-local (Electron, Qt, Flask/Tauri)
5. **Batch imports** – Gegevens bulk importeren van USB, niet fetch van internet

### ❌ Vermijden
- Live API-calls naar auto-fabrikanten
- Cloud-opslag als standaard (alleen als Stefan dit wil)
- Real-time synchronisatie
- Afhankelijkheid van externe services

## Synchronisatie (Later)

Wanneer Stefan later WiFi heeft, kan synchronisatie toegevoegd worden:

### Mogelijke Sync-Modi
1. **Lokaal naar cloud** – Backup naar USB/NAS of cloud-opslag (Nextcloud, etc.)
2. **Cloud naar lokaal** – Handleidingen/updates downloaden bij beschikbaarheid
3. **Hybrid** – Offline werken, sync wanneer beschikbaar

### Sync niet vereist voor MVP
- Alles werkt 100% offline
- Sync kan later via: `sync/` map, separate script, of update-mechanisme

## Mapstructuur Waarom

| Map | Doel | Offline | Later Sync |
|-----|------|---------|-----------|
| `offline/handleidingen/` | Technische docs | ✅ Essentieel | ✅ Kan sync van meer docs |
| `offline/voertuigen/` | Voertuigdata | ✅ Essentieel | ✅ Updates/nieuw voertuigen |
| `offline/klusgegevens/` | Notities Stefan | ✅ Essentieel | ✅ Backup/archief |
| `offline/cache/` | Snelle lookup | ✅ Handig | ✅ Kan verwijderd & opnieuw gebouwd |
| `logs/` | Audit trail | ✅ Lokaal | ✅ Kan naar archief |

## Implementatie Roadmap

### Fase 1: Structuur (NU)
- [x] Mappenstructuur aanmaken
- [x] Documentatie schrijven
- [ ] Voorbeeld-handleidingen toevoegen
- [ ] Voorbeeld-voertuiggegevens (JSON)

### Fase 2: Lokale Storage (Snel)
- [ ] SQLite schema's definiëren
- [ ] Data-import scripts (CSV → SQLite)
- [ ] CLI tool voor lookup

### Fase 3: UI (Middellang)
- [ ] Desktop-applicatie (Electron/Qt)
- [ ] Offline-ready interface
- [ ] Zoeken in handleidingen
- [ ] Klus-notitiën beheren

### Fase 4: Sync (Toekomstig)
- [ ] Backup-mechanisme
- [ ] Optional cloud-sync
- [ ] Update-mechanisme voor docs

## Veiligheid & Geheimen

- **`.gitignore`** verhindert dat configs/secrets committed worden
- Lokale wachtwoorden voor database (indien nodig) in `.env` (niet in repo)
- Voertuigdata is openbaar (specs, handleidingen)
- Klus-notities: privé (kunnen later encrypted worden)

## Testen Offline Functionaliteit

Wanneer functionaliteit klaar is:
1. **Verwijder internet** – Test zonder WiFi
2. **Zoeek handleiding** – Kan je snel iets vinden?
3. **Voertuigdata opzoeken** – Werkt het?
4. **Notitiën maken** – Werkt lokaal opslaan?
5. **Logs checken** – Alles geregistreerd?

Alles moet werken zonder verbinding.

## Vragen / Vervolgstappen?

Verwijs naar:
- `PROJECTSTATUS.md` – Status en beslissingen
- `AGENTS.md` – Agent-instructies
- `.github/copilot-instructions.md` – Copilot-richtlijnen
