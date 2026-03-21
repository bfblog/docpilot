---
typ: artefakt
name: Tradeoff Canvas Technik
kontext: Hilfsvorlage zur expliziten Abwägung konkurrierender technischer Qualitätsziele und Architekturfaktoren; optional als Workshop-Notiz oder Vorstufe zu einem ADR
rollen:
  - Softwarearchitekt
artefakte:
  - Tradeoff Canvas Produkt
  - Architecture Decision Record
  - arc42 Architekturdokumentation
workflows: []
---

# Artefakt: Tradeoff Canvas Technik

## Über den Tradeoff Canvas (Technik)

Der **Tradeoff Canvas Technik** strukturiert **Spannungen zwischen technischen Zielen** (nicht-funktionale Anforderungen, Betrieb, Komplexität, Kosten der Änderung). Er unterstützt Diskussionen im Team, bevor oder während eine Entscheidung in ein **Architecture Decision Record (ADR)** oder in arc42 (z. B. Qualitätsziele, Randbedingungen) einfließt.

**Abgrenzung:** Wirtschaftlicher Scope, Termindruck ohne technische Ursachen oder reine Backlog-Priorität gehören in den **Tradeoff Canvas Produkt** (`tradeoff-canvas-produkt.md`).

---

## Sinn und Zweck

- **Qualitätsziele sichtbar machen:** Was wird optimiert, was wird bewusst schlechter oder teurer akzeptiert?
- **Technische Schulden und Risiken benennen:** Tradeoffs explizit statt „still“ im Code
- **Bessere ADRs:** Kriterien und Abwägungen sind oft schon vorbereitet
- **Betrieb & Entwicklung:** Auswirkungen auf Monitoring, On-Call, Release, Testaufwand klären

---

## Ablage (außerhalb der Bibliothek)

Optional:

- `{DOCS}/{ADR}/` z. B. als `adr-entwurf-tradeoff-[thema].md` oder `drafts/tradeoff-[thema].md`
- oder Anhang in **Feature-Spezifikation** / **SRS**, wenn die Spannung featuregebunden ist

Nach gereifter Entscheidung: Kern in ein **ADR** überführen und den Canvas archivieren oder verlinken.

---

## Vorlage (Markdown)

```markdown
# Tradeoff Canvas Technik: [Kurztitel]

**Datum:** [Datum]  
**Owner:** [Softwarearchitekt / Team]  
**Status:** [Entwurf | Vereinbart | Überholt]

## 1. Technische Fragestellung

Zu dokumentieren:
[HIER: Welche Architektur- oder Technologiefrage löst den Tradeoff aus?]

## 2. Kontext & Randbedingungen

Zu dokumentieren:
[HIER: Bestehende Systeme, Vorgaben, Compliance, Teamgröße, Betriebsmodell, relevante Metriken]

## 3. Qualitätsattribute & Treiber

Typische *-ilities* und Faktoren (4–8 auswählen):

| Treiber | Kurzbeschreibung |
|---------|------------------|
| Performance / Latenz | … |
| Verfügbarkeit / Resilienz | … |
| Skalierbarkeit | … |
| Konsistenz / Korrektheit | … |
| Sicherheit | … |
| Wartbarkeit / Verständlichkeit | … |
| Time-to-Market / Änderbarkeit | … |
| Betriebsaufwand / Kosten | … |

Zu dokumentieren:
[HIER: Relevante Treiber für diese Frage]

## 4. Gewichtung / Priorität

Zu dokumentieren:
[HIER: Welche Treiber sind in diesem Kontext am wichtigsten, welche dürfen zurückstehen?]

## 5. Optionen oder Architekturvarianten

Zu dokumentieren:
[HIER: Z. B. synchrone vs. asynchrone Kommunikation, andere Datenbank, mehr Caching, stärkere Kopplung für Geschwindigkeit, …]

## 6. Bewertung der Optionen

| Option | Vorteile | Nachteile / Kosten | Risiken |
|--------|----------|--------------------|---------|
| [A] | … | … | … |
| [B] | … | … | … |

## 7. Empfehlung / Entscheidung

Zu dokumentieren:
[HIER: Bevorzugte Option und Begründung anhand der Gewichtung]

## 8. Konsequenzen

Zu dokumentieren:
[HIER: Auswirkungen auf Entwicklung, Tests, Deployment, Monitoring, Dokumentation; positive und negative Effekte]

## 9. Grenzen / Nicht-Ziele

Zu dokumentieren:
[HIER: Was löst diese Wahl nicht? Welche Qualitätsziele werden ausdrücklich nicht maximiert?]

## 10. Überleitung zu ADR / arc42

Zu dokumentieren:
[HIER: Link oder Titel des folgenden ADRs; welche arc42-Kapitel (z. B. 1, 4, 9) sind zu pflegen?]
```

---

## Hinweise für die Anwendung

- **Messbar machen**, wo möglich (z. B. P95-Latenz, Verfügbarkeit in %, RTO/RPO)
- **Eine Frage pro Canvas**; bei mehreren unabhängigen Themen trennen
- Nach Team-Alignment: **ADR** mit Status „Vorgeschlagen“ oder „Akzeptiert“ erstellen
- Wenn die Konfliktlinie primär **Produkt** ist (was liefern wir wann), zuerst **Tradeoff Canvas Produkt** klären

---

## Zu dokumentieren (Kurz-Checkliste)

```
Fragestellung: [HIER]
Treiber & Gewichtung: [HIER]
Empfehlung: [HIER]
Nicht-Ziele: [HIER]
ADR / arc42 Follow-up: [HIER]
```
