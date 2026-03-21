---
typ: artefakt
name: Tradeoff Canvas Produkt
kontext: Hilfsvorlage zur expliziten Abwägung konkurrierender Produkt-Prioritäten (Scope, Zeit, Wert, Risiko); optional als Workshop-Notiz oder kurzes Doku-Fragment außerhalb der Bibliothek
rollen:
  - Product Owner
artefakte:
  - Tradeoff Canvas Technik
  - Anforderungsmanagement
workflows: []
---

# Artefakt: Tradeoff Canvas Produkt

## Über den Tradeoff Canvas (Produkt)

Der **Tradeoff Canvas Produkt** strukturiert **Spannungen zwischen Produktzielen** und macht Prioritäten sowie bewusste Abstriche für Stakeholder nachvollziehbar. Er eignet sich für Backlog-Diskussionen, Release-Planung, MVP-Abgrenzung und Alignment zwischen Business, Nutzerbedarf und Lieferfähigkeit.

Er ist **kein** Ersatz für Anforderungsdokumente oder User Stories, sondern ein **Arbeits- und Kommunikationsformat** vor oder neben der formalen Priorisierung (MoSCoW, RICE, Value-vs.-Effort).

**Abgrenzung:** Technische Kompromisse zwischen Qualitätsattributen (z. B. Latenz vs. Konsistenz) gehören in den **Tradeoff Canvas Technik** (`tradeoff-canvas-technik.md`).

---

## Sinn und Zweck

- **Transparenz:** Warum wird etwas später, kleiner oder riskanter geliefert?
- **Alignment:** Gemeinsames Bild, welche Dimensionen „flexibel“ und welche „geschützt“ sind
- **Weniger Neuaushandlung:** Dokumentierte Tradeoffs können bei Kontextwechseln erneut genutzt werden
- **Brücke zum Team:** Klare Übergabe, welche Produktpriorität bei Konflikten Vorrang hat

---

## Ablage (außerhalb der Bibliothek)

Optional, je nach Projekt:

- `{DOCS}/` z. B. `docs/tradeoffs/produkt-[thema].md`
- oder als Anhang zu `{REQUIREMENTS.MD}` / Product-Backlog-Notizen

Persistenz ist **nicht zwingend**; der Canvas kann auch nur in einer Session ausgefüllt werden.

---

## Vorlage (Markdown)

```markdown
# Tradeoff Canvas Produkt: [Kurztitel]

**Datum:** [Datum]  
**Owner:** [Product Owner / Team]  
**Status:** [Entwurf | Vereinbart | Überholt]

## 1. Spannungsfeld / Fragestellung

Zu dokumentieren:
[HIER: Welche konkrete Entscheidung oder Prioritätsfrage soll geklärt werden?]

## 2. Kontext & Stakeholder

Zu dokumentieren:
[HIER: Geschäftslage, Deadline, Markt/Regulatorik, relevante Stakeholder und ihre Interessen]

## 3. Dimensionen (Tradeoff-Achsen)

Typische Dimensionen (3–6 auswählen oder anpassen):

| Dimension | Kurzbeschreibung |
|-------------|------------------|
| Nutzerwert / Business Value | … |
| Umfang / Scope | … |
| Zeit / Termin | … |
| Qualität / Polish (UX, Stabilität) | … |
| Risiko / Unsicherheit | … |
| Kosten / Kapazität | … |

Zu dokumentieren:
[HIER: Gewählte Dimensionen und warum genau diese für diese Frage relevant sind]

## 4. Gewichtung / Priorität

Zu dokumentieren:
[HIER: Reihenfolge oder Gewichtung – was ist in diesem Kontext am wenigsten verhandelbar, was am ehesten flexibel?  
Optional: Skala 1–5 oder „fix / wichtig / flexibel“ pro Dimension]

## 5. Optionen oder Szenarien

Zu dokumentieren:
[HIER: Z. B. „Alles in Release X“, „MVP ohne Feature A“, „Termin schieben“ – kurz benennen]

## 6. Bewertung der Optionen

| Option / Szenario | Was gewinnen wir? | Was geben wir bewusst auf? | Risiko |
|-------------------|-------------------|----------------------------|--------|
| [Option 1] | … | … | … |
| [Option 2] | … | … | … |

## 7. Vereinbarung

Zu dokumentieren:
[HIER: Welche Option gilt? Kurze Begründung in einem Absatz]

## 8. Konsequenzen & Follow-up

Zu dokumentieren:
[HIER: Auswirkungen auf Backlog, Roadmap, Kommunikation; offene Punkte; Review-Datum]

## 9. Grenzen / Nicht-Ziele

Zu dokumentieren:
[HIER: Wofür gilt diese Vereinbarung nicht? Was wird ausdrücklich nicht entschieden?]

## 10. Schnittstelle zur Technik (optional)

Zu dokumentieren:
[HIER: Wenn sich daraus technische Spannungen ergeben – Verweis auf Tradeoff Canvas Technik oder ADR]
```

---

## Hinweise für die Anwendung

- Pro Canvas **eine** klare Fragestellung; bei mehreren Themen separate Canvas-Dateien
- **Konkrete** Annahmen statt vager Prioritäten („schnell“ → bis wann, welcher Umfang?)
- Bei fehlenden Informationen: Annahmen treffen und **kennzeichnen**
- Bei starker technischer Komponente: **Tradeoff Canvas Technik** einbeziehen oder nacheinander nutzen

---

## Zu dokumentieren (Kurz-Checkliste)

```
Spannungsfeld: [HIER: eine Satz-Frage]
Dimensionen und Gewichtung: [HIER]
Vereinbarung: [HIER]
Nicht-Ziele: [HIER]
```
