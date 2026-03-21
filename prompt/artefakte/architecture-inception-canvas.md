---
typ: artefakt
name: Architecture Inception Canvas
kontext: Hilfsvorlage für ein gemeinsames Bild zu Zielen, Stakeholdern, Problem, Systemidee und Rahmenbedingungen eines Vorhabens — vor Detailarchitektur und vor verbindlichen Architekturentscheidungen
rollen:
  - Softwarearchitekt
artefakte:
  - Architekturdokumentation nach arc42
  - System Context Canvas
  - Domain Bounded Context Canvas
  - Quality Attribute Canvas
  - Tradeoff Canvas Produkt
  - Tradeoff Canvas Technik
workflows: []
---

# Artefakt: Architecture Inception Canvas

## Über den Architecture Inception Canvas

Der **Architecture Inception Canvas** strukturiert die **frühe Klärung** eines Projekts oder Vorhabens: Ziele, Betroffene, Probleme, eine grobe Systemidee, Randbedingungen, Risiken und bewusste Nicht-Ziele. Er orientiert sich am Konzept der **Software Architecture Canvas**-Familie (u. a. im Umfeld von [arc42 Canvas](https://canvas.arc42.org/)) und dient dem **gemeinsamen Verständnis** zwischen Fachbereich und Technik — **ohne** bereits eine ausgearbeitete Architektur oder technische Feinentscheidungen zu liefern.

**Abgrenzung:**

- **Kein Ersatz** für arc42, ADR oder Feature-Spezifikation — sondern **Input** und **Alignment** davor.
- **Tradeoff Canvas** und **Architecture Decision Canvas** greifen typisch **danach**, wenn Optionen und Entscheidungen im Fokus stehen (siehe `{PROMPT}/doc/artefakt-zusammenhaenge.md`).

---

## Sinn und Zweck

- **Einheitliches Bild** vor Investition in Design und Implementierung
- **Frühe Sichtbarkeit** von Risiken, Annahmen und Widersprüchen
- **Grundlage** für Vision, Anforderungen (`{REQUIREMENTS.MD}`) und später arc42 (z. B. Stakeholder, Randbedingungen, Kontext)
- **Workshop-tauglich** (1–2 Seiten, Stichpunkte)

---

## Eingabe (für die Sitzung / den Prompt)

| Platzhalter | Bedeutung |
|-------------|-----------|
| Vorhaben / Projekt | Kurzname oder Initiative |
| Problemstellung | Was soll verbessert oder ermöglicht werden? |
| Kontext (optional) | Markt, Legacy, regulatorisch, organisatorisch |
| Stakeholder (optional) | Bekannte Rollen/Gruppen |
| Annahmen (optional) | Explizit oder von der KI ergänzt und gekennzeichnet |

---

## Ablage (außerhalb der Bibliothek)

Typisch unter `{DOCS}/`, z. B. `docs/inception/[vorhaben]-inception-canvas.md` oder als Anhang zur Vision — je nach Projektvereinbarung. Persistenz ist sinnvoll, damit spätere Teams den Ausgangspunkt nachvollziehen können.

---

## Vorlage (Markdown)

**Zielumfang:** strukturierte Abschnitte mit Stichpunkten, **maximal etwa 1–2 Seiten** (ohne Romane, keine Detailarchitektur).

```markdown
# Architecture Inception Canvas: [Vorhaben / Projekt]

**Datum:** [Datum]  
**Facilitator:** [z. B. Softwarearchitekt]  
**Teilnehmer:** [optional]  
**Status:** [Entwurf | Vereinbart | Überholt]

## 1. Ziele (Business & Technik)

Zu dokumentieren:
- [HIER: Was soll erreicht werden? Business- und technische Ziele, messbar oder beschreibbar]
- [HIER: Erfolgskriterien — wann gilt das Vorhaben als erfolgreich angestoßen bzw. abgeschlossen?]

## 2. Stakeholder & Nutzer

Zu dokumentieren:
- [HIER: Wer ist betroffen, wer nutzt das System, wer entscheidet mit?]
- [HIER: Interessen und Ziele der wichtigsten Gruppen]

## 3. Probleme / Needs

Zu dokumentieren:
- [HIER: Konkrete Probleme, die gelöst werden sollen]
- [HIER: Pain Points der aktuellen Situation (As-Is)]

## 4. Systemidee (High-Level)

Zu dokumentieren:
- [HIER: Grobe Lösungsskizze in wenigen Sätzen — keine Detailarchitektur]
- [HIER: Zentrale Prinzipien oder Ansätze (z. B. API-first, schrittweise Migration, SaaS)]

## 5. Randbedingungen & Constraints

Zu dokumentieren:
- [HIER: Technische Vorgaben — bestehende Systeme, Stacks, Standards, Integrationen]
- [HIER: Organisatorische Rahmen — Budget, Zeit, Teamgröße, Compliance]

## 6. Risiken & Unklarheiten

Zu dokumentieren:
- [HIER: Größte Risiken]
- [HIER: Offene Fragen; Annahmen klar als Annahme kennzeichnen]

## 7. Nicht-Ziele (Out of Scope)

Zu dokumentieren:
- [HIER: Was gehört bewusst nicht zum Vorhaben?]

## Widersprüche (falls vorhanden)

Zu dokumentieren:
- [HIER: Spannungen zwischen Zielen, Stakeholdern oder Randbedingungen — nicht weglächeln]
```

---

## Anforderungen an die Ausfüllung (für die KI / das Team)

- Klar, prägnant, für **Fach- und Technikpublikum** verständlich
- **Keine Detailarchitektur** — Fokus auf gemeinsames Verständnis
- **Implizite Annahmen explizit** machen und kennzeichnen
- **Widersprüche benennen**, nicht verschweigen

---

## Nächste Schritte (optional)

Zu dokumentieren:
- [HIER: z. B. Vision/`{VISION.MD}` schärfen, `{REQUIREMENTS.MD}` anlegen, arc42-Kapitel 1–3 befüllen, Inception-Review-Termin]
- [HIER: Wenn System und Umfeld klar genug: System Context Canvas → Eingang arc42 Kapitel 3 / C4 Context]
- [HIER: Wenn Optionen offen: Tradeoff Canvas Produkt und/oder Technik; bei Entscheidungsreife: Architecture Decision Canvas → ADR]

---

## Zu dokumentieren (Kurz-Checkliste)

```
Vorhaben: [HIER]
Top-3-Ziele: [HIER]
Top-Stakeholder + Interesse: [HIER]
Kernproblem: [HIER]
Systemidee (1 Absatz): [HIER]
Härteste Randbedingung: [HIER]
Top-Risiko + offene Frage: [HIER]
Nicht-Ziele: [HIER]
```
