---
typ: artefakt
name: System Context Canvas
kontext: Hilfsvorlage zur klaren Darstellung von Systemgrenzen, externen Akteuren, Nachbarsystemen, Schnittstellen und Datenflüssen — ohne interne Bausteine (Fokus Kontextebene, vergleichbar C4 Level 1 / arc42 Kapitel 3)
rollen:
  - Softwarearchitekt
artefakte:
  - Architekturdokumentation nach arc42
  - Integration Canvas
  - Domain Bounded Context Canvas
workflows: []
---

# Artefakt: System Context Canvas

## Über den System Context Canvas

Der **System Context Canvas** strukturiert das **Umfeld eines Systems**: was das System ist, wer es nutzt, welche externen Systeme eine Rolle spielen, über welche Kanäle kommuniziert wird und welche Daten fließen. Er dient **Verständnis und Abgrenzung** — **keine** Detailarchitektur und **keine** Aufschlüsselung interner Komponenten.

**Typischer Anschluss:** Inhalte fließen in **arc42 Kapitel 3 (Kontext und Abgrenzung)** bzw. in ein **C4-Context-Diagramm** in `{SOFTWARE-ARCHITECTURE.MD}` ein. Wenn das System **fachlich** mehrere Modelle oder Schnitte birgt, schließt sich oft ein **Domain / Bounded Context Canvas** an. Verwandte Ideen finden sich bei [arc42 Canvas](https://canvas.arc42.org/) (Architecture Communication / Systemkontext).

---

## Sinn und Zweck

- **Gemeinsames Bild** von Systemgrenze und Nachbarschaft (Team, Stakeholder, Betrieb)
- **Abhängigkeiten und Schnittstellen** früh sichtbar machen (auch implizite)
- **Grundlage** für Anforderungen an Integration, Sicherheit und Betrieb
- **Workshop-tauglich** mit einfachen Tabellen oder ASCII-Skizzen

---

## Eingabe (für die Sitzung / den Prompt)

| Platzhalter | Bedeutung |
|-------------|-----------|
| System | Name oder Arbeitsname des betrachteten Systems |
| Zweck | Warum existiert das System? |
| Externe Systeme (optional) | Bekannte Nachbarn |
| Akteure (optional) | Menschen, Rollen, andere Organisationseinheiten |
| Schnittstellen (optional) | Bekannte APIs, Protokolle, Dateitransfer |

---

## Ablage (außerhalb der Bibliothek)

Typisch unter `{DOCS}/` oder als Teil der Architekturdokumentation, z. B. `docs/kontext/[system]-context-canvas.md` oder Abschnitt in `{SOFTWARE-ARCHITECTURE.MD}`.

---

## Vorlage (Markdown)

```markdown
# System Context Canvas: [Systemname]

**Datum:** [Datum]  
**Owner:** [z. B. Softwarearchitekt]  
**Status:** [Entwurf | Vereinbart | Überholt]

## 1. System (im Zentrum)

Zu dokumentieren:
- [HIER: Kurzbeschreibung des Systems — was ist es?]
- [HIER: Hauptverantwortung / Kernaufgabe in einem Satz]

## 2. Akteure / Nutzer

Zu dokumentieren:
- [HIER: Wer nutzt das System? (Rollen, Organisationen)]
- [HIER: Typische Interaktionen — was lösen die Akteure aus?]

Optional — Tabelle:

| Akteur | Interaktion / Nutzen |
|--------|----------------------|
| … | … |

## 3. Externe Systeme

Zu dokumentieren:
- [HIER: Nachbarsysteme mit Rolle — Upstream (liefert an uns), Downstream (wir liefern an sie), Peer]
- [HIER: Kurz, wofür jedes System im Kontext steht]

| externes System | Richtung / Rolle | Kurzbeschreibung |
|-----------------|------------------|------------------|
| … | … | … |

## 4. Schnittstellen & Kommunikationsarten

Zu dokumentieren:
- [HIER: Wie wird kommuniziert? z. B. REST, gRPC, Messaging, Datei/Batch, UI]
- [HIER: Synchron vs. asynchron wo relevant]
- [HIER: Sicherheitsrelevante Aspekte nur auf Kontextebene (z. B. „über öffentliches Internet“, „VPN“)]

| von | nach | Art | Bemerkung |
|-----|------|-----|-----------|
| … | … | … | … |

## 5. Datenflüsse

Zu dokumentieren:
- [HIER: Welche Daten fließen wohin? (fachlich, nicht physische Tabellen)]
- [HIER: Producer / Consumer pro wichtigstem Fluss]

| Daten / Artefakt | Producer | Consumer | Richtung |
|------------------|----------|----------|----------|
| … | … | … | … |

## 6. Systemgrenzen

Zu dokumentieren:
- [HIER: Was gehört explizit zum System (Scope dieses Canvas)?]
- [HIER: Was liegt bewusst außerhalb? (klare Out-of-Scope-Nachbarn)]

## 7. Annahmen & offene Punkte

Zu dokumentieren:
- [HIER: Unklare oder noch zu verifizierende Integrationen]
- [HIER: Risiken im Kontext (Single Points of Failure, Verträge, SLA unklar, …)]
- [HIER: Annahmen kennzeichnen]

## Optional: ASCII-Kontextübersicht

Zu dokumentieren (wenn hilfreich):

```
        [Akteur A]          [ext. System X]
              \                 /
               \               /
                v             v
            +---------------------+
            |    [Unser System]   |
            +---------------------+
                ^             ^
               /               \
        [Akteur B]          [ext. System Y]
```

## Verknüpfung arc42 / C4

Zu dokumentieren:
- [HIER: Wie wird dies in arc42 Kapitel 3 bzw. C4 Context in `{SOFTWARE-ARCHITECTURE.MD}` übernommen?]
```

---

## Anforderungen an die Ausfüllung

- Fokus auf **Abgrenzung und Interaktionen**, nicht auf innere Module
- **Implizite Abhängigkeiten** benennen (z. B. impliziter Aufruf eines Drittsystems über einen anderen Nachbarn)
- **Einfache** Tabellen oder ASCII — keine Pflicht zu Zeichentools
- Bei Lücken: **Annahmen** explizit und Review vormerken

---

## Zu dokumentieren (Kurz-Checkliste)

```
System + Hauptverantwortung: [HIER]
Top-3-Akteure: [HIER]
Top-3-Nachbarsysteme: [HIER]
Kritischster Datenfluss: [HIER]
Klare Out-of-Scope-Grenze: [HIER]
Größte offene Frage: [HIER]
```
