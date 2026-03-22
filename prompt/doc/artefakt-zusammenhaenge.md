# Artefakt-Zusammenhänge (Übersicht)

Die Erklärung ist in **zwei Dokumente** geteilt:

| Dokument | Inhalt |
|----------|--------|
| **[artefakt-zusammenhaenge-architektur.md](artefakt-zusammenhaenge-architektur.md)** | arc42 und Dokumentationsmittel, Abhängigkeitsketten, **Metamodell** (Mermaid mit beschrifteten Kanten), alle **Architektur-Canvas**, Tradeoff → Architecture Decision Canvas → ADR |
| **[artefakt-zusammenhaenge-delivery.md](artefakt-zusammenhaenge-delivery.md)** | **Lieferkette:** Anforderungen → User Stories → Feature-Spezifikation → Tasks → Code; Tests, Rollen, Rückverfolgbarkeit; **Hybrid-Diagramm** (Architektur-Dokumentationsmittel + Liefer-Artefakte, vereinfacht) und **reines** Workflow-Diagramm nur Lieferung/QA |

**Wann welches lesen?**

- Architektur strukturieren, dokumentieren, entscheiden, Canvas einsetzen → **Architektur-Dokument**.
- Backlog, Umsetzung, QA, Traceability aus Lieferperspektive → **Delivery-Dokument** (kürzer).

Beide Teile hängen zusammen: **Feature-Spezifikation** und Anforderungen **verweisen** auf Architektur-Leitplanken und **ADRs** — die Feature-Spezifikation ist **kein** arc42-Kapitel, sondern **Lieferartefakt**. Canvas-Ergebnisse fließen in Vision, Anforderungen und `{SOFTWARE-ARCHITECTURE.MD}` ein (siehe Verweise im Architektur-Dokument).
