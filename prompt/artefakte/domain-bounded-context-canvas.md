---
typ: artefakt
name: Domain Bounded Context Canvas
kontext: Hilfsvorlage nach Domain-Driven Design zur fachlichen Strukturierung — Domänen, Bounded Contexts, Verantwortlichkeiten, Kontextbeziehungen und Ubiquitous Language; ohne vorschnelle technische Aufteilung
rollen:
  - Softwarearchitekt
artefakte:
  - Architekturdokumentation nach arc42
  - System Context Canvas
  - Architecture Building Blocks Canvas
  - Feature-Spezifikation
workflows: []
---

# Artefakt: Domain / Bounded Context Canvas

## Über den Domain / Bounded Context Canvas

Der **Domain / Bounded Context Canvas** strukturiert die **fachliche Zerlegung** eines Systems: welche **Domänen** und **Bounded Contexts** es gibt, wo **Verantwortung** und **Datenhoheit** liegen, wie Kontexte **zusammenspielen** und wo **Sprachgrenzen** oder **Konflikte** lauern. Orientierung bietet **Domain-Driven Design** (Eric Evans, u. a. **Strategic Design**); nahe verwandt mit Ideen wie dem [Bounded Context Canvas](https://github.com/ddd-crew/bounded-context-canvas) (Community).

**Abgrenzung:**

- **Fachliche** Struktur — **keine** Empfehlung zu „ein Microservice pro Context“ ohne weiteres Abwägen
- **Kein Ersatz** für arc42-Bausteinsicht, sondern **Input** für Kapitel zu Kontext, Bausteinen und Schnittstellen
- Sinnvoll **nach** oder **parallel** zum **System Context Canvas**, wenn die Systemgrenze grob steht, das **Innenleben fachlich** noch unklar ist

---

## Sinn und Zweck

- **Klare fachliche Grenzen** und **Ownership** von Modellen und Daten
- **Upstream/Downstream** und Integrationsarten **explizit** machen
- **Ubiquitous Language** pro Kontext schärfen — Missverständnisse früh erkennen
- Grundlage für **Feature-Spezifikationen**, **Teamzuordnung** und **ADRs** zu Integrationsmustern

---

## Eingabe (für die Sitzung / den Prompt)

| Platzhalter | Bedeutung |
|-------------|-----------|
| System / Vorhaben | Name oder Scope des betrachteten Systems |
| Fachlicher Kontext | Branche, Prozess, Organisation |
| Domänen (optional) | Bereits bekannte Fachbegriffe / Teilbereiche |
| Probleme / Herausforderungen (optional) | z. B. Legacy, organisatorische Schnitte |

---

## Ablage (außerhalb der Bibliothek)

Typisch unter `{DOCS}/` oder in der Architekturdokumentation, z. B. `docs/domains/[system]-bounded-contexts.md` oder Abschnitt in `{SOFTWARE-ARCHITECTURE.MD}` (z. B. zu strategischer Aufteilung / Bausteinen).

---

## Vorlage (Markdown)

```markdown
# Domain / Bounded Context Canvas: [System / Vorhaben]

**Datum:** [Datum]  
**Facilitator:** [z. B. Softwarearchitekt]  
**Fachliche Expert:in:** [optional mit angeben]  
**Status:** [Entwurf | Vereinbart | Überholt]

## 1. Fachliche Domänen

Zu dokumentieren:
- [HIER: Zentrale fachliche Bereiche (Subdomains / Fachgebiete)]
- [HIER: Kurzbeschreibung je Bereich — was ist der Kerninhalt?]

| Domäne / Bereich | Kurzbeschreibung |
|------------------|------------------|
| … | … |

## 2. Bounded Contexts

Zu dokumentieren:
- [HIER: Abgrenzbare Kontexte mit **eigenem Modell** und klarer **Verantwortung**]
- [HIER: Was **gehört** in den Kontext? Was **gehört ausdrücklich nicht** hinein?]

| Bounded Context | Gehört dazu | Gehört nicht dazu |
|-----------------|-------------|-------------------|
| … | … | … |

## 3. Verantwortlichkeiten

Zu dokumentieren:
- [HIER: Welche fachlichen Aufgaben / Use-Case-Cluster liegen in welchem Kontext?]
- [HIER: Wer „besitzt“ welche **Daten / Entitäten** (fachlich, nicht DB-Tabellen)?]

| Kontext | Kerntätigkeiten | Daten-/Modell-Ownership (fachlich) |
|---------|-----------------|-------------------------------------|
| … | … | … |

## 4. Beziehungen zwischen Kontexten

Zu dokumentieren:
- [HIER: **Upstream / Downstream** (wer liefert das führende Modell?)]
- [HIER: Abhängigkeiten und **Integrationstypen** — z. B. Events, REST API, gemeinsame DB (bewusst?), Batch, File]

| Kontext A | Richtung / Rolle | Kontext B | Integration | Bemerkung |
|-----------|------------------|-----------|-------------|-----------|
| … | upstream / downstream | … | … | … |

## 5. Sprachgrenzen (Ubiquitous Language)

Zu dokumentieren:
- [HIER: **Gleicher Begriff, andere Bedeutung** in verschiedenen Kontexten]
- [HIER: Potenzielle **Missverständnisse** zwischen Teams oder Modulen]

| Begriff | Kontext A (Bedeutung) | Kontext B (Bedeutung) |
|---------|------------------------|------------------------|
| … | … | … |

## 6. Konflikte / Schnittprobleme

Zu dokumentieren:
- [HIER: **Unklare Grenzen** — wo ist unklar, welcher Context führt?]
- [HIER: **Reibungen** — politisch, organisatorisch oder modelltechnisch]
- [HIER: Annahmen kennzeichnen]

## Annahmen & offene Punkte

Zu dokumentieren:
- [HIER: Was ist noch zu validieren? Mit wem?]

## Verknüpfung arc42 / Umsetzung

Zu dokumentieren:
- [HIER: Wie fließt dies in arc42 (z. B. Bausteinsicht, Schnittstellen, Kontext) und in Feature-Arbeit ein?]
- [HIER: Bewusst **keine** Entscheidung zu Deployment-Grenzen — oder Verweis auf ADR, sobald getroffen]
```

---

## Anforderungen an die Ausfüllung

- Fokus auf **fachliche Struktur**, nicht auf Technikstack oder Service-Granularität
- **Verantwortlichkeiten** und **Sprachgrenzen** klar benennen
- **Implizite Annahmen** sichtbar machen und reviewen
- **Keine vorschnelle Mikroservice-Aufteilung** — erst fachliche Grenzen stabilisieren, dann technische Konsequenzen (z. B. mit **Tradeoff Canvas Technik** und **ADR**) ableiten

---

## Zu dokumentieren (Kurz-Checkliste)

```
Anzahl Bounded Contexts (Namensliste): [HIER]
Stärkster fachlicher Schnitt / größte Unklarheit: [HIER]
Kritischer Upstream→Downstream: [HIER]
Ein Begriff mit zwei Bedeutungen: [HIER]
Offener Konflikt: [HIER]
```
