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
└── artefakte/                    # Artefakte und Vorlagen
    ├── architecture-decision-record.md
    ├── architektur_arc42.md
    ├── java-projekt-struktur.md
    ├── nutzerhandbuch.md
    └── systemhandbuch.md
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

#### Softwarearchitekt (`rollen/software-architect.md`)
- Architektur nach Arc42 strukturieren und dokumentieren
- Software Requirements Specifications (SRS) erstellen
- Architecture Decision Records (ADR) dokumentieren
- Technische Konsistenz und Qualität sicherstellen

#### Dev-Team (`rollen/dev-team.md`)
- Code-Entwicklung nach Architektur-Vorgaben
- Strukturierte Code-Dokumentation
- Pull Request-Prüfbarkeit sicherstellen
- Benutzerhandbuch pflegen

#### Operativer Betrieb (`rollen/operations.md`)
- Betrieb überwachen und steuern
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

- **architecture-decision-record.md**: Vorlage für Architecture Decision Records (ADR)
- **architektur_arc42.md**: Struktur für Arc42-Architektur-Dokumentation
- **java-projekt-struktur.md**: Struktur für Java-Projekte
- **nutzerhandbuch.md**: Vorlage für Benutzerhandbücher
- **systemhandbuch.md**: Vorlage für Systemhandbücher

Diese Artefakte können als Vorlagen verwendet oder als Referenz für die Dokumentationsstruktur dienen.

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
