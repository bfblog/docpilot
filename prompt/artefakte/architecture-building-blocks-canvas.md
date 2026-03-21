---
typ: artefakt
name: Architecture Building Blocks Canvas
kontext: Hilfsvorlage zum Entwurf der inneren Systemstruktur — zentrale Bausteine, Verantwortlichkeiten, Schnittstellen, Daten-Ownership, Abhängigkeiten und Hotspots; ohne Implementierungsdetails (Anschluss an arc42 Bausteinsicht / C4 Container & Component)
rollen:
  - Softwarearchitekt
artefakte:
  - Architekturdokumentation nach arc42
  - System Context Canvas
  - Domain Bounded Context Canvas
  - Feature-Spezifikation
  - Integration Canvas
  - Architecture Decision Record
workflows: []
---

# Artefakt: Architecture Building Blocks Canvas

## Über den Architecture Building Blocks Canvas

Der **Architecture Building Blocks Canvas** strukturiert die **innere Gliederung** eines Systems: welche **Bausteine (Komponenten)** es gibt, welche **Aufgaben** sie tragen, wie sie **schnittstellenbasiert** zusammenspielen und wo **Datenhoheit** sowie **riskante Kopplungen** liegen. Er dient dem **Strukturentwurf** — nicht dem Feintuning von Code, Frameworks oder Klassendesign.

**Typischer Anschluss:** Inhalte fließen in **arc42 Kapitel 5 (Bausteinsicht)** und in **C4**-Diagramme auf **Container-** und ggf. **Component-Ebene** in `{SOFTWARE-ARCHITECTURE.MD}` ein. Verwandte Impulse finden sich bei [arc42 Canvas](https://canvas.arc42.org/) (Architektur aus Bausteinen denken).

**Abgrenzung:**

- **System Context Canvas:** Außengrenze und Umwelt — **kein** Innenleben
- **Domain / Bounded Context Canvas:** **Fachliche** Grenzen und Sprachen — Building Blocks sind oft **technisch-organisatorisch** und können sich von Bounded Contexts **unterscheiden** (mehrere Bausteine pro Context oder ein Baustein über mehrere — bewusst entscheiden)
- **Kein Overengineering:** Wenige, gut benannte Bausteine bevorzugen; bei zu vielen Boxen **vereinfachen** und begründen

---

## Sinn und Zweck

- **Gemeinsames Bild** der groben Modul- oder Service-Struktur
- **Verantwortlichkeiten** und **Schnittstellen** explizit machen
- **Daten-Ownership** klären (wer ist „Source of Truth“?)
- **Hotspots und kritische Abhängigkeiten** früh markieren
- Grundlage für **Feature-Spezifikationen** und **ADRs** zu Schnittstellenmustern

---

## Eingabe (für die Sitzung / den Prompt)

| Platzhalter | Bedeutung |
|-------------|-----------|
| System | Name oder Scope des Systems |
| Anforderungen | Funktional / nicht-funktional, Prioritäten |
| Kontext (optional) | Brownfield, Legacy, Teamaufteilung, Cloud-On-Prem-Mix |

---

## Ablage (außerhalb der Bibliothek)

Typisch unter `{DOCS}/` oder in `{SOFTWARE-ARCHITECTURE.MD}`, z. B. `docs/architektur/building-blocks-[system].md`.

---

## Vorlage (Markdown)

```markdown
# Architecture Building Blocks Canvas: [Systemname]

**Datum:** [Datum]  
**Owner:** [z. B. Softwarearchitekt]  
**Status:** [Entwurf | Vereinbart | Überholt]

## 1. Zentrale Bausteine (Components)

Zu dokumentieren:
- [HIER: Die **wichtigsten** Bausteine — bewusst begrenzte Anzahl (Orientierung: oft einstellig bis niedrig zweistellig)]
- [HIER: Kurzbeschreibung je Baustein — wofür ist er da?]

| Baustein | Kurzbeschreibung |
|----------|------------------|
| … | … |

## 2. Verantwortlichkeiten

Zu dokumentieren:
- [HIER: Welche **fachlichen und technischen** Aufgaben erfüllt jeder Baustein?]
- [HIER: Wo liegt zentrale **Geschäftslogik** vs. Infrastruktur / Cross-Cutting?]

| Baustein | Kerntätigkeiten / Logik |
|-----------|-------------------------|
| … | … |

## 3. Schnittstellen zwischen Bausteinen

Zu dokumentieren:
- [HIER: Wie kommunizieren die Bausteine? — z. B. synchrone APIs, asynchrone Events, gemeinsame Datenhaltung (bewusst?), Datei/Batch]
- [HIER: Wichtigste **Nachrichten** oder **APIs** nur auf struktureller Ebene, ohne Protokoll-Details]

| Von | Nach | Art (API / Event / DB / …) | Inhalt / Zweck (kurz) |
|-----|------|----------------------------|------------------------|
| … | … | … | … |

## 4. Datenverantwortung

Zu dokumentieren:
- [HIER: Welcher Baustein **besitzt** welche **Daten** bzw. welches fachliche Aggregat / Bounded-Context-Mapping?]
- [HIER: Bekannte **Replikation** oder **Read Models** — wer führt, wer folgt?]

| Daten / fachlicher Gegenstand | Owner-Baustein | Leser / Konsumenten | Bemerkung |
|-------------------------------|----------------|----------------------|-----------|
| … | … | … | … |

## 5. Abhängigkeiten

Zu dokumentieren:
- [HIER: Abhängigkeitsrichtung (A braucht B)]
- [HIER: **Kritische Kopplungen** — enge zyklische Abhängigkeiten, Shared DB, geteilte Bibliotheken]

| Baustein A | hängt von | Baustein B | Bewertung (ok / riskant) |
|------------|-----------|-------------|---------------------------|
| … | … | … | … |

## 6. Kritische Bausteine / Hotspots

Zu dokumentieren:
- [HIER: Besonders **zentrale**, **komplexe** oder **risikobehaftete** Bausteine]
- [HIER: Warum kritisch? (Last, Sicherheit, Änderungshäufigkeit, Wissenssilos, Single Point of Failure)]

| Hotspot | Risiko / Rolle | Maßnahme / nächster Schritt (optional) |
|---------|----------------|----------------------------------------|
| … | … | … |

## Optional: Diagramm-Beschreibung (Text)

Zu dokumentieren:
- [HIER: Kurze **beschreibende** Skizze für ein C4-Container- oder Component-Diagramm — z. B. „oben API-Gateway, links Auth-Service, Mitte Kern-Domain-Service, rechts Reporting Read Model“]

## Verknüpfung arc42 / C4 / DDD

Zu dokumentieren:
- [HIER: Mapping zu **arc42 Kapitel 5** und C4-Ebenen]
- [HIER: Bezug zu **Bounded Contexts** (falls Domain Canvas existiert) — 1:1, n:1 oder bewusst getrennt?]
```

---

## Anforderungen an die Ausfüllung

- Fokus auf **Struktur und Verantwortung**, nicht auf Klassen, Frameworks oder Code-Layout
- **Klare Zuordnung** — unklare Grenzen benennen statt verwischen
- **Komplexität im Zaum** — bei Explosion der Bausteinzahl: vereinfachen und **Overengineering** ansprechen
- **Annahmen** kennzeichnen; Widersprüche zu Anforderungen oder Domain Canvas **sichtbar** machen

---

## Zu dokumentieren (Kurz-Checkliste)

```
Anzahl Bausteine (Zahl): [HIER]
Stärkste Abhängigkeitskette: [HIER]
Kritischer Daten-Owner-Konflikt: [HIER]
Größter Hotspot: [HIER]
Vereinfachungsvorschlag (falls nötig): [HIER]
```
