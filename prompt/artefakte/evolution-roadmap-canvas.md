---
typ: artefakt
name: Evolution Roadmap Canvas
kontext: Hilfsvorlage zur schrittweisen Planung der Architekturentwicklung — Ist, Zielbild, Zwischenstufen, Migration, Abhängigkeiten und Risiken; ohne Big-Bang, mit realistischer Zeit-/Reihenfolge-Logik
rollen:
  - Softwarearchitekt
artefakte:
  - Architekturdokumentation nach arc42
  - Risk Technical Debt Canvas
  - Architecture Decision Record
  - Tradeoff Canvas Technik
  - Feature-Spezifikation
workflows: []
---

# Artefakt: Evolution / Roadmap Canvas

## Über den Evolution / Roadmap Canvas

Der **Evolution / Roadmap Canvas** strukturiert, **wie** sich eine Architektur **incrementell** weiterentwickeln soll: **Ausgangslage** und Druckpunkte, **Zielbild** und zentrale Verbesserungen, **sinnvolle Zwischenstufen** mit Reihenfolge, **Migrationsweg** inklusive Transformationsrisiken, **Abhängigkeiten** (technisch und organisatorisch) sowie **typische Stolpersteine**. Er unterstützt **keine** idealisierte Big-Bang-Umstellung, sondern **evolutionäre** Schritte, die mit Lieferrhythmus und Betrieb vereinbar sind.

**Typischer Anschluss:** Abgleich mit **Product Backlog** / Roadmap (PO), Verankerung in **arc42** (Strategie, Änderungen über die Zeit), **ADRs** pro größerem Schritt, **Feature-Spezifikationen** für konkrete Umsetzungspakete; Input aus **Risk / Technical Debt Canvas**.

---

## Sinn und Zweck

- **Transparenz:** Alle sehen denselben Pfad von „heute“ nach „dort hin“
- **Risikoarm:** Kleine, überprüfbare Schritte statt monolithischer Umbauten
- **Abstimmung:** Technik, Betrieb und Fachlichkeit an **gleicher** Erzählung
- **Entscheidungsgrundlage:** Wo **Tradeoffs** und **ADRs** nötig sind, wird sichtbar

---

## Eingabe (für die Sitzung / den Prompt)

| Platzhalter | Bedeutung |
|-------------|-----------|
| Aktuelles System | Ist-Architektur, Brownfield-Kontext |
| Zielbild (optional) | Gewünschter Soll-Zustand, Constraints |
| Bekannte Probleme (optional) | Schmerzpunkte, Schulden, Incidents |

---

## Ablage (außerhalb der Bibliothek)

Typisch unter `{DOCS}/`, z. B. `docs/architektur/evolution-roadmap-[system].md` oder Anhang zu `{SOFTWARE-ARCHITECTURE.MD}` / Strategiekapitel.

---

## Vorlage (Markdown)

```markdown
# Evolution / Roadmap Canvas: [Systemname]

**Datum:** [Datum]  
**Owner:** [z. B. Softwarearchitekt]  
**Horizont:** [z. B. 6 / 12 / 18 Monate]  
**Status:** [Entwurf | Vereinbart | Überholt]

## 1. Ausgangssituation

Zu dokumentieren:
- [HIER: **Aktueller Stand** der Architektur und Organisation — kurz, aber ehrlich]
- [HIER: **Hauptprobleme** — Performance, Kopplung, Betrieb, Time-to-Market, Compliance, …]

## 2. Zielbild

Zu dokumentieren:
- [HIER: **Gewünschte Architektur** — grob, nicht jedes Detail]
- [HIER: **Zentrale Verbesserungen** — 3–7 Punkte, die den Mehrwert tragen]

## 3. Entwicklungsschritte

Zu dokumentieren:
- [HIER: **Zwischenstufen** — evolvieren, nicht springen]
- [HIER: **Reihenfolge** — was muss vor was (technisch / fachlich / organisatorisch)]

### Optional: Zeitachse (logisch)

| Phase / Zeitraum | Zustand / Fähigkeit | Wesentliche Ergebnisse |
|------------------|---------------------|-------------------------|
| Jetzt | … | … |
| +[X] | … | … |
| Ziel | … | … |

## 4. Migration

Zu dokumentieren:
- [HIER: **Wie** vom Ist zum Ziel? — strangler, parallel run, feature toggles, Datenmigration, …]
- [HIER: **Risiken der Transformation** — Downtime, Datenverlust, Rollback, Doppelhaltung]

| Migrationsthema | Vorgehen | Risiko | Gegenmaßnahme |
|-------------------|----------|--------|----------------|
| … | … | … | … |

## 5. Abhängigkeiten

Zu dokumentieren:
- [HIER: **Technische** Abhängigkeiten — APIs, Daten, Releases anderer Teams, Infrastruktur]
- [HIER: **Organisatorische** Abhängigkeiten — Budget, Personal, Schulungen, Verträge]

| Abhängigkeit | Typ | Einfluss auf Roadmap |
|---------------|-----|----------------------|
| … | technisch / organisatorisch | … |

## 6. Risiken

Zu dokumentieren:
- [HIER: **Typische Stolpersteine** — Scope-Creep, falscher Schnitt der Schritte, ungetestete Migration]
- [HIER: **Mögliche Rückschläge** — was passiert bei Verzögerung, Prioritätswechsel]

| Risiko | Wahrscheinlichkeit / Impact (grob) | Frühindikator / Mitigation |
|--------|-------------------------------------|-----------------------------|
| … | … | … |

## Verknüpfung Backlog / ADR / arc42

Zu dokumentieren:
- [HIER: Verbindung zu `{PRODUCT-BACKLOG.MD}`, Epics/Features; ADRs für größere Richtungsentscheidungen; arc42-Aktualisierung pro Meilenstein]
```

---

## Anforderungen an die Ausfüllung

- **Realistische, schrittweise** Entwicklung — jeder Schritt sollte **liefer- und betreibbar** sein
- **Keine Big-Bang-Transformation** als Default; wenn unvermeidbar, **explizit** begründen und Risiken ausweisen
- **Risiken** klar benennen — inklusive politischer/organisatorischer Risiken
- **Annahmen** kennzeichnen (Last, Teamgröße, Genehmigungen)

---

## Zu dokumentieren (Kurz-Checkliste)

```
Größter Schmerzpunkt heute: [HIER]
Ein Satz Zielbild: [HIER]
Erster sinnvoller Zwischenschritt: [HIER]
Kritischste Migration: [HIER]
Ein Abhängigkeit, die alles blockieren kann: [HIER]
```
