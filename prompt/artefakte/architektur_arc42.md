---
typ: artefakt
name: Architekturdokumentation nach arc42
kontext: Template zur Dokumentation von Softwarearchitekturen nach arc42-Standard
rollen:
  - Softwarearchitekt
artefakte:
  - ADR
  - Architecture Communication Canvas
  - Feature-Spezifikation
  - SRS
workflows: []
---

# Artefakt: Architekturdokumentation nach arc42

## Über arc42

arc42 ist ein bewährtes und praxisorientiertes Template zur Dokumentation und Kommunikation von Softwarearchitekturen. Es bietet eine strukturierte Gliederung, die es ermöglicht, alle relevanten Aspekte einer Architektur systematisch zu erfassen und zu dokumentieren.

**Kernprinzipien:**
- Flexibel und anpassbar an spezifische Bedürfnisse
- Unterstützt beliebige Technologien und Werkzeuge
- Prozessagnostisch (geeignet für agile und traditionelle Ansätze)
- Open Source und kostenfrei nutzbar

**Kern der Architekturdokumentation:**
- Kontextabgrenzung (Kapitel 3)
- Drei Sichten: Bausteinsicht, Laufzeitsicht, Verteilungssicht (Kapitel 5-7)
- Querschnittliche Konzepte (Kapitel 8)

Die restlichen Kapitel ergänzen die Dokumentation mit Zielen, Entscheidungen, Risiken und einem gemeinsamen Glossar.

---

## Über dieses Artefakt

Dieses Artefakt ist ein Template für die Erstellung einer arc42 Architekturdokumentation.

**Wie verwende ich dieses Artefakt?**

Dieses Artefakt ist ein **Template/Ablageort** für deine Architekturdokumentation. Du beginnst mit den Informationen, die du bereits hast, und arbeitest dich iterativ vor.

1. **Kopiere die Struktur:** Nutze dieses Template als Vorlage für deine Architekturdokumentation
2. **Beginne mit bekannten Informationen:** Starte mit den Kapiteln, für die du bereits Informationen hast
3. **Nicht alle Kapitel sind Pflicht:** Fülle nur die Kapitel aus, die für dein Projekt relevant sind
4. **Arbeite iterativ:** Erweitere die Dokumentation schrittweise, wenn neue Informationen verfügbar sind

**Für iterative Vorgehensweise:** Siehe die Softwarearchitekt-Rolle für Details zur kontinuierlichen Dokumentation und agilen Arbeitsweise.

**Für wen ist dieses Artefakt?**

- Softwarearchitekten, die eine Architektur dokumentieren
- Entwicklerteams, die ihre Architektur strukturiert erfassen wollen
- Projekte, die eine vollständige Architekturdokumentation benötigen

---

## Dokumentationsstruktur: Modulare Kapitel

**Wichtig:** Die arc42 Architekturdokumentation kann als einzelne Datei oder als modulare Struktur mit separaten Kapiteldateien organisiert werden.

### Modulare Struktur (empfohlen)

**Prinzip:** Jedes Hauptkapitel wird in eine eigene Markdown-Datei gelegt. Dies verbessert:
- **Wartbarkeit:** Einzelne Kapitel können unabhängig bearbeitet werden
- **Übersichtlichkeit:** Kleinere Dateien sind leichter zu navigieren
- **Kollaboration:** Mehrere Personen können parallel an verschiedenen Kapiteln arbeiten
- **Versionierung:** Änderungen sind besser nachvollziehbar

**Verzeichnisstruktur:**
```
architektur/
├── README.md                    # Übersicht und Navigation zu allen Kapiteln
├── 01-einfuehrung.md            # Kapitel 1: Einführung und Ziele
├── 02-randbedingungen.md        # Kapitel 2: Randbedingungen
├── 03-kontext.md                # Kapitel 3: Kontextabgrenzung
├── 04-loesungsstrategie.md      # Kapitel 4: Lösungsstrategie
├── 05-bausteinsicht.md          # Kapitel 5: Bausteinsicht
├── 06-laufzeitsicht.md          # Kapitel 6: Laufzeitsicht
├── 07-verteilungssicht.md       # Kapitel 7: Verteilungssicht
├── 08-querschnittliche-konzepte.md  # Kapitel 8: Querschnittliche Konzepte
├── 09-architekturentscheidungen.md  # Kapitel 9: Architekturentscheidungen
├── 10-qualitaetsszenarien.md    # Kapitel 10: Qualitätsanforderungen
├── 11-risiken.md                # Kapitel 11: Risiken und technische Schulden
└── 12-glossar.md                # Kapitel 12: Glossar
```

**Benennungskonvention:**
- Dateinamen: `[Nummer]-[kapitelname].md` (z.B. `03-kontext.md`)
- Kleingeschrieben, Bindestriche statt Leerzeichen
- Nummerierung entspricht arc42-Kapitelnummern

**Verweise zwischen Kapiteln:**
- Verwende Markdown-Hyperlinks für Verweise zwischen Kapiteln
- Format: `[Link-Text]([dateiname].md#abschnitt)` oder `[Link-Text]([dateiname].md)`
- Beispiel: `Siehe [Kapitel 5: Bausteinsicht](05-bausteinsicht.md) für Details zu den Komponenten.`
- Beispiel: `Die Qualitätsziele werden in [Kapitel 1.2](01-einfuehrung.md#12-qualitaetsziele) definiert.`

**README.md als Navigation:**
Die `README.md` sollte eine Übersicht aller Kapitel mit Links enthalten:
```markdown
# Architekturdokumentation: [Projektname]

## Inhaltsverzeichnis

1. [Einführung und Ziele](01-einfuehrung.md)
2. [Randbedingungen](02-randbedingungen.md)
3. [Kontextabgrenzung](03-kontext.md)
4. [Lösungsstrategie](04-loesungsstrategie.md)
5. [Bausteinsicht](05-bausteinsicht.md)
6. [Laufzeitsicht](06-laufzeitsicht.md)
7. [Verteilungssicht](07-verteilungssicht.md)
8. [Querschnittliche Konzepte](08-querschnittliche-konzepte.md)
9. [Architekturentscheidungen](09-architekturentscheidungen.md)
10. [Qualitätsanforderungen](10-qualitaetsszenarien.md)
11. [Risiken und technische Schulden](11-risiken.md)
12. [Glossar](12-glossar.md)
```

### Einzelne Datei (Alternative)

Für kleine Projekte oder initiale Dokumentation kann auch eine einzelne Datei `architektur.md` verwendet werden. Diese kann später in die modulare Struktur aufgeteilt werden.

**Wachstumsprinzip:**
- **Start:** Einzelne Datei `architektur.md` mit ersten Kapiteln
- **Bei Bedarf:** Aufteilen in modulare Struktur `architektur/` mit separaten Kapiteldateien
- **Entscheidung:** Basierend auf Größe, Komplexität und Teamgröße

### Empfehlung für KI-gestützte Dokumentation

**Bei modularem Ansatz:**
- Erstelle nur die Kapiteldateien, für die bereits Informationen vorhanden sind
- Verwende Hyperlinks für Verweise zwischen Kapiteln (auch wenn Zielkapitel noch nicht existiert)
- Erstelle eine `README.md` mit Navigation zu allen existierenden Kapiteln
- Ergänze neue Kapiteldateien iterativ, wenn Informationen verfügbar werden

**Beispiel-Workflow:**
1. Starte mit `README.md` und ersten Kapiteln (z.B. `01-einfuehrung.md`, `03-kontext.md`)
2. Erstelle weitere Kapiteldateien, wenn Informationen verfügbar sind
3. Aktualisiere `README.md` mit Links zu neuen Kapiteln
4. Verwende Hyperlinks in Kapiteln für Verweise (z.B. `Siehe [Kapitel 5](05-bausteinsicht.md) für Details`)

---

## Quick-Start-Guide: Erste Schritte mit arc42

**Wichtig:** Dieses Artefakt ist ein Template/Ablageort. Die iterative Vorgehensweise kommt aus deiner Rolle (siehe Softwarearchitekt-Rolle für Details zur agilen Dokumentation).

### Schritt 1: Beginne mit bekannten Informationen

Starte nicht mit leeren Kapiteln, sondern mit dem, was du bereits weißt:

- **Du hast bereits eine Vision?** → Beginne mit Kapitel 1.1 (Anforderungen) und Kapitel 3 (Systemkontext)
- **Du kennst die Hauptkomponenten?** → Beginne mit Kapitel 5 (Bausteinsicht, Level 1)
- **Du hast bereits technische Entscheidungen getroffen?** → Beginne mit Kapitel 9 (Architekturentscheidungen) oder dokumentiere sie als ADRs
- **Du kennst die Qualitätsziele?** → Beginne mit Kapitel 1.2 (Qualitätsziele)

**Prinzip:** Lege die Informationen dort ab, wo sie in der arc42-Struktur hingehören. Du musst nicht alle Kapitel sofort ausfüllen.

### Schritt 2: Nicht alle Kapitel sind Pflicht

arc42 ist flexibel - nicht alle Kapitel müssen für jedes Projekt ausgefüllt werden:

**Kern-Kapitel (meist wichtig):**
- Kapitel 3: Kontextabgrenzung
- Kapitel 5: Bausteinsicht
- Kapitel 6: Laufzeitsicht (mindestens ein wichtiges Szenario)

**Ergänzende Kapitel (nach Bedarf):**
- Kapitel 1: Einführung und Ziele (wenn Qualitätsziele wichtig sind)
- Kapitel 4: Lösungsstrategie (wenn strategische Entscheidungen wichtig sind)
- Kapitel 7: Verteilungssicht (wenn Deployment relevant ist)
- Kapitel 8: Querschnittliche Konzepte (wenn übergreifende Konzepte wichtig sind)
- Kapitel 9: Architekturentscheidungen (kann auch als separate ADRs dokumentiert werden)
- Kapitel 10: Qualitätsszenarien (wenn Qualitätsvalidierung wichtig ist)
- Kapitel 11: Risiken (wenn Risikomanagement wichtig ist)
- Kapitel 12: Glossar (wenn viele Fachbegriffe verwendet werden)

**Prinzip:** Fülle nur die Kapitel aus, die für dein Projekt relevant sind. Ein MVP kann mit 3-4 Kapiteln starten.

### Schritt 3: Arbeite dich iterativ vor

Wenn du neue Informationen hast, ergänze die entsprechenden Kapitel:

- **Neues Feature implementiert?** → Aktualisiere Kapitel 5 (Bausteinsicht) und Kapitel 6 (Laufzeitsicht)
- **Neue technische Entscheidung?** → Ergänze Kapitel 9 oder erstelle ein ADR
- **Neue Qualitätsanforderung?** → Aktualisiere Kapitel 1.2 (Qualitätsziele) und Kapitel 10 (Qualitätsszenarien)

**Prinzip:** Die Dokumentation wächst mit dem Projekt. Du musst nicht alles sofort perfekt dokumentieren.

### Schritt 4: Nutze die empfohlene Reihenfolge als Orientierung

Die empfohlene Reihenfolge (siehe Abschnitt "Empfohlene Reihenfolge beim Ausfüllen" weiter unten) hilft dir, Abhängigkeiten zu berücksichtigen. Aber: Beginne trotzdem mit dem, was du bereits weißt, auch wenn es nicht der empfohlenen Reihenfolge entspricht.

**Beispiel:** Du kennst bereits die Hauptkomponenten, aber noch nicht die Qualitätsziele? → Beginne mit Kapitel 5 (Bausteinsicht) und ergänze später Kapitel 1.2 (Qualitätsziele).

---

## Traceability: Nachvollziehbarkeit von Entscheidungen

**Zweck:** Dieser Abschnitt beschreibt, wie Traceability in der arc42 Architekturdokumentation dokumentiert wird. Traceability macht Entscheidungen nachvollziehbar und zeigt, wie die verschiedenen Kapitel zusammenhängen.

**Metapher:** arc42 ist wie ein Schrank mit Ablagefächern - jedes Fach (Kapitel) enthält bestimmte Informationen. Die Traceability zeigt, wie die Fächer zusammenhängen und wie Entscheidungen von einem Fach zum anderen nachvollzogen werden können.

**Warum Traceability wichtig ist:**
- **Nachvollziehbarkeit:** Leser können verstehen, warum bestimmte Entscheidungen getroffen wurden
- **Konsistenz:** Sichert, dass alle Kapitel konsistent sind und aufeinander aufbauen
- **Wartbarkeit:** Erleichtert das Aktualisieren der Dokumentation, da Abhängigkeiten klar sind
- **Validierung:** Hilft zu prüfen, ob alle Qualitätsziele erfüllt werden

**Wo wird Traceability dokumentiert?**

In einem arc42 Architekturdokument sollte Traceability an folgenden Stellen dokumentiert werden:

1. **In jedem Kapitel:** Jedes Kapitel dokumentiert seine Abhängigkeiten zu anderen Kapiteln (siehe Abschnitt "Abhängigkeiten" in jedem Kapitel)
2. **Traceability-Matrizen:** Systematische Übersicht wichtiger Entscheidungen (z.B. Qualitätsziele) - wird im Zieldokument erstellt
3. **Verweise zwischen Kapiteln:** Explizite Verweise zeigen Zusammenhänge (z.B. "Siehe Kapitel 4 für Lösungsstrategie")

**Hinweis:** Die folgenden Abschnitte zeigen die Struktur und Platzhalter für Traceability-Matrizen. Diese werden im Zieldokument mit den tatsächlichen Qualitätszielen, ADRs und Bausteinen ausgefüllt.

---

## Dokumentationsbausteine und deren Abhängigkeiten

Die arc42 Architekturdokumentation besteht aus verschiedenen Dokumentationsbausteinen, die inhaltlich den arc42-Kapiteln entsprechen. Die Bausteine haben inhaltliche Abhängigkeiten (Input/Begründung/Verfeinerung), die bei der Erstellung der Dokumentation beachtet werden sollten.

**Hinweis:** Für eine systematische Übersicht der Traceability siehe Abschnitt "Traceability: Nachvollziehbarkeit von Entscheidungen" weiter oben.

### Mapping der Dokumentationsbausteine auf arc42-Kapitel

| Dokumentationsbaustein      | arc42 Kapitel                    |
| --------------------------- | -------------------------------- |
| Produktkarton               | 1. Einführung und Ziele (Kontext) |
| Qualitätsziele              | 1. Einführung und Ziele          |
| Persona                     | 1. Einführung und Ziele          |
| Übergreifendes Konzept      | 8. Querschnittliche Konzepte     |
| Randbedingungen             | 2. Randbedingungen               |
| Systemkontext               | 3. Kontextabgrenzung             |
| Lösungsstrategie            | 4. Lösungsstrategie              |
| Architekturentscheidung     | 9. Architekturentscheidungen     |
| Bausteinsicht               | 5. Bausteinsicht                 |
| Laufzeitsicht               | 6. Laufzeitsicht                 |
| Verteilungssicht            | 7. Verteilungssicht              |
| Qualitätsszenarien          | 10. Qualitätsanforderungen       |
| Technische Risiken          | 11. Risiken                      |
| Schnittstellenbeschreibung  | 5. Bausteinsicht (primär)         |
| Glossar                     | 12. Glossar                      |

### Abhängigkeiten zwischen Dokumentationsbausteinen

Die folgenden Abhängigkeiten zeigen, wie die Dokumentationsbausteine aufeinander aufbauen und sich gegenseitig beeinflussen. Diese Abhängigkeiten sollten bei der Erstellung der arc42 Architekturdokumentation berücksichtigt werden.

**Kapitel 1 - Einführung und Ziele:**

- **Produktkarton:** Der Produktkarton (Vision/Zielbild) liefert Kontext für Anforderungen (Kapitel 1.1). 
  Anforderungen wiederum liefern Kontext für den Systemkontext (Kapitel 3) und beeinflussen Qualitätsziele (1.2) und Personas (1.3).

- **Persona:** Personas leiten sich aus Anforderungen (Kapitel 1.1) ab. 
  Personas beeinflussen die Qualitätsziele (1.2). 
  Personas beeinflussen Szenarien in den Qualitätsszenarien (Kapitel 10). 
  Personas sind Input für die Laufzeitsicht (Kapitel 6).

- **Qualitätsziele:** Qualitätsziele werden aus Anforderungen (Kapitel 1.1) abgeleitet. 
  Qualitätsziele werden aus Personas (1.3) abgeleitet. 
  Qualitätsziele werden durch Qualitätsszenarien (Kapitel 10) konkretisiert. 
  Qualitätsziele treiben die Lösungsstrategie (Kapitel 4). 
  Qualitätsziele beeinflussen Architekturentscheidungen (Kapitel 9).

**Kapitel 2 - Randbedingungen:**

- **Randbedingungen:** Randbedingungen beeinflussen die Lösungsstrategie. Randbedingungen beeinflussen Architekturentscheidungen. Randbedingungen beeinflussen übergreifende Konzepte (Kapitel 8). Randbedingungen sind Quelle für technische Risiken.

**Hinweis:** Übergreifende Konzepte gehören zu Kapitel 8 (Querschnittliche Konzepte), nicht zu Kapitel 2. 
Randbedingungen können jedoch die Grundlage für übergreifende Konzepte bilden.

**Kapitel 3 - Kontextabgrenzung:**

- **Systemkontext:** Der Systemkontext wird aus Anforderungen (Kapitel 1.1) abgeleitet. 
  Der Systemkontext beeinflusst die Schnittstellenbeschreibung (Kapitel 5). 
  Der Systemkontext beeinflusst die Bausteinsicht (Kapitel 5). 
  Der Systemkontext beeinflusst die Verteilungssicht (Kapitel 7). 
  Der Systemkontext ist Referenz für die Laufzeitsicht (Kapitel 6).

**Kapitel 4 - Lösungsstrategie:**

- **Lösungsstrategie:** Die Lösungsstrategie basiert auf Qualitätszielen. Die Lösungsstrategie basiert auf Randbedingungen. Die Lösungsstrategie basiert auf übergreifenden Konzepten. Die Lösungsstrategie berücksichtigt technische Risiken. Die Lösungsstrategie wird durch Architekturentscheidungen konkretisiert. Die Lösungsstrategie leitet Struktur für die Bausteinsicht. Die Lösungsstrategie leitet Struktur für die Verteilungssicht. Die Lösungsstrategie leitet Struktur für die Laufzeitsicht.

**Kapitel 5 - Bausteinsicht:**

- **Bausteinsicht:** Die Bausteinsicht wird aus der Lösungsstrategie abgeleitet. Die Bausteinsicht wird durch übergreifende Konzepte beeinflusst. Die Bausteinsicht berücksichtigt Qualitätsszenarien. Die Bausteinsicht nutzt Schnittstellenbeschreibungen. Die Bausteinsicht wird von Architekturentscheidungen beeinflusst. Die Bausteinsicht ist Referenz für die Laufzeitsicht.

- **Schnittstellenbeschreibung:** Schnittstellenbeschreibungen basieren auf dem Systemkontext. Schnittstellenbeschreibungen konkretisieren die Bausteinsicht. Schnittstellenbeschreibungen sind Referenz für die Laufzeitsicht. Schnittstellenbeschreibungen sind Referenz für die Verteilungssicht.

**Kapitel 6 - Laufzeitsicht:**

- **Laufzeitsicht:** Die Laufzeitsicht basiert auf der Bausteinsicht. Die Laufzeitsicht basiert auf Schnittstellenbeschreibungen. Die Laufzeitsicht nutzt Szenarien aus Qualitätsszenarien. Die Laufzeitsicht berücksichtigt Personas. Die Laufzeitsicht beeinflusst technische Risiken.

**Kapitel 7 - Verteilungssicht:**

- **Verteilungssicht:** Die Verteilungssicht basiert auf der Bausteinsicht. Die Verteilungssicht basiert auf der Lösungsstrategie. Die Verteilungssicht wird durch übergreifende Konzepte beeinflusst. Die Verteilungssicht berücksichtigt Randbedingungen. Die Verteilungssicht beeinflusst technische Risiken.

**Kapitel 8 - Querschnittliche Konzepte:**

- **Übergreifendes Konzept:** Übergreifende Konzepte wirken auf die Bausteinsicht. Übergreifende Konzepte wirken auf die Laufzeitsicht. Übergreifende Konzepte wirken auf die Verteilungssicht. Übergreifende Konzepte wirken auf Schnittstellenbeschreibungen.

**Kapitel 9 - Architekturentscheidungen:**

- **Architekturentscheidung:** Architekturentscheidungen begründen die Bausteinsicht. Architekturentscheidungen begründen die Verteilungssicht. Architekturentscheidungen begründen die Laufzeitsicht. Architekturentscheidungen entstehen aus der Lösungsstrategie. Architekturentscheidungen werden durch Qualitätsziele getrieben. Architekturentscheidungen werden durch Randbedingungen eingeschränkt. Architekturentscheidungen adressieren technische Risiken.

**Kapitel 10 - Qualitätsanforderungen:**

- **Qualitätsszenarien:** Qualitätsszenarien konkretisieren Qualitätsziele. Qualitätsszenarien beeinflussen die Lösungsstrategie. Qualitätsszenarien treiben Architekturentscheidungen. Qualitätsszenarien validieren die Bausteinsicht. Qualitätsszenarien validieren die Laufzeitsicht.

**Kapitel 11 - Risiken:**

- **Technische Risiken:** Technische Risiken entstehen aus Randbedingungen. Technische Risiken entstehen aus der Verteilungssicht. Technische Risiken entstehen aus der Laufzeitsicht. Technische Risiken entstehen aus der Lösungsstrategie. Technische Risiken werden durch Architekturentscheidungen adressiert.

**Kapitel 12 - Glossar:**

- **Glossar:** Das Glossar wird von allen Kapiteln referenziert. Das Glossar ist besonders wichtig für den Systemkontext, die Bausteinsicht und Schnittstellenbeschreibungen.

### Empfohlene Reihenfolge beim Ausfüllen

**Hinweis:** Diese Reihenfolgen sind Orientierungshilfen, keine Pflicht. Beginne mit den Kapiteln, für die du bereits Informationen hast (siehe Quick-Start-Guide oben). Die Reihenfolge hilft dir, Abhängigkeiten zu berücksichtigen, wenn du neue Kapitel ergänzt.

**Basierend auf Abhängigkeiten (empfohlen für neue Projekte):**

1. **Start:** Anforderungen, Personas, Systemkontext (Kapitel 1.1, 1.3, Kapitel 3)
2. **Grundlagen:** Qualitätsziele, Randbedingungen (Kapitel 1.2, Kapitel 2)
3. **Strategie:** Lösungsstrategie, übergreifende Konzepte (Kapitel 4, Kapitel 8)
4. **Kern:** Bausteinsicht, Schnittstellenbeschreibung, Laufzeitsicht, Verteilungssicht (Kapitel 5, 6, 7)
5. **Qualität & Risiken:** Qualitätsszenarien, technische Risiken (Kapitel 10, 11)
6. **Entscheidungen:** Architekturentscheidungen (Kapitel 9)
7. **Abschluss:** Glossar (Kapitel 12)

**Alternative (arc42-Standard-Reihenfolge):**

1. **Start:** Kapitel 1 (Einführung und Ziele) und Kapitel 3 (Kontextabgrenzung)
2. **Kern:** Kapitel 5 (Bausteinsicht), Kapitel 6 (Laufzeitsicht), Kapitel 7 (Verteilungssicht)
3. **Ergänzung:** Kapitel 4 (Lösungsstrategie), Kapitel 8 (Querschnittliche Konzepte)
4. **Abschluss:** Kapitel 2 (Randbedingungen), Kapitel 9 (Architekturentscheidungen), 
   Kapitel 10 (Qualitätsanforderungen), Kapitel 11 (Risiken), Kapitel 12 (Glossar)

**Wichtig:** Nicht alle Kapitel müssen ausgefüllt werden. Fülle nur die aus, die für dein Projekt relevant sind.

### Traceability-Matrizen (für das Zieldokument)

**Zweck:** Traceability-Matrizen zeigen systematisch, wie Entscheidungen nachvollziehbar sind. Sie verbinden verschiedene Kapitel und zeigen die Abhängigkeiten zwischen Entscheidungen.

**Hinweis:** Die folgenden Matrizen sind Platzhalter/Beispiele für das Zieldokument. Im echten arc42 Architekturdokument werden diese Matrizen mit den tatsächlichen Qualitätszielen, ADRs, Bausteinen etc. ausgefüllt.

#### Traceability-Matrix: Qualitätsziele

**Zweck:** Diese Matrix zeigt, wie jedes Qualitätsziel (aus Kapitel 1.2) durch verschiedene Kapitel erfüllt wird.

**Zu dokumentieren im Zieldokument:**
```
[HIER: Traceability-Matrix für Qualitätsziele erstellen]

| Qualitätsziel | Priorität | Erfüllt durch Lösungsstrategie (K4) | Erfüllt durch Bausteine (K5) | Erfüllt durch Laufzeitsicht (K6) | Erfüllt durch Verteilungssicht (K7) | Erfüllt durch Konzepte (K8) | Erfüllt durch ADRs (K9) | Validierung (K10) |
|---------------|-----------|-------------------------------------|------------------------------|----------------------------------|-------------------------------------|----------------------------|------------------------|-------------------|
| [Qualitätsziel 1] | [Priorität] | [Strategischer Ansatz] | [Baustein-Name] | [Szenario-Name] | [Deployment-Aspekt] | [Konzept-Name] | [ADR-Nummer: Titel] | [Qualitätsszenario] |
| [Qualitätsziel 2] | [Priorität] | [Strategischer Ansatz] | [Baustein-Name] | [Szenario-Name] | [Deployment-Aspekt] | [Konzept-Name] | [ADR-Nummer: Titel] | [Qualitätsszenario] |

**Legende:**
- **K4** = Kapitel 4 (Lösungsstrategie)
- **K5** = Kapitel 5 (Bausteinsicht)
- **K6** = Kapitel 6 (Laufzeitsicht)
- **K7** = Kapitel 7 (Verteilungssicht)
- **K8** = Kapitel 8 (Querschnittliche Konzepte)
- **K9** = Kapitel 9 (Architekturentscheidungen)
- **K10** = Kapitel 10 (Qualitätsszenarien)
```

**Verwendung:** Diese Matrix hilft zu prüfen, ob jedes Qualitätsziel vollständig erfüllt wird. Für jedes Qualitätsziel sollte mindestens eine Erfüllung in jedem relevanten Kapitel dokumentiert sein.

**Beispiel:** Siehe Kapitel 1.2, Abschnitt "Erfüllung der Qualitätsziele" für ein detailliertes Beispiel.

#### Traceability-Matrix: Entscheidungsfluss

**Zweck:** Diese Matrix zeigt den vollständigen Weg von Anforderungen zu Architekturentscheidungen.

**Zu dokumentieren im Zieldokument:**
```
[HIER: Traceability-Matrix für Entscheidungsfluss erstellen]

| Anforderung (K1.1) | Qualitätsziel (K1.2) | Lösungsstrategie (K4) | Architekturentscheidung (K9) | Umsetzung (K5/K6/K7) | Validierung (K10) |
|---------------------|----------------------|------------------------|------------------------------|----------------------|-------------------|
| "[Anforderung 1]" | [Qualitätsziel] ([Priorität]) | [Strategischer Ansatz] | [ADR-Nummer: Titel] | [Baustein/Szenario] ([Kapitel]) | [Qualitätsszenario] |
| "[Anforderung 2]" | [Qualitätsziel] ([Priorität]) | [Strategischer Ansatz] | [ADR-Nummer: Titel] | [Baustein/Szenario] ([Kapitel]) | [Qualitätsszenario] |
```

**Verwendung:** Diese Matrix zeigt den vollständigen Weg von einer Anforderung über Qualitätsziele und Strategie bis zur konkreten Architekturentscheidung und deren Umsetzung.

#### Entscheidungsfluss-Diagramm

**Zweck:** Zeigt visuell den Fluss von Anforderungen zu Architekturentscheidungen.

**Zu dokumentieren im Zieldokument:**
```
[HIER: Entscheidungsfluss-Diagramm erstellen]

Anforderungen (K1.1)
    ↓
Qualitätsziele (K1.2) ← Personas (K1.3)
    ↓
Lösungsstrategie (K4) ← Randbedingungen (K2), Konzepte (K8)
    ↓
Architekturentscheidungen (K9)
    ↓
Bausteinsicht (K5) → Laufzeitsicht (K6) → Verteilungssicht (K7)
    ↓
Validierung durch Qualitätsszenarien (K10)
```

**Hinweis:** Nicht alle Entscheidungen folgen diesem Fluss linear - es gibt Rückkopplungen und parallele Abhängigkeiten. Das Diagramm zeigt den typischen Entscheidungsfluss.

### Navigation zwischen Kapiteln

**Zweck:** In einem arc42 Architekturdokument sollten Leser zwischen verwandten Kapiteln navigieren können.

**Wie wird Navigation dokumentiert?**

1. **In jedem Kapitel:** Der Abschnitt "Abhängigkeiten" zeigt, auf welche Kapitel das aktuelle Kapitel aufbaut
2. **Verweise im Text:** Explizite Verweise wie "Siehe Kapitel 4, Abschnitt 'Lösungsstrategie'" zeigen Zusammenhänge
3. **Traceability-Matrizen:** Systematische Übersicht der Abhängigkeiten (siehe Abschnitt "Traceability-Matrizen (für das Zieldokument)" weiter oben)

**Beispiel für Verweise:**

- In Kapitel 1.2 (Qualitätsziele): "Diese Qualitätsziele werden in Kapitel 4 (Lösungsstrategie) durch strategische Ansätze erfüllt. Siehe Abschnitt 'Erfüllung der Qualitätsziele' für Details."
- In Kapitel 4 (Lösungsstrategie): "Diese Lösungsstrategie basiert auf den Qualitätszielen aus Kapitel 1.2. Die konkrete Umsetzung wird in Kapitel 5 (Bausteinsicht) beschrieben."
- In Kapitel 9 (Architekturentscheidungen): "Diese ADR erfüllt das Qualitätsziel 'Performance' aus Kapitel 1.2. Die Umsetzung wird in Kapitel 5, Baustein 'Cache-Service' beschrieben."

### Best Practices für Traceability

- ✅ **Dokumentiere Abhängigkeiten explizit:** Jedes Kapitel sollte klar zeigen, auf welche anderen Kapitel es aufbaut
- ✅ **Verwende Traceability-Matrizen:** Für wichtige Entscheidungen (z.B. Qualitätsziele) systematische Matrizen erstellen
- ✅ **Verweise zwischen Kapiteln:** Explizite Verweise zeigen Zusammenhänge (z.B. "Siehe Kapitel X, Abschnitt Y")
- ✅ **Aktualisiere Traceability regelmäßig:** Wenn sich Entscheidungen ändern, auch die Traceability aktualisieren
- ✅ **Validiere Traceability:** Prüfe regelmäßig, ob alle Qualitätsziele erfüllt werden
- ❌ **Vermeide:** Vage Verweise ohne konkrete Kapitel/Abschnitte
- ❌ **Vermeide:** Traceability nur am Anfang dokumentieren, dann vergessen

---

## 1. Einführung und Ziele

Dieses Kapitel der arc42 Architekturdokumentation beschreibt die grundlegenden Anforderungen, Qualitätsziele und Stakeholder. Die Inhalte dieses Kapitels bilden die Basis für alle weiteren Kapitel der arc42 Architekturdokumentation.

### 1.1 Anforderungen

**Zweck:** Beschreibung der grundlegenden Anforderungen an das System.

**Hinweis:** Der Produktkarton (Zielbild, Nutzen, Zielgruppe) kann als Kontext für die Anforderungen dienen, 
ist aber nicht identisch mit Anforderungen. Anforderungen sind spezifische, testbare Anforderungen, 
während der Produktkarton eine höhere Abstraktionsebene (Vision) beschreibt.

**Abhängigkeiten:**
- Anforderungen werden aus dem Produktkarton/Vision abgeleitet (Kontext).
- Anforderungen liefern Kontext für den Systemkontext (Kapitel 3).
- Anforderungen beeinflussen die Qualitätsziele (Kapitel 1.2).
- Anforderungen beeinflussen Personas (Kapitel 1.3).
- Anforderungen sind Input für die Lösungsstrategie (Kapitel 4).

**Inhalt:**
- Funktionale Anforderungen (Was soll das System tun?)
- Nicht-funktionale Anforderungen (Wie soll das System sein?)
- Geschäftsziele und -treiber
- Wichtige Use Cases oder User Stories

**Zu dokumentieren:**
```
[HIER: Liste der wichtigsten Anforderungen auflisten]
- Anforderung 1: ...
- Anforderung 2: ...
```

### 1.2 Qualitätsziele

**Zweck:** Definition der wichtigsten Qualitätsziele, die die Architektur beeinflussen.

**Abhängigkeiten:**
- Qualitätsziele werden aus Anforderungen (Kapitel 1.1) abgeleitet.
- Qualitätsziele werden aus Personas (Kapitel 1.3) abgeleitet.
- Qualitätsziele werden durch Qualitätsszenarien (Kapitel 10) konkretisiert.
- Qualitätsziele treiben die Lösungsstrategie (Kapitel 4).
- Qualitätsziele beeinflussen Architekturentscheidungen (Kapitel 9).

**Traceability:** Für eine systematische Übersicht der Abhängigkeiten siehe Abschnitt "Traceability: Nachvollziehbarkeit von Entscheidungen". Im Zieldokument sollte eine Traceability-Matrix für Qualitätsziele erstellt werden, die zeigt, wie jedes Qualitätsziel durch verschiedene Kapitel erfüllt wird.

**Inhalt:**
- Priorisierte Liste der Qualitätsziele (z.B. Performance, Sicherheit, Wartbarkeit, Skalierbarkeit)
- Begründung für die Priorisierung
- Konflikte zwischen Qualitätszielen und deren Auflösung

**Zu dokumentieren:**
```
[HIER: Qualitätsziele mit Priorisierung auflisten]
1. [Qualitätsziel 1] - Priorität: Hoch/Mittel/Niedrig
   - Begründung: ...
   - Erfüllt durch: [Siehe Abschnitt "Erfüllung der Qualitätsziele" unten]
2. [Qualitätsziel 2] - Priorität: Hoch/Mittel/Niedrig
   - Begründung: ...
   - Erfüllt durch: [Siehe Abschnitt "Erfüllung der Qualitätsziele" unten]
```

### Erfüllung der Qualitätsziele

**Zweck:** Dieser Abschnitt zeigt, wo und wie jedes Qualitätsziel in der Architektur erfüllt wird. Dies verbessert die Nachvollziehbarkeit und hilft bei der Validierung der Architektur.

**Traceability:** Für eine systematische Übersicht der Traceability-Struktur siehe Abschnitt "Traceability: Nachvollziehbarkeit von Entscheidungen". Im Zieldokument sollte eine Traceability-Matrix für Qualitätsziele erstellt werden, die zeigt, wie jedes Qualitätsziel durch verschiedene Kapitel erfüllt wird.

**Wo werden Qualitätsziele erfüllt?**

Qualitätsziele werden in verschiedenen Kapiteln der arc42 Architekturdokumentation erfüllt:

- **Kapitel 4 (Lösungsstrategie):** Beschreibt die strategischen Ansätze zur Erfüllung der Qualitätsziele (z.B. Microservices für Skalierbarkeit, Caching für Performance)
- **Kapitel 5 (Bausteinsicht):** Zeigt, welche Bausteine zur Erfüllung der Qualitätsziele beitragen (z.B. Load Balancer für Performance, Security Gateway für Sicherheit)
- **Kapitel 6 (Laufzeitsicht):** Beschreibt, wie Qualitätsziele zur Laufzeit erfüllt werden (z.B. Caching-Strategien für Performance, Retry-Mechanismen für Zuverlässigkeit)
- **Kapitel 7 (Verteilungssicht):** Zeigt, wie die Deployment-Architektur Qualitätsziele erfüllt (z.B. horizontale Skalierung für Skalierbarkeit, Multi-Region für Verfügbarkeit)
- **Kapitel 8 (Querschnittliche Konzepte):** Beschreibt übergreifende Konzepte zur Erfüllung der Qualitätsziele (z.B. Security-Konzept für Sicherheit, Logging-Konzept für Wartbarkeit)
- **Kapitel 9 (Architekturentscheidungen):** Dokumentiert konkrete Entscheidungen zur Erfüllung der Qualitätsziele (z.B. ADR: "Verwendung von Redis für Caching zur Erfüllung des Performance-Ziels")
- **Kapitel 10 (Qualitätsszenarien):** Definiert messbare Szenarien zur Validierung der Qualitätsziele

**Zu dokumentieren:**
```
[HIER: Erfüllung jedes Qualitätsziels dokumentieren]

### Übersicht: Erfüllung der Qualitätsziele

| Qualitätsziel | Priorität | Erfüllt durch Lösungsstrategie | Erfüllt durch Bausteine | Erfüllt durch Architekturentscheidungen | Validierung (Qualitätsszenarien) |
|---------------|-----------|-------------------------------|------------------------|----------------------------------------|----------------------------------|
| Performance | Hoch | Caching-Strategie, Load Balancing | Cache-Service, Load Balancer | ADR-001: Redis für Caching | Szenario: Response Time < 2s (Kapitel 10) |
| Sicherheit | Hoch | Security-First-Ansatz, Zero-Trust | Security Gateway, Auth-Service | ADR-002: Keycloak für Authentication | Szenario: OWASP Top 10 Compliance (Kapitel 10) |
| Skalierbarkeit | Mittel | Microservices-Architektur | Auto-Scaling, Message Queue | ADR-003: Kubernetes für Orchestrierung | Szenario: Horizontal Scaling (Kapitel 10) |

### Detaillierte Erfüllung pro Qualitätsziel

#### Qualitätsziel 1: [Name, z.B. "Performance"]

**Priorität:** Hoch/Mittel/Niedrig

**Begründung:** [Warum ist dieses Qualitätsziel wichtig?]

**Erfüllt durch:**

1. **Lösungsstrategie (Kapitel 4):**
   - [Strategischer Ansatz 1, z.B. "Caching-Strategie für häufig abgerufene Daten"]
   - [Strategischer Ansatz 2, z.B. "Load Balancing für gleichmäßige Lastverteilung"]
   - Verweis: Siehe Kapitel 4, Abschnitt "[Relevanter Abschnitt]"

2. **Bausteinsicht (Kapitel 5):**
   - [Baustein 1, z.B. "Cache-Service"] - Implementiert Caching-Strategie
   - [Baustein 2, z.B. "Load Balancer"] - Verteilt Last gleichmäßig
   - Verweis: Siehe Kapitel 5, Level 2: "[Baustein-Name]"

3. **Laufzeitsicht (Kapitel 6):**
   - [Laufzeitszenario, z.B. "Caching bei Datenabfrage"] - Zeigt, wie Caching zur Laufzeit funktioniert
   - Verweis: Siehe Kapitel 6, Szenario: "[Szenario-Name]"

4. **Verteilungssicht (Kapitel 7):**
   - [Deployment-Aspekt, z.B. "Horizontale Skalierung"] - Ermöglicht Performance-Skalierung
   - Verweis: Siehe Kapitel 7, Abschnitt "[Relevanter Abschnitt]"

5. **Querschnittliche Konzepte (Kapitel 8):**
   - [Konzept, z.B. "Performance-Monitoring"] - Überwacht Performance-Metriken
   - Verweis: Siehe Kapitel 8, Abschnitt "[Relevanter Abschnitt]"

6. **Architekturentscheidungen (Kapitel 9):**
   - [ADR-Name, z.B. "ADR-001: Verwendung von Redis für Caching"] - Konkrete Entscheidung zur Erfüllung
   - Verweis: Siehe Kapitel 9, ADR-001

7. **Validierung (Kapitel 10):**
   - [Qualitätsszenario, z.B. "Systemantwortzeit bei hoher Last"] - Messbares Szenario zur Validierung
   - Verweis: Siehe Kapitel 10, Qualitätsszenario: "[Szenario-Name]"

**Messgrößen:**
- [Metrik 1, z.B. "Response Time (95th Percentile)"]: Zielwert < 2 Sekunden
- [Metrik 2, z.B. "Throughput"]: Zielwert > 1000 Requests/Sekunde

**Status:** ✅ Erfüllt / ⚠️ Teilweise erfüllt / ❌ Nicht erfüllt

#### Qualitätsziel 2: [Name, z.B. "Sicherheit"]
[Wiederhole die Struktur für jedes weitere Qualitätsziel]
```

**Best Practices:**
- ✅ Dokumentiere für jedes Qualitätsziel explizit, wo es erfüllt wird
- ✅ Verweise auf konkrete Kapitel, Abschnitte und ADRs
- ✅ Zeige die Verbindung zwischen Qualitätszielen und ihrer Umsetzung
- ✅ Dokumentiere Messgrößen und Validierung
- ✅ Aktualisiere den Status regelmäßig (erfüllt/teilweise erfüllt/nicht erfüllt)
- ❌ Vermeide: Vage Verweise ohne konkrete Kapitel/Abschnitte

### 1.3 Stakeholder / Personas

**Zweck:** Übersicht der wichtigsten Stakeholder und deren Erwartungen an die Architektur. Personas beschreiben typische Nutzer- oder Stakeholderprofile.

**Abhängigkeiten:**
- Personas leiten sich aus Anforderungen (Kapitel 1.1) ab.
- Personas beeinflussen die Qualitätsziele (Kapitel 1.2).
- Personas beeinflussen Szenarien in den Qualitätsszenarien (Kapitel 10).
- Personas sind Input für die Laufzeitsicht (Kapitel 6).

**Inhalt:**
- Liste der Stakeholder (Entwickler, Product Owner, Operations, Endnutzer, etc.)
- Erwartungen und Anforderungen jedes Stakeholders
- Einfluss und Interesse der Stakeholder

**Zu dokumentieren:**
```
[HIER: Stakeholder-Liste mit Erwartungen]
| Stakeholder | Rolle | Erwartungen |
|-------------|-------|-------------|
| ... | ... | ... |
```

---

## 2. Randbedingungen

**Zweck:** Dokumentation aller externen Vorgaben und Einschränkungen, die das Design und die Implementierung beeinflussen.

**Abhängigkeiten:**
- Randbedingungen beeinflussen die Lösungsstrategie (Kapitel 4).
- Randbedingungen beeinflussen Architekturentscheidungen (Kapitel 9).
- Randbedingungen beeinflussen übergreifende Konzepte (Kapitel 8).
- Randbedingungen sind Quelle für technische Risiken (Kapitel 11).
- Randbedingungen werden in der Verteilungssicht (Kapitel 7) berücksichtigt.

**Inhalt:**
- Technische Randbedingungen (z.B. verwendete Technologien, Standards, Frameworks)
- Organisatorische Randbedingungen (z.B. Teamstruktur, Prozesse, Zeitvorgaben)
- Konventionen (z.B. Coding Standards, Namenskonventionen)
- Gesetzliche und regulatorische Anforderungen

**Zu dokumentieren:**
```
[HIER: Randbedingungen kategorisiert auflisten]

### Technische Randbedingungen
- ...

### Organisatorische Randbedingungen
- ...

### Konventionen
- ...

### Gesetzliche/Regulatorische Anforderungen
- ...
```

---

## 3. Kontextabgrenzung / Systemkontext

**Zweck:** Abgrenzung des Systems von externen Kommunikationspartnern und Definition der Schnittstellen. Der Systemkontext beschreibt externe Systeme, Akteure und Schnittstellen auf hoher Ebene.

**Abhängigkeiten:**
- Der Systemkontext wird aus Anforderungen (Kapitel 1.1) abgeleitet.
- Der Systemkontext beeinflusst die Schnittstellenbeschreibung (Kapitel 5).
- Der Systemkontext beeinflusst die Bausteinsicht (Kapitel 5).
- Der Systemkontext beeinflusst die Verteilungssicht (Kapitel 7).
- Der Systemkontext ist Referenz für die Laufzeitsicht (Kapitel 6).

**Inhalt:**
- Kontextdiagramm (System und seine Umgebung)
- Beschreibung der Nachbarsysteme
- Beschreibung der Benutzer und deren Rollen
- Schnittstellen zu externen Systemen
- Datenflüsse zwischen System und Umgebung

**Zu dokumentieren:**
```
[HIER: Kontextdiagramm einfügen oder beschreiben]

### Nachbarsysteme
- [System 1]: Beschreibung, Schnittstelle, Protokoll
- [System 2]: Beschreibung, Schnittstelle, Protokoll

### Benutzer
- [Rolle 1]: Beschreibung, Zugriff, Berechtigungen
- [Rolle 2]: Beschreibung, Zugriff, Berechtigungen

### Schnittstellen
- [Schnittstelle 1]: Protokoll, Format, Richtung
- [Schnittstelle 2]: Protokoll, Format, Richtung
```

---

## 4. Lösungsstrategie

**Zweck:** Beschreibung der zentralen Lösungsansätze und -ideen, die den Übergang von Anforderungen zur konkreten Architektur beschreiben.

**Abhängigkeiten:**
- Die Lösungsstrategie basiert auf Qualitätszielen (Kapitel 1.2).
- Die Lösungsstrategie basiert auf Randbedingungen (Kapitel 2).
- Die Lösungsstrategie basiert auf übergreifenden Konzepten (Kapitel 8).
- Die Lösungsstrategie berücksichtigt technische Risiken (Kapitel 11).
- Die Lösungsstrategie wird durch Architekturentscheidungen (Kapitel 9) umgesetzt und konkretisiert.
- Die Lösungsstrategie leitet Struktur für die Bausteinsicht (Kapitel 5).
- Die Lösungsstrategie leitet Struktur für die Verteilungssicht (Kapitel 7).
- Die Lösungsstrategie leitet Struktur für die Laufzeitsicht (Kapitel 6).

**Inhalt:**
- Architekturprinzipien und -entscheidungen
- Technologieentscheidungen und deren Begründung (z.B. Apache Kafka, PostgreSQL, Keycloak)
- Architekturmuster (z.B. Layered Architecture, Microservices, Event-Driven)
- Strategische Designentscheidungen
- Abwägungen und Alternativen

**Hinweis zur Technologieauswahl:**
- **Kapitel 4 (Lösungsstrategie):** Zusammenfassung der Technologieentscheidungen mit Begründung
- **Kapitel 9 (Architekturentscheidungen):** Detaillierte ADRs für wichtige Technologieentscheidungen
- **Kapitel 2 (Randbedingungen):** Technische Vorgaben (z.B. "Wir müssen PostgreSQL verwenden")
- **Kapitel 8 (Querschnittliche Konzepte):** Technische Konzepte (z.B. "Welche Technologien verwenden wir für Persistenz?")

**Zu dokumentieren:**
```
[HIER: Lösungsstrategie beschreiben]

### Architekturprinzipien
- Prinzip 1: Beschreibung und Begründung
- Prinzip 2: Beschreibung und Begründung

### Technologieentscheidungen
- [Technologie 1]: Begründung, Alternativen, Trade-offs
- [Technologie 2]: Begründung, Alternativen, Trade-offs
```

**Beispiel-Technologieentscheidungen:**

#### Apache Kafka für Event-Driven Communication
- **Begründung:** Asynchrone Kommunikation zwischen Microservices, Event Sourcing, hohe Skalierbarkeit
- **Alternativen:** RabbitMQ, AWS SQS, NATS
- **Trade-offs:** 
  - ✅ Vorteile: Hohe Performance, Event-Streaming, Replay-Funktionalität
  - ❌ Nachteile: Komplexere Konfiguration, höherer Wartungsaufwand
- **Entscheidung:** Apache Kafka für Event-Driven Communication zwischen Services
- **Dokumentiert als ADR:** ADR-5 (siehe Kapitel 9)

#### PostgreSQL für Persistenz
- **Begründung:** ACID-Konformität, SQL-Standard, JSON-Support, Open Source
- **Alternativen:** MySQL, MongoDB, Oracle
- **Trade-offs:**
  - ✅ Vorteile: Relationale Integrität, JSON-Support, gute Performance
  - ❌ Nachteile: Weniger flexibel als NoSQL für sehr große Datenmengen
- **Entscheidung:** PostgreSQL als primäre Datenbank für relationale Daten
- **Dokumentiert als ADR:** ADR-3 (siehe Kapitel 9)

#### Keycloak für Authentifizierung und Autorisierung
- **Begründung:** Open Source, OAuth2/OIDC-Standard, Multi-Tenant-Fähigkeit
- **Alternativen:** Auth0, Okta, AWS Cognito
- **Trade-offs:**
  - ✅ Vorteile: Open Source, selbst gehostet, OAuth2/OIDC-Standard
  - ❌ Nachteile: Eigene Infrastruktur nötig, Wartungsaufwand
- **Entscheidung:** Keycloak für Authentifizierung und Autorisierung
- **Dokumentiert als ADR:** ADR-7 (siehe Kapitel 9)

**Hinweis:** Wichtige Technologieentscheidungen sollten als ADRs (Architecture Decision Records) in Kapitel 9 dokumentiert werden. In der Lösungsstrategie (Kapitel 4) werden die Entscheidungen zusammengefasst und begründet. Details und Alternativen werden in den ADRs dokumentiert.

### Architekturmuster
- [Muster 1]: Beschreibung, Anwendung, Begründung
- [Muster 2]: Beschreibung, Anwendung, Begründung
```

---

## 5. Bausteinsicht

**Zweck:** Beschreibung der fachlichen und technischen Bausteine des Systems in hierarchischer Form. Die Bausteinsicht zeigt sowohl die fachliche Struktur (Domänen, Bounded Contexts) als auch die technische Umsetzung (Komponenten, Services, Module).

**Empfehlung:** Beginnen Sie mit fachlichen Bausteinen (Level 1), die die Domänen und fachlichen Bereiche des Systems beschreiben. Diese werden dann auf technische Bausteine (Level 2+) gemappt, die die konkrete technische Umsetzung zeigen. Dieser Ansatz entspricht Domain-Driven Design (DDD) und verbessert die Nachvollziehbarkeit für Stakeholder.

**Abhängigkeiten:**
- Die Bausteinsicht wird aus der Lösungsstrategie (Kapitel 4) abgeleitet.
- Die Bausteinsicht wird durch übergreifende Konzepte (Kapitel 8) beeinflusst.
- Die Bausteinsicht berücksichtigt Qualitätsszenarien (Kapitel 10).
- Die Bausteinsicht nutzt Schnittstellenbeschreibungen. Schnittstellenbeschreibungen werden in Abschnitt "Schnittstellenbeschreibung" in diesem Kapitel 5 dokumentiert.
- Die Bausteinsicht wird von Architekturentscheidungen (Kapitel 9) beeinflusst.
- Die Bausteinsicht ist Referenz für die Laufzeitsicht (Kapitel 6).
- Die Bausteinsicht beeinflusst die Verteilungssicht (Kapitel 7).

**Inhalt:**
- **Level 1:** Fachliche Bausteine (Domänen, Bounded Contexts, fachliche Bereiche)
- **Level 2:** Technische Bausteine (Services, Komponenten, Module, die die fachlichen Bausteine umsetzen)
- **Level 3+:** Detaillierung wichtiger technischer Bausteine (Sub-Komponenten, Packages)
- Abhängigkeiten zwischen Bausteinen (sowohl fachlich als auch technisch)
- Verantwortlichkeiten der einzelnen Bausteine
- Schnittstellen zwischen Bausteinen
- Mapping zwischen fachlichen und technischen Bausteinen

**Zu dokumentieren:**
```
[HIER: Bausteinsicht hierarchisch beschreiben]

### Level 1: Fachliche Bausteine (Domänen/Bounded Contexts)

[Diagramm oder Beschreibung der fachlichen Hauptbausteine]

#### [Fachlicher Baustein 1: z.B. "User Management"]
- **Fachliche Verantwortlichkeit:** Verwaltung von Benutzerkonten, Authentifizierung, Autorisierung
- **Fachliche Abhängigkeiten:** Nutzt "Payment" für Zahlungsabwicklung, liefert Daten an "Order Processing"
- **Gemappt auf technische Bausteine:** UserService, UserRepository, AuthService (siehe Level 2: Technische Bausteine)

#### [Fachlicher Baustein 2: z.B. "Order Processing"]
- **Fachliche Verantwortlichkeit:** Bestellabwicklung, Bestellstatus-Verwaltung
- **Fachliche Abhängigkeiten:** Nutzt "User Management" für Benutzerdaten, nutzt "Payment" für Zahlungen
- **Gemappt auf technische Bausteine:** OrderService, OrderRepository, OrderAPI (siehe Level 2: Technische Bausteine)

### Level 2: Technische Bausteine (Komponenten/Services)

#### [Technischer Baustein: z.B. "UserService"]
- **Technische Verantwortlichkeit:** Implementiert die User Management Domäne, Business-Logik für Benutzer
- **Gehört zu fachlichem Baustein:** User Management (Level 1)
- **Schnittstellen:** 
  - REST API: `/api/users` (GET, POST, PUT, DELETE)
  - Event: `UserCreated`, `UserUpdated`
- **Abhängigkeiten:** 
  - Benötigt: UserRepository (für Persistenz)
  - Benötigt: AuthService (für Authentifizierung)
  - Benötigt: NotificationService (für E-Mail-Benachrichtigungen)
- **Enthaltene Sub-Bausteine:** UserValidator, UserMapper (siehe Level 3: Detaillierung)

#### [Technischer Baustein: z.B. "UserRepository"]
- **Technische Verantwortlichkeit:** Datenzugriff für User Management, Persistenz
- **Gehört zu fachlichem Baustein:** User Management (Level 1)
- **Schnittstellen:** 
  - Datenbank: User-Tabelle
  - Interface: IUserRepository
- **Abhängigkeiten:** 
  - Benötigt: Database Service (für Datenbankverbindung)

### Level 3: Detaillierung (optional, nur bei Bedarf)

#### [Sub-Baustein: z.B. "UserValidator"]
- **Verantwortlichkeit:** Validierung von Benutzerdaten (E-Mail-Format, Passwort-Stärke)
- **Gehört zu technischem Baustein:** UserService (Level 2: Technische Bausteine)
- **Schnittstellen:** Interface: IUserValidator
- **Abhängigkeiten:** Keine externen Abhängigkeiten
```

### Mapping zwischen fachlichen und technischen Bausteinen

**Zweck:** Das Mapping zeigt die Beziehung zwischen fachlichen Bausteinen (Level 1) und ihrer technischen Umsetzung (Level 2+). Dies verbessert die Nachvollziehbarkeit und hilft Stakeholdern zu verstehen, wie fachliche Anforderungen technisch umgesetzt werden.

**Mapping-Prinzipien:**
- **1:1-Mapping:** Ein fachlicher Baustein kann auf einen technischen Baustein gemappt werden
- **1:N-Mapping:** Ein fachlicher Baustein kann auf mehrere technische Bausteine gemappt werden (häufigster Fall)
- **N:1-Mapping:** Mehrere fachliche Bausteine können auf einen technischen Baustein gemappt werden (seltener, z.B. Shared Kernel)

**Bidirektionale Dokumentation:**
- **Level 1 → Level 2:** Jeder fachliche Baustein dokumentiert, auf welche technischen Bausteine er gemappt wird (Feld: "Gemappt auf technische Bausteine")
- **Level 2 → Level 1:** Jeder technische Baustein dokumentiert, zu welchem fachlichen Baustein er gehört (Feld: "Gehört zu fachlichem Baustein")
- **Level 3 → Level 2:** Jeder Sub-Baustein dokumentiert, zu welchem technischen Baustein er gehört (Feld: "Gehört zu technischem Baustein")

**Zu dokumentieren:**
```
[HIER: Mapping-Übersicht erstellen]

### Übersicht: Mapping zwischen fachlichen und technischen Bausteinen

| Fachlicher Baustein (Level 1) | Technische Bausteine (Level 2) | Sub-Bausteine (Level 3) |
|-------------------------------|-------------------------------|------------------------|
| User Management | UserService, UserRepository, AuthService | UserValidator, UserMapper (zu UserService) |
| Order Processing | OrderService, OrderRepository, OrderAPI | - |
| Payment | PaymentService, PaymentGateway | PaymentValidator (zu PaymentService) |

**Legende:**
- **Fachlicher Baustein:** Beschreibt die fachliche Domäne oder den Bounded Context
- **Technische Bausteine:** Implementieren die fachliche Domäne
- **Sub-Bausteine:** Detaillierung wichtiger technischer Bausteine (optional)

### Mapping-Details pro fachlichem Baustein

#### [Fachlicher Baustein: z.B. "User Management"]

**Gemappt auf folgende technische Bausteine:**

1. **UserService** (Level 2)
   - **Rolle:** Implementiert die Business-Logik für User Management
   - **Schnittstellen:** REST API `/api/users`, Events `UserCreated`, `UserUpdated`
   - **Enthaltene Sub-Bausteine:** UserValidator, UserMapper (Level 3)

2. **UserRepository** (Level 2)
   - **Rolle:** Datenzugriff und Persistenz für User Management
   - **Schnittstellen:** Datenbank User-Tabelle, Interface IUserRepository

3. **AuthService** (Level 2)
   - **Rolle:** Authentifizierung und Autorisierung
   - **Schnittstellen:** REST API `/api/auth`, JWT-Token-Generierung

**Begründung des Mappings:**
- UserService kapselt die Business-Logik und ist der primäre Einstiegspunkt für User Management
- UserRepository trennt Datenzugriff von Business-Logik (Repository Pattern)
- AuthService ist fachlich Teil von User Management, aber technisch als separater Service implementiert (Separation of Concerns)
```

**Detaillierungsgrad:**
- **Level 1:** Muss vollständig sein (Übersicht über fachliche Bausteine/Domänen)
- **Level 2:** Mindestens für kritische Bausteine (z.B. Core Domain, externe Schnittstellen)
- **Level 3+:** Nur bei Bedarf für komplexe oder kritische Sub-Bausteine

**Empfehlung:** Starte mit Level 1 (fachliche Bausteine), erweitere schrittweise auf Level 2 für wichtige technische Bausteine. Level 3+ nur bei Bedarf für komplexe Sub-Komponenten.

**Best Practices:**
- ✅ Verwende konsistente Abstraktionsebenen (nicht Level 1 mit Code-Details mischen)
- ✅ Dokumentiere Verantwortlichkeiten, nicht Implementierungsdetails
- ✅ Zeige Abhängigkeiten klar (wer nutzt wen)
- ✅ Beginne mit fachlichen Bausteinen (Level 1), dann technische Umsetzung (Level 2+)
- ✅ Zeige Mapping zwischen fachlichen und technischen Bausteinen
- ❌ Vermeide: Zu viele Ebenen (Level 4+ ist meist zu detailliert)
- ❌ Vermeide: Code-Beispiele in der Bausteinsicht (gehört in Code-Dokumentation)
- ❌ Vermeide: Technische Details ohne fachlichen Kontext

**Hinweis zu Domain-Driven Design (DDD):**
Wenn Sie Domain-Driven Design verwenden, entsprechen die fachlichen Bausteine (Level 1) den Bounded Contexts. Die technischen Bausteine (Level 2) implementieren diese Bounded Contexts. Diese Struktur verbessert die Nachvollziehbarkeit und Stabilität der Architektur, da fachliche Strukturen sich langsamer ändern als technische Umsetzungen.

### Schnittstellenbeschreibung

**Zweck:** Definition der angebotenen und benötigten Schnittstellen zwischen Bausteinen und zu externen Systemen.

**Abhängigkeiten:**
- Schnittstellenbeschreibungen basieren auf dem Systemkontext (Kapitel 3).
- Schnittstellenbeschreibungen konkretisieren die Bausteinsicht. Die Bausteinsicht wird in Abschnitt "Bausteinsicht" in diesem Kapitel 5 dokumentiert.
- Schnittstellenbeschreibungen sind Referenz für die Laufzeitsicht (Kapitel 6).
- Schnittstellenbeschreibungen sind Referenz für die Verteilungssicht (Kapitel 7).
- Schnittstellenbeschreibungen werden durch übergreifende Konzepte (Kapitel 8) beeinflusst.

**Zu dokumentieren:**
```
[HIER: Schnittstellenbeschreibungen dokumentieren]

### Schnittstelle: [Name der Schnittstelle]
- **Angeboten von:** [Baustein]
- **Genutzt von:** [Baustein/Externes System]
- **Protokoll:** [z.B. REST, GraphQL, Message Queue]
- **Format:** [z.B. JSON, XML]
- **Verantwortlichkeit:** [Was macht diese Schnittstelle?]
- **Daten:** [Welche Daten werden übertragen?]
```

---

## 6. Laufzeitsicht

**Zweck:** Darstellung wichtiger Laufzeitszenarien, die das Verhalten des Systems zur Laufzeit veranschaulichen.

**Abhängigkeiten:**
- Die Laufzeitsicht basiert auf der Bausteinsicht (Kapitel 5).
- Die Laufzeitsicht basiert auf Schnittstellenbeschreibungen (Kapitel 5).
- Die Laufzeitsicht nutzt Szenarien aus Qualitätsszenarien (Kapitel 10).
- Die Laufzeitsicht berücksichtigt Personas (Kapitel 1.3).
- Die Laufzeitsicht beeinflusst technische Risiken (Kapitel 11).

**Inhalt:**
- Wichtige Laufzeitszenarien (z.B. typische Benutzerinteraktionen, Fehlerbehandlung)
- Sequenzdiagramme oder Aktivitätsdiagramme
- Interaktionen zwischen Bausteinen zur Laufzeit
- Zustandsübergänge
- Parallele Abläufe und Synchronisation

**Zu dokumentieren:**
```
[HIER: Wichtige Laufzeitszenarien beschreiben]

### Szenario 1: [Name des Szenarios]
**Beschreibung:** ...
**Trigger:** ...
**Ablauf:**
1. ...
2. ...
3. ...

[Sequenzdiagramm oder Aktivitätsdiagramm einfügen]

### Szenario 2: [Name des Szenarios]
**Beschreibung:** ...
**Trigger:** ...
**Ablauf:**
1. ...
2. ...
3. ...

[Sequenzdiagramm oder Aktivitätsdiagramm einfügen]
```

**Beispiel-Szenario:**

#### Szenario: Benutzer-Login
**Beschreibung:** Ein Benutzer meldet sich am System an. Die Laufzeitsicht zeigt die Interaktionen zwischen den Bausteinen zur Laufzeit.

**Trigger:** POST /api/auth/login mit Credentials (E-Mail, Passwort)

**Ablauf:**
1. User sendet Login-Anfrage an AuthService (REST API)
2. AuthService validiert Credentials gegen UserRepository
3. UserRepository fragt Datenbank ab (User-Tabelle)
4. Datenbank liefert User-Daten zurück
5. AuthService erstellt JWT-Token (mit User-ID und Rollen)
6. AuthService sendet Token an User zurück (HTTP 200 mit Token)
7. User speichert Token lokal (für nachfolgende Anfragen)

**Beteiligte Bausteine:**
- AuthService (User Management Domäne)
- UserRepository (User Management Domäne)
- Database Service (Infrastruktur)

**Sequenzdiagramm:**
```
User → AuthService: POST /api/auth/login (Credentials)
AuthService → UserRepository: validateUser(email, password)
UserRepository → Database: SELECT * FROM users WHERE email = ?
Database → UserRepository: User-Daten
UserRepository → AuthService: User-Objekt (validiert)
AuthService → AuthService: Erstelle JWT-Token
AuthService → User: HTTP 200 + Token
```

**Best Practices:**
- ✅ Dokumentiere die wichtigsten Laufzeitszenarien (Happy Path + Fehlerfälle)
- ✅ Zeige Interaktionen zwischen Bausteinen klar
- ✅ Verwende Sequenzdiagramme für komplexe Abläufe
- ✅ Berücksichtige auch Fehlerfälle (z.B. ungültige Credentials)
- ❌ Vermeide: Zu viele Details (Code-Level gehört nicht in die Laufzeitsicht)

---

## 7. Verteilungssicht

**Zweck:** Beschreibung der physischen Verteilung des Systems auf Hardware, Infrastruktur und Deployment-Umgebungen.

**Abhängigkeiten:**
- Die Verteilungssicht basiert auf der Bausteinsicht (Kapitel 5).
- Die Verteilungssicht basiert auf der Lösungsstrategie (Kapitel 4).
- Die Verteilungssicht wird durch übergreifende Konzepte (Kapitel 8) beeinflusst.
- Die Verteilungssicht berücksichtigt Randbedingungen (Kapitel 2).
- Die Verteilungssicht beeinflusst technische Risiken (Kapitel 11).

**Inhalt:**
- Deployment-Diagramm
- Verteilung auf Server, Container, Cloud-Services
- Netzwerkstruktur und Kommunikationswege
- Infrastrukturkomponenten (z.B. Load Balancer, Datenbanken, Message Queues)
- Deployment-Prozess und Umgebungen (Development, Staging, Production)

**Zu dokumentieren:**
```
[HIER: Verteilungssicht beschreiben]

### Deployment-Übersicht
[Deployment-Diagramm einfügen]

### Infrastrukturkomponenten
- [Komponente 1]: Typ, Standort, Verantwortlichkeit
- [Komponente 2]: Typ, Standort, Verantwortlichkeit

### Umgebungen
- **Development:** Beschreibung, Konfiguration
- **Staging:** Beschreibung, Konfiguration
- **Production:** Beschreibung, Konfiguration

### Netzwerkstruktur
- Beschreibung der Netzwerkarchitektur
- Kommunikationswege und Protokolle
- Sicherheitszonen
```

**Beispiel-Deployment:**

#### Deployment-Übersicht: Microservices-Architektur

**Infrastrukturkomponenten:**

- **Load Balancer:** 
  - Typ: AWS Application Load Balancer
  - Standort: Public Subnet (DMZ)
  - Verantwortlichkeit: Verteilt eingehende Anfragen auf API-Gateway-Instanzen

- **API-Gateway:**
  - Typ: Kubernetes Deployment (3 Replicas)
  - Standort: Private Subnet (Application Tier)
  - Verantwortlichkeit: Routing, Authentifizierung, Rate Limiting

- **UserService:**
  - Typ: Kubernetes Deployment (2 Replicas)
  - Standort: Private Subnet (Application Tier)
  - Verantwortlichkeit: User Management Domäne

- **OrderService:**
  - Typ: Kubernetes Deployment (2 Replicas)
  - Standort: Private Subnet (Application Tier)
  - Verantwortlichkeit: Order Processing Domäne

- **Database:**
  - Typ: AWS RDS PostgreSQL (Multi-AZ)
  - Standort: Private Subnet (Database Tier)
  - Verantwortlichkeit: Persistenz für alle Services

- **Message Queue:**
  - Typ: AWS SQS
  - Standort: AWS Managed Service
  - Verantwortlichkeit: Asynchrone Kommunikation zwischen Services

**Umgebungen:**

- **Development:**
  - Lokale Entwicklung: Docker Compose auf Entwickler-Maschinen
  - Shared Development: Kubernetes Cluster (1 Node)
  - Konfiguration: Debug-Modus, Logging-Level DEBUG

- **Staging:**
  - Kubernetes Cluster (3 Nodes)
  - Konfiguration: Production-ähnlich, Logging-Level INFO
  - Verwendung: Integration-Tests, UAT

- **Production:**
  - Kubernetes Cluster (5 Nodes, Multi-AZ)
  - Konfiguration: Production-Optimiert, Logging-Level WARN
  - Monitoring: APM, Logging, Alerting aktiviert

**Netzwerkstruktur:**

- **Public Subnet (DMZ):** Load Balancer
- **Private Subnet (Application Tier):** API-Gateway, Services
- **Private Subnet (Database Tier):** Database (nur aus Application Tier erreichbar)
- **Kommunikationswege:** HTTPS (extern), HTTP (intern), TCP (Database)

**Best Practices:**
- ✅ Zeige klare Trennung zwischen Umgebungen
- ✅ Dokumentiere Skalierungsstrategie (z.B. Anzahl Replicas)
- ✅ Beschreibe Netzwerkstruktur und Sicherheitszonen
- ✅ Zeige Mapping von Bausteinen auf Infrastruktur
- ❌ Vermeide: Zu detaillierte Infrastruktur-Konfigurationen (gehört in Infrastruktur-Dokumentation)

---

## 8. Querschnittliche Konzepte / Übergreifendes Konzept

**Zweck:** Behandlung übergreifender Themen, die oft sehr technisch und detailliert sind. Übergreifende Konzepte sind querschnittliche Leitlinien (z.B. Architekturprinzipien, Domänenmodell, Stil).

**Abhängigkeiten:**
- Übergreifende Konzepte basieren auf Randbedingungen (Kapitel 2).
- Übergreifende Konzepte beeinflussen die Lösungsstrategie (Kapitel 4).
- Übergreifende Konzepte beeinflussen die Bausteinsicht (Kapitel 5).
- Übergreifende Konzepte beeinflussen die Verteilungssicht (Kapitel 7).
- Übergreifende Konzepte beeinflussen die Laufzeitsicht (Kapitel 6).
- Übergreifende Konzepte beeinflussen Schnittstellenbeschreibungen (Kapitel 5).

**Inhalt:**
- Sicherheitskonzept (Authentifizierung, Autorisierung, Verschlüsselung)
- Persistenzstrategie (Datenbankdesign, Caching, Backup)
- Logging und Monitoring
- Fehlerbehandlung und Exception Handling
- Transaktionsmanagement
- Konfigurationsmanagement
- Internationalisierung (i18n)
- Caching-Strategien
- API-Design und Versionierung

**Zu dokumentieren:**
```
[HIER: Querschnittliche Konzepte beschreiben]

### Sicherheit
- Authentifizierung: ...
- Autorisierung: ...
- Verschlüsselung: ...
- Sicherheitsrichtlinien: ...

### Persistenz
- Datenbankdesign: ...
- Caching-Strategie: ...
- Backup-Strategie: ...
- Migrationsstrategie: ...

### Logging und Monitoring
- Logging-Strategie: ...
- Monitoring-Konzept: ...
- Alerting: ...
- Metriken: ...

### Fehlerbehandlung
- Exception-Handling-Strategie: ...
- Fehlerprotokollierung: ...
- Retry-Mechanismen: ...

### [Weitere querschnittliche Konzepte]
- ...
```

---

## 9. Architekturentscheidungen

**Zweck:** Dokumentation wichtiger Entscheidungen, die nicht in anderen Kapiteln beschrieben sind, um deren Nachvollziehbarkeit zu gewährleisten. Architekturentscheidungen werden als Architecture Decision Records (ADRs) dokumentiert.

**Wichtige Technologieentscheidungen** (z.B. Apache Kafka, PostgreSQL, Keycloak, Protokolle) sollten als ADRs dokumentiert werden. Diese ADRs enthalten die detaillierte Begründung, erwogene Alternativen und die Entscheidung mit Konsequenzen. In der Lösungsstrategie (Kapitel 4) werden die Technologieentscheidungen zusammengefasst.

**Abhängigkeiten:**
- Architekturentscheidungen begründen die Bausteinsicht (Kapitel 5).
- Architekturentscheidungen begründen die Verteilungssicht (Kapitel 7).
- Architekturentscheidungen begründen die Laufzeitsicht (Kapitel 6).
- Architekturentscheidungen entstehen aus der Lösungsstrategie (Kapitel 4).
- Architekturentscheidungen werden durch Qualitätsziele (Kapitel 1.2) getrieben.
- Architekturentscheidungen werden durch Randbedingungen (Kapitel 2) eingeschränkt.
- Architekturentscheidungen adressieren technische Risiken (Kapitel 11).

**Format:** ADR (Architecture Decision Records) nach dem offiziellen Format von Michael Nygard

**Hinweis:** ADRs können auch in separaten Dateien im `{DOCS}/{ADR}` Verzeichnis dokumentiert werden. 
Die Rolle des Softwarearchitekten beschreibt, wie ADRs erstellt werden (siehe `{PROMPT}/rollen/software-architect.md`). 
In diesem Kapitel werden wichtige ADRs zusammengefasst oder referenziert.

**ADR-Struktur (offizielles Format):**
- Titel
- Status (vorgeschlagen, akzeptiert, abgelehnt, ersetzt, abgelaufen)
- Datum
- Entscheider (optional)
- Technische Story (optional)
- Kontext
- Erwogene Optionen
- Entscheidung
- Konsequenzen

**Zu dokumentieren:**
```
[HIER: Architekturentscheidungen dokumentieren]

### ADR-1: [Titel der Entscheidung]

**Status:** [vorgeschlagen | akzeptiert | abgelehnt | ersetzt | abgelaufen]

**Datum:** [Datum der Entscheidung]

**Entscheider:** [Person oder Team, das die Entscheidung getroffen hat] (optional)

**Technische Story:** [Beschreibung oder Link zu Ticket/Issue] (optional)

**Kontext:**
Beschreibung der Situation, die die Entscheidung erforderlich macht:
- Problemstellung oder Herausforderung
- Relevante Hintergrundinformationen
- Technische, organisatorische oder geschäftliche Randbedingungen
- Betroffene Systeme oder Komponenten

**Erwogene Optionen:**
- **Option 1:** [Beschreibung]
  - Vorteile: ...
  - Nachteile: ...
  
- **Option 2:** [Beschreibung]
  - Vorteile: ...
  - Nachteile: ...

**Entscheidung:**
Wir entscheiden uns für [gewählte Option].

**Konsequenzen:**
- Positive Konsequenzen: ...
- Negative Konsequenzen: ...
- Auswirkungen auf andere Bereiche: ...
- Notwendige Maßnahmen: ...

### ADR-2: [Titel der Entscheidung]
...
```

**Status-Werte:**
- **Vorgeschlagen:** Die Entscheidung wird diskutiert, aber noch nicht getroffen
- **Akzeptiert:** Die Entscheidung wurde getroffen und wird umgesetzt
- **Abgelehnt:** Die Entscheidung wurde nicht getroffen (mit Begründung)
- **Ersetzt:** Die Entscheidung wurde durch ein neues ADR ersetzt (Verweis auf neues ADR)
- **Abgelaufen:** Die Entscheidung ist nicht mehr relevant (z.B. durch Änderungen im Kontext)

---

## 10. Qualitätsanforderungen / Qualitätsszenarien

**Zweck:** Detaillierte Beschreibung der Qualitätsziele in Form eines Qualitätsbaums und Qualitätsszenarien. Qualitätsszenarien sind messbare Szenarien zur Bewertung von Qualität.

**Abhängigkeiten:**
- Qualitätsszenarien konkretisieren Qualitätsziele (Kapitel 1.2). Jedes Qualitätsszenario bezieht sich auf ein oder mehrere Qualitätsziele aus Kapitel 1.2.
- Qualitätsszenarien beeinflussen die Lösungsstrategie (Kapitel 4).
- Qualitätsszenarien treiben Architekturentscheidungen (Kapitel 9).
- Qualitätsszenarien validieren die Bausteinsicht (Kapitel 5).
- Qualitätsszenarien validieren die Laufzeitsicht (Kapitel 6).

**Wichtig:** Jedes Qualitätsszenario sollte explizit auf die zugehörigen Qualitätsziele aus Kapitel 1.2 verweisen. Die Erfüllung der Qualitätsziele wird in Kapitel 1.2, Abschnitt "Erfüllung der Qualitätsziele" dokumentiert.

**Inhalt:**
- Qualitätsbaum (Strukturierung der Qualitätsziele)
- Qualitätsszenarien (konkrete Szenarien zur Überprüfung der Qualitätsziele)
- Metriken und Messgrößen
- Akzeptanzkriterien

**Zu dokumentieren:**
```
[HIER: Qualitätsanforderungen detailliert beschreiben]

### Qualitätsbaum
[Strukturierte Darstellung der Qualitätsziele]
- Qualitätsziel 1
  - Unterziel 1.1
  - Unterziel 1.2
- Qualitätsziel 2
  - Unterziel 2.1

### Qualitätsszenarien

#### Szenario 1: [Qualitätsziel]
**Bezieht sich auf Qualitätsziel:** [Qualitätsziel aus Kapitel 1.2, z.B. "Performance"]
**Erfüllt durch:** [Siehe Kapitel 1.2, Abschnitt "Erfüllung der Qualitätsziele" für Details zur Umsetzung]

**Stimulus:** ...
**Umgebung:** ...
**Reaktion:** ...
**Messgröße:** ...
**Akzeptanzkriterium:** ...

#### Szenario 2: [Qualitätsziel]
**Stimulus:** ...
**Umgebung:** ...
**Reaktion:** ...
**Messgröße:** ...
**Akzeptanzkriterium:** ...

### Metriken
- [Metrik 1]: Zielwert, Messmethode, Häufigkeit
- [Metrik 2]: Zielwert, Messmethode, Häufigkeit
```

**Beispiel-Szenario:**

#### Szenario: Systemantwortzeit bei hoher Last
**Bezieht sich auf Qualitätsziel:** Performance (Kapitel 1.2)
**Erfüllt durch:** Siehe Kapitel 1.2, Abschnitt "Erfüllung der Qualitätsziele" → Qualitätsziel "Performance"

**Stimulus:** 1000 gleichzeitige Benutzer-Anfragen an die REST API

**Umgebung:** Produktionsumgebung, normale Last, Standard-Konfiguration

**Reaktion:** Das System verarbeitet alle Anfragen und liefert Antworten zurück.

**Messgröße:** Response Time (95th Percentile) gemessen in Sekunden

**Akzeptanzkriterium:** 95% der Anfragen werden innerhalb von 2 Sekunden beantwortet (95th Percentile < 2 Sekunden)

**Messmethode:** 
- Monitoring-Tool: Application Performance Monitoring (APM)
- Metrik: HTTP Response Time (95th Percentile)
- Häufigkeit: Kontinuierlich während Betriebszeit

**Validierung:**
- Load-Test mit 1000 gleichzeitigen Anfragen
- Messung über 1 Stunde
- 95th Percentile muss < 2 Sekunden sein

**Best Practices:**
- ✅ Formuliere Qualitätsszenarien messbar (mit konkreten Zahlen)
- ✅ Definiere klare Akzeptanzkriterien
- ✅ Verwende realistische Szenarien (basierend auf erwarteter Last)
- ✅ Dokumentiere Messmethode und Validierung
- ❌ Vermeide: Vage Formulierungen wie "schnell" oder "zuverlässig"

---

## 11. Risiken und technische Schulden / Technische Risiken

**Zweck:** Dokumentation bekannter Probleme, Risiken und technischer Schulden, um frühzeitig Gegenmaßnahmen planen zu können. Technische Risiken sind erkannte technische Unsicherheiten und Gefahren.

**Abhängigkeiten:**
- Technische Risiken entstehen aus Randbedingungen (Kapitel 2).
- Technische Risiken entstehen aus der Verteilungssicht (Kapitel 7).
- Technische Risiken entstehen aus der Laufzeitsicht (Kapitel 6).
- Technische Risiken entstehen aus der Lösungsstrategie (Kapitel 4).
- Technische Risiken werden durch Architekturentscheidungen (Kapitel 9) adressiert.

**Inhalt:**
- Risiken (mit Wahrscheinlichkeit, Auswirkung, Maßnahmen)
- Technische Schulden (mit Beschreibung, Auswirkung, Priorität, Lösungsplan)
- Bekannte Probleme und Limitationen
- Offene Fragen

**Zu dokumentieren:**
```
[HIER: Risiken und technische Schulden dokumentieren]

### Risiken

| ID | Risiko | Wahrscheinlichkeit | Auswirkung | Maßnahmen | Status |
|----|--------|-------------------|------------|-----------|--------|
| R1 | ... | Hoch/Mittel/Niedrig | Hoch/Mittel/Niedrig | ... | Offen/In Bearbeitung/Gelöst |

### Technische Schulden

| ID | Beschreibung | Auswirkung | Priorität | Lösungsplan | Status |
|----|--------------|------------|-----------|-------------|--------|
| TD1 | ... | ... | Hoch/Mittel/Niedrig | ... | Offen/Geplant/In Bearbeitung |

### Bekannte Probleme und Limitationen
- Problem 1: Beschreibung, Workaround, geplante Lösung
- Problem 2: Beschreibung, Workaround, geplante Lösung

### Offene Fragen
- Frage 1: ...
- Frage 2: ...
```

---

## 12. Glossar

**Zweck:** Definition wichtiger und spezifischer Begriffe, um eine gemeinsame Sprache unter den Stakeholdern sicherzustellen. Das Glossar klärt wichtige Begriffe aus allen Dokumentationsbausteinen.

**Abhängigkeiten:**
- Das Glossar wird von allen Kapiteln referenziert.
- Das Glossar ist besonders wichtig für den Systemkontext (Kapitel 3), die Bausteinsicht (Kapitel 5) und Schnittstellenbeschreibungen (Kapitel 5).

**Inhalt:**
- Fachbegriffe
- Abkürzungen
- Technische Begriffe
- Domänenspezifische Begriffe

**Zu dokumentieren:**
```
[HIER: Glossar mit Definitionen füllen]

| Begriff | Definition |
|---------|------------|
| Begriff 1 | Definition des Begriffs 1 |
| Begriff 2 | Definition des Begriffs 2 |
| Abkürzung 1 | Ausgeschrieben: ... - Bedeutung: ... |
| Abkürzung 2 | Ausgeschrieben: ... - Bedeutung: ... |
```

---

## Beteiligte Rollen

- **Softwarearchitekt:** Erstellt und pflegt die arc42 Architekturdokumentation. 
  Der Softwarearchitekt verwendet dieses Template zur strukturierten Dokumentation von Softwarearchitekturen. 
  Siehe `{PROMPT}/rollen/software-architect.md` für die vollständige Rollendefinition.
- **Product Owner:** Liefert Anforderungen (Kapitel 1.1) und Qualitätsziele (Kapitel 1.2) für die arc42 Architekturdokumentation. 
  Der Product Owner arbeitet mit dem Softwarearchitekten zusammen, um Anforderungen in Architektur zu übersetzen. 
  Siehe `{PROMPT}/rollen/product-owner.md` für die vollständige Rollendefinition.

## Erzeugte Artefakte

- **ADR (Architecture Decision Record):** Architekturentscheidungen (Kapitel 9) werden als ADRs dokumentiert. 
  ADRs dokumentieren wichtige technische Entscheidungen mit Context, erwogenen Optionen, Entscheidung und Konsequenzen. 
  Siehe `{PROMPT}/artefakte/architecture-decision-record.md` für das ADR-Template.
- **Feature-Spezifikation:** Feature-Spezifikationen beschreiben technische Umsetzung basierend auf der arc42 Architekturdokumentation. 
  Feature-Spezifikationen verwenden die arc42 Architekturdokumentation als Leitplanke für die technische Umsetzung. 
  Siehe `{PROMPT}/artefakte/feature-spezifikation.md` für das Feature-Spezifikation-Template.
- **SRS (Software Requirements Specification):** SRS-Dokumente definieren neue Produkt-Features mit technischen Anforderungen. 
  SRS-Dokumente werden nach Erstellung in die arc42 Architekturdokumentation integriert.

## Verknüpfungen zu anderen Artefakten

- **Anforderungsmanagement:** Anforderungen (Kapitel 1.1) werden strukturiert dokumentiert. 
  Das Anforderungsmanagement liefert die Basis für die arc42 Architekturdokumentation. 
  Siehe `{PROMPT}/artefakte/anforderungsmanagement.md` für das Anforderungsmanagement-Template.

---

## Anhang

### A. Abkürzungen

```
[HIER: Liste aller verwendeten Abkürzungen]
- ADR: Architecture Decision Record
- API: Application Programming Interface
- ...
```

### B. Referenzen

**Allgemeine Referenzen (immer gültig):**

- **arc42:** https://arc42.org/ - Offizielle arc42-Website
- **arc42 Dokumentation:** https://docs.arc42.org/ - Detaillierte Dokumentation mit Tipps und Beispielen
- **arc42 Template (GitHub):** https://github.com/arc42/arc42-template - Offizielles Template-Repository
- **ISO/IEC 25010:** Qualitätsmerkmale für Software (relevant für Qualitätsszenarien in Kapitel 10)

**Projektspezifische Referenzen (hier dokumentieren):**

```
[HIER: Projektspezifische Referenzen und Links dokumentieren]

### Dokumentation
- [Projektdokumentation]: [Link oder Pfad]
- [API-Dokumentation]: [Link oder Pfad]
- [Technische Spezifikationen]: [Link oder Pfad]

### Standards
- [Relevanter Standard 1]: [Beschreibung, Link]
- [Relevanter Standard 2]: [Beschreibung, Link]

### Tools
- [Tool 1]: [Beschreibung, Link]
- [Tool 2]: [Beschreibung, Link]

### Literatur
- [Buch/Artikel 1]: [Autor, Titel, Jahr]
- [Buch/Artikel 2]: [Autor, Titel, Jahr]

### Externe Systeme
- [Nachbarsystem 1]: [Dokumentation, Link]
- [Nachbarsystem 2]: [Dokumentation, Link]
```

### C. Changelog

```
[HIER: Änderungshistorie der Architekturdokumentation]

| Version | Datum | Autor | Änderung |
|---------|-------|-------|----------|
| 1.0 | [Datum] | [Autor] | Initiale Version |
| ... | ... | ... | ... |
```

---

## Hinweise für Autoren

### Allgemeine Richtlinien

1. **Zielgruppe beachten:** Die Dokumentation sollte für verschiedene Stakeholder verständlich sein (Entwickler, Product Owner, Operations, etc.)

2. **Detaillierungsgrad:** 
   - Nicht alles muss gleich detailliert sein
   - Wichtige und komplexe Bereiche sollten ausführlicher beschrieben werden
   - Einfache oder offensichtliche Aspekte können knapper sein

3. **Diagramme:**
   - Verwende Diagramme zur Visualisierung (z.B. Kontextdiagramm, Bausteindiagramm, Sequenzdiagramm)
   - Diagramme sollten konsistent sein (gleiche Notation, gleiche Abstraktionsebene)
   - Diagramme sollten selbsterklärend sein oder kurz erläutert werden

4. **Aktualität:**
   - Die Dokumentation sollte regelmäßig aktualisiert werden
   - Änderungen sollten im Changelog dokumentiert werden

5. **Flexibilität:**
   - arc42 ist ein Template - nicht alle Kapitel müssen vollständig ausgefüllt sein
   - Kapitel können angepasst, erweitert oder weggelassen werden, wenn es für das Projekt sinnvoll ist

6. **Konsistenz:**
   - Verwende konsistente Begriffe (siehe Glossar)
   - Halte den Schreibstil konsistent
   - Verwende einheitliche Formatierungen

**Hinweis:** Siehe Abschnitt "Empfohlene Reihenfolge beim Ausfüllen" weiter oben für zwei alternative Ansätze 
(basiert auf Abhängigkeiten vs. arc42-Standard-Reihenfolge).

### Tools und Notationen

- **Diagramme:** PlantUML, Mermaid, draw.io, Enterprise Architect, etc.
- **ADR:** Architecture Decision Records können in separaten Dateien oder in Kapitel 9 dokumentiert werden
- **Versionierung:** Die Dokumentation sollte zusammen mit dem Code versioniert werden
