---
typ: artefakt
name: Anforderungsmanagement
kontext: Template zur strukturierten Erfassung, Dokumentation und Verwaltung von Anforderungen
rollen:
  - Product Owner
artefakte: []
workflows: []
---

# Artefakt: Anforderungsmanagement

## Über Anforderungsmanagement

**Anforderungsmanagement** ist der Prozess der systematischen Erfassung, Analyse, Dokumentation, Priorisierung und Verwaltung von Anforderungen für ein Software-System. Es verbindet Geschäftsziele mit technischer Umsetzung.

Anforderungen werden aus Visionen abgeleitet und bilden die Grundlage für:
- User Stories (PO-Perspektive: Mehrwert)
- Feature-Spezifikationen (Architekt + Team: Technische Umsetzung)
- Backlog-Items (Priorisierung und Planung)

---

## Sinn und Zweck

### Warum Anforderungsmanagement?

**1. Klarheit und Struktur**
- Systematische Erfassung aller Anforderungen
- Klare Strukturierung nach Typen (funktional, nicht-funktional, Randbedingungen)
- Nachvollziehbare Dokumentation

**2. Vollständigkeit**
- Keine wichtigen Anforderungen werden vergessen
- Alle Stakeholder-Interessen werden berücksichtigt
- Geschäftsziele werden mit technischen Anforderungen verbunden

**3. Priorisierung**
- Anforderungen werden nach Product Value priorisiert
- Klare Entscheidungsgrundlage für PO
- Ressourcen werden optimal eingesetzt

**4. Rückverfolgbarkeit (Traceability)**
- Anforderungen können zu Geschäftszielen zurückverfolgt werden
- Änderungen sind nachvollziehbar
- Impact-Analyse bei Änderungen möglich

**5. Qualitätssicherung**
- Anforderungen werden validiert und verifiziert
- Widersprüche werden früh erkannt
- Testbarkeit wird sichergestellt

---

## Anforderungstypen

### Funktionale Anforderungen

**Beschreibung:** Was soll das System tun?

**Beispiele:**
- "Als Nutzer kann ich mich mit E-Mail und Passwort anmelden"
- "Das System soll Bestellungen verarbeiten"
- "Das System soll Rechnungen generieren"

**Dokumentation:**
- User Stories (aus Nutzersicht)
- Use Cases (detaillierte Abläufe)
- Business Processes (Geschäftsprozesse)
- System Features (technische Funktionalitäten)

### Nicht-funktionale Anforderungen (Qualitätsanforderungen)

**Beschreibung:** Wie soll das System sein?

**Kategorien:**
- **Performance:** Antwortzeiten, Durchsatz, Skalierbarkeit
- **Sicherheit:** Authentifizierung, Autorisierung, Datenschutz
- **Usability:** Benutzerfreundlichkeit, Accessibility
- **Zuverlässigkeit:** Verfügbarkeit, Fehlertoleranz
- **Wartbarkeit:** Wartbarkeit, Erweiterbarkeit
- **Compliance:** Rechtliche und regulatorische Anforderungen

**Beispiele:**
- "Die API soll innerhalb von 200ms antworten (P95)"
- "Das System soll 99.9% Verfügbarkeit haben"
- "Das System soll DSGVO-konform sein"

### Randbedingungen

**Beschreibung:** Externe Vorgaben und Einschränkungen

**Kategorien:**
- **Technische Randbedingungen:** Framework, Datenbank, Standards
- **Organisatorische Randbedingungen:** Team-Struktur, Prozesse, Zeitvorgaben
- **Gesetzliche/Regulatorische Randbedingungen:** Compliance, Datenschutz, Sicherheit

**Beispiele:**
- "Das System muss mit PostgreSQL 15 kompatibel sein"
- "Das System muss DSGVO-konform sein"
- "Das System muss innerhalb von 6 Monaten fertig sein"

---

## Anforderungsstruktur

### Einfache Struktur (Start)

**Für kleine Projekte oder Startphase:**

```
docs/
└── anforderungen.md
```

**Inhalt:**
- Funktionale Anforderungen
- Nicht-funktionale Anforderungen
- Randbedingungen
- Priorisierung

### Erweiterte Struktur (bei Bedarf)

**Für größere Projekte:**

```
docs/
└── anforderungen/
    ├── README.md                    # Übersicht und Index
    ├── funktionale-anforderungen.md
    ├── nicht-funktionale-anforderungen.md
    ├── randbedingungen.md
    ├── priorisierung.md
    └── traceability.md              # Rückverfolgbarkeit
```

---

## Anforderungsformat

### Standard-Format für Anforderungen

```markdown
## REQ-[Nummer]: [Titel der Anforderung]

**Typ:** [Funktional | Nicht-funktional | Randbedingung]
**Priorität:** [Hoch | Mittel | Niedrig]
**Status:** [Neu | In Bearbeitung | Abgenommen | Abgelehnt]

**Beschreibung:**
[Klare, präzise Beschreibung der Anforderung]

**Begründung:**
[Warum ist diese Anforderung wichtig? Welches Geschäftsziel unterstützt sie?]

**Akzeptanzkriterien:**
- [ ] Kriterium 1: [Testbares Kriterium]
- [ ] Kriterium 2: [Testbares Kriterium]

**Abhängigkeiten:**
- Abhängig von: [REQ-XXX, REQ-YYY]
- Beeinflusst: [REQ-ZZZ]

**Verweise:**
- User Story: [US-XXX]
- Feature-Spezifikation: [Feature-XXX]
- ADR: [ADR-XXX]

**Stakeholder:**
- [Stakeholder 1]: [Interesse]
- [Stakeholder 2]: [Interesse]

**Geschätzt:** [Story Points oder Stunden]
**Verantwortlich:** [Team oder Person]
```

### Beispiel: Funktionale Anforderung

```markdown
## REQ-001: User-Login-Funktionalität

**Typ:** Funktional
**Priorität:** Hoch
**Status:** Abgenommen

**Beschreibung:**
Registrierte Nutzer müssen sich mit E-Mail und Passwort anmelden können, 
um auf ihre persönlichen Daten zuzugreifen.

**Begründung:**
Diese Anforderung ist grundlegend für alle weiteren Features, die eine 
Authentifizierung erfordern. Sie unterstützt das Geschäftsziel "Sicherer 
Zugang zu Nutzerdaten".

**Akzeptanzkriterien:**
- [ ] Nutzer kann sich mit korrekter E-Mail und Passwort anmelden
- [ ] Nutzer sieht Fehlermeldung bei falschen Credentials
- [ ] Nutzer wird nach erfolgreichem Login zur Dashboard-Seite weitergeleitet
- [ ] Passwort wird verschlüsselt gespeichert (bcrypt)

**Abhängigkeiten:**
- Abhängig von: REQ-002 (User-Registrierung)
- Beeinflusst: REQ-003 (Profil-Verwaltung), REQ-004 (Geschützte Features)

**Verweise:**
- User Story: US-001 (Als registrierter Nutzer möchte ich mich anmelden)
- Feature-Spezifikation: Feature-User-Login
- ADR: ADR-002 (JWT für Session-Management)

**Stakeholder:**
- Endnutzer: Sichere Authentifizierung
- Business: Zugang zu Nutzerdaten ermöglichen
- Security: Sicherheitsstandards einhalten

**Geschätzt:** 21 Story Points
**Verantwortlich:** Backend-Team
```

### Beispiel: Nicht-funktionale Anforderung

```markdown
## REQ-010: API-Performance

**Typ:** Nicht-funktional (Performance)
**Priorität:** Hoch
**Status:** Abgenommen

**Beschreibung:**
Alle API-Endpoints müssen innerhalb von 200ms antworten (95. Perzentil).

**Begründung:**
Gute Performance ist wichtig für Nutzererfahrung und Skalierbarkeit. 
Langsame APIs führen zu schlechter Nutzererfahrung und können Skalierungsprobleme verursachen.

**Akzeptanzkriterien:**
- [ ] 95% aller API-Requests antworten innerhalb von 200ms
- [ ] Performance-Tests zeigen, dass Anforderung erfüllt wird
- [ ] Monitoring zeigt kontinuierliche Einhaltung der Anforderung

**Abhängigkeiten:**
- Beeinflusst: Alle funktionalen Anforderungen mit API-Zugriff

**Verweise:**
- Feature-Spezifikation: Feature-API-Performance
- ADR: ADR-005 (Caching-Strategie)

**Stakeholder:**
- Endnutzer: Schnelle Antwortzeiten
- Business: Gute Nutzererfahrung
- Operations: Skalierbarkeit

**Geschätzt:** 8 Story Points
**Verantwortlich:** Backend-Team
```

### Beispiel: Randbedingung

```markdown
## REQ-020: PostgreSQL-Kompatibilität

**Typ:** Randbedingung (Technisch)
**Priorität:** Hoch
**Status:** Abgenommen

**Beschreibung:**
Das System muss mit PostgreSQL 15 kompatibel sein.

**Begründung:**
PostgreSQL 15 ist die Standard-Datenbank im Unternehmen. 
Kompatibilität ist notwendig für Integration mit bestehenden Systemen.

**Akzeptanzkriterien:**
- [ ] System funktioniert mit PostgreSQL 15
- [ ] Alle Datenbank-Queries sind PostgreSQL-kompatibel
- [ ] Migration-Skripte funktionieren mit PostgreSQL 15

**Abhängigkeiten:**
- Beeinflusst: Alle Features mit Datenbank-Zugriff

**Verweise:**
- ADR: ADR-001 (PostgreSQL als primäre Datenbank)

**Stakeholder:**
- Operations: Einheitliche Datenbank-Infrastruktur
- Entwickler: Bekannte Technologie

**Geschätzt:** N/A (Architektur-Entscheidung)
**Verantwortlich:** Architektur-Team
```

---

## Anforderungs-ID-System

### ID-Schema

**Format:** `REQ-[Nummer]-[Kategorie]`

**Kategorien:**
- `REQ-001`, `REQ-002`, ... - Allgemeine Anforderungen
- `FUNC-001`, `FUNC-002`, ... - Funktionale Anforderungen
- `QUAL-001`, `QUAL-002`, ... - Qualitätsanforderungen (nicht-funktional)
- `CONST-001`, `CONST-002`, ... - Randbedingungen

**Beispiele:**
- `REQ-001` - User-Login-Funktionalität
- `QUAL-001` - API-Performance
- `CONST-001` - PostgreSQL-Kompatibilität

### Verlinkung zwischen Anforderungen

**Interne Verweise:**
- `[[REQ-001]]` - Verweis auf andere Anforderung
- `Siehe auch: [[REQ-002]], [[REQ-003]]`

**Externe Verweise:**
- `User Story: [US-001](./user-stories/us-001.md)`
- `Feature-Spezifikation: [Feature-User-Login](./features/feature-user-login.md)`
- `ADR: [ADR-002](./adr/adr-002.md)`

---

## Workflow: Von Vision zu Umsetzung

### Phase 1: Vision (PO)

**Artefakt:** `{DOCS}/{VISION.MD}`

**Inhalt:**
- Geschäftsziele
- Produktvision
- Ideen und Inspiration

### Phase 2: Anforderungen (PO)

**Artefakt:** `{DOCS}/{REQUIREMENTS.MD}` oder `{DOCS}/{REQUIREMENTS}/`

**Prozess:**
1. PO leitet Anforderungen aus Vision ab
2. Anforderungen werden strukturiert dokumentiert
3. Anforderungen werden priorisiert
4. Anforderungen werden mit Stakeholdern abgestimmt

**Ergebnis:** Strukturierte Anforderungen mit Priorisierung

### Phase 3: User Stories (PO)

**Artefakt:** `{DOCS}/{USER-STORIES}/`

**Prozess:**
1. PO leitet User Stories aus Anforderungen ab
2. User Stories beschreiben Mehrwert aus Nutzersicht
3. Akzeptanzkriterien werden definiert (aus Nutzersicht)

**Ergebnis:** User Stories mit Mehrwert-Beschreibung

### Phase 4: Feature-Spezifikationen (Architekt + Team)

**Artefakt:** `{DOCS}/{FEATURES}` oder `{DOCS}/{SRS}`

**Prozess:**
1. Architekt + Team erstellen Feature-Spezifikation basierend auf User Story
2. Technische Anforderungen werden definiert
3. Architektur-Leitplanken werden gesetzt
4. Technische Akzeptanzkriterien werden definiert

**Ergebnis:** Technische Umsetzungsspezifikation

### Phase 5: Tasks (Team)

**Artefakt:** Task-Management-System

**Prozess:**
1. Team leitet Tasks aus Feature-Spezifikation ab
2. Tasks werden geschätzt
3. Feature-Verantwortlicher koordiniert Tasks

**Ergebnis:** Konkrete, umsetzbare Tasks

---

## Priorisierung

### Priorisierungsmethoden

**MoSCoW:**
- **Must Have:** Kritisch für Systemerfolg
- **Should Have:** Wichtig, aber nicht kritisch
- **Could Have:** Wünschenswert, falls Zeit/Ressourcen
- **Won't Have:** Nicht in aktueller Iteration

**Value vs. Effort:**
- Hoher Value, niedriger Effort = hohe Priorität
- Hoher Value, hoher Effort = mittlere Priorität
- Niedriger Value, niedriger Effort = niedrige Priorität
- Niedriger Value, hoher Effort = niedrige Priorität

**Priorisierungsfaktoren:**
- **Product Value:** Welchen Wert bringt die Anforderung?
- **Geschäftswert:** Unterstützt sie Geschäftsziele?
- **Risiko:** Reduziert sie Risiken?
- **Dependencies:** Welche Abhängigkeiten gibt es?
- **Effort:** Wie viel Aufwand ist nötig?

### Priorisierung dokumentieren

```markdown
## Priorisierung

### Must Have (Hoch)
- REQ-001: User-Login-Funktionalität
- REQ-002: User-Registrierung
- QUAL-001: API-Performance

### Should Have (Mittel)
- REQ-003: Profil-Verwaltung
- REQ-004: Passwort-Reset

### Could Have (Niedrig)
- REQ-005: Social-Login
- REQ-006: Zwei-Faktor-Authentifizierung

### Won't Have (Nicht in dieser Iteration)
- REQ-007: Biometrische Authentifizierung
```

---

## Rückverfolgbarkeit (Traceability)

### Traceability-Matrix

**Zweck:** Nachvollziehen, welche Anforderungen zu welchen Artefakten führen

**Struktur:**

```markdown
## Traceability-Matrix

| Anforderung | Vision | User Story | Feature-Spezifikation | Tasks | Status |
|-------------|--------|------------|----------------------|-------|--------|
| REQ-001 | Vision-1 | US-001 | Feature-Login | Task-1, Task-2 | ✅ Done |
| REQ-002 | Vision-1 | US-002 | Feature-Registration | Task-3, Task-4 | 🔄 In Progress |
| QUAL-001 | Vision-2 | - | Feature-Performance | Task-5 | 📋 Planned |
```

### Rückverfolgbarkeit dokumentieren

**Von Geschäftsziel zu Code:**
- Geschäftsziel → Vision → Anforderung → User Story → Feature-Spezifikation → Tasks → Code

**Beispiel:**
```
Geschäftsziel: "Sicherer Zugang zu Nutzerdaten"
  ↓
Vision: "Nutzer können sich sicher anmelden"
  ↓
Anforderung: REQ-001 (User-Login-Funktionalität)
  ↓
User Story: US-001 (Als Nutzer möchte ich mich anmelden)
  ↓
Feature-Spezifikation: Feature-User-Login
  ↓
Tasks: Task-1 (UserService implementieren), Task-2 (AuthController erstellen)
  ↓
Code: UserService.java, AuthController.java
```

---

## Qualitätskriterien für Anforderungen

### SMART-Kriterien

**S** - Spezifisch: Klar und eindeutig formuliert
**M** - Messbar: Kann gemessen/getestet werden
**A** - Akzeptabel: Von Stakeholdern akzeptiert
**R** - Realistisch: Technisch und organisatorisch machbar
**T** - Terminiert: Klarer Zeitrahmen

### Weitere Qualitätskriterien

**Testbar:**
- Jede Anforderung muss testbar sein
- Akzeptanzkriterien sind testbar definiert

**Eindeutig:**
- Keine Mehrdeutigkeiten
- Keine Widersprüche

**Vollständig:**
- Alle Aspekte abgedeckt
- Keine wichtigen Details fehlen

**Konsistent:**
- Widerspruchsfreiheit zwischen Anforderungen
- Konsistente Terminologie

**Nachvollziehbar:**
- Begründung vorhanden
- Verknüpfung zu Geschäftszielen

---

## Best Practices

### Anforderungen formulieren

**Gut:**
- "Als Nutzer kann ich mich mit E-Mail und Passwort anmelden"
- "Die API soll innerhalb von 200ms antworten (P95)"
- "Das System soll 99.9% Verfügbarkeit haben"

**Schlecht:**
- "Das System soll schnell sein" (nicht messbar)
- "Das System soll gut aussehen" (nicht spezifisch)
- "Das System soll alles können" (nicht realistisch)

### Anforderungen strukturieren

**Strukturierung nach:**
- Typ (funktional, nicht-funktional, Randbedingung)
- Priorität (Hoch, Mittel, Niedrig)
- Status (Neu, In Bearbeitung, Abgenommen, Abgelehnt)
- Stakeholder (wer ist betroffen?)

### Anforderungen verwalten

**Kontinuierliche Pflege:**
- Anforderungen regelmäßig überprüfen
- Status aktualisieren
- Prioritäten anpassen
- Abhängigkeiten prüfen

**Änderungsmanagement:**
- Änderungen dokumentieren
- Impact-Analyse durchführen
- Stakeholder informieren
- Traceability aktualisieren

---

## Integration mit anderen Artefakten

### Verknüpfung mit Vision

- Anforderungen leiten sich aus Vision ab
- Vision wird in `{DOCS}/{VISION.MD}` dokumentiert
- Anforderungen referenzieren Vision

### Verknüpfung mit User Stories

- User Stories leiten sich aus Anforderungen ab
- Anforderungen werden in User Stories umgesetzt
- Traceability zwischen Anforderungen und User Stories

### Verknüpfung mit Feature-Spezifikationen

- Feature-Spezifikationen implementieren Anforderungen technisch
- Technische Anforderungen aus Feature-Spezifikationen referenzieren Anforderungen
- Traceability zwischen Anforderungen und Feature-Spezifikationen

### Verknüpfung mit ADRs

- Architektur-Entscheidungen (ADRs) können Anforderungen beeinflussen
- Anforderungen können ADRs erfordern
- Traceability zwischen Anforderungen und ADRs

### Verknüpfung mit arc42

- Anforderungen fließen in arc42-Kapitel 1 (Einführung und Ziele) ein
- Randbedingungen fließen in arc42-Kapitel 2 (Randbedingungen) ein
- Qualitätsanforderungen fließen in arc42-Kapitel 10 (Qualitätsanforderungen) ein

---

## Zusammenfassung

**Anforderungsmanagement ist wichtig, weil es:**
- Klarheit und Struktur schafft
- Vollständigkeit sicherstellt
- Priorisierung ermöglicht
- Rückverfolgbarkeit gewährleistet
- Qualität sichert

**Eine gute Anforderung:**
- Ist SMART (Spezifisch, Messbar, Akzeptabel, Realistisch, Terminiert)
- Ist testbar
- Ist eindeutig
- Ist vollständig
- Ist konsistent
- Ist nachvollziehbar

**Anforderungen verbinden:**
- Vision (Geschäftsziele) → Anforderungen → User Stories → Feature-Spezifikationen → Tasks → Code

**Anforderungsmanagement ist Teil des Workflows:**
- PO sammelt Anforderungen aus Vision
- PO leitet User Stories aus Anforderungen ab
- Architekt + Team erstellen Feature-Spezifikationen basierend auf User Stories
- Team leitet Tasks aus Feature-Spezifikationen ab
