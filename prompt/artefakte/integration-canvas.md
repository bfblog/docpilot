---
typ: artefakt
name: Integration Canvas
kontext: Hilfsvorlage zur Analyse und Strukturierung von Systemintegration — Partner, Integrationsarten, Datenflüsse, Kopplung, Resilienz und Risiken; ohne vorschnelle Technologiewahl
rollen:
  - Softwarearchitekt
artefakte:
  - Architekturdokumentation nach arc42
  - System Context Canvas
  - Architecture Building Blocks Canvas
  - Deployment Operations Canvas
  - Architecture Decision Record
  - Risk Technical Debt Canvas
  - Tradeoff Canvas Technik
workflows: []
---

# Artefakt: Integration Canvas

## Über den Integration Canvas

Der **Integration Canvas** strukturiert, **wie Systeme und Bausteine miteinander integriert** werden: wer **Producer**, **Consumer** oder **beides** ist, welche **Integrationsarten** (synchron, asynchron, Batch, Streaming) zum Einsatz kommen, wie **Datenflüsse** verlaufen, wie **lose oder eng** die Kopplung ist und welche **Fehler- und Resilienzstrategien** greifen. Fokus liegt auf **Nachvollziehbarkeit und Risikotransparenz**, nicht auf der Auswahl eines konkreten Produkts ohne Anforderungsbezug.

**Typischer Anschluss:** Inhalte fließen in **arc42** (u. a. **Kontext**, **Bausteine**, **Laufzeitsicht / Kapitel 6**, Schnittstellen) und in **ADRs** zu Integrationsmustern, Protokollen oder Messaging. Ergänzt **System Context Canvas** (Wer mit wem) und **Architecture Building Blocks Canvas** (innere Bausteine und deren Schnittstellen).

---

## Sinn und Zweck

- **Integrationslandschaft** und **Rollen** (Producer/Consumer) explizit machen
- **Integrationsarten** klar trennen und bewusst mischen, wo nötig
- **Datenflüsse** inkl. ungefährer **Frequenz** und **Volumina** (wenn bekannt)
- **Kopplung** und **zeitliche Abhängigkeiten** benennen
- **Resilienz** und **Fehlerpfade** früh durchdenken
- **Risiken** (Bottlenecks, Abhängigkeiten, Komplexität) realistisch einschätzen

---

## Eingabe (für die Sitzung / den Prompt)

| Platzhalter | Bedeutung |
|-------------|-----------|
| Systemlandschaft | Beteiligte Systeme / Bausteine / Nachbarn |
| Integrationsanforderungen | Funktional, zeitlich, verfügbarkeit, Konsistenz, Compliance |
| Technologien (optional) | Bekannte Vorgaben — nur dokumentieren, nicht bevorzugen ohne Begründung |

---

## Ablage (außerhalb der Bibliothek)

Typisch unter `{DOCS}/` oder in `{SOFTWARE-ARCHITECTURE.MD}`, z. B. `docs/integration/[initiative]-integration-canvas.md`.

---

## Vorlage (Markdown)

```markdown
# Integration Canvas: [Titel / Systemlandschaft]

**Datum:** [Datum]  
**Owner:** [z. B. Softwarearchitekt]  
**Status:** [Entwurf | Vereinbart | Überholt]

## 1. Integrationspartner

Zu dokumentieren:
- [HIER: Welche **Systeme** oder **Bausteine** müssen integriert werden?]
- [HIER: Rolle je Partner — **Producer**, **Consumer** oder **beides**]

| Partner | Rolle (Producer / Consumer / beides) | Kurzbeschreibung |
|---------|----------------------------------------|------------------|
| … | … | … |

## 2. Integrationsarten

Zu dokumentieren:
- [HIER: **Synchron** — z. B. REST, RPC, GraphQL (nur wenn sachlich begründet)]
- [HIER: **Asynchron** — Events, Messaging, Queues]
- [HIER: **Batch** / **Streaming** — wo relevant]
- [HIER: Pro Pfad: warum diese Art?]

| Integrationspfad | Art (sync / async / Batch / Stream) | Bemerkung |
|-------------------|--------------------------------------|-----------|
| … | … | … |

## 3. Datenflüsse

Zu dokumentieren:
- [HIER: **Wer sendet was an wen?** (fachlicher Inhalt / Nachrichtentyp)]
- [HIER: **Frequenz** und **Volumen** falls bekannt — sonst „unklar“ + Annahme kennzeichnen]

| Quelle | Ziel | Daten / Ereignis | Frequenz | Volumen (falls bekannt) |
|--------|------|------------------|----------|-------------------------|
| … | … | … | … | … |

## 4. Kopplung

Zu dokumentieren:
- [HIER: **Lose** vs. **enge** Kopplung je Verbindung — gemeinsame Modelle, gemeinsame DB, gemeinsame Deployments?]
- [HIER: **Zeitliche Abhängigkeiten** — online erforderlich vs. entkoppelt]

| Verbindung | Kopplung (lose / mittel / eng) | Zeitliche Abhängigkeit |
|------------|--------------------------------|-------------------------|
| … | … | … |

## 5. Fehler- und Resilienzstrategien

Zu dokumentieren:
- [HIER: **Retry**, **Backoff**, **Idempotenz** wo nötig]
- [HIER: **Dead Letter** / Poison Message Handling]
- [HIER: **Fallback**, **Degradation**, **Circuit Breaker** falls relevant]
- [HIER: Umgang mit **Ausfällen** einzelner Partner — wer entscheidet, wer informiert wird]

## 6. Risiken & Herausforderungen

Zu dokumentieren:
- [HIER: **Bottlenecks** (Durchsatz, Latenz, sequenzielle Abhängigkeiten)]
- [HIER: **Kritische Abhängigkeiten** von Drittsystemen oder Teams]
- [HIER: **Komplexität** — viele Protokolle, viele Datenformate, fehlende Standards]

| Risiko | Auswirkung | Mitigation / nächster Schritt |
|--------|------------|-------------------------------|
| … | … | … |

## Verknüpfung arc42 / ADR

Zu dokumentieren:
- [HIER: Zuordnung zu arc42-Kapiteln (Kontext, Bausteine, Laufzeit, Schnittstellen)]
- [HIER: Welche Punkte werden als **ADR** festgehalten (Muster, Technologie, Vertrag)?]
```

---

## Anforderungen an die Ausfüllung

- **Klare Trennung** der Integrationsarten; Mischformen **benennen**
- Schwerpunkt auf **Datenflüssen** und **Kopplung**
- **Risiken** realistisch — weder verharmlosen noch ohne Grund dramatisieren
- **Keine unnötige Technologiepräferenz**; Vorgaben aus dem Kontext neutral übernehmen, Alternativen bei offenen Entscheidungen mit **Tradeoff Canvas Technik** oder **ADR** klären

---

## Zu dokumentieren (Kurz-Checkliste)

```
Kritischster Integrationspfad: [HIER]
Stärkste Kopplung (wo?): [HIER]
Größte Resilienz-Lücke: [HIER]
Offenes Technologie-Thema für ADR: [HIER]
```
