# Artefakt-Zusammenhänge

Diese Dokumentation erklärt die Zusammenhänge zwischen Anforderungen, User Stories, Feature-Spezifikationen, Testplänen und anderen Artefakten im Entwicklungsprozess.

---

## Abhängigkeitskette der Dokumentationsmittel (nach Stefan Zörner)

Basierend auf Stefan Zörners Buch "Softwarearchitekturen dokumentieren und kommunizieren" zeigt die folgende Abhängigkeitskette, wie verschiedene Dokumentationsmittel aufeinander aufbauen:

Die **nummerierte Liste** unten ist eine **didaktisch linear verkürzte Lesereihenfolge** — gut, um den Einstieg zu strukturieren. Zörners **Metamodell** im Buch ist ein **Netz**: mehrere Mittel wirken **parallel und direkt** auf **Architekturentscheidungen** (z. B. Randbedingungen, technische Risiken, Qualitätsziele, Qualitätsszenarien). Die **Visualisierung weiter unten** folgt diesem Netz inklusive **beschrifteter Kanten** (entsprechend der Darstellung bei Zörner 2021).

### Die Abhängigkeitskette

**1. Personas + Produktkarton → Systemkontext**
- Nutzer, Nutzenversprechen und Systemidee bestimmen, welche externen Akteure und Nachbarsysteme relevant sind.

**2. Systemkontext → Qualitätsziele & Qualitätsszenarien**
- Umfeld und Nutzung treiben die nicht-funktionalen Anforderungen.

**3. Qualitätsziele + Randbedingungen + Risiken → Lösungsstrategie**
- Qualitätsanforderungen, feste Vorgaben und erkannte Risiken bestimmen die grobe architektonische Richtung.

**4. Lösungsstrategie → Architekturentscheidungen**
- Die Strategie wird durch konkrete, begründete Entscheidungen (ADRs) verbindlich gemacht.

**5. Architekturentscheidungen → Bausteinsicht**
- Entscheidungen formen die statische Struktur (Komponenten, Schichten, Verantwortlichkeiten).

**6. Bausteinsicht → Schnittstellenbeschreibungen**
- Aus den Bausteinen ergeben sich ihre Interfaces und Verträge.

**7. Bausteinsicht + Architekturentscheidungen → Laufzeitsicht**
- Struktur und Designentscheidungen bestimmen die Interaktionen und Abläufe zur Laufzeit.

**8. Bausteinsicht + Laufzeitsicht → Verteilungssicht**
- Struktur und Laufzeitverhalten bestimmen das Deployment auf Infrastruktur.

**9. Übergreifende Konzepte → alle Sichten**
- Querschnittsthemen (z. B. Security, Logging, Fehlerbehandlung) wirken auf Baustein-, Laufzeit- und Verteilungssicht.

**10. Glossar → alle Dokumentationsmittel**
- Sichert einheitliche Begriffe über alle Artefakte hinweg.

### Kurzform

**Verständnisartefakte → Qualitäts- & Rahmen-Treiber → Strategie → Entscheidungen → Struktur → Schnittstellen & Verhalten → Verteilung** — mit Querschnittskonzepten und Glossar über allem.

### Verbindung zu unserem Workflow

Die arc42-Abhängigkeitskette passt zu unserem praktischen Workflow:

- **Personas + Produktkarton** → entsprechen unserer **Vision** (`{VISION.MD}`)
- **Systemkontext** → wird in **Anforderungen** (`{REQUIREMENTS.MD}`) und **arc42 Kapitel 3** dokumentiert
- **Qualitätsziele & Qualitätsszenarien** → sind Teil der **Anforderungen** (nicht-funktionale Anforderungen)
- **Lösungsstrategie** → wird in **Feature-Spezifikationen** (`{FEATURES}/`) und **arc42 Kapitel 4** dokumentiert
- **Architekturentscheidungen** → werden als **ADRs** (`{ADR}/`) dokumentiert (entspricht arc42 Kapitel 9)
- **Bausteinsicht, Laufzeitsicht, Verteilungssicht** → werden in **arc42** (`{SOFTWARE-ARCHITECTURE.MD}`) dokumentiert
- **Schnittstellenbeschreibungen** → sind Teil der **Feature-Spezifikationen** und **arc42**

### Architecture Inception Canvas

Der **Architecture Inception Canvas** steht typischerweise **ganz am Anfang** eines neuen Vorhabens oder bei großer Unklarheit zu Zielen und Rahmen. Er schafft ein **gemeinsames Verständnis** über Problem, Ziele, Stakeholder und Randbedingungen — **bevor** konkrete Architekturentscheidungen oder ausgearbeitete arc42-Dokumentation im Fokus stehen. Umfang bewusst knapp (oft 1–2 Seiten), ohne Detailarchitektur.

**Typischer Anschluss:** Inhalte fließen in **Vision**, **Anforderungen** und die frühen arc42-Kapitel (u. a. Stakeholder, Randbedingungen, Kontext) ein. Sobald das betrachtete System **benennbar** ist, lohnt oft ein **System Context Canvas** für Grenze und Nachbarschaft. Ist das System **fachlich heterogen**, folgt häufig ein **Domain / Bounded Context Canvas** (strategische DDD-Aufteilung). Wenn mehrere Lösungsoptionen oder harte Zielkonflikte sichtbar werden, schließen sich **Tradeoff Canvas**, **Architecture Decision Canvas** und **ADR** an (siehe unten).

Vorlage: `{PROMPT}/artefakte/architecture-inception-canvas.md`.

### System Context Canvas

Der **System Context Canvas** fokussiert die **Kontextebene** eines bestehenden oder geplanten Systems: Akteure, externe Nachbarsysteme, Schnittstellen, Datenflüsse und eine klare **Innen-/Außen-Grenze**. Er ist **kein** Ersatz für die vollständige arc42-Kontextbeschreibung, liefert aber eine **kompakte, workshop-taugliche** Grundlage und passt zu **C4 Level 1** bzw. **arc42 Kapitel 3 (Kontext und Abgrenzung)**.

Typische Reihenfolge: oft **nach** oder **parallel** zur Inception, wenn das Vorhaben genug Kontur hat, um „unser System“ vs. „Umwelt“ sinnvoll zu benennen — oder bei **Brownfield**, wenn das Umfeld neu kartiert werden muss.

Vorlage: `{PROMPT}/artefakte/system-context-canvas.md`.

### Domain / Bounded Context Canvas

Der **Domain / Bounded Context Canvas** dient der **fachlichen Strukturierung** nach **Domain-Driven Design**: **Domänen**, **Bounded Contexts** mit klaren **Verantwortlichkeiten**, **Beziehungen** (z. B. Upstream/Downstream), **Integrationstypen** auf Modell-Ebene sowie **Ubiquitous Language** und typische **Schnittstellen zwischen Sprachen**. Er zielt **nicht** auf technische Zerlegung (Services, Deployments), sondern auf ein geteiltes **Fachmodell** und tragfähige **Grenzen**.

Typische Reihenfolge: **nach** dem **System Context Canvas**, wenn klar ist, was „unser System“ ist, aber **innen** noch mehrere fachliche Modelle oder organisatorische Schnitte existieren. Ergebnisse fließen in **arc42** (u. a. Bausteine, Schnittstellen) und in **Feature-Spezifikationen** ein; Spannungen zwischen Kontexten können **Tradeoff Canvas Technik** und **ADRs** (Integrationsmuster) auslösen.

Vorlage: `{PROMPT}/artefakte/domain-bounded-context-canvas.md`.

### Architecture Building Blocks Canvas

Der **Architecture Building Blocks Canvas** adressiert die **technische Grobstruktur** **innerhalb** der Systemgrenze: **Bausteine (Komponenten)**, **Verantwortlichkeiten**, **Schnittstellen** (APIs, Events, Datenflüsse), **Daten-Ownership**, **Abhängigkeiten** und **Hotspots**. Er steht **unterhalb** der reinen Kontextebene und **ergänzt** die **fachliche** Zerlegung aus dem Domain Canvas — Mapping zwischen Bounded Context und Baustein ist oft **n:1** oder **1:n** und soll **bewusst** dokumentiert werden.

Typische Reihenfolge: **nach** **System Context** und idealerweise mit Input aus **Domain / Bounded Context Canvas**, bevor die **arc42-Bausteinsicht** (Kapitel 5) und **C4**-Container/Component-Diagramme ausformuliert werden. Ergebnisse stützen **Feature-Spezifikationen**; Spannungen an Schnittstellen können **Tradeoff Canvas Technik** und **ADRs** auslösen.

Vorlage: `{PROMPT}/artefakte/architecture-building-blocks-canvas.md`.

### Integration Canvas

Der **Integration Canvas** vertieft die Frage, **wie** Systeme und Bausteine **technisch und betrieblich** zusammenspielen: **Integrationspartner** mit Rolle (Producer/Consumer), **Integrationsarten** (synchron, asynchron, Batch, Streaming), **Datenflüsse** inklusive grober Lastannahmen, **Kopplung** (lose vs. eng, zeitliche Abhängigkeit), **Fehler- und Resilienzstrategien** sowie **Risiken** und Bottlenecks. Er ergänzt den **System Context Canvas** (wer außen anbindet) und den **Architecture Building Blocks Canvas** (innere Bausteine und deren Schnittstellen), indem er **Verbindungen und Betriebsszenarien** bündelt.

Typische Reihenfolge: wenn **Kontext** und **Bausteine** grob stehen, aber noch Klärungsbedarf zu **Protokollen**, **Messaging**, **SLA** oder **Ausfallverhalten** besteht. Ergebnisse fließen in **arc42** (u. a. Laufzeitsicht, Schnittstellen) und in **ADRs**; offene Technologieentscheidungen bewusst **nicht** im Canvas „festnageln“, sondern per **Tradeoff Canvas Technik** oder ADR klären.

Vorlage: `{PROMPT}/artefakte/integration-canvas.md`.

### Domain, Building Blocks und Integration: drei Linsen auf dasselbe System

Die Architektur-**Canvas** in dieser Bibliothek sind **keine isolierten Einzelwerkzeuge**. Sie **ergänzen** sich und bauen **logisch** aufeinander auf: Jeder Canvas beleuchtet eine **andere Perspektive** auf dasselbe System — wie **verschiedene Linsen**, durch die man es nacheinander schärft.

**Für die Kette aus fachlicher Struktur, technischer Zerlegung und Zusammenspiel** eignet sich folgende **Denkreihenfolge** (nachdem klar ist, **welches** System betrachtet wird und wo die **äußere Grenze** liegt — dafür sind **Architecture Inception Canvas** und **System Context Canvas** typischerweise die passende **Vorbereitung**):

1. **Domain / Bounded Context Canvas** — **fachliche Sicht:** Welche **Domänen** und **Bounded Contexts** gibt es, welche **Verantwortlichkeiten** und **sinnvollen Grenzen**? Ziel ist **fachliche Struktur**, **unabhängig** von konkreten Technikentscheidungen.

2. **Architecture Building Blocks Canvas** — **technische Struktur:** Welche **Bausteine oder Komponenten** gibt es, welche **Aufgaben** übernehmen sie, wie sind **Verantwortlichkeiten** verteilt? Die fachliche Zerlegung wird in **konkrete Systemteile** übersetzt (Mapping n:1 oder 1:n bewusst dokumentieren).

3. **Integration Canvas** — **Interaktion und Vernetzung:** Wie arbeiten diese Bausteine **miteinander** und mit **Nachbarsystemen** zusammen? Sichtbar werden **Schnittstellen**, **Datenflüsse**, **synchrone vs. asynchrone** Kommunikation und damit das System als **Netzwerk** von Teilen.

**Kurz die Leitfragen:**

| Canvas | Zentrale Frage |
|--------|----------------|
| **Domain / Bounded Context** | Wie ist das Problem **fachlich** strukturiert? |
| **Architecture Building Blocks** | Wie setzen wir diese Struktur **technisch** um? |
| **Integration** | Wie **arbeiten die Teile zusammen**? |

**Merksatz:** **Fachliche Struktur → technische Struktur → Interaktion** — oder: **Was gehört zusammen → wie bauen wir es → wie verbindet sich alles.**

```mermaid
flowchart LR
    D[Domain / Bounded Context Canvas] --> B[Architecture Building Blocks Canvas]
    B --> N[Integration Canvas]
    style D fill:#f0e6ff
    style B fill:#ffe6cc
    style N fill:#cce5ff
```

**Nutzen:** Man kann **Problemstellungen sauber trennen** — fachliche Modellierung, technische Zerlegung und Integrationsdesign **nacheinander** statt alles in einem Schritt zu vermischen. Das reduziert das Risiko, zu früh Technik zu wählen oder fachliche Grenzen an Deployments zu „verkleben“.

### Überblick: Absicherung, Betrieb, Kommunikation und Weiterentwicklung

Die folgenden Canvas ergänzen **Design- und Entscheidungs-Artefakte** (Inception, Kontext, Bausteine, Integration, Tradeoffs, ADRs) um eine Perspektive, die in **arc42** stark in den Kapiteln zu **Qualität**, **Risiken**, **Verteilung/Betrieb** und der **Erzählung** der Architektur vorkommt: *Funktioniert das System in der Praxis, und verstehen es die Beteiligten? Wie bleibt es über die Zeit handhabbar?*

#### Qualität und Risiken

Der **Quality Attribute Canvas** beantwortet die Frage, **wie gut** das System bestimmte Eigenschaften erfüllen muss — etwa Performance, Skalierbarkeit, Verfügbarkeit oder Sicherheit. Er hilft, diese Anforderungen nicht nur zu **benennen**, sondern zu **priorisieren** und in **Szenarien** zu konkretisieren; dabei werden **Zielkonflikte** sichtbar (z. B. hohe Performance vs. starke Konsistenz).

Der **Risk / Technical Debt Canvas** ergänzt das um **Risiken** und **technische Schulden**: bewusste oder unbewusste Kompromisse in der Architektur, mögliche **Folgen** von Entscheidungen und **Priorisierung** von Gegenmaßnahmen.

**Zusammen** liefern beide eine **realistische Einschätzung und Absicherung** der Architektur — passend zu arc42-Qualitätszielen und zum Risikokapitel.

#### Kommunikation

Der **Architecture Communication Canvas** zielt nicht auf die technische Zeichnung allein, sondern darauf, **wie** die Architektur **verschiedenen Zielgruppen** erklärt wird: welche **Botschaften** zählen, welche **Sichten** gezeigt werden und wie komplexe Inhalte **verständlich** vermittelt werden. So wird sichergestellt, dass Architektur **nicht nur existiert, sondern auch verstanden wird**.

#### Betrieb und Weiterentwicklung

Der **Deployment / Operations Canvas** richtet den Blick auf den **laufenden Betrieb**: Deployment und Umgebungen, **Skalierung**, **Monitoring**, **Verfügbarkeit** und Umgang mit **Ausfällen**. Damit wird sichtbar, ob die Architektur im Alltag **stabil und betreibbar** ist.

Der **Evolution / Roadmap Canvas** blickt **voraus**: vom **Ist-Zustand** zum **Zielbild**, mit **Zwischenstufen**, **Abhängigkeiten** und **Risiken** der Transformation — bewusst **evolutionär**, ohne Big-Bang als Standardannahme.

**Zusammen** unterstützen beide, die Architektur **langfristig tragfähig** zu machen (Betrieb heute, Entwicklung morgen).

#### Mental model (Kurz)

| Cluster | Leitfrage | Canvas |
|--------|-----------|--------|
| Qualität und Risiken | Wie gut muss es sein, und wo droht Gefahr? | Quality Attribute, Risk / Technical Debt |
| Kommunikation | Wie erklären wir es, damit es ankommt? | Architecture Communication |
| Betrieb und Zeit | Wie betreiben wir es stabil, und wie entwickelt es sich weiter? | Deployment / Operations, Evolution / Roadmap |

**Gesamtzusammenhang:** **Qualität und Risiko** stützen die **Tragfähigkeit**; **Kommunikation** die **Verständlichkeit**; **Betrieb und Evolution** die **Nutzbarkeit über Zeit und im Tagesgeschäft**.

> **Funktioniert es gut?** → Quality Attribute Canvas.  
> **Was kann schiefgehen?** → Risk / Technical Debt Canvas.  
> **Versteht es jede Zielgruppe?** → Architecture Communication Canvas.  
> **Läuft es stabil im Betrieb?** → Deployment / Operations Canvas.  
> **Bleibt es zukunftsfähig?** → Evolution / Roadmap Canvas.

```mermaid
flowchart TB
  subgraph QR[Qualität und Risiken]
    direction LR
    QAC[Quality Attribute Canvas]
    RTD[Risk / Technical Debt Canvas]
  end
  subgraph KO[Kommunikation]
    ACC[Architecture Communication Canvas]
  end
  subgraph BO[Betrieb und Weiterentwicklung]
    direction LR
    DPO[Deployment / Operations Canvas]
    ERV[Evolution / Roadmap Canvas]
  end
  QR --> T[Tragfähigkeit<br/>realistisch einschätzen]
  KO --> V[Von Stakeholdern<br/>verstanden werden]
  BO --> L[Im Betrieb stabil<br/>und über Zeit entwickelbar]
  style QR fill:#fff0cc
  style KO fill:#e8e8f8
  style BO fill:#d4edda
  style T fill:#f5f5f5
  style V fill:#f5f5f5
  style L fill:#f5f5f5
```

Vorlagen: `{PROMPT}/artefakte/quality-attribute-canvas.md`, `{PROMPT}/artefakte/risk-technical-debt-canvas.md`, `{PROMPT}/artefakte/architecture-communication-canvas.md`, `{PROMPT}/artefakte/deployment-operations-canvas.md`, `{PROMPT}/artefakte/evolution-roadmap-canvas.md`.

### Quality Attribute Canvas

Der **Quality Attribute Canvas** ist eine **querliegende Linse** auf **Qualität** und **nicht-funktionale Anforderungen**: welche *-ilities* **zählen**, wie sie **priorisiert** werden, wie sie sich in **konkreten Szenarien** (Stimulus–Reaktion–Maß) ausdrücken, wo **Zielkonflikte** entstehen und welche **Risiken** bei Nichterreichen drohen. Er ergänzt die strukturellen Canvas (Domain, Building Blocks, Integration) — denn dieselbe Zerlegung kann unterschiedliche Qualitätsziele **unterschiedlich stark** belasten.

Typische **Eingaben:** **Anforderungen** (`{REQUIREMENTS.MD}`), **Inception** (Ziele, Randbedingungen) und Stimmen aus **Betrieb** oder **Sicherheit**. **Ausgabe:** Übernahme in **arc42 Kapitel 1.2** und Qualitätsszenarien, Verankerung in **Feature-Spezifikationen**; bei harten Spannungen **Tradeoff Canvas Technik** und **ADRs**.

Vorlage: `{PROMPT}/artefakte/quality-attribute-canvas.md`.

### Risk / Technical Debt Canvas

Der **Risk / Technical Debt Canvas** fasst **Risiken** (technisch, organisatorisch, Integration) und **technische Schulden** zusammen: **Ursachen**, mögliche **Auswirkungen**, grobe **Wahrscheinlichkeit** und **Impact**, **Maßnahmen** (Vermeidung, Reduktion, Monitoring) sowie eine **priorisierte** Übersicht. Er ist bewusst **ehrlich** gedacht — ohne Beschönigung — und macht **implizite** Risiken und **still akzeptierte** Kompromisse sichtbar.

Typische **Eingaben:** Erkenntnisse aus **Quality Attribute Canvas** (was passiert bei Nichterreichen), **Integration Canvas**, **Feature-Umsetzung**, **Inception** und Betrieb/Incidents. **Ausgabe:** Pflege in **arc42** (Risiken), Einbindung in **Backlog** und **Feature-Spezifikationen**, bei strategischen Themen **ADRs** oder **Tradeoff Canvas Technik**.

Vorlage: `{PROMPT}/artefakte/risk-technical-debt-canvas.md`.

### Architecture Communication Canvas

Der **Architecture Communication Canvas** adressiert **nicht den Inhalt** der Architektur allein, sondern **wie** er **zielgruppengerecht** vermittelt wird: **Zielgruppen** und ihre Bedürfnisse, **Kernbotschaften** („was soll hängen bleiben?“), **relevante Sichten** (Kontext, Bausteine, Datenflüsse, …), **Kommunikationsmittel** (Diagramme, Dokumente, Präsentationen), **bewusste Vereinfachung** sowie **Risiken** der Kommunikation (Missverständnisse, falsche Erwartungen). Er **ergänzt** arc42 und die übrigen Canvas, indem er eine **Kommunikationsstrategie** pro Anlass strukturiert.

Typische **Eingabe:** bestehende oder geplante Darstellung in **`{SOFTWARE-ARCHITECTURE.MD}`**, **System Context** / **C4**-Material, ADR-Kurzüberblicke. **Ausgabe:** abgestimmte **Storyline** und Mittelwahl für Reviews, Onboarding, Management oder Fachbereich.

Vorlage: `{PROMPT}/artefakte/architecture-communication-canvas.md`.

### Deployment / Operations Canvas

Der **Deployment / Operations Canvas** fasst die **operative Realität** zusammen: **wo** und **wie** Software läuft (Deployment-Struktur, Umgebungen, Cluster/Nodes), **Skalierung** und Engpässe, **Logging, Monitoring und Alerting**, **Verfügbarkeit und Resilienz** (Redundanz, Failover, Recovery), **Betriebsaufwand** (Komplexität, erforderliche Skills) sowie **betriebliche Risiken** und Single Points of Failure. Er ist bewusst **nicht** als idealisiertes Architekturplakat gedacht, sondern als **ehrliche** Grundlage für Architektur, **Systemhandbuch** und **Betriebshandbuch**.

Typische **Eingaben:** **Integration Canvas** (Laufzeit und Schnittstellen), **Architecture Building Blocks** (was deployed wird), **Quality Attribute Canvas** (SLAs, Verfügbarkeit). **Rollen:** Softwarearchitekt und **Operativer Betrieb** sollten **gemeinsam** daran arbeiten.

Vorlage: `{PROMPT}/artefakte/deployment-operations-canvas.md`.

### Evolution / Roadmap Canvas

Der **Evolution / Roadmap Canvas** plant die **schrittweise Weiterentwicklung** der Architektur: **Ausgangslage** und Probleme, **Zielbild**, **sinnvolle Zwischenstufen** mit Reihenfolge, **Migrationsweg** inklusive Transformationsrisiken, **Abhängigkeiten** und typische **Stolpersteine**. Er ist auf **evolutionäre** Änderungen ausgelegt — **kein** Standard-Big-Bang; große Sprünge nur mit **expliziter** Begründung und Risikohinweis.

Typische **Eingaben:** aktueller **arc42**-Stand, **Risk / Technical Debt Canvas**, **Inception**-Ziele, Abstimmung mit **Product Owner** (Lieferrhythmus). **Ausgabe:** Meilensteine, die in **ADRs**, **Feature-Spezifikationen** und die **Architekturdokumentation** einfließen; **Communication Canvas** kann die Erzählung pro Stakeholdergruppe unterstützen.

Vorlage: `{PROMPT}/artefakte/evolution-roadmap-canvas.md`.

### Tradeoff Canvas, Architecture Decision Canvas und ADR

In der Architektur- und Produktarbeit erfüllen **Trade-off Canvas**, **Architecture Decision Canvas** und **Architecture Decision Record (ADR)** unterschiedliche, aber zusammenhängende Rollen **innerhalb desselben Entscheidungsprozesses** — oft **nach** einer ersten Inception- oder Kontextklärung. Nicht jede Entscheidung braucht alle Schritte: Bei kleinen oder eindeutigen Themen kann ein ADR ausreichen; bei komplexen oder teamübergreifenden Fragen lohnt sich der gesamte Verlauf inklusive Inception.

#### 1. Trade-off Canvas — Optionen verstehen und vergleichen

Typischerweise steht am Anfang (oder parallel zur Klärung des Problems) der **Trade-off Canvas**. Er dient dazu, **Lösungs- oder Prioritätsoptionen strukturiert** miteinander zu vergleichen. Dabei werden insbesondere **Unterschiede und Zielkonflikte** sichtbar: was eine Option bringt und was man dafür in Kauf nimmt. Ziel ist in dieser Phase noch nicht zwingend die finale Entscheidung, sondern ein **gemeinsames Verständnis der Optionen und Tradeoffs**.

In dieser Bibliothek gibt es dafür **zwei Vorlagen** (je nach Art der Spannung):

| Artefakt | Zuständigkeit | Fokus |
|----------|----------------|--------|
| **Tradeoff Canvas Produkt** | Product Owner | Scope, Termin, Nutzerwert, Risiko, Lieferfähigkeit u. a. |
| **Tradeoff Canvas Technik** | Softwarearchitekt | Qualitätsattribute, Betrieb, Komplexität, technische Varianten |

Überschneidungen (z. B. „Termin vs. technische Qualität“) können **beide Canvas** nacheinander oder in einer gemeinsamen Session sinnvoll sein.

Vorlagen: `{PROMPT}/artefakte/tradeoff-canvas-produkt.md`, `{PROMPT}/artefakte/tradeoff-canvas-technik.md`.

#### 2. Architecture Decision Canvas — entscheiden und begründen

Darauf aufbauend (oder bei klarer Optionenlage von dort startend) kommt der **Architecture Decision Canvas** zum Einsatz. Hier wird die **eigentliche Entscheidung vorbereitet und getroffen**: das Problem wird präzise formuliert, **relevante Kriterien** werden festgelegt, die Optionen werden **entlang dieser Kriterien bewertet**, und am Ende steht eine **konkrete, begründete Entscheidung** inklusive Konsequenzen und Nicht-Zielen.

Vorlage (Bibliothek): `{PROMPT}/artefakte/architecture-decision-canvas.md` (sobald das Artefakt angelegt ist).

#### 3. ADR — dauerhaft festhalten

Das Ergebnis wird anschließend in einem **Architecture Decision Record (ADR)** festgehalten. Der ADR ist die **kompakte, langfristige Dokumentation** der Entscheidung mit Kontext, Begründung und Konsequenzen — nachvollziehbar für **später Einstiegende** und für alle, die nicht in der ursprünglichen Diskussion dabei waren. Ablage im Projekt typischerweise unter `{DOCS}/{ADR}/`.

Vorlage: `{PROMPT}/artefakte/architecture-decision-record.md`.

#### Kurz zusammengefasst

- **Trade-off Canvas:** Optionen und Zielkonflikte **verstehen** und vergleichen.  
- **Architecture Decision Canvas:** Entscheidung **vorbereiten, treffen und begründen**.  
- **ADR:** Ergebnis **dauerhaft und knapp dokumentieren**.

Noch kürzer: **Erst das Vorhaben verorten, dann Optionen verstehen, dann entscheiden, dann dokumentieren.**

```mermaid
flowchart LR
    I[Architecture Inception Canvas] --> T[Tradeoff Canvas<br/>Produkt und/oder Technik]
    T --> D[Architecture Decision Canvas]
    D --> A[ADR]
    style I fill:#e8f4e8
    style T fill:#e1f5ff
    style D fill:#fff4e1
    style A fill:#ffffe1
```

### Visualisierung der Abhängigkeitskette

Das Diagramm entspricht dem **Metamodell** (Zörner 2021): **Architekturentscheidung** als Zentralpunkt, **beschriftete Kanten** wie im Original. Abweichungen zur nummerierten Liste sind u. a.: **Randbedingungen** und **technische Risiken** wirken **direkt** auf die Entscheidung (nicht nur über die Lösungsstrategie); **Übergreifende Konzepte konkretisieren** die Entscheidung; **Schnittstellenbeschreibung** ist aus dem **Systemkontext** begründet, die **Bausteinsicht konkretisiert deren Nutzung**; **Verteilungssicht** zeigt das **Deployment der Bausteinsicht**.

```mermaid
flowchart TB
    PE[Persona]
    PK[Produktkarton]
    SK[Systemkontext]
    QZ[Qualitätsziele]
    QS[Qualitätsszenarien]
    LS[Lösungsstrategie]
    UK[Übergreifendes Konzept]
    RB[Randbedingungen]
    TR[Technische Risiken]
    AE[Architekturentscheidung]
    BS[Bausteinsicht]
    LZ[Laufzeitsicht]
    VS[Verteilungssicht]
    SB[Schnittstellenbeschreibung]

    PK -->|macht lebendig| PE
    PK -->|grenzt Inhalte ein| SK
    PE -->|liefert Quellen und Auslöser für| QS
    SK -->|liefert Quellen für| QS
    QS -->|konkretisiert| QZ
    QZ -->|klingen an in| PK

    LS -->|adressiert| QZ
    LS -->|verweist auf| UK
    UK -->|konkretisiert| AE
    LS -->|verweist auf| AE
    QZ -->|leiten| AE
    QS -->|machen bewertbar| AE
    RB -->|schränken ein| AE
    TR -->|treiben| AE

    AE -->|setzt Eckpfeiler für| BS
    AE -->|beeinflusst| VS
    VS -->|zeigt Deployment von| BS
    LZ -->|ergänzt um Dynamik| BS
    BS -->|verfeinert| SK
    SB -->|beschreibt Interaktionspunkte aus| SK
    BS -->|konkretisiert Nutzung von| SB
    LZ -->|nutzt API aus| SB

    style AE fill:#f5e1ff
    style BS fill:#e1ffff
    style SK fill:#fff4e1
    style UK fill:#ffe1f5
```

**Glossar** (im Buch zu allen Mitteln gestrichelt angedeutet): klärt wichtige Begriffe **über** Persona, Produktkarton, Kontext, Qualität, Strategie, Entscheidungen und Sichten hinweg — im Diagramm weggelassen, um Lesbarkeit zu wahren.

### Kombiniertes Diagramm: arc42-Abhängigkeitskette + Praktischer Workflow

Das folgende Diagramm zeigt, wie die arc42-Abhängigkeitskette mit unserem praktischen Workflow (Anforderungen → User Stories → Feature-Spezifikation → Tasks) zusammenhängt. Der **architektur-strukturelle** Teil bleibt dabei **weiterhin bewusst verkürzt** (lineare Leserichtung); für Zörners **vollständiges Metamodell** siehe die **Visualisierung der Abhängigkeitskette** oben.

```mermaid
flowchart TD
    subgraph "Verständnis & Vision"
        A[Personas<br/>Produktkarton<br/>Vision]
        A --> B[Systemkontext<br/>Anforderungen]
    end
    
    subgraph "Qualitäts- & Rahmen-Treiber"
        B --> C[Qualitätsziele<br/>Randbedingungen<br/>Risiken]
    end
    
    subgraph "Strategie & Entscheidungen"
        C --> D[Lösungsstrategie<br/>Feature-Spezifikation]
        D --> E[Architekturentscheidungen<br/>ADRs]
    end
    
    subgraph "User Stories & Umsetzung"
        B --> F[User Stories]
        F --> D
        D --> G[Tasks]
    end
    
    subgraph "Struktur & Verhalten"
        E --> H[Bausteinsicht]
        H --> I[Schnittstellenbeschreibungen]
        H --> J[Laufzeitsicht]
        E --> J
        H --> K[Verteilungssicht]
        J --> K
    end
    
    subgraph "Querschnitt & Glossar"
        L[Übergreifende Konzepte] --> H
        L --> J
        L --> K
        M[Glossar] --> A
        M --> B
        M --> C
        M --> D
        M --> E
        M --> F
        M --> G
        M --> H
        M --> I
        M --> J
        M --> K
        M --> L
    end
    
    subgraph "Testing"
        F --> N[UAT Testplan]
        D --> O[Technischer Testplan]
        G --> P[Code-Tests]
        N --> Q[QA Testing]
        O --> Q
        P --> Q
    end
    
    style A fill:#e1f5ff
    style B fill:#fff4e1
    style C fill:#ffe1f5
    style D fill:#e1ffe1
    style E fill:#f5e1ff
    style F fill:#ffe1e1
    style G fill:#f5e1ff
    style H fill:#e1ffff
    style I fill:#ffffe1
    style J fill:#e1ffff
    style K fill:#e1ffff
    style L fill:#ffe1f5
    style M fill:#e1f5ff
    style N fill:#ffffe1
    style O fill:#e1ffff
    style P fill:#ffe1e1
    style Q fill:#e1ffe1
```

---

## Praktischer Workflow

In der Praxis läuft der Prozess folgendermaßen ab:

1. **Anforderungsmanager** definiert Anforderungen (strukturiert, mit REQ-IDs)
2. **Product Owner** kennt diese Anforderungen und erstellt User Stories (Mehrwert aus Nutzersicht)
3. **Architect + Dev Team** erstellen Feature-Spezifikation (technische Umsetzung)
4. **Tester/QA** definiert Testplan auf Basis der Feature-Spezifikation (und User Story)

**Hinweis:** In kleineren Teams kann der Product Owner auch die Rolle des Anforderungsmanagers übernehmen.

---

## 1. Anforderungen → User Stories → Feature-Spezifikation → Tasks

### Anforderungen (`{REQUIREMENTS.MD}`)

**Was:** Strukturierte Dokumentation aller Anforderungen (funktional, nicht-funktional, Randbedingungen)

**Wer:** Anforderungsmanager (oder Product Owner in kleineren Teams)

**Zweck:** Systematische Erfassung aller Anforderungen mit Priorisierung

**Enthält:**
- REQ-IDs (z.B. REQ-001, FUNC-001, QUAL-001, CONST-001)
- Beschreibungen
- Begründungen
- Prioritäten

**Beispiel:**
```
REQ-001: Als Nutzer kann ich mich anmelden
Typ: Funktional
Priorität: Hoch
Beschreibung: Nutzer können sich mit E-Mail und Passwort anmelden
```

**Verknüpfung:** Wird zu User Stories, verweist auf Vision

---

### User Stories (`{USER-STORIES}/`)

**Was:** Mehrwert-Beschreibung aus Nutzersicht

**Wer:** Product Owner

**Zweck:** Übersetzung von Anforderungen in nutzerzentrierte Stories

**Enthält:**
- Format: "Als [Rolle] möchte ich [Ziel], damit [Mehrwert]"
- Akzeptanzkriterien (aus Nutzersicht)
- Verknüpfung zu Anforderungen (REQ-IDs)

**Beispiel:**
```
US-001: Als Nutzer möchte ich mich mit E-Mail und Passwort anmelden, 
        damit ich auf meine Daten zugreifen kann.
        
Verknüpft mit: REQ-001

Akzeptanzkriterien (aus Nutzersicht):
- Nutzer kann sich mit gültigen Credentials anmelden
- Nach Anmeldung wird Dashboard angezeigt
- Bei ungültigen Credentials wird Fehlermeldung angezeigt
```

**Verknüpfung:** Leitet sich aus Anforderungen ab, verweist auf REQ-IDs, wird zu Feature-Spezifikation

---

### Feature-Spezifikation (`{FEATURES}/`)

**Was:** Technische Umsetzungsspezifikation

**Wer:** Softwarearchitekt + Entwicklerteam

**Zweck:** Detaillierte technische Beschreibung der Umsetzung

**Enthält:**
- Technische Anforderungen (Was ändert sich?)
- Architektur-Leitplanken (Wie wird es umgesetzt?)
- **Technische Akzeptanzkriterien** (Testbarkeit)
- Abhängigkeiten
- Risiken
- ADRs (Architecture Decision Records)

**Beispiel:**
```
Feature-001: User-Login-Implementierung

Verknüpft mit: US-001

Technische Anforderungen:
- Login-API Endpoint: POST /api/auth/login
- Datenbank: User-Tabelle mit E-Mail und Passwort-Hash
- Frontend: Login-Komponente

Architektur-Leitplanken:
- RESTful API Design
- JWT für Authentifizierung
- bcrypt für Password-Hashing

Technische Akzeptanzkriterien:
- Funktionale Tests: Login-API akzeptiert gültige Credentials → 200 OK + JWT Token
- Integration-Tests: Login-Flow: Frontend → API → Datenbank → Response
- Performance-Tests: Login-API antwortet innerhalb von 200ms (P95)
- Sicherheits-Tests: Passwort wird gehasht (bcrypt), Rate-Limiting aktiv
```

**Verknüpfung:** Basiert auf User Story, verweist auf User Story und ADRs, wird zu Tasks

---

### Tasks

**Was:** Konkrete Umsetzungsschritte

**Wer:** Entwicklerteam

**Zweck:** Umsetzbare Arbeitseinheiten

**Enthält:**
- Code-Änderungen
- Tests
- Dokumentation

**Beispiel:**
```
Task 1: Login-API Endpoint implementieren
Task 2: Datenbank-Schema erweitern
Task 3: Frontend Login-Komponente erstellen
Task 4: Unit Tests schreiben
Task 5: Integration Tests schreiben
```

**Verknüpfung:** Leitet sich aus Feature-Spezifikation ab, resultiert in Code

---

## 2. Testpläne und Akzeptanzkriterien

**Wichtig:** Testpläne sind nicht als separates Artefakt definiert, sondern sind Teil der verschiedenen Artefakte.

### In User Stories: Akzeptanzkriterien (aus Nutzersicht)

**Was:** Beschreibt, wann die User Story erfüllt ist (aus Nutzersicht)

**Wer:** Product Owner

**Zweck:** Definiert, wann die User Story als "fertig" gilt

**Beispiel:**
```
Akzeptanzkriterien:
- Nutzer kann sich mit gültigen Credentials anmelden
- Nach Anmeldung wird Dashboard angezeigt
- Bei ungültigen Credentials wird Fehlermeldung angezeigt
```

**Führt zu:** User Acceptance Tests (UAT)

---

### In Feature-Spezifikationen: Technische Akzeptanzkriterien

**Was:** Detaillierte Test-Spezifikationen

**Wer:** Softwarearchitekt + Entwicklerteam

**Zweck:** Beschreibt, wie technisch getestet wird

**Enthält:**
- **Funktionale Tests:** Was funktioniert?
- **Integration-Tests:** Wie funktioniert es zusammen?
- **Performance-Tests:** Wie schnell ist es?
- **Sicherheits-Tests:** Wie sicher ist es?

**Beispiel:**
```
Technische Akzeptanzkriterien:

Funktionale Tests:
- Login-API akzeptiert gültige Credentials → 200 OK + JWT Token
- Login-API lehnt ungültige Credentials ab → 401 Unauthorized

Integration-Tests:
- Login-Flow: Frontend → API → Datenbank → Response
- JWT Token wird korrekt generiert und validiert

Performance-Tests:
- Login-API antwortet innerhalb von 200ms (P95)
- System kann 1000 Login-Requests/Minute verarbeiten

Sicherheits-Tests:
- Passwort wird gehasht (bcrypt)
- Rate-Limiting aktiv (max 5 Versuche/Minute)
- JWT Token ist signiert und ablaufbar
```

**Führt zu:** Technische Tests (Unit, Integration, Performance, Security)

---

### Testpläne entstehen aus:

1. **User Story Akzeptanzkriterien** → User Acceptance Tests (UAT)
   - Testet aus Nutzersicht
   - Prüft, ob der Mehrwert geliefert wird
   - Wird von QA/PO geprüft

2. **Feature-Spezifikation technische Akzeptanzkriterien** → Technische Tests
   - Unit Tests (Entwickler)
   - Integration Tests (Entwickler + QA)
   - Performance Tests (QA)
   - Security Tests (QA + Security)

---

## 3. Rückverfolgbarkeit (Traceability)

Alle Artefakte sind miteinander verknüpft:

```
Vision ({VISION.MD})
  ↓
Anforderungen ({REQUIREMENTS.MD})
  REQ-001, REQ-002, ...
  ↓
User Stories ({USER-STORIES}/)
  US-001 → verweist auf REQ-001
  ↓
Feature-Spezifikation ({FEATURES}/)
  Feature-001 → verweist auf US-001
  ↓
Tasks (Task-Management)
  Task 1, Task 2, ... → verweisen auf Feature-001
  ↓
Code ({LANGUAGE}/)
  Code → verweist auf Tasks
```

### Vorteile der Rückverfolgbarkeit:

- **Änderungen können zurückverfolgt werden:** Wenn sich eine Anforderung ändert, kann man sehen, welche User Stories, Features und Tasks betroffen sind
- **Impact-Analyse möglich:** Bei Änderungen kann man den Impact auf andere Artefakte analysieren
- **Vollständigkeit kann geprüft werden:** Man kann prüfen, ob alle Anforderungen abgedeckt sind
- **Testabdeckung kann nachvollzogen werden:** Man kann sehen, welche Tests zu welchen Anforderungen gehören

---

## 4. Rollen-Verantwortlichkeiten für Tests

### Product Owner

**Verantwortlich für:**
- Definiert User Story Akzeptanzkriterien (aus Nutzersicht)
- Prüft User Acceptance Tests (UAT)
- Entscheidet, ob User Story erfüllt ist

**Nicht verantwortlich für:**
- Technische Test-Details
- Unit Tests
- Performance-Tests

---

### Softwarearchitekt

**Verantwortlich für:**
- Definiert technische Akzeptanzkriterien in Feature-Spezifikation
- Prüft Architektur-Konformität
- Führt Architektur-Reviews durch

**Nicht verantwortlich für:**
- User Story Akzeptanzkriterien (das ist PO-Aufgabe)
- Konkrete Test-Implementierung (das ist Team-Aufgabe)

---

### Entwicklerteam

**Verantwortlich für:**
- Schreibt Unit Tests basierend auf technischen Akzeptanzkriterien
- Schreibt Integration Tests
- Implementiert Code, der Tests erfüllt
- Führt Code-Reviews durch

**Nicht verantwortlich für:**
- User Story Akzeptanzkriterien (das ist PO-Aufgabe)
- Architektur-Leitplanken (das ist Architekt-Aufgabe)

---

### QA / Tester

**Verantwortlich für:**
- Erstellt Testpläne basierend auf:
  - **Feature-Spezifikation** (Hauptquelle für technische Tests)
  - User Story Akzeptanzkriterien (UAT)
  - Technischen Akzeptanzkriterien (Feature-Spezifikation)
- Führt Tests durch:
  - User Acceptance Tests (basierend auf User Story)
  - Integration Tests (basierend auf Feature-Spezifikation)
  - Performance Tests (basierend auf Feature-Spezifikation)
  - Security Tests (basierend auf Feature-Spezifikation)
- Prüft Definition of Done

**Wichtig:** Der Testplan sollte primär auf der Feature-Spezifikation basieren, da diese die technischen Akzeptanzkriterien enthält. Die User Story Akzeptanzkriterien werden für UAT verwendet.

**Nicht verantwortlich für:**
- User Story Definition (das ist PO-Aufgabe)
- Technische Spezifikation (das ist Architekt + Team-Aufgabe)

---

## 5. Kompletter Durchlauf: Beispiel

### Schritt 1: Anforderung

```
REQ-001: User-Login-Funktionalität
Typ: Funktional
Priorität: Hoch
Beschreibung: Nutzer können sich mit E-Mail und Passwort anmelden
Begründung: Ermöglicht personalisierten Zugriff auf Benutzerdaten
```

---

### Schritt 2: User Story

```
US-001: Als Nutzer möchte ich mich mit E-Mail und Passwort anmelden, 
        damit ich auf meine Daten zugreifen kann.
        
Verknüpft mit: REQ-001

Akzeptanzkriterien (aus Nutzersicht):
- Nutzer kann sich mit gültigen Credentials anmelden
- Nach Anmeldung wird Dashboard angezeigt
- Bei ungültigen Credentials wird Fehlermeldung angezeigt
```

---

### Schritt 3: Feature-Spezifikation

```
Feature-001: User-Login-Implementierung

Verknüpft mit: US-001

Technische Anforderungen:
- Login-API Endpoint: POST /api/auth/login
- Datenbank: User-Tabelle mit E-Mail und Passwort-Hash
- Frontend: Login-Komponente

Architektur-Leitplanken:
- RESTful API Design
- JWT für Authentifizierung
- bcrypt für Password-Hashing
- Rate-Limiting: max 5 Versuche/Minute

Technische Akzeptanzkriterien:
- Funktionale Tests:
  * Login-API akzeptiert gültige Credentials → 200 OK + JWT Token
  * Login-API lehnt ungültige Credentials ab → 401 Unauthorized
- Integration-Tests:
  * Login-Flow: Frontend → API → Datenbank → Response
- Performance-Tests:
  * Login-API antwortet innerhalb von 200ms (P95)
- Sicherheits-Tests:
  * Passwort wird gehasht (bcrypt)
  * Rate-Limiting aktiv (max 5 Versuche/Minute)
```

---

### Schritt 4: Tasks

```
Task 1: Login-API Endpoint implementieren
Task 2: Datenbank-Schema erweitern (User-Tabelle)
Task 3: Frontend Login-Komponente erstellen
Task 4: Unit Tests für Login-Service schreiben
Task 5: Integration Tests für Login-Flow schreiben
Task 6: Performance-Tests durchführen
Task 7: Security-Tests durchführen
```

---

### Schritt 5: Testpläne

#### UAT Testplan (aus User Story):

```
Test 1: Nutzer meldet sich mit gültigen Credentials an
- Erwartung: Dashboard wird angezeigt
- Status: [ ] Bestanden / [ ] Fehlgeschlagen

Test 2: Nutzer meldet sich mit ungültigen Credentials an
- Erwartung: Fehlermeldung wird angezeigt
- Status: [ ] Bestanden / [ ] Fehlgeschlagen
```

#### Technischer Testplan (aus Feature-Spezifikation):

```
Unit Tests:
- Login-Service: Password-Hashing funktioniert
- Login-Service: JWT-Generierung funktioniert
- Login-Service: Rate-Limiting funktioniert

Integration Tests:
- API-Endpoint: Login-Flow funktioniert end-to-end
- Datenbank: User-Daten werden korrekt gespeichert/abgerufen

Performance Tests:
- Response-Zeit < 200ms (P95)
- System kann 1000 Requests/Minute verarbeiten

Security Tests:
- Password-Hashing: bcrypt wird verwendet
- Rate-Limiting: Max 5 Versuche/Minute
- JWT Token: Signiert und ablaufbar
```

---

## 6. Workflow-Diagramm

```mermaid
flowchart TD
    A[Vision<br/>{VISION.MD}] --> B[Anforderungen<br/>{REQUIREMENTS.MD}<br/>REQ-001, REQ-002, ...]
    B --> C[User Stories<br/>{USER-STORIES}/<br/>US-001, US-002, ...]
    
    C --> D[Feature-Spezifikation<br/>{FEATURES}/<br/>Feature-001, ...]
    D --> E[Tasks<br/>Task-Management]
    E --> F[Code<br/>{LANGUAGE}/]
    
    C --> G[User Story<br/>Akzeptanzkriterien<br/>aus Nutzersicht]
    G --> H[UAT Testplan<br/>User Acceptance Tests]
    
    D --> I[Technische<br/>Akzeptanzkriterien<br/>Funktional, Integration,<br/>Performance, Security]
    I --> J[Technischer Testplan<br/>Unit, Integration,<br/>Performance, Security Tests]
    
    F --> K[Code-Tests<br/>Unit Tests,<br/>Integration Tests]
    
    H --> L[QA Testing<br/>Basierend auf<br/>beiden Testplänen]
    J --> L
    K --> L
    
    L --> M[Definition of Done<br/>Alle Tests bestanden]
    
    style A fill:#e1f5ff
    style B fill:#fff4e1
    style C fill:#ffe1f5
    style D fill:#e1ffe1
    style E fill:#f5e1ff
    style F fill:#ffe1e1
    style G fill:#ffffe1
    style H fill:#ffffe1
    style I fill:#e1ffff
    style J fill:#e1ffff
    style K fill:#ffe1e1
    style L fill:#e1ffe1
    style M fill:#e1f5ff
```

---

## Zusammenfassung

### Praktischer Workflow:

1. **Anforderungsmanager** definiert Anforderungen (strukturiert, mit REQ-IDs)
2. **Product Owner** erstellt User Stories basierend auf Anforderungen (Mehrwert aus Nutzersicht)
3. **Architect + Dev Team** erstellen Feature-Spezifikation basierend auf User Story (technische Umsetzung)
4. **Tester/QA** definiert Testplan primär auf Basis der Feature-Spezifikation (und User Story für UAT)

### Verantwortlichkeiten:

- **Anforderungen:** Anforderungsmanager (oder PO in kleineren Teams)
- **User Stories:** Product Owner
- **Feature-Spezifikationen:** Softwarearchitekt + Entwicklerteam
- **Tasks:** Entwicklerteam
- **Testpläne:** Tester/QA (primär basierend auf Feature-Spezifikation)

### Testpläne:

- **Hauptquelle:** Feature-Spezifikation (technische Akzeptanzkriterien)
- **Zusätzlich:** User Story Akzeptanzkriterien (für UAT)
- **Ergebnis:** Vollständiger Testplan mit technischen Tests und UAT

### Rückverfolgbarkeit:

Alle Artefakte sind miteinander verknüpft:
- Anforderungen (REQ-IDs) → User Stories (US-IDs) → Feature-Spezifikationen → Tasks → Code
