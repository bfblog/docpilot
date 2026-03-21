---
typ: artefakt
name: Quality Attribute Canvas
kontext: Hilfsvorlage zur Identifikation, Priorisierung und Konkretisierung der wichtigsten Qualitätsattribute (NFR) mit Szenarien, Zielkonflikten und Risiken; Anschluss an arc42 Qualitätsziele und Qualitätsszenarien
rollen:
  - Softwarearchitekt
artefakte:
  - Architekturdokumentation nach arc42
  - Tradeoff Canvas Technik
  - Risk Technical Debt Canvas
  - Architecture Decision Record
  - Feature-Spezifikation
workflows: []
---

# Artefakt: Quality Attribute Canvas

## Über den Quality Attribute Canvas

Der **Quality Attribute Canvas** bündelt die **wichtigsten Qualitätsanforderungen** (nicht-funktionale Anforderungen, *-ilities*): welche Attribute **relevant** sind, wie sie **priorisiert** werden, wie sie sich in **konkreten Szenarien** ausdrücken, wo **Zielkonflikte** entstehen und welche **Risiken** drohen, wenn Ziele verfehlt werden. Er dient dem **gemeinsamen Verständnis** zwischen Architektur, Entwicklung, Betrieb und Fachbereich — **ohne** bereits alle technischen Lösungen festzulegen.

**Typischer Anschluss:** Inhalte fließen in **arc42 Kapitel 1.2 (Qualitätsziele)** und **Qualitätsszenarien**, in **`{REQUIREMENTS.MD}`** (NFR), in **Feature-Spezifikationen** und bei harten Spannungen in den **Tradeoff Canvas Technik** sowie in **ADRs**.

---

## Sinn und Zweck

- **Fokus:** Die wenigen wirklich **entscheidenden** Qualitätsattribute statt einer endlosen NFR-Liste
- **Messbarkeit:** Szenarien im Stil „Wenn …, dann … innerhalb von …“ (an ISO/IEC 25010 / arc42-Qualitätsszenarien angelehnt)
- **Transparenz:** **Zielkonflikte** benennen statt später im Projekt „auszuverhandeln“
- **Risiko:** Folgen von **Nichterreichen** explizit machen (Betrieb, Compliance, Kosten)

---

## Eingabe (für die Sitzung / den Prompt)

| Platzhalter | Bedeutung |
|-------------|-----------|
| System / Vorhaben | Name oder Scope |
| Kontext | Nutzung, Last, regulatorisch, Cloud/On-Prem, kritikalität |
| Bekannte Anforderungen (optional) | Bereits genannte NFR, SLAs, Standards |

---

## Ablage (außerhalb der Bibliothek)

Typisch unter `{DOCS}/` oder in `{SOFTWARE-ARCHITECTURE.MD}` / `{REQUIREMENTS.MD}`, z. B. `docs/qualitaet/[system]-quality-attribute-canvas.md`.

---

## Vorlage (Markdown)

```markdown
# Quality Attribute Canvas: [System / Vorhaben]

**Datum:** [Datum]  
**Owner:** [z. B. Softwarearchitekt]  
**Status:** [Entwurf | Vereinbart | Überholt]

## 1. Qualitätsattribute

Zu dokumentieren:
- [HIER: Die **wichtigsten** Qualitätsmerkmale für dieses System — bewusst begrenzte Liste]
- [HIER: Kurz, **warum** jedes Attribut für dieses Vorhaben relevant ist]

Typische Kategorien (nur nutzen, was passt): Performance, Skalierbarkeit, Verfügbarkeit, Sicherheit, Wartbarkeit, Änderbarkeit, Benutzbarkeit, Kompatibilität, Betreibbarkeit, Kosten / Ressourcenverbrauch, Compliance.

| Qualitätsattribut | Kurz: Relevanz für dieses System |
|-------------------|----------------------------------|
| … | … |

## 2. Priorisierung

Zu dokumentieren:
- [HIER: Gewichtung **hoch / mittel / niedrig** je Attribut mit **einer Satz-Begründung**]

| Qualitätsattribut | Priorität (hoch / mittel / niedrig) | Begründung (kurz) |
|-------------------|-------------------------------------|-------------------|
| … | … | … |

## 3. Konkretisierung (Szenarien)

Zu dokumentieren:
- [HIER: **Konkrete** Szenarien — möglichst **messbar** oder überprüfbar]
- [HIER: Muster: „Wenn **[Stimulus]** eintritt, muss das System **[Reaktion]** innerhalb von **[Maß]** liefern“]

| ID | Szenario (Stimulus → Reaktion → Maß) | Bezug zu Attribut(en) |
|----|--------------------------------------|------------------------|
| QA-1 | … | … |

## 4. Zielkonflikte

Zu dokumentieren:
- [HIER: **Spannungsfelder** zwischen Qualitätsattributen — klar benennen, keine generischen „Tradeoffs“ ohne Kontext]

| Konflikt (Attribut A vs. Attribut B) | Beschreibung | Hinweis auf Klärung (Tradeoff Canvas / ADR) |
|--------------------------------------|--------------|---------------------------------------------|
| … | … | … |

## 5. Risiken

Zu dokumentieren:
- [HIER: Was passiert, wenn zentrale Qualitätsziele **nicht** erreicht werden? — Betrieb, Reputation, Kosten, rechtliche Folgen]

| Qualitätsziel / Szenario | Risiko bei Nichterreichen | Wahrscheinlichkeit / Schaden (grob) |
|---------------------------|---------------------------|-------------------------------------|
| … | … | … |

## Annahmen

Zu dokumentieren:
- [HIER: Alle **Annahmen** zu Last, Nutzerverhalten, Infrastruktur — explizit kennzeichnen]

## Verknüpfung arc42 / Anforderungen

Zu dokumentieren:
- [HIER: Übernahme in arc42 Kapitel 1.2 und Qualitätsszenarien; Verweis auf `{REQUIREMENTS.MD}` / Feature-Spezifikationen]
```

---

## Anforderungen an die Ausfüllung

- **Keine generischen Floskeln** („schnell“, „sicher“, „skalierbar“ ohne Kontext)
- **Konkrete, bevorzugt messbare** Formulierungen in den Szenarien
- **Zielkonflikte** explizit; bei Bedarf **Tradeoff Canvas Technik** oder **ADR** vormerken
- **Annahmen** immer sichtbar machen

---

## Zu dokumentieren (Kurz-Checkliste)

```
Top-3-Qualitätsziele (nach Priorität): [HIER]
Stärkstes Szenario (eine Zeile): [HIER]
Größter Zielkonflikt: [HIER]
Größtes Risiko bei Fehlschlag: [HIER]
```
