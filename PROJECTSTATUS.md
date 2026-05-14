# Project Status – wppulles

**Datum:** 2026-05-14  
**Status:** 🔵 Initieel opzet  
**Eigenaar:** Stefan (automonteur/technisch specialist)

---

## Kritieke Beslissingen

### ✅ Besloten
1. **HP is niet meer beschikbaar** → Werkplaatslaptop is primair apparaat
2. **Offline-first benadering** → Internet is uitzondering, niet standaard
3. **Werkplaatslaptop primair** → Alles moet geschikt zijn voor Windows-laptop
4. **Copilot-vriendelijk** → Expliciete instructies voor AI-gestuurde hulp
5. **Geen externe API-afhankelijkheid** → Tenzij kritiek nodig
6. **Lokale opslag standaard** → SQLite, JSON, tekstbestanden
7. **Geen Secrets in Repo** → `.gitignore` strikt gehandhaafd

---

## Wat Klaar Is

| Item | Status | Opmerking |
|------|--------|-----------|
| `.github/copilot-instructions.md` | ✅ | Copilot-richtlijnen |
| `AGENTS.md` | ✅ | Agent-werkwijze |
| `README.md` | ✅ | Projectoverzicht |
| `OFFLINE_STRATEGIE.md` | ✅ | Offline-architectuur |
| `PROJECTSTATUS.md` | ✅ | Deze file |
| `.gitignore` | ✅ | Security & exclusions |
| Mappenstructuur | ✅ | Mappen aangemaakt met `.gitkeep` |

---

## Open Punten

| Punt | Prioriteit | Notitie |
|------|------------|---------|
| Voorbeeld handleidingen toevoegen | 🟡 Medium | PDF's of markdown |
| Voertuigdata schema's definiëren | 🟡 Medium | SQLite of JSON |
| CLI/Desktop-prototype | 🟠 Hoog | Eerste werkende tool |
| Importscripts (CSV → DB) | 🟡 Medium | Data-migratie |
| Testsuite voor offline-werking | 🟡 Medium | Ensure geen internet-deps |

---

## Volgende Beste Stappen

### Korte Termijn (Week 1)
1. Voorbeeld-voertuigdata toevoegen (`offline/voertuigen/`)
2. Basis SQLite-schema's definiëren
3. Eerste import-script schrijven

### Middellange Termijn (Week 2-3)
4. CLI-tool voor voertuig-lookup
5. Desktop-shell (Electron of Qt proof-of-concept)
6. Handleidingen-zoekindex

### Lange Termijn (Later)
7. Full UI voor klus-notitiën
8. Sync-mechanisme (optioneel)
9. Mobile companion-app

---

## Koppelingen naar Relevante Docs

| Document | Doel |
|----------|------|
| `.github/copilot-instructions.md` | Hoe Copilot/Chat moet werken |
| `AGENTS.md` | Agent-specifieke richtlijnen |
| `OFFLINE_STRATEGIE.md` | Hoe offline-architectuur werkt |
| `README.md` | Projectoverzicht |

---

## Architectuur Decision Record (ADR)

### ADR-001: Offline-First
**Besluit:** Alle kritieke data lokaal beschikbaar.  
**Reden:** Werkplaats heeft geen stabiele internet.  
**Impact:** Geen cloud-API's standaard, lokale DB nodig.

### ADR-002: Werkplaatslaptop Primair
**Besluit:** Windows-laptop is hoofdapparaat, HP is vervallen.  
**Reden:** HP niet meer beschikbaar.  
**Impact:** Windows-compatible tools, geen Mac-only code.

### ADR-003: Copilot-Vriendelijk
**Besluit:** Expliciete AI-instructies in repo.  
**Reden:** Stefan gaat dit met Copilot/Chat uitbreiden.  
**Impact:** Extra docs, maar betere tool-ondersteuning.

---

## Contactpunten voor Wijzigingen

Voor grote wijzigingen of vragen:
1. Check `PROJECTSTATUS.md` (deze file) voor context
2. Lees `OFFLINE_STRATEGIE.md` voor offline-requirements
3. Volg `AGENTS.md` voor werkwijze (als agent)
4. Raadpleeg `.github/copilot-instructions.md` (als Copilot)

---

## Versiegeschiedenis

| Datum | Wat | Door |
|-------|-----|------|
| 2026-05-14 | Initial setup & docs | Copilot |

---

**Laatst bijgewerkt:** 2026-05-14 10:30 UTC
