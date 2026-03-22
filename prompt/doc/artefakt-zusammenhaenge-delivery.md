# Artefakt-Zusammenhänge: Delivery (Lieferkette & Tests)

Kurzfassung: wie **Vision → Anforderungen → User Stories → Feature-Spezifikation → Tasks → Code** zusammenspielt und wie **Tests** und **Rückverfolgbarkeit** daran hängen.

**Architektur-Dokumentation, Canvas und Metamodell:** [artefakt-zusammenhaenge-architektur.md](artefakt-zusammenhaenge-architektur.md)  
**Überblick beider Teile:** [artefakt-zusammenhaenge.md](artefakt-zusammenhaenge.md)

---

## Brücke zur Architektur

**Feature-Spezifikation** ist ein **Lieferartefakt** (dieses Dokument), **kein** Bestandteil von **arc42**. Die **Architekturdokumentation** (`{SOFTWARE-ARCHITECTURE.MD}` nach arc42) und **ADRs** (`{ADR}/`) beschreiben das System **über** Einzellieferungen hinweg.

Verbindung in der Praxis: NFR und Randbedingungen stammen aus **Anforderungen**; in der Feature-Spezifikation stehen **Leitplanken** und typisch **Verweise auf ADRs** (und bei Bedarf auf arc42-Kapitel), statt Architektur dauerhaft zu duplizieren. **Canvas** und das **Metamodell** erläutern die Architektur-Seite im **[Architektur-Dokument](artefakt-zusammenhaenge-architektur.md)**.

---

## Diagramm: arc42-Kette und praktischer Workflow (vereinfacht)

### Zwei Abstraktionsebenen — bewusst in einem Bild

Dieses Diagramm ist **kein** Ersatz für das **Bibliotheks-Metamodell** im Architektur-Dokument. Es verbindet **zwei unterschiedliche Denkebenenen**:

| Ebene | Was im Diagramm steckt | Typische Artefakte / Begriffe |
|-------|-------------------------|-------------------------------|
| **Architektur-Dokumentation** | arc42-nahe **Dokumentationsmittel** und Sichten | Bausteinsicht, Laufzeitsicht, Verteilungssicht, ADRs, Glossar, … |
| **Lieferung & Umsetzung** | **Backlog und Engineering** | User Stories, Tasks, Code, Testpläne, QA |

**Warum gemischt?** Um in **einem Überblick** zu zeigen, *wo* Vision/Anforderungen, **arc42/Architekturdokumentation** und Sprint-Artefakte **aneinandergrenzen**. Die **Feature-Spezifikation** liegt auf der **Liefer**-Seite und **verweist** auf Architektur — sie ist **kein** arc42-Kapitel. **Kanten und Reihenfolge** sind **stark vereinfacht** und **nicht** mit dem detaillierten **Netz** der Dokumentationsmittel gleichzusetzen.

**Für die reine Architektur-Sicht** (nur Dokumentationsmittel, **beschriftete Kanten**, Zentralpunkt Architekturentscheidung): [artefakt-zusammenhaenge-architektur.md](artefakt-zusammenhaenge-architektur.md) — Abschnitt *Visualisierung der Abhängigkeitskette*.

**Für die reine Lieferkette** (ohne arc42-Subgraphen): siehe weiter unten im Abschnitt **Workflow-Diagramm (Lieferung & QA)** in derselben Datei.

```mermaid
flowchart TD
    subgraph "Verständnis & Vision"
        A[Personas<br/>Produktkarton<br/>Vision]
        A --> B[Systemkontext<br/>Anforderungen]
    end
    
    subgraph "Qualitäts- & Rahmen-Treiber"
        B --> C[Qualitätsziele<br/>Randbedingungen<br/>Risiken]
    end
    
    subgraph "Strategie & Entscheidungen (Architekturdokumentation)"
        C --> LS[Lösungsstrategie<br/>arc42 Kap. 4]
        LS --> E[Architekturentscheidungen<br/>ADRs]
    end
    
    subgraph "User Stories & Umsetzung (Lieferkette)"
        B --> F[User Stories]
        F --> FS[Feature-Spezifikation<br/>Lieferartefakt · {FEATURES}/]
        FS --> G[Tasks]
        FS -->|Leitplanken · ADR-Ref| E
        C -->|NFR · Rahmen| FS
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
        M --> LS
        M --> FS
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
        FS --> O[Technischer Testplan]
        G --> P[Code-Tests]
        N --> Q[QA Testing]
        O --> Q
        P --> Q
    end
    
    style A fill:#e1f5ff
    style B fill:#fff4e1
    style C fill:#ffe1f5
    style LS fill:#e1ffe1
    style FS fill:#c8e6c9
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

## Ablauf in Kürze

1. **Anforderungsmanager** (oder PO in kleinen Teams): Anforderungen mit REQ-IDs (`{REQUIREMENTS.MD}`).
2. **Product Owner**: User Stories mit Verweis auf REQ-IDs, **Akzeptanzkriterien aus Nutzersicht** (`{USER-STORIES}/`).
3. **Softwarearchitekt + Dev-Team**: **Feature-Spezifikation** — technische Umsetzung, Leitplanken, **technische Akzeptanzkriterien**, Verweise auf ADRs (`{FEATURES}/`).
4. **Dev-Team**: Tasks → Code (`{LANGUAGE}/`).
5. **QA**: Testpläne — **primär** aus Feature-Spezifikation (technische Kriterien), **UAT** aus User-Story-Kriterien.

---

## Kette der Artefakte (Steckbrief)

| Artefakt | Ort / Platzhalter | Wer | Kern |
|----------|-------------------|-----|------|
| **Anforderungen** | `{REQUIREMENTS.MD}` | Anforderungsmanager / PO | REQ-IDs, fachlich + NFR + Randbedingungen |
| **User Stories** | `{USER-STORIES}/` | PO | Nutzenformulierung, REQ-Verknüpfung, **nutzerseitige** Akzeptanzkriterien |
| **Feature-Spezifikation** | `{FEATURES}/` | Architekt + Team | Technik, Leitplanken, **technische** Akzeptanzkriterien, ADR-Referenzen |
| **Tasks** | Task-Tool | Team | Umsetzbare Schritte, verknüpft mit Feature |
| **Code** | `{LANGUAGE}/` | Team | Implementierung; Commit/PR ggf. mit Task-Referenz |

**Hinweis zu ADRs:** Bindende Architekturentscheidungen sollten unter `{DOCS}/{ADR}/` liegen; die Feature-Spezifikation **verweist** darauf, statt Entscheidungen dauerhaft nur inline zu duplizieren.

---

## Tests (ohne separates „Testdokument“ als Pflicht)

- **User Story:** Akzeptanzkriterien (Nutzerperspektive) → **UAT**.
- **Feature-Spezifikation:** Technische Akzeptanzkriterien (funktional, Integration, Performance, Security wo nötig) → **Unit-, Integrations-, Last-, Security-Tests** nach Vereinbarung im Team.

---

## Rückverfolgbarkeit

```
Vision ({VISION.MD})
  → Anforderungen ({REQUIREMENTS.MD}), REQ-…
  → User Stories ({USER-STORIES}/), US-… → REQ-…
  → Feature-Spezifikation ({FEATURES}/), Feature-… → US-…
  → Tasks → Feature-…
  → Code → Tasks
```

**Nutzen:** Impact bei Änderungen, Vollständigkeit der Abdeckung, Nachvollziehbarkeit der Testbasis.

---

## Rollen bei Tests (Kurz)

| Rolle | UAT / Story-Kriterien | Technische Tests & Feature-Spez |
|-------|----------------------|----------------------------------|
| **Product Owner** | definiert, bewertet | nicht |
| **Softwarearchitekt** | nicht | technische Akzeptanzkriterien, Architektur-Review |
| **Dev-Team** | nicht | implementiert Tests laut Kriterien |
| **QA** | plant/führt UAT | plant/führt techn. Tests, DoD |

---

## Workflow-Diagramm (Lieferung & QA)

Dieses Diagramm bleibt auf der **Liefer- und Testebene** (Platzhalter-Pfade, IDs). Es enthält **keine** Baustein-/Laufzeit-/Verteilungssicht — die gehören zur **Architekturdokumentation** und zum **Metamodell** im [Architektur-Teil](artefakt-zusammenhaenge-architektur.md).

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

- **Kette:** REQ → US → Feature → Tasks → Code, durchgängig referenziert.
- **Tests:** UAT aus Story; technische Tests **primär** aus Feature-Spezifikation.
- **Zwei Diagramme:** Das **große** Diagramm oben mischt **Architektur-Dokumentation** und **Lieferung** (vereinfacht); darin sind **Lösungsstrategie (arc42 Kap. 4)** und **Feature-Spezifikation** **getrennt** — Feature ist **Lieferartefakt**, kein arc42-Kapitel. Das **Workflow-Diagramm** unten zeigt nur **Lieferung & QA**; das **Metamodell** nur mit Dokumentationsmitteln steht im Architektur-Teil.
- **Architektur:** Leitplanken und ADRs im Architektur-Dokument; die Feature-Spezifikation **verweist** darauf. Details im **[Architektur-Teil](artefakt-zusammenhaenge-architektur.md)**.
