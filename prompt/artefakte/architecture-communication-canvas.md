---
typ: artefakt
name: Architecture Communication Canvas
kontext: Hilfsvorlage zur zielgruppengerechten Vermittlung von Architektur — Kernbotschaften, passende Sichten, Kommunikationsmittel, bewusste Vereinfachung und Kommunikationsrisiken; ergänzt arc42/C4, ersetzt sie nicht
rollen:
  - Softwarearchitekt
artefakte:
  - Architekturdokumentation nach arc42
  - System Context Canvas
  - Architecture Building Blocks Canvas
  - Integration Canvas
workflows: []
---

# Artefakt: Architecture Communication Canvas

## Über den Architecture Communication Canvas

Der **Architecture Communication Canvas** strukturiert, **wie** Architektur **verständlich und wirkungsvoll** vermittelt wird: **Zielgruppen** und ihre Bedürfnisse, **Kernbotschaften** pro Gruppe, **relevante Sichten** (Kontext, Bausteine, Datenflüsse, …), **Kommunikationsmittel** (Diagramme, Dokumente, Präsentationen), **bewusste Vereinfachung** sowie **Risiken** in der Kommunikation (Missverständnisse, falsche Erwartungen). Er adressiert **nicht den technischen Inhalt** der Architektur allein, sondern die **Aufbereitung** und den **Kanal**.

Die Idee steht im Umfeld der [Software Architecture Canvas](https://canvas.arc42.org/)-Familie; siehe auch [Architecture Communication Canvas (arc42)](https://canvas.arc42.org/architecture-communication-canvas).

**Abgrenzung:** **Kein Ersatz** für `{SOFTWARE-ARCHITECTURE.MD}` / arc42 — sondern **Plan**, **wie** aus dem vorhandenen oder geplanten Material **die richtigen** Aussagen für **die richtigen** Personen entstehen.

---

## Sinn und Zweck

- **Zielgruppenorientierung** statt „ein Dokument für alle“
- **Klare Takeaways** — was soll „hängen bleiben“?
- **Reduktion von Komplexität** durch bewusstes Weglassen pro Kontext
- **Frühzeitige** Erkennung von **Kommunikationsrisiken**

---

## Eingabe (für die Sitzung / den Prompt)

| Platzhalter | Bedeutung |
|-------------|-----------|
| System / Architektur | Was soll vermittelt werden? |
| Zielgruppen (optional) | z. B. Management, Fachbereich, Entwicklung, Betrieb |
| Kontext | Anlass: Review, Onboarding, Ausschreibung, Release, Audit |

---

## Ablage (außerhalb der Bibliothek)

Typisch unter `{DOCS}/`, z. B. `docs/architektur/kommunikation-[system]-canvas.md` oder als Anhang zur Präsentationsplanung.

---

## Vorlage (Markdown)

```markdown
# Architecture Communication Canvas: [System / Architektur]

**Datum:** [Datum]  
**Owner:** [z. B. Softwarearchitekt]  
**Anlass:** [Review / Onboarding / …]  
**Status:** [Entwurf | Vereinbart | Überholt]

## 1. Zielgruppen

Zu dokumentieren:
- [HIER: **Wer** soll die Architektur verstehen bzw. welche Entscheidung soll unterstützt werden?]
- [HIER: **Bedürfnis** je Gruppe — z. B. Entscheidungsreife, operative Einschätzung, fachliches Vertrauen]

| Zielgruppe | Bedarf / Fragestellung |
|------------|-------------------------|
| … | … |

## 2. Kernbotschaften

Zu dokumentieren:
- [HIER: Was muss jede **wichtige** Zielgruppe **unbedingt** mitnehmen?]
- [HIER: Formulierungen **kurz und prägnant** — keine Technik-Jargon-Wände für Nicht-Techniker]

| Zielgruppe | Kernbotschaft (1–3 Sätze) |
|------------|---------------------------|
| … | … |

## 3. Relevante Sichten

Zu dokumentieren:
- [HIER: Welche **Perspektiven** sind für welche Gruppe **relevant**? — z. B. Systemkontext, Bausteine/Container, Datenflüsse, Deployment, Sicherheitszonen]
- [HIER: Verweis auf arc42-Kapitel / C4-Ebenen / bestehende Diagramme]

| Zielgruppe | Sichten (Priorität) | Quelle in Dokumentation |
|------------|---------------------|-------------------------|
| … | … | … |

## 4. Kommunikationsmittel

Zu dokumentieren:
- [HIER: **Diagramme** — welche, für wen, welches Detailgrad]
- [HIER: **Dokumente** — arc42-Auszüge, One-Pager, ADR-Zusammenfassung]
- [HIER: **Präsentationen** / Workshops — Dauer, interaktiv vs. frontal]

| Mittel | Zielgruppe | Inhalt / Link |
|--------|------------|---------------|
| … | … | … |

## 5. Vereinfachung

Zu dokumentieren:
- [HIER: Was wird **bewusst weggelassen** oder nur „on demand“ erklärt?]
- [HIER: Wie wird **Komplexität reduziert** — Metaphern, Schichtung, iteratives Tiefergehen]

## 6. Risiken in der Kommunikation

Zu dokumentieren:
- [HIER: Typische **Missverständnisse** (z. B. „Microservices = unabhängige Teams“ ohne Abstimmungskosten)]
- [HIER: **Falsche Erwartungen** (Verfügbarkeit, Kosten, Zeit bis Feature X)]
- [HIER: Gegenmaßnahmen — explizite Nicht-Ziele, Glossar, Q&A]

| Risiko | Betroffene Zielgruppe | Mitigation |
|--------|------------------------|------------|
| … | … | … |

## Verknüpfung zur Architekturdokumentation

Zu dokumentieren:
- [HIER: `{SOFTWARE-ARCHITECTURE.MD}`, ADRs, ggf. Canvas-Artefakte als Rohmaterial]
```

---

## Anforderungen an die Ausfüllung

- **Zielgruppenorientiert** denken — Sprache und Tiefe anpassen
- **Komplexität reduzieren** — weniger ist oft mehr pro Termin
- **Klare Botschaften** — testen: „Könnte jemand nach dem Termin in einem Satz wiedergeben, worum es ging?“
- **Keine unnötigen Details** im ersten Kontakt; Vertiefung **nach Bedarf**

---

## Zu dokumentieren (Kurz-Checkliste)

```
Wichtigste Zielgruppe: [HIER]
Eine unverzichtbare Kernbotschaft: [HIER]
Eine bewusst weggelassene Komplexität: [HIER]
Größtes Kommunikationsrisiko: [HIER]
```
