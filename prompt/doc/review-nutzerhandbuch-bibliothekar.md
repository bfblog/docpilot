# Review: Nutzerhandbuch - Perspektive Bibliothekar

**Reviewer:** Bibliothekar und Qualitätssicherer  
**Datum:** 2026-01-31  
**Artefakt:** `prompt/artefakte/nutzerhandbuch.md`  
**Prüfkriterien:** 9 Bibliothekar-Regeln aus `_koordinator.md`

---

## Zusammenfassung

**Gesamtbewertung:** ⚠️ **3/9 Regeln erfüllt** - Kritische Compliance-Probleme

**Status:**
- ✅ **Regel 1:** YAML-Frontmatter - **FEHLT KOMPLETT**
- ✅ **Regel 2:** Titel-Struktur - **FEHLT** (falscher Titel)
- ⚠️ **Regel 3:** Abschnittsüberschriften - **TEILWEISE** (viele generische Titel)
- ❌ **Regel 4:** Beziehungen als klare Sätze - **FEHLT**
- ❌ **Regel 5:** Beziehungsabschnitte - **FEHLT**
- ✅ **Regel 6:** Terminologie-Konsistenz - **GUT**
- ⚠️ **Regel 7:** Isolierte Verständlichkeit - **TEILWEISE** (viele "siehe"-Referenzen)
- ✅ **Regel 8:** Ordnerstruktur - **NICHT RELEVANT** (Einzeldatei)
- ✅ **Regel 9:** Kein Keyword-Spam - **GUT**

**Kritische Probleme:**
1. **FEHLT:** YAML-Frontmatter komplett
2. **FEHLT:** Korrekte Titel-Struktur ("Artefakt: Nutzerhandbuch")
3. **FEHLT:** Beziehungsabschnitte (Beteiligte Rollen, Verknüpfungen zu anderen Artefakten)
4. **FEHLT:** Beziehungen als klare Sätze im Text
5. **PROBLEM:** Viele generische Überschriften ohne Kontext
6. **PROBLEM:** Viele "siehe"-Referenzen ohne isolierte Verständlichkeit

---

## Detaillierte Prüfung gegen Bibliothekar-Regeln

### Regel 1: YAML-Frontmatter zur Identität

**Status:** ❌ **FEHLT KOMPLETT**

**Aktueller Zustand:**
- Die Datei beginnt direkt mit `# Nutzerhandbuch / Benutzerhandbuch - Aufbau und Struktur`
- Kein YAML-Frontmatter vorhanden

**Erforderlich:**
```yaml
---
typ: artefakt
name: Nutzerhandbuch
kontext: Template zur Erstellung eines Nutzerhandbuchs für Endnutzer
rollen:
  - Product Owner
  - Technical Writer
artefakte: []
workflows: []
---
```

**Bewertung:** **KRITISCH** - Ohne Frontmatter kann das Dokument nicht korrekt identifiziert und kategorisiert werden. RAG-Systeme benötigen diese Metadaten für die korrekte Zuordnung.

---

### Regel 2: Titel-Struktur

**Status:** ❌ **FEHLT**

**Aktueller Titel:**
```markdown
# Nutzerhandbuch / Benutzerhandbuch - Aufbau und Struktur
```

**Erforderlich:**
```markdown
# Artefakt: Nutzerhandbuch
```

**Begründung:**
- Der Titel muss immer "Dokumenttyp + eindeutiger Name" enthalten
- Beispiele aus den Regeln: "Artefakt: Architekturdokumentation nach arc42", "Rolle: Softwarearchitekt"
- Der aktuelle Titel ist zu lang und enthält keine Dokumenttyp-Kennzeichnung

**Bewertung:** **KRITISCH** - Titel-Struktur ist essentiell für RAG-Systeme, um Dokumenttypen zu identifizieren.

---

### Regel 3: Abschnittsüberschriften

**Status:** ⚠️ **TEILWEISE PROBLEMATISCH**

**Problembeispiele:**

1. **Generische Titel ohne Kontext:**
   - `## Über Nutzerhandbücher` → **GUT** (hat Kontext)
   - `## Zielgruppe und Zweck` → **GUT** (hat Kontext)
   - `## Aufbau des Nutzerhandbuchs` → **GUT** (hat Kontext)
   - `## 1. Einführung und Schnellstart` → **GUT** (hat Kontext)
   - `## 1.1 Willkommen` → ⚠️ **PROBLEMATISCH** (generisch, fehlt Kontext)
   - `## 1.2 Über dieses Handbuch` → ⚠️ **PROBLEMATISCH** (generisch, fehlt Kontext)
   - `## 1.3 Schnellstart` → ⚠️ **PROBLEMATISCH** (generisch, fehlt Kontext)
   - `## 2. Erste Schritte` → **GUT** (hat Kontext)
   - `## 3. Grundfunktionen` → **GUT** (hat Kontext)
   - `## 4. Erweiterte Funktionen` → **GUT** (hat Kontext)

**Verbesserungsvorschläge:**
- `## 1.1 Willkommen` → `## 1.1 Willkommen im Nutzerhandbuch`
- `## 1.2 Über dieses Handbuch` → `## 1.2 Über das Nutzerhandbuch`
- `## 1.3 Schnellstart` → `## 1.3 Schnellstart-Anleitung für Nutzerhandbuch`

**Bewertung:** **TEILWEISE** - Viele Überschriften sind gut, aber einige sind zu generisch und verlieren ihren Kontext bei isolierter Betrachtung (wichtig für RAG-Chunking).

---

### Regel 4: Beziehungen als klare Sätze

**Status:** ❌ **FEHLT**

**Aktueller Zustand:**
- Keine expliziten Beziehungsabschnitte vorhanden
- Keine klaren Sätze über Beziehungen zu Rollen oder anderen Artefakten

**Erforderlich:**
Das Dokument sollte klare Sätze enthalten wie:
- "Der Product Owner erstellt Nutzerhandbücher gemeinsam mit Technical Writern. Nutzerhandbücher beschreiben die Bedienung der Software für Endnutzer."
- "Nutzerhandbücher ergänzen Systemhandbücher: Während Systemhandbücher die technische Funktionsweise beschreiben, erklären Nutzerhandbücher die Bedienung für Endnutzer."
- "Nutzerhandbücher basieren auf User Stories und Feature-Spezifikationen, um die Funktionalität aus Nutzersicht zu dokumentieren."

**Bewertung:** **KRITISCH** - Ohne klare Beziehungssätze können RAG-Systeme die Verbindungen zu anderen Dokumenten nicht herstellen.

---

### Regel 5: Beziehungsabschnitte

**Status:** ❌ **FEHLT**

**Aktueller Zustand:**
- Keine Abschnitte "Beteiligte Rollen"
- Keine Abschnitte "Erzeugte Artefakte"
- Keine Abschnitte "Verknüpfungen zu anderen Artefakten"

**Erforderlich:**
Am Ende des Dokuments sollten folgende Abschnitte stehen:

```markdown
## Beteiligte Rollen

- **Product Owner:** Verantwortlich für die Produktvision und Anforderungen, die im Nutzerhandbuch dokumentiert werden.
- **Technical Writer:** Erstellt und pflegt das Nutzerhandbuch, stellt Verständlichkeit und Vollständigkeit sicher.
- **UX-Designer:** Liefert Informationen zur Benutzeroberfläche und Interaktionsmustern.
- **Support-Team:** Liefert Informationen zu häufigen Fragen und Problemen.

## Verknüpfungen zu anderen Artefakten

- **User Stories:** Nutzerhandbücher beschreiben die Umsetzung von User Stories aus Nutzersicht.
- **Feature-Spezifikationen:** Nutzerhandbücher dokumentieren die Funktionalität, die in Feature-Spezifikationen beschrieben wird.
- **Systemhandbuch:** Nutzerhandbücher ergänzen Systemhandbücher - während Systemhandbücher die technische Funktionsweise beschreiben, erklären Nutzerhandbücher die Bedienung für Endnutzer.
- **Vision:** Nutzerhandbücher helfen, die Produktvision für Endnutzer greifbar zu machen.
```

**Bewertung:** **KRITISCH** - Diese Abschnitte sind essentiell für die Nachvollziehbarkeit von Beziehungen in RAG-Systemen.

---

### Regel 6: Terminologie-Konsistenz

**Status:** ✅ **GUT**

**Aktueller Zustand:**
- Konsistente Verwendung von "Nutzerhandbuch" und "Benutzerhandbuch" (beide werden als Synonyme verwendet)
- Konsistente Verwendung von "Endnutzer", "Benutzer", "Anwender"
- Keine Synonymwechsel für Kernobjekte

**Beispiele:**
- Immer "Nutzerhandbuch" oder "Benutzerhandbuch" (beide sind akzeptiert)
- Immer "Endnutzer" oder "Benutzer" (konsistent)
- Keine Abkürzungen wie "NH" oder "UH"

**Bewertung:** **GUT** - Terminologie ist konsistent verwendet.

---

### Regel 7: Isolierte Verständlichkeit

**Status:** ⚠️ **TEILWEISE PROBLEMATISCH**

**Problembeispiele:**

1. **"siehe"-Referenzen ohne Kontext:**
   - Zeile 314: `💡 **Tipp:** Sie können Ihre Einstellungen später jederzeit ändern (siehe Kapitel 7).`
   - Zeile 487: `- **Daten anzeigen:** [Kurzbeschreibung] → Siehe Kapitel 3.2`
   - Zeile 488: `- **Daten erstellen:** [Kurzbeschreibung] → Siehe Kapitel 3.3`
   - Zeile 1040: `1. Öffnen Sie die Einstellungen (siehe Kapitel 7.1)`

**Verbesserungsvorschläge:**
- Statt: `(siehe Kapitel 7)` → `(Einstellungen werden in Kapitel 7 "Konfiguration und Einstellungen" beschrieben)`
- Statt: `→ Siehe Kapitel 3.2` → `→ Detaillierte Beschreibung in Kapitel 3.2 "Daten anzeigen"`

**Gute Beispiele (isolierte Verständlichkeit):**
- Zeile 8-10: Unterschied zu anderen Dokumentationen wird klar erklärt
- Zeile 22-74: Zielgruppe und Zweck sind vollständig beschrieben

**Bewertung:** **TEILWEISE** - Viele Abschnitte sind isoliert verständlich, aber einige "siehe"-Referenzen fehlen Kontext. Bei RAG-Chunking können diese Referenzen isoliert betrachtet werden und verlieren ihre Bedeutung.

---

### Regel 8: Ordnerstruktur

**Status:** ✅ **NICHT RELEVANT**

**Begründung:**
- Diese Regel betrifft die Ordnerstruktur, nicht einzelne Dateien
- Die Datei liegt korrekt in `artefakte/`
- Keine Probleme mit der Ordnerstruktur

**Bewertung:** **NICHT RELEVANT** - Regel betrifft Ordnerstruktur, nicht einzelne Dateien.

---

### Regel 9: Kein Keyword-Spam

**Status:** ✅ **GUT**

**Aktueller Zustand:**
- Keine Keyword-Listen im Text
- Keine SEO-Blöcke
- Keine künstlichen Begriffsketten
- Keywords kommen natürlich im Text vor

**Beispiele:**
- "Nutzerhandbuch", "Endnutzer", "Benutzerhandbuch" kommen natürlich im Text vor
- Keine künstlichen Wiederholungen
- Keine Keyword-Dichte-Optimierung

**Bewertung:** **GUT** - Kein Keyword-Spam vorhanden.

---

## Zusammenfassung der kritischen Probleme

### Priorität 1 (KRITISCH - Muss behoben werden):

1. **YAML-Frontmatter fehlt komplett**
   - **Auswirkung:** Dokument kann nicht korrekt identifiziert werden
   - **Lösung:** YAML-Frontmatter am Anfang hinzufügen

2. **Titel-Struktur falsch**
   - **Auswirkung:** Dokumenttyp nicht erkennbar
   - **Lösung:** Titel zu `# Artefakt: Nutzerhandbuch` ändern

3. **Beziehungsabschnitte fehlen**
   - **Auswirkung:** Beziehungen zu Rollen und Artefakten nicht nachvollziehbar
   - **Lösung:** Abschnitte "Beteiligte Rollen" und "Verknüpfungen zu anderen Artefakten" hinzufügen

4. **Beziehungen als klare Sätze fehlen**
   - **Auswirkung:** RAG-Systeme können Verbindungen nicht herstellen
   - **Lösung:** Klare Sätze über Beziehungen im Text ergänzen

### Priorität 2 (WICHTIG - Sollte behoben werden):

5. **Generische Überschriften ohne Kontext**
   - **Auswirkung:** Bei isolierter Betrachtung (RAG-Chunking) verlieren Überschriften ihren Kontext
   - **Lösung:** Überschriften wie "Willkommen" → "Willkommen im Nutzerhandbuch" erweitern

6. **"siehe"-Referenzen ohne Kontext**
   - **Auswirkung:** Bei isolierter Betrachtung sind Referenzen nicht nachvollziehbar
   - **Lösung:** "siehe Kapitel X" → "Details in Kapitel X 'Titel'" erweitern

---

## Empfohlene Korrekturen

### 1. YAML-Frontmatter hinzufügen

**Position:** Ganz am Anfang der Datei

```yaml
---
typ: artefakt
name: Nutzerhandbuch
kontext: Template zur Erstellung eines Nutzerhandbuchs für Endnutzer
rollen:
  - Product Owner
  - Technical Writer
  - UX-Designer
  - Support-Team
artefakte:
  - User Stories
  - Feature-Spezifikationen
  - Systemhandbuch
  - Vision
workflows: []
---
```

### 2. Titel korrigieren

**Von:**
```markdown
# Nutzerhandbuch / Benutzerhandbuch - Aufbau und Struktur
```

**Zu:**
```markdown
# Artefakt: Nutzerhandbuch
```

### 3. Beziehungsabschnitte hinzufügen

**Position:** Am Ende des Dokuments, vor "Zusammenfassung"

```markdown
## Beteiligte Rollen

- **Product Owner:** Verantwortlich für die Produktvision und Anforderungen, die im Nutzerhandbuch dokumentiert werden. Der Product Owner definiert die Zielgruppe und die wichtigsten Funktionen, die dokumentiert werden müssen.
- **Technical Writer:** Erstellt und pflegt das Nutzerhandbuch, stellt Verständlichkeit und Vollständigkeit sicher. Technical Writer übersetzen technische Informationen in benutzerfreundliche Anleitungen.
- **UX-Designer:** Liefert Informationen zur Benutzeroberfläche und Interaktionsmustern. UX-Designer helfen dabei, die Bedienung aus Nutzersicht zu beschreiben.
- **Support-Team:** Liefert Informationen zu häufigen Fragen und Problemen. Das Support-Team identifiziert typische Nutzerprobleme, die im Handbuch dokumentiert werden sollten.

## Verknüpfungen zu anderen Artefakten

- **User Stories:** Nutzerhandbücher beschreiben die Umsetzung von User Stories aus Nutzersicht. Die in User Stories definierten Funktionen werden im Nutzerhandbuch als Schritt-für-Schritt-Anleitungen dokumentiert.
- **Feature-Spezifikationen:** Nutzerhandbücher dokumentieren die Funktionalität, die in Feature-Spezifikationen beschrieben wird. Während Feature-Spezifikationen die technische Umsetzung beschreiben, erklären Nutzerhandbücher die Bedienung für Endnutzer.
- **Systemhandbuch:** Nutzerhandbücher ergänzen Systemhandbücher. Während Systemhandbücher die technische Funktionsweise für Operations und Support beschreiben, erklären Nutzerhandbücher die Bedienung für Endnutzer.
- **Vision:** Nutzerhandbücher helfen, die Produktvision für Endnutzer greifbar zu machen. Die in der Vision beschriebenen Nutzenversprechen werden im Nutzerhandbuch durch konkrete Anleitungen umgesetzt.
```

### 4. Beziehungen als klare Sätze ergänzen

**Position:** Im Abschnitt "Über Nutzerhandbücher" (nach Zeile 10)

```markdown
**Unterschied zu anderen Dokumentationen:**
- **Architekturdokumentation (z.B. arc42):** Fokus auf "Warum" und Design, Zielgruppe: Entwickler, Architekten
- **Systemhandbuch:** Fokus auf "Wie funktioniert es technisch", Zielgruppe: Operative, Support
- **Nutzerhandbuch:** Fokus auf "Wie benutze ich es", Zielgruppe: Endnutzer, Anwender

**Beziehungen zu anderen Artefakten:**
- Nutzerhandbücher basieren auf User Stories und Feature-Spezifikationen, um die Funktionalität aus Nutzersicht zu dokumentieren.
- Nutzerhandbücher ergänzen Systemhandbücher: Während Systemhandbücher die technische Funktionsweise beschreiben, erklären Nutzerhandbücher die Bedienung für Endnutzer.
- Der Product Owner erstellt Nutzerhandbücher gemeinsam mit Technical Writern, um Endnutzern die effiziente Nutzung der Software zu ermöglichen.
```

### 5. Generische Überschriften erweitern

**Beispiele:**
- `## 1.1 Willkommen` → `## 1.1 Willkommen im Nutzerhandbuch`
- `## 1.2 Über dieses Handbuch` → `## 1.2 Über das Nutzerhandbuch`
- `## 1.3 Schnellstart` → `## 1.3 Schnellstart-Anleitung`

### 6. "siehe"-Referenzen erweitern

**Beispiele:**
- `(siehe Kapitel 7)` → `(Einstellungen werden in Kapitel 7 "Konfiguration und Einstellungen" beschrieben)`
- `→ Siehe Kapitel 3.2` → `→ Detaillierte Beschreibung in Kapitel 3.2 "Daten anzeigen"`

---

## Fazit

Das Nutzerhandbuch ist **inhaltlich gut strukturiert**, erfüllt aber **nur 3 von 9 Bibliothekar-Regeln**. Die kritischen Probleme (fehlendes YAML-Frontmatter, falsche Titel-Struktur, fehlende Beziehungsabschnitte) müssen behoben werden, damit das Dokument RAG-tauglich ist und korrekt in die Bibliothek integriert werden kann.

**Nächste Schritte:**
1. YAML-Frontmatter hinzufügen
2. Titel korrigieren
3. Beziehungsabschnitte hinzufügen
4. Beziehungen als klare Sätze ergänzen
5. Generische Überschriften erweitern
6. "siehe"-Referenzen mit Kontext versehen

**Empfehlung:** Die Korrekturen sollten **priorisiert** durchgeführt werden, beginnend mit den kritischen Problemen (Priorität 1).
