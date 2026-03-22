# Prompt-Bibliothek

Diese Bibliothek enthält strukturierte Prompts für verschiedene Anwendungsfälle.

## 📁 Struktur

```
/prompt/
├── README.md                    # Diese Datei
├── _koordinator.md              # Hauptrolle: Koordinator aller Rollen
├── rollen/                      # Rollen-Prompts
│   ├── prompt-coach.md          # Prompt-Coach
│   ├── product-owner.md         # Product Owner
│   ├── software-architect.md    # Softwarearchitekt
│   ├── dev-team.md              # Dev-Team
│   ├── operations.md            # Operativer Betrieb
│   └── clean-code-coach.md      # Clean Code Coach
├── artefakte/                   # Artefakte und Vorlagen
│   ├── architecture-decision-canvas.md
│   ├── architecture-decision-record.md
│   ├── architecture-inception-canvas.md
│   ├── anforderungsmanagement.md
│   ├── architektur_arc42.md
│   ├── system-context-canvas.md
│   ├── domain-bounded-context-canvas.md
│   ├── architecture-building-blocks-canvas.md
│   ├── integration-canvas.md
│   ├── deployment-operations-canvas.md
│   ├── evolution-roadmap-canvas.md
│   ├── quality-attribute-canvas.md
│   ├── risk-technical-debt-canvas.md
│   ├── architecture-communication-canvas.md
│   ├── feature-spezifikation.md
│   ├── java-projekt-struktur.md
│   ├── nutzerhandbuch.md
│   ├── systemhandbuch.md
│   ├── tradeoff-canvas-produkt.md
│   └── tradeoff-canvas-technik.md
└── doc/                         # Bibliotheks-Dokumentation
    ├── artefakt-zusammenhaenge.md            # Übersicht: Architektur vs. Delivery
    ├── artefakt-zusammenhaenge-architektur.md
    └── artefakt-zusammenhaenge-delivery.md   # Lieferkette & Tests (kompakt)
```

## 🎯 Verwendung

### Koordinator - Hauptrolle (Empfohlen)

Der `_koordinator.md` ist die Hauptrolle, die alle anderen Rollen koordiniert.

**Funktionen:**
- Kennt alle Rollen im Verzeichnis `./rollen`
- Interagiert direkt mit dem Nutzer
- Berät den Nutzer und schlägt die passende Rolle vor
- Macht jeden Rollenwechsel explizit und meldet ihn in der Konsole

**Verwendung:**
1. Den kompletten Inhalt von `_koordinator.md` kopieren
2. Als Startprompt in die KI-Session einfügen
3. Der Koordinator führt dich zu den passenden Rollen

**Beispiel:**
```
🔄 Ich agiere nun in der Rolle: prompt-coach
```

### Verfügbare Rollen

#### Prompt-Coach (`rollen/prompt-coach.md`)
- Entwicklung, Bewertung und Verbesserung von Prompts
- Strukturierung nach W-Fragen-Systematik
- Qualitätsprüfung und Kompaktheits-Check

#### Product Owner (`rollen/product-owner.md`)
- Visionen entwickeln und Ideen sammeln
- Product Backlog verwalten und priorisieren
- User Stories erstellen und strukturieren
- Anforderungen aus Visionen ableiten
- Produkt-Tradeoffs mit dem Tradeoff Canvas Produkt strukturieren

#### Softwarearchitekt (`rollen/software-architect.md`)
- Neue Vorhaben mit dem Architecture Inception Canvas strukturiert einordnen
- Systemgrenzen und Umfeld mit dem System Context Canvas klären
- Fachliche Grenzen mit dem Domain / Bounded Context Canvas (DDD) strukturieren
- Innere Systemstruktur mit dem Architecture Building Blocks Canvas entwerfen
- Integration mit dem Integration Canvas analysieren und strukturieren
- Deployment und Betrieb mit dem Deployment / Operations Canvas strukturieren
- Qualitätsanforderungen mit dem Quality Attribute Canvas priorisieren und als Szenarien konkretisieren
- Risiken und technische Schuld mit dem Risk / Technical Debt Canvas erfassen und priorisieren
- Architektur-Evolution mit dem Evolution / Roadmap Canvas schrittweise planen
- Architektur mit dem Architecture Communication Canvas zielgruppengerecht vermitteln
- Architektur nach Arc42 strukturieren und dokumentieren
- Software Requirements Specifications (SRS) erstellen
- Architecture Decision Records (ADR) dokumentieren
- Architekturentscheidungen mit dem Architecture Decision Canvas strukturieren (vor dem ADR)
- Technische Tradeoffs mit dem Tradeoff Canvas Technik strukturieren
- Technische Konsistenz und Qualität sicherstellen

#### Dev-Team (`rollen/dev-team.md`)
- Code-Entwicklung nach Architektur-Vorgaben
- Strukturierte Code-Dokumentation
- Pull Request-Prüfbarkeit sicherstellen
- Benutzerhandbuch pflegen

#### Operativer Betrieb (`rollen/operations.md`)
- Betrieb überwachen und steuern
- Deployment und operative Landschaft mit dem Deployment / Operations Canvas erfassen (mit Architektur)
- Störungen frühzeitig erkennen
- Probleme systematisch analysieren
- Operationen (Start/Stop/Rollout) durchführen

#### Clean Code Coach (`rollen/clean-code-coach.md`)
- Code analysieren und Verbesserungspotenziale identifizieren
- Clean Code Prinzipien vermitteln (SOLID, DRY, KISS, etc.)
- Code-Reviews durchführen und Feedback geben
- Refactoring-Strategien vorschlagen

### Einzelne Rollen verwenden

Du kannst auch einzelne Rollen direkt verwenden:

1. Den kompletten Inhalt der gewünschten Rolle aus `rollen/[rolle].md` kopieren
2. Als Startprompt in die KI-Session einfügen
3. Die KI arbeitet dann nach den definierten Regeln und Strukturen

## 📋 Artefakte

Das Verzeichnis `artefakte/` enthält Vorlagen und Strukturen für verschiedene Dokumentations-Artefakte:

- **architecture-decision-canvas.md**: Hilfsvorlage für strukturierte Architekturentscheidungen (Optionen, Kriterien, Bewertung, Konsequenzen; typisch vor dem ADR)
- **architecture-decision-record.md**: Vorlage für Architecture Decision Records (ADR)
- **architecture-inception-canvas.md**: Hilfsvorlage für frühes gemeinsames Verständnis zu Vorhaben (Ziele, Stakeholder, Problem, Systemidee, Randbedingungen)
- **system-context-canvas.md**: Hilfsvorlage für Systemkontext (Grenzen, Akteure, Nachbarsysteme, Schnittstellen, Datenflüsse)
- **domain-bounded-context-canvas.md**: Hilfsvorlage für DDD — Bounded Contexts, Verantwortlichkeiten, Kontextbeziehungen, Sprachgrenzen
- **architecture-building-blocks-canvas.md**: Hilfsvorlage für Bausteine, Schnittstellen, Daten-Ownership und Hotspots (arc42 / C4)
- **integration-canvas.md**: Hilfsvorlage für Integration — Datenflüsse, Kopplung, Resilienz, Risiken
- **deployment-operations-canvas.md**: Hilfsvorlage für Deployment, Betrieb, Skalierung, Monitoring, Resilienz
- **evolution-roadmap-canvas.md**: Hilfsvorlage für Architektur-Evolution — Roadmap, Migration, Zwischenstufen
- **quality-attribute-canvas.md**: Hilfsvorlage für Qualitätsattribute (NFR) — Priorisierung, Szenarien, Konflikte
- **risk-technical-debt-canvas.md**: Hilfsvorlage für Risiken und technische Schuld — Bewertung, Maßnahmen, Priorisierung
- **architecture-communication-canvas.md**: Hilfsvorlage für Architektur-Kommunikation — Zielgruppen, Kernbotschaften, Mittel
- **tradeoff-canvas-produkt.md**: Hilfsvorlage für Produkt-Prioritäten und Abwägungen (Scope, Zeit, Wert, Risiko)
- **tradeoff-canvas-technik.md**: Hilfsvorlage für technische Qualitäts- und Architektur-Tradeoffs (Vorstufe zu ADR)
- **architektur_arc42.md**: Struktur für Arc42-Architektur-Dokumentation
- **java-projekt-struktur.md**: Struktur für Java-Projekte
- **nutzerhandbuch.md**: Vorlage für Benutzerhandbücher
- **systemhandbuch.md**: Vorlage für Systemhandbücher

Diese Artefakte können als Vorlagen verwendet oder als Referenz für die Dokumentationsstruktur dienen.

## 📚 Bibliotheks-Dokumentation

Das Verzeichnis `doc/` enthält Dokumentation über die Bibliothek selbst:

- **artefakt-zusammenhaenge.md**: Übersicht mit Links zu Architektur- und Delivery-Teil
- **artefakt-zusammenhaenge-architektur.md**: arc42, Canvas, Entscheidungsketten, Metamodell-Visualisierung
- **artefakt-zusammenhaenge-delivery.md**: Lieferkette (REQ → Story → Feature → Tasks → Code), Tests, Rückverfolgbarkeit (kompakt)

## 📝 Prompt-Entwicklung

### Qualitätskriterien

Ein guter Prompt sollte:
- ✅ Eindeutig sein
- ✅ Kurz und verständlich sein
- ✅ Keine unnötigen Adjektive oder Prosa enthalten
- ✅ Klare Ziele definieren
- ✅ W-Fragen beantworten (Wer? Warum? Wie? Was? Wann? Wo?)
- ✅ Rollen, Kontext und Grenzen benennen
- ✅ Klare Handlungen oder Anforderungen vorgeben
- ✅ Spätere Fehler vermeiden
- ✅ Für Menschen und KI gleichermaßen lesbar sein

### Entwicklungsprozess

1. **Verständnisfragen stellen** - Was soll der Prompt erreichen?
2. **Ziel definieren** - Klare Zielsetzung formulieren
3. **Promptstruktur erzeugen** - W-Fragen beantworten
4. **Promptvorschlag erstellen** - Erste Version formulieren
5. **Kompaktheits-Check durchführen** - Auf Wesentliches reduzieren
6. **Zustimmung einholen oder nachbessern** - Iterative Verbesserung

## 🔄 Erweiterung der Bibliothek

Neue Prompts können hinzugefügt werden:
- Klare, beschreibende Dateinamen verwenden
- Strukturierte Formatierung (Markdown)
- Dokumentation der Verwendung im README ergänzen
- Bei neuen Rollen: Koordinator aktualisieren

## 📚 Weitere Ressourcen

- [Prompt Engineering Guide](https://platform.openai.com/docs/guides/prompt-engineering)
- [Best Practices für Prompts](https://help.openai.com/en/articles/6654000-best-practices-for-prompt-engineering-with-openai-api)
