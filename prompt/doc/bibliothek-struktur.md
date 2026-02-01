# Bibliotheks-Struktur und Verknüpfungen

Diese Dokumentation beschreibt die Gesamtstruktur der Bibliothek und wie die verschiedenen Komponenten (Rollen, Artefakte, Workflows) miteinander verknüpft sind.

---

## Überblick der Bibliothek

Die Bibliothek besteht aus drei Hauptkomponenten:

1. **Rollen** (`rollen/`) - Definieren, wer was tut
2. **Artefakte** (`artefakte/`) - Definieren, was erstellt wird
3. **Dokumentation** (`doc/`) - Erklärt Zusammenhänge und Workflows
4. **Koordinator** (`_koordinator.md`) - Zentrale Koordinationsrolle

**Zukünftig geplant:**
- **Fähigkeiten** (Skills) - Spezifische Kompetenzen
- **Workflows** - Prozessbeschreibungen

---

## Aktuelle Verknüpfungsarten

### 1. Namentliche Erwähnungen

**Wie es funktioniert:**
- Rollen werden namentlich erwähnt (z.B. "Product Owner", "Softwarearchitekt")
- Artefakte werden namentlich erwähnt (z.B. "Feature-Spezifikation", "ADR")
- Konzepte werden namentlich erwähnt (z.B. "User Story", "Anforderung")

**Beispiel:**
```markdown
Der Product Owner erstellt User Stories basierend auf Anforderungen.
Die Feature-Spezifikation verweist auf ADRs.
```

**Cursor.AI kann:**
- ✅ Semantisch nach Begriffen suchen (`codebase_search`)
- ✅ Exakte Namen finden (`grep`)
- ✅ Kontext aus verschiedenen Dateien zusammenführen

---

### 2. Platzhalter-System

**Wie es funktioniert:**
- Zentrale Definition im Koordinator (`{REQUIREMENTS.MD}`, `{FEATURES}/`)
- Alle Rollen verwenden diese Platzhalter
- Mapping zu echten Dateinamen/Verzeichnissen

**Beispiel:**
```markdown
{REQUIREMENTS.MD} → docs/anforderungen.md
{FEATURES}/ → docs/features/
{USER-STORIES}/ → docs/user-stories/
```

**Cursor.AI kann:**
- ✅ Platzhalter im Koordinator finden
- ✅ Mapping verstehen
- ✅ Konsistente Verwendung sicherstellen

---

### 3. Markdown-Links

**Wie es funktioniert:**
- Relative Pfade zu anderen Dateien
- Verweise auf Artefakte, Rollen, Dokumentation

**Beispiel:**
```markdown
Siehe auch: [Feature-Spezifikation](./artefakte/feature-spezifikation.md)
User Story: [US-001](./user-stories/us-001.md)
ADR: [ADR-002](./adr/adr-002.md)
```

**Cursor.AI kann:**
- ✅ Links folgen (`read_file` mit Pfad)
- ✅ Verknüpfungen nachverfolgen
- ✅ Zirkuläre Abhängigkeiten erkennen

---

### 4. Semantische Verknüpfungen

**Wie es funktioniert:**
- Beschreibungen von Beziehungen ("verweist auf", "basiert auf", "leitet sich ab von")
- Workflow-Beschreibungen
- Abhängigkeitsketten

**Beispiel:**
```markdown
User Stories leiten sich aus Anforderungen ab.
Feature-Spezifikationen basieren auf User Stories.
ADRs werden in Feature-Spezifikationen referenziert.
```

**Cursor.AI kann:**
- ✅ Semantisch nach Beziehungen suchen (`codebase_search`)
- ✅ Workflows verstehen
- ✅ Abhängigkeiten nachvollziehen

---

### 5. Strukturelle Verknüpfungen

**Wie es funktioniert:**
- Verzeichnisstruktur zeigt Hierarchie
- Dateinamen zeigen Zugehörigkeit
- Koordinator listet alle Rollen/Artefakte auf

**Beispiel:**
```
prompt/
├── rollen/
│   ├── product-owner.md
│   └── software-architect.md
├── artefakte/
│   ├── feature-spezifikation.md
│   └── architecture-decision-record.md
└── doc/
    └── artefakt-zusammenhaenge.md
```

**Cursor.AI kann:**
- ✅ Verzeichnisstruktur lesen (`list_dir`)
- ✅ Dateien finden (`glob_file_search`)
- ✅ Strukturelle Zusammenhänge verstehen

---

## Wie Cursor.AI die Verknüpfungen nutzt

### Automatische Fähigkeiten

**1. Semantische Suche:**
```python
# Cursor.AI kann semantisch suchen:
codebase_search("Wie werden User Stories zu Feature-Spezifikationen?")
# Findet: product-owner.md, feature-spezifikation.md, artefakt-zusammenhaenge.md
```

**2. Exakte Suche:**
```python
# Cursor.AI kann exakt suchen:
grep("Feature-Spezifikation")
# Findet: Alle Erwähnungen von "Feature-Spezifikation"
```

**3. Datei-Verknüpfungen:**
```python
# Cursor.AI kann Links folgen:
read_file("artefakte/feature-spezifikation.md")
# Liest die Datei und kann dann Links darin folgen
```

**4. Kontext-Zusammenführung:**
- Cursor.AI kann mehrere Dateien gleichzeitig lesen
- Verknüpfungen zwischen verschiedenen Komponenten verstehen
- Konsistenz prüfen

---

## Aktuelle Verknüpfungsmatrix

### Rollen ↔ Artefakte

| Rolle | Erstellt/Verwendet | Artefakt |
|-------|-------------------|----------|
| Product Owner | Erstellt | Anforderungen, User Stories, Vision |
| Product Owner | Verwendet | Feature-Spezifikation (prüft) |
| Softwarearchitekt | Erstellt | arc42, ADRs, Feature-Spezifikation |
| Softwarearchitekt | Verwendet | Anforderungen, User Stories |
| Dev Team | Erstellt | Tasks, Code, Feature-Spezifikation (mit) |
| Dev Team | Verwendet | Feature-Spezifikation, ADRs, arc42 |
| Operations | Erstellt | Systemhandbuch, Betriebshandbuch |
| Operations | Verwendet | arc42 (Verteilungssicht) |

### Artefakte ↔ Artefakte

| Von | Zu | Verknüpfung |
|-----|-----|-------------|
| Vision | Anforderungen | "leitet sich ab" |
| Anforderungen | User Stories | "wird zu" |
| User Stories | Feature-Spezifikation | "basiert auf" |
| Feature-Spezifikation | ADRs | "referenziert" |
| Feature-Spezifikation | arc42 | "folgt Leitplanken" |
| Feature-Spezifikation | Tasks | "wird umgesetzt durch" |
| Code | arc42 | "dokumentiert in" |
| Code | Systemhandbuch | "beschrieben in" |

---

## RAG-Optimierung für MS 365 Copilot

### Das Problem mit RAG-Systemen

**RAG-Chunking:**
- Lange Dokumente werden in Abschnitte (Chunks) zerlegt
- Jeder Chunk wird einzeln in die Vektordatenbank indexiert
- Verschiedene Chunks können unter verschiedenen Keywords landen

**Beispiel:**
- Ein langes arc42-Dokument (600+ Zeilen) wird in mehrere Chunks zerlegt:
  - Chunk 1 (Kapitel 1-3): Keywords → "Einführung", "Ziele", "Randbedingungen"
  - Chunk 2 (Kapitel 5): Keywords → "Bausteinsicht", "Komponenten", "Modularisierung"
  - Chunk 3 (Kapitel 9): Keywords → "Architekturentscheidungen", "ADRs", "Entscheidungen"

**Konsequenz:**
- Suche nach "arc42" findet vielleicht nur einen Chunk, nicht das ganze Dokument
- Verschiedene Chunks haben verschiedene Keyword-Schwerpunkte
- Verknüpfungen zwischen Dokumenten müssen über Keywords im Text hergestellt werden

### Unterschied: Links vs. Keywords

**Cursor.AI (aktuell):**
```markdown
Siehe auch: [arc42 Template](./artefakte/architektur_arc42.md)
```
→ Funktioniert: Direkter Dateisystem-Zugriff, Link kann verfolgt werden

**MS 365 Copilot (RAG):**
```markdown
Siehe auch: [arc42 Template](./artefakte/architektur_arc42.md)
```
→ Funktioniert nicht: RAG kann Link nicht verfolgen, muss Dokument über Keywords finden

**Lösung für MS 365:**
```markdown
Für die Architektur-Dokumentation verwende das arc42 Template. 
Das arc42 Template bietet eine strukturierte Gliederung für Softwarearchitekturen 
mit Kapiteln zu Bausteinsicht, Laufzeitsicht, Verteilungssicht und Architekturentscheidungen.
```
→ Funktioniert: Keywords "arc42", "Architektur-Dokumentation", "Bausteinsicht" helfen RAG, das richtige Dokument zu finden

### Empfehlungen für RAG-Optimierung

**1. Keyword-reiche Verknüpfungen statt Links:**

**Statt:**
```markdown
Du verwendest die Arc42-Struktur für die Gesamtarchitektur.
Siehe auch: [arc42 Template](./artefakte/architektur_arc42.md)
```

**Besser:**
```markdown
Du verwendest die Arc42-Struktur für die Gesamtarchitektur. 
Das arc42 Template bietet eine strukturierte Gliederung für Softwarearchitekturen 
mit Kapiteln zu Bausteinsicht, Laufzeitsicht, Verteilungssicht, 
Architekturentscheidungen und Querschnittlichen Konzepten.
```

**2. Explizite Keyword-Erwähnungen:**

**Statt:**
```markdown
Du dokumentierst Architekturentscheidungen als ADRs.
Siehe auch: [ADR Template](./artefakte/architecture-decision-record.md)
```

**Besser:**
```markdown
Du dokumentierst Architekturentscheidungen als Architecture Decision Records (ADRs). 
ADRs dokumentieren wichtige technische Entscheidungen mit Context, 
erwogenen Optionen, Entscheidung und Konsequenzen. 
Das ADR Format hilft dabei, Architekturentscheidungen nachvollziehbar zu machen.
```

**3. Mehrfache Keyword-Erwähnungen:**

Da RAG-Chunking Dokumente zerlegt, sollten wichtige Keywords mehrfach erwähnt werden:

**Beispiel:**
```markdown
## Architektur nach Arc42

Du strukturierst die Architektur nach Arc42. 
Das arc42 Template ist ein bewährtes Template zur Dokumentation von Softwarearchitekturen.
Arc42 bietet eine strukturierte Gliederung mit 12 Kapiteln.
Die wichtigsten arc42 Kapitel sind: Kontextabgrenzung, Bausteinsicht, 
Laufzeitsicht, Verteilungssicht und Architekturentscheidungen.
```

**4. Kontext-reiche Beschreibungen:**

**Statt:**
```markdown
Siehe Feature-Spezifikation.
```

**Besser:**
```markdown
Die Feature-Spezifikation beschreibt die technische Umsetzung eines Features 
basierend auf einer User Story. Feature-Spezifikationen enthalten technische 
Anforderungen, Architektur-Leitplanken und technische Akzeptanzkriterien.
```

## Verbesserungspotenziale

### Was bereits gut funktioniert:

✅ **Semantische Verknüpfungen:** Cursor.AI kann Beziehungen verstehen
✅ **Strukturelle Verknüpfungen:** Verzeichnisstruktur ist klar
✅ **Namentliche Erwähnungen:** Konsistente Begriffe werden verwendet
✅ **Platzhalter-System:** Zentrale Definition ermöglicht Änderungen

### Was verbessert werden könnte:

🔧 **RAG-Optimierung für MS 365 Copilot:** 
- Aktuell: Links funktionieren nur für Cursor.AI
- Verbesserung: Keyword-reiche Verknüpfungen für RAG-Systeme
- Problem: RAG-Chunking zerlegt lange Dokumente, Keywords müssen mehrfach erwähnt werden

🔧 **Explizite Verknüpfungen:** 
- Aktuell: Meist implizit durch Beschreibungen
- Verbesserung: Explizite Verknüpfungsfelder in Artefakten

🔧 **Verknüpfungs-IDs:**
- Aktuell: Namen und Links
- Verbesserung: Eindeutige IDs (z.B. `ROLE:PO`, `ARTEFACT:FEATURE-SPEC`)

🔧 **Verknüpfungs-Typen:**
- Aktuell: Freitext-Beschreibungen
- Verbesserung: Standardisierte Verknüpfungstypen (erstellt, verwendet, referenziert, basiert auf)

🔧 **Workflow-Dokumentation:**
- Aktuell: Beschreibungen in verschiedenen Dateien
- Verbesserung: Zentrale Workflow-Dokumentation mit expliziten Schritten

---

## Empfehlungen für zukünftige Erweiterungen

### 1. Explizite Verknüpfungsfelder

Jedes Artefakt könnte ein "Verknüpfungen"-Feld haben:

```markdown
## Verknüpfungen

**Erstellt von:** ROLE:PO
**Basiert auf:** ARTEFACT:USER-STORY:US-001
**Referenziert:** ARTEFACT:ADR:ADR-002
**Wird verwendet von:** ROLE:DEV-TEAM
```

### 2. Verknüpfungs-Typen

Standardisierte Verknüpfungstypen:
- `erstellt` - Wer erstellt was
- `verwendet` - Wer verwendet was
- `basiert_auf` - Was basiert auf was
- `referenziert` - Was referenziert was
- `wird_zu` - Was wird zu was
- `folgt` - Was folgt was

### 3. Workflow-Dokumentation

Zentrale Workflow-Dateien:
- `workflows/user-story-to-feature.md`
- `workflows/feature-to-tasks.md`
- `workflows/requirements-to-user-stories.md`

### 4. Fähigkeiten (Skills)

Zukünftige Struktur:
```
prompt/
├── rollen/
├── artefakte/
├── workflows/
├── skills/          # Neue Komponente
│   ├── user-story-writing.md
│   ├── architecture-review.md
│   └── test-planning.md
└── doc/
```

---

## Zusammenfassung

**Aktueller Stand:**
- ✅ Verknüpfungen funktionieren durch semantische Suche
- ✅ Cursor.AI kann Zusammenhänge verstehen
- ✅ Strukturelle Verknüpfungen sind klar

**Wie Cursor.AI aktuell arbeitet:**
1. Semantische Suche findet relevante Informationen
2. Exakte Suche findet spezifische Erwähnungen
3. Datei-Links werden verfolgt
4. Kontext wird aus mehreren Dateien zusammengeführt

**Verbesserungspotenzial:**
- Explizitere Verknüpfungen würden die Suche verbessern
- Standardisierte Verknüpfungstypen würden Konsistenz erhöhen
- Zentrale Workflow-Dokumentation würde Klarheit schaffen

Die Bibliothek funktioniert bereits gut mit Cursor.AI, aber explizitere Verknüpfungen würden die Nutzung noch verbessern.
