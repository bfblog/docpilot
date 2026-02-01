# RAG-Optimierung für Dokumentation

Diese Dokumentation erklärt, wie Dokumente strukturiert werden müssen, damit RAG-Systeme (wie MS 365 Copilot) sie sinnvoll verarbeiten können.

---

## Das Problem mit RAG-Chunking

### Was passiert beim Chunking?

**RAG-Systeme:**
1. Zerlegen Dokumente in kleine Abschnitte (Chunks, typisch 200-500 Tokens)
2. Indexieren jeden Chunk einzeln in einer Vektordatenbank
3. Finden relevante Chunks über semantische Ähnlichkeit (Embeddings)

**Probleme:**
- Struktur geht verloren (Kapitel, Abschnitte)
- Verzeichnisse und Dateinamen werden ignoriert
- Zufällige Keyword-Überschneidungen führen zu falschen Treffern
- Kontext zwischen Chunks geht verloren

**Beispiel:**
- Ein arc42-Dokument (600+ Zeilen) wird in 10-20 Chunks zerlegt
- Chunk 1: "Einführung und Ziele" → Keywords: "Einführung", "Ziele", "Anforderungen"
- Chunk 2: "Bausteinsicht" → Keywords: "Bausteinsicht", "Komponenten", "Struktur"
- Problem: Suche nach "Ziele" findet nur Chunk 1, nicht das ganze Dokument

---

## Lösung 1: Dokumentstruktur für RAG optimieren

### 1.1 Klare Markdown-Struktur verwenden

**Wichtig:** RAG-Systeme können Markdown-Header erkennen und als Struktur verwenden.

**Gut strukturiert:**
```markdown
# Architekturdokumentation nach arc42

## Über arc42

arc42 ist ein Template zur Dokumentation von Softwarearchitekturen...

## 1. Einführung und Ziele

### 1.1 Anforderungen

**Zweck:** Beschreibung der grundlegenden Anforderungen...

### 1.2 Qualitätsziele

**Zweck:** Definition der wichtigsten Qualitätsziele...
```

**Warum:** Header helfen RAG, Struktur zu erkennen und Chunks sinnvoll zu setzen.

---

### 1.2 YAML-Frontmatter zur Identität

**Jedes Dokument sollte mit YAML-Frontmatter beginnen:**

```markdown
---
typ: artefakt
name: Architekturdokumentation nach arc42
kontext: Template zur Dokumentation von Softwarearchitekturen
rollen:
  - Softwarearchitekt
artefakte:
  - ADR
  - Feature-Spezifikation
  - SRS
workflows: []
---

# Artefakt: Architekturdokumentation nach arc42

## Über arc42
```

**Wichtig:**
- YAML-Frontmatter enthält Identität (typ, name, kontext, rollen, artefakte, workflows)
- **Keine Keyword-Listen im Frontmatter** - Keywords gehören in den Text
- Frontmatter wird oft als separater Chunk indexiert
- Erhöht Chance, dass RAG das richtige Dokument findet

**Alternative (falls YAML nicht möglich):**
Falls YAML-Frontmatter nicht möglich ist, verwende einen Metadaten-Bereich im Markdown-Format:
```markdown
# Artefakt: Architekturdokumentation nach arc42

**Dokumenttyp:** Artefakt-Template
**Bereich:** Softwarearchitektur
**Standard:** arc42
**Zweck:** Template zur Dokumentation von Softwarearchitekturen
**Verwandte Dokumente:** ADR, Feature-Spezifikation, SRS
**Verwandte Rollen:** Softwarearchitekt

**Hinweis:** Keywords gehören in den Text, nicht in Metadaten.

---

## Über arc42
```

---

### 1.3 Wiederholte Kontext-Informationen

**Problem:** Jeder Chunk verliert Kontext zum Gesamtdokument.

**Lösung:** Wichtige Informationen mehrfach erwähnen:

```markdown
## 1. Einführung und Ziele

Dieses Kapitel ist Teil der arc42 Architekturdokumentation. 
Arc42 ist ein Template zur Dokumentation von Softwarearchitekturen...

### 1.1 Anforderungen

**Zweck:** Beschreibung der grundlegenden Anforderungen an das System.
Dies ist Teil des arc42 Templates Kapitel 1...

### 1.2 Qualitätsziele

**Zweck:** Definition der wichtigsten Qualitätsziele.
Dies ist Teil des arc42 Templates Kapitel 1...
```

**Warum:** Jeder Chunk enthält Kontext zum Gesamtdokument.

---

### 1.4 Kapitel-Übersichten

**Am Anfang jedes Kapitels:**

```markdown
## 5. Bausteinsicht

**Überblick:** Dieses Kapitel beschreibt die statische Struktur des Systems.
Es ist Teil der arc42 Architekturdokumentation (Kapitel 5 von 12).

**Inhalt:**
- Übersicht über die Bausteine (Level 1)
- Detaillierung wichtiger Bausteine (Level 2, 3, ...)
- Abhängigkeiten zwischen Bausteinen
- Verantwortlichkeiten der einzelnen Bausteine

**Verwandte Kapitel:**
- Kapitel 6: Laufzeitsicht (beschreibt Interaktionen zwischen Bausteinen)
- Kapitel 7: Verteilungssicht (beschreibt Deployment der Bausteine)
- Kapitel 8: Querschnittliche Konzepte (betrifft alle Bausteine)
```

**Warum:** 
- Übersicht wird als separater Chunk indexiert
- Enthält alle wichtigen Keywords des Kapitels
- Verknüpft Kapitel miteinander

---

## Lösung 2: Spezifische Keywords verwenden

### 2.1 Das Problem mit generischen Keywords

**Generische Keywords (schlecht):**
- "Einführung" → kommt in vielen Dokumenten vor
- "Ziele" → kommt in vielen Dokumenten vor
- "Stakeholder" → kommt in vielen Dokumenten vor

**Problem:** RAG findet zufällige Dokumente, nicht die richtigen.

---

### 2.2 Spezifische Keywords verwenden

**Spezifische Keywords (gut):**
- "arc42 Einführung" statt "Einführung"
- "arc42 Qualitätsziele" statt "Ziele"
- "arc42 Stakeholder" statt "Stakeholder"
- "arc42 Bausteinsicht" statt "Bausteinsicht"

**Beispiel:**
```markdown
## 1. Einführung und Ziele

Dieses Kapitel ist Teil der arc42 Architekturdokumentation.
Die arc42 Einführung beschreibt die grundlegenden Anforderungen...
Die arc42 Qualitätsziele definieren die wichtigsten Qualitätsanforderungen...
```

**Warum:** Spezifische Keywords reduzieren zufällige Treffer.

---

### 2.3 Namespace-Prefixe für Keywords

**Für jedes Dokument einen Namespace:**

```markdown
**Namespace:** arc42
**Spezifische Keywords:** 
- arc42-Einführung
- arc42-Qualitätsziele
- arc42-Bausteinsicht
- arc42-Laufzeitsicht
- arc42-Architekturentscheidungen
```

**Beispiel in Text:**
```markdown
Die arc42-Bausteinsicht beschreibt die statische Struktur des Systems.
Die arc42-Laufzeitsicht beschreibt Interaktionen zur Laufzeit.
Die arc42-Verteilungssicht beschreibt das Deployment.
```

**Warum:** Namespace-Prefixe machen Keywords eindeutig.

---

### 2.4 Dokument-spezifische Begriffe verwenden

**Statt generischer Begriffe:**

**arc42-Dokument:**
```markdown
Die arc42 Bausteinsicht beschreibt die statische Struktur.
Die arc42 Laufzeitsicht beschreibt Interaktionen.
Die arc42 Verteilungssicht beschreibt Deployment.
```

**Anforderungsmanagement-Dokument:**
```markdown
Funktionale Anforderungen beschreiben, was das System tun soll.
Nicht-funktionale Anforderungen beschreiben, wie das System sein soll.
Randbedingungen beschreiben externe Vorgaben.
```

**Warum:** Jedes Dokument verwendet spezifische Begriffe.

---

## Lösung 3: Verknüpfungen zwischen Dokumenten

### 3.1 Beziehungen als klare Sätze

**Wichtig:** Beziehungen müssen als klare Sätze im Text stehen. Links allein reichen nicht für RAG-Systeme.

**Statt:**
```markdown
Siehe auch: [ADR](./artefakte/architecture-decision-record.md)
```

**Besser:**
```markdown
Architekturentscheidungen werden als Architecture Decision Records (ADRs) dokumentiert.
ADRs dokumentieren wichtige technische Entscheidungen mit Context, 
erwogenen Optionen, Entscheidung und Konsequenzen.
Das ADR Format hilft dabei, Architekturentscheidungen nachvollziehbar zu machen.
ADRs werden in der arc42 Architekturdokumentation in Kapitel 9 behandelt.
```

**Warum:** 
- Beziehungen sind als klare Sätze formuliert (nicht nur Links)
- Keywords "ADR", "Architecture Decision Record", "Architekturentscheidungen"
- Kontext erklärt die Beziehung
- RAG kann das verknüpfte Dokument finden

---

### 3.2 Beziehungsabschnitte

**Am Ende jedes Kapitels/Dokuments sollten explizite Beziehungsabschnitte stehen:**

```markdown
## Beteiligte Rollen

- **Softwarearchitekt:** Erstellt arc42 Architekturdokumentation und ADRs. 
  Der Softwarearchitekt verwendet das arc42 Template zur strukturierten Dokumentation.
- **Dev Team:** Verwendet arc42 Architektur als Leitplanke für Entwicklung.
  Das Dev Team orientiert sich an der arc42 Bausteinsicht für die Code-Struktur.

## Erzeugte Artefakte

- **ADR (Architecture Decision Record):** Dokumentiert Architekturentscheidungen 
  mit Context, Optionen, Entscheidung und Konsequenzen. ADRs werden in arc42 Kapitel 9 behandelt.
- **Feature-Spezifikation:** Beschreibt technische Umsetzung von Features 
  mit Architektur-Leitplanken und technischen Akzeptanzkriterien.
- **SRS (Software Requirements Specification):** Definiert neue Produkt-Features 
  mit technischen Anforderungen und Architektur-Änderungen.

## Wirkt mit in Workflows

- **Workflow: User Story zu Feature-Spezifikation:** 
  Die arc42 Architektur dient als Leitplanke für Feature-Spezifikationen.
- **Workflow: Architekturentscheidungen dokumentieren:** 
  ADRs werden nach arc42 Kapitel 9 strukturiert.
```

**Warum:**
- Explizite Beziehungsabschnitte mit stabilen Begriffen
- Beziehungen sind als klare Sätze formuliert (nicht nur Listen)
- Kontext erklärt Beziehungen
- RAG kann verknüpfte Dokumente finden

---

### 3.3 Cross-Referenzen mit spezifischen Keywords

**Statt:**
```markdown
Siehe Kapitel 5 für Details zur Bausteinsicht.
```

**Besser:**
```markdown
Die arc42 Bausteinsicht (Kapitel 5) beschreibt die statische Struktur des Systems.
Die arc42 Bausteinsicht zeigt Komponenten, Schichten und deren Verantwortlichkeiten.
Für Details zur arc42 Bausteinsicht siehe Kapitel 5 der arc42 Architekturdokumentation.
```

**Warum:** 
- Spezifische Keywords "arc42 Bausteinsicht"
- Mehrfache Erwähnung erhöht Chance, dass RAG findet
- Kontext erklärt, was gemeint ist

---

## Lösung 4: Dokumentstruktur für Chunking optimieren

### 4.1 Chunk-Grenzen respektieren

**Problem:** RAG-Chunking kann mitten in einem Abschnitt enden.

**Lösung:** Jeder Abschnitt sollte selbstständig sein:

```markdown
## 5. Bausteinsicht

**Überblick:** Dieses Kapitel beschreibt die statische Struktur des Systems.
Es ist Teil der arc42 Architekturdokumentation (Kapitel 5 von 12).

**Zweck:** Beschreibung des Aufbaus des Quellcodes und der Modularisierung 
des Systems in hierarchischer Form.

**Inhalt:**
- Übersicht über die Bausteine (Level 1)
- Detaillierung wichtiger Bausteine (Level 2, 3, ...)
- Abhängigkeiten zwischen Bausteinen
- Verantwortlichkeiten der einzelnen Bausteine

### 5.1 Level 1: Übersicht

Die arc42 Bausteinsicht Level 1 zeigt die Hauptkomponenten des Systems.
Diese Übersicht ist Teil der arc42 Architekturdokumentation Kapitel 5...

[Inhalt Level 1]

### 5.2 Level 2: Detaillierung

Die arc42 Bausteinsicht Level 2 detailliert wichtige Bausteine aus Level 1.
Diese Detaillierung ist Teil der arc42 Architekturdokumentation Kapitel 5...

[Inhalt Level 2]
```

**Warum:** Jeder Abschnitt enthält Kontext und kann einzeln verstanden werden.

---

### 4.2 Zusammenfassungen am Ende jedes Kapitels

**Am Ende jedes Kapitels:**

```markdown
## Zusammenfassung Kapitel 5: Bausteinsicht

Dieses Kapitel der arc42 Architekturdokumentation beschrieb die statische Struktur:

- **Level 1:** Übersicht über Hauptkomponenten
- **Level 2:** Detaillierung wichtiger Bausteine
- **Abhängigkeiten:** Zwischen Bausteinen
- **Verantwortlichkeiten:** Der einzelnen Bausteine

**Verwandte Kapitel:**
- Kapitel 6: Laufzeitsicht (zeigt Interaktionen zwischen diesen Bausteinen)
- Kapitel 7: Verteilungssicht (zeigt Deployment dieser Bausteine)
- Kapitel 8: Querschnittliche Konzepte (betrifft alle Bausteine)
```

**Warum:** Zusammenfassung wird als separater Chunk indexiert und enthält alle Keywords.

---

### 4.3 Glossar am Ende

**Glossar mit spezifischen Begriffen:**

```markdown
## Glossar

**arc42:** Template zur Dokumentation von Softwarearchitekturen mit 12 Kapiteln

**arc42 Bausteinsicht:** Beschreibt die statische Struktur des Systems (Kapitel 5)

**arc42 Laufzeitsicht:** Beschreibt Interaktionen zur Laufzeit (Kapitel 6)

**arc42 Verteilungssicht:** Beschreibt Deployment auf Infrastruktur (Kapitel 7)

**arc42 Architekturentscheidungen:** Dokumentiert wichtige Entscheidungen (Kapitel 9)
```

**Warum:** Glossar wird als separater Chunk indexiert und enthält alle wichtigen Begriffe.

---

## Lösung 5: Reduzierung zufälliger Referenzen

### 5.1 Namespace-Prefixe für alle wichtigen Begriffe

**Für jedes Dokument:**

```markdown
**Dokument-Namespace:** arc42
**Spezifische Begriffe:**
- arc42-Bausteinsicht (nicht nur "Bausteinsicht")
- arc42-Laufzeitsicht (nicht nur "Laufzeitsicht")
- arc42-Architekturentscheidungen (nicht nur "Architekturentscheidungen")
```

**Verwendung im Text:**
```markdown
Die arc42-Bausteinsicht beschreibt die statische Struktur.
Die arc42-Laufzeitsicht beschreibt Interaktionen.
Die arc42-Architekturentscheidungen dokumentieren wichtige Entscheidungen.
```

**Warum:** Reduziert zufällige Treffer in anderen Dokumenten.

---

### 5.2 Dokument-spezifische Kontexte

**Jedes Dokument sollte seinen Kontext klar machen:**

```markdown
# Architekturdokumentation nach arc42

**Kontext:** Dieses Dokument beschreibt das arc42 Template zur Dokumentation 
von Softwarearchitekturen. Es ist ein Artefakt-Template für Softwarearchitekten.

**Nicht zu verwechseln mit:**
- Anforderungsmanagement (andere Dokumentation)
- Feature-Spezifikationen (andere Dokumentation)
- Systemhandbuch (andere Dokumentation)
```

**Warum:** Klärt Kontext und reduziert Verwechslungen.

---

### 5.3 Explizite Abgrenzung

**Am Anfang jedes Dokuments:**

```markdown
## Über dieses Dokument

Dieses Dokument beschreibt das **arc42 Template** zur Dokumentation von 
Softwarearchitekturen. Es ist speziell für Softwarearchitekten gedacht, 
die ihre Architektur strukturiert dokumentieren möchten.

**Dieses Dokument ist NICHT:**
- Eine Anleitung zur Anforderungsanalyse (siehe Anforderungsmanagement)
- Eine Vorlage für Feature-Spezifikationen (siehe Feature-Spezifikation)
- Ein Systemhandbuch (siehe Systemhandbuch)
```

**Warum:** Explizite Abgrenzung reduziert Verwechslungen.

---

## Best Practices Zusammenfassung

### Für jedes Dokument:

1. **YAML-Frontmatter zur Identität:**
   - Typ, Name, Kontext, Rollen, Artefakte, Workflows
   - **Keine Keyword-Listen im Frontmatter** - Keywords gehören in den Text

2. **Titel-Struktur:**
   - Haupttitel = Dokumenttyp + eindeutiger Name
   - Beispiel: "Artefakt: Architekturdokumentation nach arc42"

3. **Abschnittsüberschriften:**
   - Müssen isoliert verständlich sein
   - Keine generischen Titel ohne Kontext ("Einleitung" → "Über arc42 Architekturdokumentation")

4. **Klare Markdown-Struktur:**
   - Header für Kapitel und Abschnitte
   - Jeder Abschnitt sollte selbstständig sein

5. **Beziehungen als klare Sätze:**
   - Beziehungen zwischen Rollen, Artefakten und Workflows als klare Sätze
   - Links allein reichen nicht (wichtig für RAG-Systeme)

6. **Beziehungsabschnitte:**
   - "Beteiligte Rollen"
   - "Erzeugte Artefakte"
   - "Wirkt mit in Workflows"
   - Verwende stabile Begriffe (keine Synonymwechsel)

7. **Terminologie-Konsistenz:**
   - Gleiche Begriffe überall gleich verwenden
   - Keine Abkürzungen oder Synonymwechsel für Kernobjekte

8. **Isolierte Verständlichkeit:**
   - Absätze müssen isoliert verständlich sein
   - Kein "siehe oben", keine unklaren Pronomen
   - Jeder Abschnitt sollte Kontext zum Gesamtdokument enthalten

9. **Wiederholte Kontext-Informationen:**
   - Wichtige Informationen mehrfach erwähnen
   - Jeder Chunk sollte Kontext zum Gesamtdokument enthalten

10. **Spezifische Keywords:**
    - Namespace-Prefixe verwenden (z.B. "arc42-Bausteinsicht")
    - Dokument-spezifische Begriffe verwenden
    - Keywords natürlich im Text (kein Keyword-Spam)

11. **Zusammenfassungen:**
    - Am Ende jedes Kapitels
    - Glossar am Ende des Dokuments

---

## Beispiel: Optimiertes arc42-Dokument

```markdown
---
typ: artefakt
name: Architekturdokumentation nach arc42
kontext: Template zur Dokumentation von Softwarearchitekturen
rollen:
  - Softwarearchitekt
artefakte:
  - ADR
  - Feature-Spezifikation
  - SRS
workflows: []
---

# Artefakt: Architekturdokumentation nach arc42

**Kontext:** Dieses Dokument beschreibt das arc42 Template zur Dokumentation 
von Softwarearchitekturen. Es ist ein Artefakt-Template für Softwarearchitekten.

---

## Über arc42 Architekturdokumentation

arc42 ist ein bewährtes Template zur Dokumentation von Softwarearchitekturen.
Die arc42 Architekturdokumentation besteht aus 12 Kapiteln...

## 1. Einführung und Ziele

Dieses Kapitel ist Teil der arc42 Architekturdokumentation.
Die arc42 Einführung beschreibt die grundlegenden Anforderungen...

### 1.1 Anforderungen

**Zweck:** Beschreibung der grundlegenden Anforderungen an das System.
Dies ist Teil des arc42 Templates Kapitel 1...

[Inhalt]

### 1.2 Qualitätsziele

**Zweck:** Definition der wichtigsten Qualitätsziele.
Dies ist Teil des arc42 Templates Kapitel 1...

[Inhalt]

## Zusammenfassung Kapitel 1

Dieses Kapitel der arc42 Architekturdokumentation beschrieb...

## Beteiligte Rollen

- **Softwarearchitekt:** Erstellt arc42 Architekturdokumentation und verwendet 
  das arc42 Template zur strukturierten Dokumentation von Softwarearchitekturen.

## Erzeugte Artefakte

- **ADR (Architecture Decision Record):** Dokumentiert Architekturentscheidungen 
  mit Context, Optionen, Entscheidung und Konsequenzen. ADRs werden in arc42 Kapitel 9 behandelt.
- **Feature-Spezifikation:** Beschreibt technische Umsetzung mit Architektur-Leitplanken 
  basierend auf der arc42 Architektur.

## Glossar

**arc42:** Template zur Dokumentation von Softwarearchitekturen
**arc42-Bausteinsicht:** Statische Struktur (Kapitel 5)
**arc42-Laufzeitsicht:** Interaktionen zur Laufzeit (Kapitel 6)
```

---

## Fazit

**Für RAG-Optimierung wichtig:**

1. ✅ YAML-Frontmatter zur Identität (typ, name, kontext, rollen, artefakte, workflows)
2. ✅ Titel-Struktur: Dokumenttyp + eindeutiger Name
3. ✅ Abschnittsüberschriften isoliert verständlich
4. ✅ Klare Struktur (Markdown-Header)
5. ✅ Beziehungen als klare Sätze (nicht nur Links)
6. ✅ Beziehungsabschnitte: "Beteiligte Rollen", "Erzeugte Artefakte", "Wirkt mit in Workflows"
7. ✅ Terminologie-Konsistenz (gleiche Begriffe überall gleich)
8. ✅ Isolierte Verständlichkeit (kein "siehe oben")
9. ✅ Spezifische Keywords mit Namespace
10. ✅ Wiederholte Kontext-Informationen
11. ✅ Zusammenfassungen und Glossar

**Vermeiden:**

1. ❌ Keyword-Listen im Frontmatter (Keywords gehören in den Text)
2. ❌ Generische Titel ohne Kontext ("Einleitung" statt "Über arc42 Architekturdokumentation")
3. ❌ Links ohne klare Sätze (Beziehungen müssen als Sätze formuliert sein)
4. ❌ Generische Keywords ohne Kontext
5. ❌ Abschnitte ohne Kontext zum Gesamtdokument
6. ❌ Verwechslungsgefahr durch ähnliche Begriffe
7. ❌ Keyword-Spam (semantische Klarheit ist wichtiger als Keyword-Dichte)

Diese Struktur hilft RAG-Systemen, Dokumente sinnvoll zu chunkieren und relevante Informationen zu finden.
