---
typ: artefakt
name: Risk Technical Debt Canvas
kontext: Hilfsvorlage zur systematischen Erfassung von Risiken, Unsicherheiten und technischer Schuld — mit Ursachen, Auswirkungen, Wahrscheinlichkeit/Impact, Maßnahmen und Priorisierung; ehrliche, nicht beschönigende Bewertung
rollen:
  - Softwarearchitekt
artefakte:
  - Architekturdokumentation nach arc42
  - Quality Attribute Canvas
  - Integration Canvas
  - Architecture Decision Record
  - Evolution Roadmap Canvas
  - Tradeoff Canvas Technik
  - Feature-Spezifikation
workflows: []
---

# Artefakt: Risk / Technical Debt Canvas

## Über den Risk / Technical Debt Canvas

Der **Risk / Technical Debt Canvas** bündelt **Risiken** (technisch, organisatorisch, Integration) und **technische Schulden**: was **droht** oder **lastet**, **warum** es so ist, welche **Folgen** eintreten können, wie **wahrscheinlich** und **schwerwiegend** das ist, und welche **Maßnahmen** (Vermeidung, Reduktion, Monitoring) sinnvoll sind. Ziel ist **Sichtbarkeit und Bewertbarkeit** — **keine** Beschönigung und **kein** „Risiko-Orakel“, sondern eine **arbeitsfähige Übersicht** für Architektur, Team und Stakeholder.

**Typischer Anschluss:** Übernahme in **arc42** (u. a. **Risiken**, Randbedingungen, Qualität), in **Backlog** / Roadmap für Schuldenabbau, in **Feature-Spezifikationen** als bekannte Randbedingung, und bei **strategischen** Abweichungen in **ADRs** oder **Tradeoff Canvas Technik**.

---

## Sinn und Zweck

- **Implizite Risiken** und **still akzeptierte Schulden** benennen
- **Priorisierung** über Wahrscheinlichkeit × Auswirkung
- **Maßnahmen** klar zuordnen (vermeiden vs. reduzieren vs. beobachten)
- **Verbindung** zwischen bewussten Kompromissen (ADRs, Zeitdruck) und **nachwachsender Schuld** herstellen

---

## Eingabe (für die Sitzung / den Prompt)

| Platzhalter | Bedeutung |
|-------------|-----------|
| System / Kontext | Was wird betrachtet? Brownfield, Release, Teilprojekt |
| Bekannte Probleme (optional) | Incidents, Reviews, bekannte Hotspots |
| Annahmen (optional) | Explizit kennzeichnen |

---

## Ablage (außerhalb der Bibliothek)

Typisch unter `{DOCS}/`, z. B. `docs/risiken/[system]-risk-debt-canvas.md` oder als lebendes Dokument mit Revisionsdatum.

---

## Vorlage (Markdown)

```markdown
# Risk / Technical Debt Canvas: [System / Kontext]

**Datum:** [Datum]  
**Owner:** [z. B. Softwarearchitekt]  
**Review-Zyklus:** [z. B. quartalsweise / nach Major Release]  
**Status:** [Entwurf | Vereinbart | Überholt]

## 1. Risiken

Zu dokumentieren:
- [HIER: **Technische** Risiken — z. B. Skalierung, Single Point of Failure, veraltete Plattform]
- [HIER: **Organisatorische** Risiken — z. B. Bus-Faktor, fehlende Skills, Abhängigkeit von Drittanbietern]
- [HIER: **Integrationsrisiken** — z. B. instabile APIs, fehlende SLAs, Brüche bei Datenformaten]

| ID | Kategorie (technisch / organisatorisch / Integration) | Kurzbeschreibung des Risikos |
|----|---------------------------------------------------------|------------------------------|
| R-1 | … | … |

## 2. Ursachen

Zu dokumentieren:
- [HIER: **Warum** entsteht jedes relevante Risiko? — Wurzeln, nicht nur Symptome]

| Risiko-ID | Ursache(n) |
|-----------|------------|
| R-1 | … |

## 3. Auswirkungen

Zu dokumentieren:
- [HIER: Was passiert bei **Eintritt** bzw. wenn die Schuld **eskalieren** darf?]

| Risiko-ID | Auswirkung (fachlich / technisch / betrieblich) |
|-----------|--------------------------------------------------|
| R-1 | … |

## 4. Wahrscheinlichkeit & Impact

Bewertung je **hoch / mittel / niedrig** (Definition im Team kurz festhalten, z. B. in Fußnote).

| Risiko-ID | Eintrittswahrscheinlichkeit | Auswirkung (Impact) | Priorität (z. B. P1–P3 oder Matrix) |
|-----------|------------------------------|---------------------|-------------------------------------|
| R-1 | hoch / mittel / niedrig | hoch / mittel / niedrig | … |

**Priorisierung:** Fokus auf **relevante** Einträge — nicht jedes kleine Thema als „hoch“ einstufen.

## 5. Maßnahmen

Zu dokumentieren:
- [HIER: **Vermeidung** — was tun wir, damit es nicht entsteht / nicht wächst]
- [HIER: **Reduktion** — konkrete Arbeiten, Owner, Zieltermin wo möglich]
- [HIER: **Monitoring** — Metriken, Alerts, Reviews, Risiko-Indikatoren]

| Risiko-ID | Vermeidung | Reduktion | Monitoring |
|-----------|------------|-----------|------------|
| R-1 | … | … | … |

## 6. Technische Schulden

Zu dokumentieren:
- [HIER: **Bewusste** Kompromisse — mit **Verweis** auf ADR, Release-Druck oder bewusste „Wir nehmen X in Kauf“]
- [HIER: **Unbewusste** oder **historische** Schulden — erkannt durch Reviews, Incidents]
- [HIER: **Folgekosten** — Wartung, Geschwindigkeit, Fehleranfälligkeit]

| Schulden-Item | Entstanden durch (bewusst / unbewusst) | Kurzbeschreibung | Folge / Zins |
|----------------|----------------------------------------|------------------|--------------|
| TD-1 | … | … | … |

## Annahmen & offene Punkte

Zu dokumentieren:
- [HIER: Unsicherheiten, die die Bewertung beeinflussen]

## Verknüpfung arc42 / Backlog / ADR

Zu dokumentieren:
- [HIER: arc42-Risikoabschnitt; Backlog-Items; ADRs zu Schulden-Strategie]
```

---

## Anforderungen an die Ausfüllung

- **Ehrlich und kritisch** — keine Beschönigung zu Gunsten des „guten Gefühls“
- **Fokus** auf Risiken und Schulden mit **echter** Tragweite
- **Implizite** Risiken aktiv suchen (Abhängigkeiten, implizite Annahmen, fehlende Tests/Monitoring)
- **Mess- oder Review-Kriterien** wo möglich statt vager „wir beobachten das“

---

## Zu dokumentieren (Kurz-Checkliste)

```
Top-3-Risiken (nach Priorität): [HIER]
Größte technische Schuld (eine Zeile): [HIER]
Eine Maßnahme mit Owner und Datum: [HIER]
Ein implizites Risiko, das sichtbar wurde: [HIER]
```
