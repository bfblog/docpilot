---
typ: artefakt
name: Architecture Decision Canvas
kontext: Hilfsvorlage zur strukturierten Erarbeitung einer Architekturentscheidung — Problem, Kontext, Optionen, Kriterien, Bewertung, Entscheidung, Konsequenzen und Nicht-Ziele; typische Zwischenstufe zwischen Tradeoff Canvas und ADR
rollen:
  - Softwarearchitekt
artefakte:
  - Tradeoff Canvas Technik
  - Tradeoff Canvas Produkt
  - Architecture Decision Record
  - arc42 Architekturdokumentation
  - Feature-Spezifikation
workflows: []
---

# Artefakt: Architecture Decision Canvas

## Über den Architecture Decision Canvas

Der **Architecture Decision Canvas** strukturiert die **Erarbeitung einer einzelnen Architekturentscheidung**: präzise **Fragestellung**, **Kontext**, **Optionen**, **Bewertungskriterien**, **systematische Bewertung**, **gewählte Option mit Begründung**, **Konsequenzen** und explizite **Nicht-Ziele**. Er zielt auf **Klarheit und Nachvollziehbarkeit** — ohne generische Floskeln.

**Typische Einordnung:** Oft **nach** einem **Tradeoff Canvas** (Produkt und/oder Technik), wenn Optionen und Spannungen schon sichtbar sind, aber noch **keine** bindende Entscheidung mit vollständiger Begründung vorliegt. Das Ergebnis fließt in ein **Architecture Decision Record (ADR)** und ggf. in **arc42** (Randbedingungen, Lösungsstrategie, Bausteine).

**Abgrenzung:** Kein Ersatz für das **ADR** — der Canvas ist **Arbeits- und Workshop-Dokument**; das ADR ist die **knappe, langfristige** Festlegung.

---

## Sinn und Zweck

- **Entscheidungsgegenstand schärfen:** Was genau wird entschieden — und was nicht?
- **Optionen vollständig machen:** Auch „weitermachen wie bisher“ und bewusstes Nicht-Tun als Option
- **Kriterien explizit machen:** Qualitätsattribute und Randbedingungen als Bewertungsmaßstab
- **Begründung dokumentieren:** Warum diese Option, welche Abstriche?
- **Konsequenzen und Risiken:** Betrieb, Team, Architektur, Folgeentscheidungen
- **Nicht-Ziele:** Scope der Entscheidung begrenzen — verhindert spätere Fehlinterpretation

---

## Ablage (außerhalb der Bibliothek)

Typisch unter `{DOCS}/`, z. B.:

- `docs/architektur/decisions/draft/decision-canvas-[kurzname].md`
- oder neben dem späteren ADR als Entwurf, bis der **ADR** unter `{DOCS}/{ADR}/` angelegt ist

Nach Festlegung: **Kern** in **ADR** übernehmen; Canvas archivieren oder per Link vom ADR aus referenzieren.

---

## Vorlage (Markdown)

```markdown
# Architecture Decision Canvas: [Kurztitel / Thema]

**Datum:** [Datum]  
**Owner:** [Softwarearchitekt / Team]  
**Status:** [Entwurf | Zur Abstimmung | Entschieden | Überholt]

## 1. Entscheidung — was soll entschieden werden?

Zu dokumentieren:
[HIER: Präzise Fragestellung — ein Satz oder kurze Bullet-Liste, was bindend geklärt werden muss]

## 2. Kontext

Zu dokumentieren:
[HIER: Rahmenbedingungen, Annahmen, Einschränkungen — technisch, organisatorisch, zeitlich, regulatorisch]

## 3. Optionen

Zu dokumentieren:
[HIER: Alle sinnvollen Alternativen, inkl. Status quo / „nichts ändern“; fehlende Optionen ergänzen]

| Option | Kurzbeschreibung |
|--------|------------------|
| A | … |
| B | … |
| C | … |

## 4. Bewertungskriterien

Zu dokumentieren:
[HIER: Qualitätsattribute und Entscheidungsfaktoren — z. B. Skalierbarkeit, Performance, Komplexität, Betrieb, Kosten, Time-to-Market, Sicherheit]

| Kriterium | Gewichtung / Priorität (grob) | Begründung |
|-----------|-------------------------------|------------|
| … | hoch / mittel / niedrig | … |

## 5. Bewertung der Optionen

Zu dokumentieren (pro Option):

| Option | Vorteile | Nachteile |
|--------|----------|-----------|
| A | … | … |
| B | … | … |
| C | … | … |

## 6. Entscheidung — gewählte Option und Begründung

Zu dokumentieren:
[HIER: **Empfehlung** — welche Option; klare Begründung **anhand der Kriterien**; ggf. bewusst akzeptierte Nachteile]

**Gewählte Option:** [A | B | C | …]

## 7. Konsequenzen

Zu dokumentieren:

- **Positive Effekte:** …
- **Negative Effekte / Risiken:** …
- **Auswirkungen auf Betrieb:** …
- **Auswirkungen auf Entwicklung / Team:** …
- **Auswirkungen auf Architektur** (Bausteine, Schnittstellen, nächste ADRs): …

## 8. Grenzen / Nicht-Ziele

Zu dokumentieren:
[HIER: Wofür diese Entscheidung **nicht** gilt — explizit abgrenzen, um Scope-Creep zu vermeiden]

---

## Nächster Schritt

- Ergebnis in **ADR** überführen: `{PROMPT}/artefakte/architecture-decision-record.md`
- **arc42** und **Feature-Spezifikationen** bei Bedarf aktualisieren
```

---

## Anforderungen an die Ausfüllung

- **Klar und prägnant** — keine Worthülsen
- **Konkrete, fachlich fundierte Argumente** statt generischer Aussagen
- **Fehlende Informationen:** sinnvolle **Annahmen** treffen und **als Annahme kennzeichnen**
- **Buzzwords** nur mit kurzer Erklärung oder gar nicht
- **Tabellen** für Vergleiche nutzen, wo es die Lesbarkeit erhöht

---

## Prompt für die Sitzung (KI)

```markdown
Du bist ein erfahrener Softwarearchitekt. Hilf mir, eine Architekturentscheidung strukturiert mit einem **Architecture Decision Canvas** zu erarbeiten.

## Ziel

Erarbeite eine klare, nachvollziehbare Entscheidung inklusive Begründung und Konsequenzen.

## Eingabe

* Problem / Fragestellung: {{Problem}}
* Kontext: {{Kontext}}
* Bekannte Optionen (optional): {{Optionen}}
* Anforderungen / Kriterien (optional): {{Kriterien}}

## Aufgabe

Strukturiere die Analyse als **Architecture Decision Canvas** mit folgenden Abschnitten:

### 1. Entscheidung

Formuliere präzise, was entschieden werden soll.

### 2. Kontext

Beschreibe die relevanten Rahmenbedingungen, Annahmen und Einschränkungen.

### 3. Optionen

Liste alle sinnvollen Alternativen auf (inkl. bestehender Lösungen). Ergänze fehlende Optionen, falls nötig.

### 4. Bewertungskriterien

Leite die wichtigsten Qualitätsattribute und Entscheidungsfaktoren ab (z. B. Skalierbarkeit, Performance, Komplexität, Betrieb, Kosten).

### 5. Bewertung der Optionen

Bewerte jede Option strukturiert:

* Vorteile
* Nachteile

### 6. Entscheidung

Empfehle eine Option und begründe sie klar anhand der Kriterien.

### 7. Konsequenzen

Beschreibe die Auswirkungen der Entscheidung:

* positive Effekte
* negative Effekte / Risiken
* Auswirkungen auf Betrieb, Entwicklung und Architektur

### 8. Grenzen / Nicht-Ziele

Definiere explizit, wofür diese Entscheidung **nicht** gilt.

## Anforderungen an die Antwort

* Klar, prägnant und strukturiert
* Keine generischen Aussagen
* Konkrete, fachlich fundierte Argumente
* Wenn Informationen fehlen, triff sinnvolle Annahmen und kennzeichne sie
* Vermeide Buzzwords ohne Erklärung

## Ausgabeformat

Nutze klare Überschriften und ggf. Tabellen für Vergleiche.
```
