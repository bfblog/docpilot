# Architecture Decision Record (ADR)

## Über Architecture Decision Records

Ein **Architecture Decision Record (ADR)** ist ein leichtgewichtiges Dokumentationsformat, das dazu dient, wichtige Architekturentscheidungen in Softwareprojekten festzuhalten. Es ermöglicht Teams, den Entscheidungsprozess, die zugrunde liegenden Überlegungen und die Auswirkungen einer Entscheidung nachvollziehbar zu dokumentieren.

ADRs wurden ursprünglich von Michael Nygard in seinem Blog-Artikel "Documenting Architecture Decisions" vorgeschlagen und haben sich als Standard für die Dokumentation von Architekturentscheidungen etabliert.

---

## Sinn und Zweck

### Warum ADRs verwenden?

**1. Nachvollziehbarkeit**
- ADRs ermöglichen es, den Kontext und die Gründe für getroffene Architekturentscheidungen zu verstehen
- Besonders hilfreich bei späteren Änderungen oder Überprüfungen von Entscheidungen
- Neue Teammitglieder können schnell den Hintergrund von Entscheidungen nachvollziehen

**2. Transparenz**
- Entscheidungen werden für alle Beteiligten transparent dokumentiert
- Fördert das gemeinsame Verständnis im Team
- Stakeholder können nachvollziehen, warum bestimmte Entscheidungen getroffen wurden

**3. Wissenssicherung**
- Dient als zentrales Nachschlagewerk für Architekturentscheidungen
- Bewahrt das Wissen innerhalb des Teams, auch wenn Mitglieder das Team verlassen
- Verhindert, dass Entscheidungen wiederholt diskutiert werden müssen

**4. Lernprozess**
- Dokumentation von Alternativen und deren Bewertung hilft bei zukünftigen Entscheidungen
- Dient als historisches Archiv für ähnliche Herausforderungen
- Ermöglicht Reflexion über getroffene Entscheidungen

**5. Compliance und Audit**
- Nachweisbare Dokumentation von Entscheidungen für Compliance-Anforderungen
- Unterstützt Audits und Reviews
- Zeigt, dass Entscheidungen bewusst und durchdacht getroffen wurden

---

## Aufbau eines ADR

Ein ADR sollte klar strukturiert und leicht verständlich sein. Die folgende Struktur hat sich als bewährt erwiesen:

### Standard-Struktur (nach Michael Nygard)

```markdown
# ADR-[Nummer]: [Titel der Entscheidung]

## Status
[Vorgeschlagen | Akzeptiert | Abgelehnt | Ersetzt | Abgelaufen]

**Datum:** [Datum der Entscheidung]  
**Entscheider:** [Person oder Team] (optional)  
**Technische Story:** [Beschreibung oder Link zu Ticket/Issue] (optional)

## Kontext
[Beschreibung des Problems oder der Situation, die die Entscheidung erforderlich macht]

## Erwogene Optionen
[Alle Alternativen, die in Betracht gezogen wurden]

## Entscheidung
[Die getroffene Entscheidung - in aktiver Form: "Wir entscheiden uns für..."]

## Konsequenzen
[Positive und negative Auswirkungen der Entscheidung]
```

### Detaillierte Struktur mit Erklärungen

#### 1. Titel und Nummer

**Format:** `ADR-[Nummer]: [Kurze, prägnante Beschreibung]`

**Beispiel:** `ADR-001: Verwendung von PostgreSQL als primäre Datenbank`

**Hinweise:**
- Nummerierung sollte sequenziell sein (001, 002, 003, ...)
- Titel sollte die Entscheidung klar beschreiben
- Titel sollte auch nach Jahren noch verständlich sein

#### 2. Status

**Mögliche Statuswerte:**
- **Vorgeschlagen:** Die Entscheidung wird diskutiert, aber noch nicht getroffen
- **Akzeptiert:** Die Entscheidung wurde getroffen und wird umgesetzt
- **Abgelehnt:** Die Entscheidung wurde nicht getroffen (mit Begründung)
- **Ersetzt:** Die Entscheidung wurde durch ein neues ADR ersetzt (Verweis auf neues ADR)
- **Abgelaufen:** Die Entscheidung ist nicht mehr relevant (z.B. durch Änderungen im Kontext)

**Zu dokumentieren:**
```
Status: [Status]
Datum: [Datum der Entscheidung]
Entscheider: [Person oder Team, das die Entscheidung getroffen hat] (optional)
Technische Story: [Beschreibung oder Link zu Ticket/Issue] (optional)
```

#### 3. Kontext

**Zweck:** Beschreibung der Situation, die die Entscheidung erforderlich macht.

**Inhalt:**
- Problemstellung oder Herausforderung
- Relevante Hintergrundinformationen
- Technische, organisatorische oder geschäftliche Randbedingungen
- Betroffene Systeme oder Komponenten
- Zeitliche oder ressourcenbezogene Einschränkungen

**Zu dokumentieren:**
```
[HIER: Kontext beschreiben]

### Problemstellung
...

### Hintergrund
...

### Randbedingungen
...

### Betroffene Bereiche
...
```

#### 4. Erwogene Optionen

**Zweck:** Dokumentation aller Alternativen, die in Betracht gezogen wurden, bevor die Entscheidung getroffen wurde.

**Inhalt:**
- Liste aller erwogenen Alternativen
- Kurze Beschreibung jeder Alternative
- Bewertung jeder Alternative (Vorteile, Nachteile)
- Gründe, warum Alternativen nicht gewählt wurden
- Vergleich mit der gewählten Lösung

**Zu dokumentieren:**
```
[HIER: Erwogene Optionen dokumentieren]

### Option 1: [Name der Option]
**Beschreibung:** ...
**Vorteile:** ...
**Nachteile:** ...
**Warum nicht gewählt:** ...

### Option 2: [Name der Option]
**Beschreibung:** ...
**Vorteile:** ...
**Nachteile:** ...
**Warum nicht gewählt:** ...

### Option 3: [Name der Option - gewählte Option]
**Beschreibung:** ...
**Vorteile:** ...
**Nachteile:** ...
**Warum gewählt:** ...
```

**Hinweis:** Die Begründung für die Entscheidung kann hier bereits in der Bewertung der Optionen enthalten sein. Alternativ kann eine separate Begründung in der Entscheidung ergänzt werden.

#### 5. Entscheidung

**Zweck:** Klare Aussage über die getroffene Entscheidung in aktiver Form.

**Inhalt:**
- Präzise Beschreibung der gewählten Lösung
- Was wird gemacht?
- Was wird nicht gemacht?
- Konkrete Maßnahmen oder Schritte
- Kurze Begründung (falls nicht bereits in "Erwogene Optionen" enthalten)

**Zu dokumentieren:**
```
[HIER: Entscheidung klar formulieren - in aktiver Form]

Wir entscheiden uns für: [Lösung]

Konkret bedeutet das:
- ...
- ...
- ...

**Begründung:** [Kurze Zusammenfassung der Hauptgründe, falls nicht bereits in "Erwogene Optionen" enthalten]
```

#### 6. Konsequenzen

**Zweck:** Beschreibung der erwarteten Auswirkungen der Entscheidung.

**Inhalt:**
- Positive Konsequenzen
- Negative Konsequenzen oder Risiken
- Auswirkungen auf andere Systeme oder Komponenten
- Notwendige Maßnahmen zur Umsetzung
- Notwendige Maßnahmen zur Risikominderung
- Auswirkungen auf Team, Prozesse oder Organisation

**Zu dokumentieren:**
```
[HIER: Konsequenzen beschreiben]

### Positive Konsequenzen
- ...
- ...

### Negative Konsequenzen / Risiken
- ...
- Maßnahmen zur Minderung: ...

### Auswirkungen auf andere Bereiche
- [Bereich 1]: ...
- [Bereich 2]: ...

### Notwendige Maßnahmen
- [Maßnahme 1]: Verantwortlich, Deadline
- [Maßnahme 2]: Verantwortlich, Deadline
```


---

## Erweiterte Struktur (Optional)

Für komplexere Entscheidungen können zusätzliche Abschnitte hinzugefügt werden:

### Compliance und Anforderungen
```
### Compliance-Anforderungen
- [Anforderung 1]: Wie wird sie erfüllt
- [Anforderung 2]: Wie wird sie erfüllt

### Nicht-funktionale Anforderungen
- Performance: ...
- Sicherheit: ...
- Skalierbarkeit: ...
```

### ADR-Verknüpfungen

**Wichtig:** ADRs sollten explizit mit verwandten ADRs verknüpft werden, um den Kontext und die Abhängigkeiten zwischen Entscheidungen zu verdeutlichen.

**Zu dokumentieren:**
```
### ADR-Verknüpfungen

**Ersetzt:** [ADR-XXX] (wenn dieses ADR ein früheres ADR ersetzt)
**Wird ersetzt durch:** [ADR-XXX] (wenn dieses ADR später ersetzt wurde)
**Verwandt mit:** 
- [ADR-XXX]: [Beschreibung der Beziehung]
- [ADR-YYY]: [Beschreibung der Beziehung]
**Abhängig von:**
- [ADR-XXX]: [Beschreibung der Abhängigkeit]
**Folgt aus:**
- [ADR-XXX]: [Beschreibung, wie dieses ADR aus dem anderen folgt]
```

**Beispiele für Verknüpfungen:**
- **Ersetzt:** Wenn eine frühere Entscheidung revidiert wird
- **Verwandt mit:** Wenn ADRs ähnliche Themen behandeln oder sich gegenseitig beeinflussen
- **Abhängig von:** Wenn eine Entscheidung eine andere voraussetzt
- **Folgt aus:** Wenn eine Entscheidung logisch aus einer anderen folgt

### Referenzen und Links
```
### Referenzen
- [Link 1]: Beschreibung
- [Link 2]: Beschreibung
- Dokument: [Titel]
- Externe Dokumentation: [Link]
- Standards: [Standard-Name, Link]
```

### Metadaten
```
### Metadaten
- Erstellt: [Datum, Autor]
- Überprüft: [Datum, Reviewer]
- Letzte Aktualisierung: [Datum, Autor]
- Betroffene Teams: [Team 1, Team 2]
- Betroffene Komponenten: [Komponente 1, Komponente 2]
```

---

## Nutzen von ADRs

### Für das Entwicklungsteam

**1. Bessere Entscheidungsfindung**
- Strukturierter Prozess zwingt zu durchdachten Entscheidungen
- Dokumentation von Alternativen fördert fundierte Abwägungen
- Reduziert impulsive oder unüberlegte Entscheidungen

**2. Effiziente Kommunikation**
- Klare, strukturierte Kommunikation von Entscheidungen
- Reduziert Missverständnisse
- Schnelle Einarbeitung neuer Teammitglieder

**3. Vermeidung von Wiederholungen**
- Verhindert, dass bereits diskutierte Entscheidungen erneut diskutiert werden
- Zeigt, welche Alternativen bereits erwogen wurden
- Spart Zeit bei ähnlichen Fragestellungen

**4. Wissensmanagement**
- Zentrales Nachschlagewerk für Architekturentscheidungen
- Bewahrt Wissen auch bei Teamwechseln
- Unterstützt Onboarding neuer Mitarbeiter

### Für das Projektmanagement

**1. Transparenz**
- Nachvollziehbare Entscheidungsprozesse
- Klare Dokumentation für Stakeholder
- Unterstützt Reporting und Status-Updates

**2. Risikomanagement**
- Dokumentierte Risiken und Maßnahmen
- Frühe Identifikation von Problemen
- Nachvollziehbare Risikoabwägungen

**3. Compliance**
- Nachweisbare Dokumentation für Audits
- Erfüllung von Dokumentationsanforderungen
- Unterstützt Governance-Prozesse

### Für die Organisation

**1. Organisationales Lernen**
- Historisches Archiv von Entscheidungen
- Lernen aus vergangenen Entscheidungen
- Best Practices können identifiziert werden

**2. Konsistenz**
- Einheitliche Entscheidungsprozesse
- Konsistente Architektur über Projekte hinweg
- Wiederverwendbare Entscheidungen

**3. Wissenssicherung**
- Wissen bleibt erhalten, auch wenn Personen gehen
- Reduziert Abhängigkeit von Einzelpersonen
- Unterstützt langfristige Wartbarkeit

---

## Best Practices

### Wann sollte ein ADR erstellt werden?

**Erstelle ein ADR für:**
- ✅ Architekturentscheidungen mit langfristigen Auswirkungen
- ✅ Entscheidungen, die schwer rückgängig zu machen sind
- ✅ Entscheidungen, die mehrere Teams oder Systeme betreffen
- ✅ Entscheidungen, die von Standards oder Best Practices abweichen
- ✅ Entscheidungen, die kontrovers diskutiert wurden
- ✅ Entscheidungen, die wichtige Trade-offs beinhalten

**Kein ADR notwendig für:**
- ❌ Triviale oder offensichtliche Entscheidungen
- ❌ Temporäre oder experimentelle Lösungen (außer sie werden produktiv)
- ❌ Reine Implementierungsdetails ohne architektonische Relevanz
- ❌ Entscheidungen, die bereits klar in Standards oder Richtlinien definiert sind

### Wie viele ADRs sind angemessen?

- **Zu wenig:** Wichtige Entscheidungen gehen verloren, Wissen wird nicht dokumentiert
- **Zu viele:** Überdokumentation, Wartungsaufwand wird zu hoch, wichtige ADRs gehen unter
- **Richtwert:** 5-15 ADRs pro Jahr für ein typisches Softwareprojekt (abhängig von Projektgröße und Komplexität)

### Qualitätskriterien für ADRs

**Ein gutes ADR:**
- ✅ Ist klar und verständlich geschrieben
- ✅ Erklärt den Kontext ausreichend
- ✅ Dokumentiert alle erwogenen Optionen vor der Entscheidung
- ✅ Begründet die Entscheidung nachvollziehbar
- ✅ Beschreibt Konsequenzen realistisch
- ✅ Verknüpft verwandte ADRs explizit
- ✅ Ist für Außenstehende nachvollziehbar (auch nach Jahren)
- ✅ Ist aktuell gehalten (Status wird aktualisiert)

**Ein schlechtes ADR:**
- ❌ Ist zu technisch oder zu oberflächlich
- ❌ Erklärt den Kontext nicht ausreichend
- ❌ Begründet die Entscheidung nicht nachvollziehbar
- ❌ Ignoriert Alternativen
- ❌ Unterschätzt oder überschätzt Konsequenzen
- ❌ Ist veraltet oder inkonsistent

### Workflow für ADRs

**1. Identifikation**
- Entscheidung wird als ADR-würdig identifiziert
- ADR wird erstellt mit Status "Vorgeschlagen"

**2. Diskussion**
- ADR wird im Team diskutiert
- Alternativen werden ergänzt
- Begründung wird geschärft

**3. Entscheidung**
- Entscheidung wird getroffen
- Status wird auf "Akzeptiert" oder "Abgelehnt" gesetzt
- Konsequenzen werden dokumentiert

**4. Umsetzung**
- Entscheidung wird umgesetzt
- Fortschritt wird verfolgt

**5. Review**
- ADR wird regelmäßig überprüft
- Status wird aktualisiert, wenn sich Kontext ändert
- Bei Bedarf wird neues ADR erstellt (Status "Ersetzt")
- ADR-Verknüpfungen werden gepflegt und aktualisiert

---

## Beispiel-ADR

```markdown
# ADR-001: Verwendung von PostgreSQL als primäre Datenbank

## Status
Akzeptiert

**Datum:** 2024-01-15  
**Entscheider:** Architektur-Team  
**Technische Story:** [Ticket-123: Datenbank-Migration von MySQL zu PostgreSQL](https://github.com/projekt/issues/123)

## Kontext

Unser System benötigt eine relationale Datenbank für die Speicherung strukturierter Daten. Die Anforderungen umfassen:
- Transaktionale Konsistenz
- ACID-Compliance
- Unterstützung für komplexe Abfragen und Joins
- Skalierbarkeit für erwartetes Wachstum
- Open-Source-Lösung bevorzugt

Aktuell verwenden wir MySQL 5.7, das jedoch Ende 2023 End-of-Life erreicht hat. Dies erfordert eine Migration auf eine neuere Datenbank-Lösung.

## Erwogene Optionen

### Option 1: MySQL 8.0 Upgrade
**Beschreibung:** Upgrade von MySQL 5.7 auf MySQL 8.0  
**Vorteile:**
- Einfache Migration (gleiche Datenbank-Familie)
- Team hat bereits MySQL-Expertise
- Geringerer Migrationsaufwand
**Nachteile:**
- Weniger moderne Features als PostgreSQL
- Geringere Performance bei komplexen Abfragen
- Weniger aktive Community-Entwicklung
**Warum nicht gewählt:** Langfristig bietet PostgreSQL mehr Vorteile bei ähnlichen Migrationskosten

### Option 2: Cloud-Datenbank (AWS RDS, Google Cloud SQL)
**Beschreibung:** Verwendung einer verwalteten Cloud-Datenbank  
**Vorteile:**
- Reduzierter Wartungsaufwand
- Automatische Backups und Updates
- Skalierbarkeit durch Cloud-Provider
**Nachteile:**
- Höhere Kosten (laufende Gebühren)
- Vendor Lock-in
- Weniger Kontrolle über Konfiguration
**Warum nicht gewählt:** Kosten und Abhängigkeiten überwiegen die Vorteile für unser Projekt

### Option 3: NoSQL-Datenbank (MongoDB, Cassandra)
**Beschreibung:** Verwendung einer NoSQL-Datenbank  
**Vorteile:**
- Gute Skalierbarkeit
- Flexible Datenstruktur
**Nachteile:**
- Unsere Daten sind stark relational strukturiert
- Benötigen ACID-Transaktionen
- Erfordert komplette Neuentwicklung des Datenmodells
**Warum nicht gewählt:** Nicht kompatibel mit unseren Datenmodell-Anforderungen

### Option 4: PostgreSQL 15 (gewählte Option)
**Beschreibung:** Migration zu PostgreSQL 15 als primäre Datenbank  
**Vorteile:**
- Modernere Features (JSON, Arrays, UUID, bessere Volltextsuche)
- Bessere Performance bei komplexen Abfragen (+15% in Benchmark-Tests)
- Aktive Open-Source-Community
- Bessere Standards-Compliance
- Weniger restriktive Lizenz als MySQL
**Nachteile:**
- Migrationsaufwand von MySQL zu PostgreSQL
- Schulungsbedarf für Team
- Kurzfristige Produktivitätsverluste
**Warum gewählt:** Langfristige Vorteile überwiegen kurzfristige Kosten

## Entscheidung

Wir entscheiden uns für **PostgreSQL 15** als primäre Datenbank für alle neuen Features und migrieren bestehende Datenbanken schrittweise von MySQL zu PostgreSQL.

Konkret bedeutet das:
- Neue Features werden ausschließlich mit PostgreSQL entwickelt
- Bestehende MySQL-Datenbanken werden schrittweise migriert
- Alle Entwickler werden in PostgreSQL geschult
- CI/CD-Pipeline wird für PostgreSQL konfiguriert

**Begründung:** Die Bewertung der Optionen zeigt, dass PostgreSQL die beste Balance zwischen modernen Features, Performance und langfristiger Wartbarkeit bietet. Der Migrationsaufwand ist überschaubar und die langfristigen Vorteile rechtfertigen die Investition.

## Konsequenzen

### Positive Konsequenzen
- Modernere Datenbank-Features verfügbar
- Bessere Performance bei komplexen Abfragen
- Langfristig geringerer Wartungsaufwand
- Bessere Compliance mit SQL-Standards
- Aktive Community-Unterstützung

### Negative Konsequenzen / Risiken
- **Migrationsrisiko:** Datenverlust oder Downtime während Migration
  - *Maßnahme:* Umfassende Tests, Staged Rollout, Backup-Strategie
- **Produktivitätsverlust:** Kurzfristige Lernkurve für Team
  - *Maßnahme:* Schulungen, Pair Programming, Dokumentation
- **Kosten:** Migrationsaufwand und Schulungen
  - *Maßnahme:* Budget eingeplant, externe Beratung bei Bedarf

### Auswirkungen auf andere Bereiche
- **Backend:** Code-Änderungen für Datenbankzugriffe erforderlich
- **DevOps:** Neue Infrastruktur-Konfiguration, Monitoring-Anpassungen
- **Testing:** Test-Datenbanken müssen migriert werden
- **Dokumentation:** Datenbank-Dokumentation muss aktualisiert werden

### Notwendige Maßnahmen
- [ ] PostgreSQL 15 in Development-Umgebung einrichten (Verantwortlich: DevOps, Deadline: 2024-01-30)
- [ ] Migrations-Skripte entwickeln und testen (Verantwortlich: Backend-Team, Deadline: 2024-02-15)
- [ ] Team-Schulung durchführen (Verantwortlich: Tech Lead, Deadline: 2024-02-01)
- [ ] CI/CD-Pipeline anpassen (Verantwortlich: DevOps, Deadline: 2024-02-10)
- [ ] Monitoring und Alerting konfigurieren (Verantwortlich: DevOps, Deadline: 2024-02-20)

## ADR-Verknüpfungen

**Verwandt mit:**
- [ADR-002: Datenbank-Migrationsstrategie](./0002-datenbank-migrationsstrategie.md) - Definiert die konkrete Migrationsstrategie für diese Entscheidung
- [ADR-003: CI/CD-Pipeline-Anpassungen](./0003-cicd-pipeline-anpassungen.md) - Erforderliche Anpassungen der Pipeline

**Abhängig von:**
- Keine

## Referenzen
- PostgreSQL Dokumentation: https://www.postgresql.org/docs/
- MySQL zu PostgreSQL Migrations-Guide: [Internes Dokument]

## Metadaten
- Erstellt: 2024-01-10, Max Mustermann
- Überprüft: 2024-01-12, Maria Schmidt
- Letzte Aktualisierung: 2024-01-15, Max Mustermann
- Betroffene Teams: Backend-Team, DevOps-Team
- Betroffene Komponenten: Datenbank-Layer, Persistenz-Service
```

---

## Organisationsstruktur für ADRs

### Dateinamenskonvention

**Empfohlene Struktur:**
```
docs/adr/
  ├── 0001-template.md
  ├── 0002-verwendung-postgresql.md
  ├── 0003-api-versionierung.md
  ├── 0004-container-orchestrierung.md
  └── README.md
```

**Namenskonvention:**
- Format: `[Nummer]-[kurzer-titel].md`
- Nummer: 4-stellig, führende Nullen (0001, 0002, ...)
- Titel: Kleinbuchstaben, Bindestriche statt Leerzeichen
- Beispiel: `0001-verwendung-postgresql.md`

### Index-Datei (README.md)

Erstelle eine `README.md` im ADR-Verzeichnis mit Übersicht:

```markdown
# Architecture Decision Records

Diese Verzeichnis enthält alle Architecture Decision Records (ADRs) für dieses Projekt.

## Übersicht

| ADR | Titel | Status | Datum |
|-----|-------|--------|-------|
| [ADR-0001](./0001-template.md) | Template | - | - |
| [ADR-0002](./0002-verwendung-postgresql.md) | Verwendung von PostgreSQL | Akzeptiert | 2024-01-15 |
| [ADR-0003](./0003-api-versionierung.md) | API-Versionierung | Akzeptiert | 2024-02-01 |

## Status-Legende
- **Vorgeschlagen:** Entscheidung wird diskutiert
- **Akzeptiert:** Entscheidung wurde getroffen
- **Abgelehnt:** Entscheidung wurde nicht getroffen
- **Ersetzt:** Entscheidung wurde durch neues ADR ersetzt
- **Abgelaufen:** Entscheidung ist nicht mehr relevant
```

### ADR-Verknüpfungen pflegen

**Wichtig:** ADRs sollten untereinander verknüpft werden, um den Kontext und die Abhängigkeiten zwischen Entscheidungen zu verdeutlichen.

**Verknüpfungstypen:**
- **Ersetzt:** Wenn ein ADR ein früheres ADR ersetzt
- **Wird ersetzt durch:** Wenn ein ADR später ersetzt wurde
- **Verwandt mit:** ADRs, die ähnliche Themen behandeln oder sich gegenseitig beeinflussen
- **Abhängig von:** ADRs, die Voraussetzung für diese Entscheidung sind
- **Folgt aus:** ADRs, aus denen diese Entscheidung logisch folgt

**Beispiel für Verknüpfungen im README:**
```markdown
## ADR-Verknüpfungen

### ADR-0002: Verwendung von PostgreSQL
- **Verwandt mit:** ADR-0003 (Migrationsstrategie)
- **Folgt aus:** ADR-0001 (Datenbank-Anforderungen)

### ADR-0003: Migrationsstrategie
- **Abhängig von:** ADR-0002 (PostgreSQL-Entscheidung)
- **Verwandt mit:** ADR-0004 (CI/CD-Anpassungen)
```

### Verknüpfung mit arc42

ADRs können in der arc42-Dokumentation referenziert werden:

**In Kapitel 9 (Architekturentscheidungen):**
```markdown
## Architekturentscheidungen

Wichtige Architekturentscheidungen sind in separaten ADRs dokumentiert:

- [ADR-0002: Verwendung von PostgreSQL](./../adr/0002-verwendung-postgresql.md)
- [ADR-0003: API-Versionierung](./../adr/0003-api-versionierung.md)
- [ADR-0004: Container-Orchestrierung](./../adr/0004-container-orchestrierung.md)

Für Details siehe das [ADR-Verzeichnis](./../adr/README.md).
```

---

## Tools und Integration

### Markdown-basierte Tools
- **Git:** ADRs als Markdown-Dateien im Repository versionieren
- **GitHub/GitLab:** Native Markdown-Unterstützung, Issues können ADRs referenzieren
- **VS Code:** Markdown-Preview für ADRs

### Spezialisierte Tools
- **adr-tools:** Command-Line-Tool für ADR-Management
- **ADR-Manager:** Visual Studio Code Extension
- **Structurizr:** Kann ADRs in Architekturdiagramme integrieren

### Integration in Entwicklungsprozess
- **Pull Requests:** ADRs können als Teil von PRs erstellt werden
- **Code Reviews:** ADRs können in Code Reviews diskutiert werden
- **Sprint Planning:** ADRs können als Teil der Sprint-Planung erstellt werden
- **Retrospektiven:** ADRs können in Retrospektiven überprüft werden

---

## Zusammenfassung

**ADRs sind wertvoll, weil sie:**
- Architekturentscheidungen nachvollziehbar dokumentieren
- Wissen im Team bewahren
- Transparenz schaffen
- Lernprozesse unterstützen
- Compliance-Anforderungen erfüllen

**Ein gutes ADR:**
- Ist klar strukturiert und verständlich
- Erklärt Kontext, Entscheidung, Begründung und Konsequenzen
- Dokumentiert Alternativen
- Wird regelmäßig aktualisiert

**ADRs sollten erstellt werden für:**
- Entscheidungen mit langfristigen Auswirkungen
- Entscheidungen, die schwer rückgängig zu machen sind
- Entscheidungen, die mehrere Teams betreffen

**ADRs sind Teil der Architekturdokumentation** und ergänzen arc42-Kapitel 9 (Architekturentscheidungen) perfekt.
