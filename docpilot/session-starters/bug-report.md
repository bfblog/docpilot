# Bug Reporting Workflow

## 🐛 Überblick

Dieser Workflow beschreibt den vollständigen Prozess von der Bug-Meldung bis zur Lösung. Der Bug selbst ist ein strukturiertes Formular, das durch verschiedene Phasen und Verantwortliche bearbeitet wird.

## 🚨 Severity & Priorität

### Severity (Schweregrad)
- **CRITICAL**: Totalsausfall, alle Nutzer betroffen, kritische Geschäftsprozesse
- **MAJOR**: Teilsystem-Ausfall, viele Nutzer betroffen, wichtige Geschäftsprozesse
- **MINOR**: Einzelne Nutzer, geringe Auswirkungen, normale Release-Zyklen

### Priorität (Dringlichkeit)
- **EXTREME**: Absoluter Ausnahmezustand, sofortige Bearbeitung
- **HIGH**: Hohe Dringlichkeit, aktueller Sprint/Release
- **NORMAL**: Standard-Priorität, normale Release-Zyklen
- **LOW**: Kann warten, wenn Zeit verfügbar
- **BACKLOG**: Todo-Liste für später

## ⏱️ Service Level Agreements (SLA)

### Response & Resolution Times
- **CRITICAL Bugs**: 4 Stunden Response, 24h Resolution
- **MAJOR Bugs**: 8 Stunden Response, 72h Resolution  
- **MINOR Bugs**: 24 Stunden Response, 1 Woche Resolution

### Escalation Matrix
| Zeit nach Meldung | CRITICAL | MAJOR | MINOR |
|-------------------|----------|-------|-------|
| **2h** | Team Lead | - | - |
| **4h** | Product Owner | Team Lead | - |
| **8h** | IT-Leitung | Product Owner | Team Lead |
| **24h** | CTO | IT-Leitung | Product Owner |

## 🏢 EVB-IT Spezifische Anforderungen

### Compliance & Governance
- **Security-Review**: Für CRITICAL/MAJOR Bugs erforderlich
- **DSGVO-Konformität**: Bei personenbezogenen Daten prüfen
- **Audit-Trail**: Vollständige Nachverfolgung für Compliance

### Business Impact
- **Geschäftsbereich**: [Administration, Entwicklung, Fachanwender, Support]
- **Betroffene Kunden**: [Interne/Externe] - für Priorisierung

## 📋 Workflow Phasen

### Phase 1: Meldung
**Verantwortlich**: Nutzer, Tester, Support

**Ziel**: Strukturierte Erfassung des Problems

**Aktivitäten**:
- Bug-Formular ausfüllen
- Alle Pflichtfelder vervollständigen
- Anhänge (Screenshots, Logs) hinzufügen
- Bug-Report an das Entwicklungsteam übermitteln

**Bug-Formular Felder**:
- **Gemeldet für Version**: [Version, in der der Bug auftritt]
- **Gemeldet für Umgebung**: [DEV/TEST/REF/PROD]
- **Fehlerbeschreibung aus Nutzersicht**: [Was erlebt der Nutzer?]
- **Erwartetes Verhalten**: [Was sollte normalerweise passieren?]
- **Aktuelles Verhalten**: [Was passiert tatsächlich?]
- **Geschäftsbereich**: [Administration, Entwicklung, Fachanwender, Support]
- **Betroffene Kunden**: [Interne/Externe]

**Markdown-Fragment (Issue-Beschreibung)**:
```markdown
## 🐛 Bug Report

### 📋 Basis-Informationen
- **Version**: [Version]
- **Umgebung**: [DEV/TEST/REF/PROD]
- **Gemeldet von**: [Name/Rolle]
- **Datum**: [Datum]

### 🏢 EVB-Business Impact
- **Geschäftsbereich**: [Administration, Entwicklung, Fachanwender, Support]
- **Betroffene Kunden**: [Interne/Externe]

### 🎯 Fehlerbeschreibung
[Fehlerbeschreibung aus Nutzersicht]

### 🔍 Verhalten
**Erwartetes Verhalten**: [Was sollte normalerweise passieren?]
**Aktuelles Verhalten**: [Was passiert tatsächlich?]

### 📎 Anhänge
- Screenshots: [Links/Dateien]
- Logs: [Debug-Informationen]
```

### Phase 2: Erstanalyse
**Verantwortlich**: Product Owner, Team Lead

**Ziel**: Bewertung und Priorisierung des Bugs

**Aktivitäten**:
- Bug-Report prüfen und validieren
- Vollständigkeit der Informationen bewerten
- Schweregrad und Priorität bestimmen
- Bug an zuständiges Team weiterleiten
- Rückfragen an Melder stellen (falls nötig)

**Erweiterte Felder**:
- **Severity**: [CRITICAL/MAJOR/MINOR]
- **Priorität**: [EXTREME/HIGH/NORMAL/LOW/BACKLOG]
- **Kategorie**: [UI/UX/Backend/Performance/etc.]
- **Zugewiesen an**: [Entwickler/Team]

**Markdown-Fragment (Issue-Kommentar)**:
```markdown
## 📊 Erstanalyse

### 🎯 Bewertung
- **Severity**: [CRITICAL/MAJOR/MINOR]
- **Priorität**: [EXTREME/HIGH/NORMAL/LOW/BACKLOG]
- **Kategorie**: [UI/UX/Backend/Performance/etc.]

### 👥 Zuweisung
- **Zugewiesen an**: [Entwickler/Team]
- **Geschätzte Bearbeitungszeit**: [Zeit]

### 📝 Anmerkungen
[Zusätzliche Bewertungen oder Rückfragen]
```

### Phase 3: Fachanalyse
**Verantwortlich**: Entwickler, Senior Developer

**Ziel**: Technische Analyse und Lösungsansatz

**Aktivitäten**:
- Bug reproduzieren
- Root Cause Analyse durchführen
- Technische Lösung planen
- Aufwand schätzen
- Abhängigkeiten identifizieren

**Technische Felder**:
- **Root Cause**: [Was verursacht das Problem?]
- **Betroffene Komponenten**: [Welche Teile sind betroffen?]
- **Lösungsansatz**: [Wie kann das Problem behoben werden?]
- **Geschätzter Aufwand**: [Zeit für die Behebung]
- **Abhängigkeiten**: [Welche Ressourcen werden benötigt?]

**Markdown-Fragment (Issue-Kommentar)**:
```markdown
## 🔧 Fachanalyse

### 🎯 Root Cause Analysis (RCA)
**5 Why's Methode:**
1. Warum ist der Bug aufgetreten? [Ursache 1]
2. Warum ist [Ursache 1] passiert? [Ursache 2]
3. Warum ist [Ursache 2] passiert? [Ursache 3]
4. Warum ist [Ursache 3] passiert? [Ursache 4]
5. Warum ist [Ursache 4] passiert? [Root Cause]

**Fishbone Diagram (Ishikawa):**
- **Methode**: [Probleme im Entwicklungsprozess]
- **Material**: [Technische Probleme]
- **Mensch**: [Human Error, Training]
- **Maschine**: [Infrastructure, Tools]
- **Umgebung**: [Environment, Configuration]

### 🏗️ Betroffene Komponenten
- [Liste der betroffenen Dateien/Module]

### 💡 Lösungsansatz
[Wie kann das Problem behoben werden?]

### ⏱️ Aufwand
- **Geschätzter Aufwand**: [Zeit für die Behebung]
- **Abhängigkeiten**: [Welche Ressourcen werden benötigt?]

### 🔍 Reproduktion
[Schritte zur Reproduktion des Bugs]

### 🛡️ Prevention Measures
- **Code Review**: [Verstärkte Reviews für betroffene Bereiche]
- **Automated Testing**: [Zusätzliche Tests für ähnliche Szenarien]
- **Monitoring**: [Enhanced Monitoring für kritische Pfade]
- **Documentation**: [Knowledge Base Update]
```

### Phase 4: Compliance & Security Review
**Verantwortlich**: Security Team, Compliance Officer

**Ziel**: Sicherheits- und Compliance-Prüfung für kritische Fixes

**Aktivitäten**:
- Security-Review für kritische Änderungen
- DSGVO-Konformität prüfen
- Compliance-Anforderungen validieren
- Audit-Trail dokumentieren

**Compliance-Felder**:
- **Security-Review**: [Erforderlich für CRITICAL/MAJOR]
- **DSGVO-Impact**: [Personenbezogene Daten betroffen?]
- **Compliance-Status**: [Genehmigt/Mit Auflagen/Abgelehnt]
- **Audit-Trail**: [Vollständige Nachverfolgung]

**Markdown-Fragment (Issue-Kommentar)**:
```markdown
## 🔒 Compliance & Security Review

### 🛡️ Security-Review
- **Security-Review erforderlich**: [Ja/Nein]
- **Security-Reviewer**: [Name]
- **Status**: [Genehmigt/Mit Auflagen/Abgelehnt]

### 📋 Compliance
- **DSGVO-Impact**: [Personenbezogene Daten betroffen?]
- **Compliance-Status**: [Genehmigt/Mit Auflagen/Abgelehnt]
- **Audit-Trail**: [Vollständige Nachverfolgung]

### 📝 Anmerkungen
[Security- und Compliance-spezifische Kommentare]
```

### Phase 5: Implementierung
**Verantwortlich**: Entwickler

**Ziel**: Bug beheben und testen

**Aktivitäten**:
- Code-Änderungen implementieren
- Unit Tests schreiben/aktualisieren
- Integration Tests durchführen
- Dokumentation aktualisieren
- Code Review durchführen

**Implementierungs-Felder**:
- **Geänderte Dateien**: [Liste der modifizierten Dateien]
- **Tests**: [Welche Tests wurden durchgeführt?]
- **Code Review**: [Wurde der Code überprüft?]

**Markdown-Fragment (Issue-Kommentar)**:
```markdown
## 🚀 Implementierung

### 📝 Geänderte Dateien
- [Liste der modifizierten Dateien mit Links]

### 🧪 Tests
- **Unit Tests**: [Beschreibung der Tests]
- **Integration Tests**: [Beschreibung der Tests]
- **Automated Testing**: [CI/CD Pipeline Integration]
- **Code Coverage**: [Coverage-Report]

### 👀 Code Review
- **Reviewer**: [Name]
- **Status**: [Genehmigt/Mit Änderungen]
- **Anmerkungen**: [Relevante Kommentare]

### 📚 Dokumentation
[Updates der relevanten Dokumentation]

### 🔧 CI/CD Integration
- **Pipeline Status**: [Erfolgreich/Fehlgeschlagen]
- **Automated Deploy**: [DEV/TEST Environment]
- **Security Scan**: [Vulnerability Check]
- **Performance Test**: [Load Testing falls relevant]
```

### Phase 6: Qualitätssicherung
**Verantwortlich**: QA Engineer, Tester

**Ziel**: Validierung der Lösung

**Aktivitäten**:
- Bug-Fix testen
- Regression Tests durchführen
- Funktionalität validieren
- Performance-Tests (falls relevant)
- User Acceptance Testing

**QA-Felder**:
- **Tests durchgeführt**: [Welche Tests wurden durchgeführt?]
- **Regression Tests**: [Funktioniert alles andere noch?]
- **QA-Status**: [Genehmigt/Abgelehnt/Weitere Tests nötig]

**Markdown-Fragment (Issue-Kommentar)**:
```markdown
## ✅ Qualitätssicherung

### 🧪 Tests durchgeführt
- **Bug-Fix Test**: [Beschreibung]
- **Regression Tests**: [Funktioniert alles andere noch?]
- **Performance Tests**: [Falls relevant]

### 🎯 QA-Status
- **Status**: [Genehmigt/Abgelehnt/Weitere Tests nötig]
- **Tester**: [Name]
- **Datum**: [Datum]

### 📋 Test-Ergebnisse
[Details zu den durchgeführten Tests]

### 🔍 Anmerkungen
[Zusätzliche QA-Kommentare oder Probleme]
```

### Phase 7: Kundenabnahme (BzA)
**Verantwortlich**: Kunde, Product Owner

**Ziel**: Kundenabnahme bei Software-Patches

**Aktivitäten**:
- BzA (Bereitstellung zur Abnahme) vorbereiten
- Kundenabnahme durchführen
- Kundenfeedback dokumentieren
- Abnahme-Status festhalten

**BzA-Felder**:
- **Lösungstyp**: [Software-Patch/Andere Lösung (Neustart, etc.)]
- **BzA erforderlich**: [Ja/Nein - nur bei Software-Patches]
- **Kundenabnahme**: [Genehmigt/Abgelehnt/Mit Auflagen]
- **Abnahme-Datum**: [Datum der Kundenabnahme]

**Markdown-Fragment (Issue-Kommentar)**:
```markdown
## 👥 Kundenabnahme (BzA)

### 🔧 Lösungstyp
- **Lösungstyp**: [Software-Patch/Andere Lösung]
- **BzA erforderlich**: [Ja/Nein - nur bei Software-Patches]

### ✅ Kundenabnahme
- **Kundenabnahme**: [Genehmigt/Abgelehnt/Mit Auflagen]
- **Abnahme-Datum**: [Datum]
- **Kunde**: [Name/Abteilung]

### 📝 Kundenfeedback
[Feedback vom Kunden zur Lösung]

### 🔍 Anmerkungen
[Zusätzliche Abnahme-Kommentare]
```

### Phase 8: Deployment
**Verantwortlich**: DevOps, Release Manager

**Ziel**: Bug-Fix über Abnahmeumgebung in Produktion bringen

**Aktivitäten**:
- Deployment in Abnahmeumgebung durchführen
- Kundenabnahme (BzA) abwarten
- Deployment nach PROD nach Kundenfreigabe
- Monitoring nach Deployment
- Rollback-Plan vorbereiten

**Deployment-Felder**:
- **Deployment-Umgebung**: [Abnahmeumgebung/PROD]
- **Kundenfreigabe**: [Erforderlich für PROD-Deployment]
- **Gelöst mit Version**: [Version, in der der Bug behoben wurde]
- **Deployment-Datum**: [Wann wurde der Fix deployed?]
- **Deployment-Status**: [Erfolgreich/Fehlgeschlagen]

**Deployment-Regeln**:
- **Standard**: Deployment erfolgt zunächst in Abnahmeumgebung
- **PROD-Deployment**: Nur nach Kundenfreigabe (BzA) erlaubt
- **Direkte PROD-Änderungen**: Absolute Ausnahme, nur in Notfällen

**Notfall-Prozedur für direkte PROD-Änderungen**:
- **Genehmigung**: Erfordert Genehmigung durch IT-Leitung
- **Dokumentation**: Vollständige Dokumentation der Notfallmaßnahme
- **Nachbereitung**: Sofortige Nachbereitung und Kundenabnahme nachträglich
- **Review**: Post-Incident Review erforderlich

**Markdown-Fragment (Issue-Kommentar)**:
```markdown
## 🚀 Deployment

### 📦 Release-Informationen
- **Gelöst mit Version**: [Version]
- **Deployment-Datum**: [Datum]
- **Deployment-Status**: [Erfolgreich/Fehlgeschlagen]

### 🔧 Deployment-Details
- **Deployment-Umgebung**: [Abnahmeumgebung/PROD]
- **Kundenfreigabe**: [Erforderlich für PROD-Deployment]
- **Deployment-Methode**: [Beschreibung]
- **Rollback-Plan**: [Falls nötig]

### 📊 Monitoring & Observability
- **Application Monitoring**: [APM - New Relic, Datadog]
- **Infrastructure Monitoring**: [Prometheus, Grafana]
- **Log Aggregation**: [ELK Stack, Splunk]
- **Alerting**: [PagerDuty, OpsGenie Integration]

### 🔍 Post-Deployment Checks
- **Health Checks**: [Application Health Status]
- **Performance Metrics**: [Response Times, Throughput]
- **Error Rates**: [Error Monitoring]
- **User Impact**: [Real User Monitoring]

### ⚠️ Deployment-Regeln
- **Standard**: Deployment erfolgt zunächst in Abnahmeumgebung
- **PROD-Deployment**: Nur nach Kundenfreigabe (BzA) erlaubt
- **Direkte PROD-Änderungen**: Absolute Ausnahme, nur in Notfällen

### 🚨 Notfall-Prozedur
- **Genehmigung**: Erfordert Genehmigung durch IT-Leitung
- **Dokumentation**: Vollständige Dokumentation der Notfallmaßnahme
- **Nachbereitung**: Sofortige Nachbereitung und Kundenabnahme nachträglich
- **Review**: Post-Incident Review erforderlich

### 📝 Anmerkungen
[Deployment-spezifische Kommentare]
```

### Phase 9: Abschluss
**Verantwortlich**: Product Owner, Team Lead

**Ziel**: Workflow abschließen und Lektionen lernen

**Aktivitäten**:
- Bug-Status auf "Geschlossen" setzen
- Melder über Lösung informieren
- Lessons Learned dokumentieren
- Prozess-Optimierung identifizieren

**Abschluss-Felder**:
- **Lösung dokumentieren**: [Wie wurde das Problem gelöst?]
- **Lektionen lernen**: [Was können wir für die Zukunft mitnehmen?]
- **Prozess-Verbesserungen**: [Was können wir optimieren?]

**Markdown-Fragment (Issue-Kommentar)**:
```markdown
## 📝 Abschluss

### ✅ Lösung
[Wie wurde das Problem gelöst?]

### 📚 Lessons Learned
- **Was gut funktioniert hat**: [Punkte]
- **Was verbessert werden kann**: [Punkte]
- **Prozess-Optimierungen**: [Vorschläge]

### 🎯 Status
- **Bug-Status**: [Geschlossen]
- **Melder informiert**: [Ja/Nein]
- **Dokumentation aktualisiert**: [Ja/Nein]

### 📊 Metriken
- **Gesamtbearbeitungszeit**: [Zeit]
- **Phasen-Durchlaufzeiten**: [Details]
- **Kundenzufriedenheit**: [Falls verfügbar]
```

## 📝 Markdown-Fragmente für Issue-System

### Verwendung der Fragmente
Jede Phase erzeugt ein Markdown-Fragment, das direkt in das Issue-System kopiert werden kann:

1. **Phase 1**: Issue-Beschreibung (Haupttext des Issues)
2. **Phase 2-9**: Issue-Kommentare (als Kommentare hinzugefügt)

### Fragment-Übersicht
| Phase | Fragment-Typ | Verantwortlich | Verwendung |
|-------|--------------|----------------|------------|
| **Phase 1** | Issue-Beschreibung | Nutzer/Tester | Haupttext des Issues |
| **Phase 2** | Issue-Kommentar | Product Owner | Bewertung & Zuweisung |
| **Phase 3** | Issue-Kommentar | Entwickler | Technische Analyse |
| **Phase 4** | Issue-Kommentar | Security Team | Compliance & Security |
| **Phase 5** | Issue-Kommentar | Entwickler | Implementierung |
| **Phase 6** | Issue-Kommentar | QA Engineer | Qualitätssicherung |
| **Phase 7** | Issue-Kommentar | Kunde/Product Owner | Kundenabnahme (BzA) |
| **Phase 8** | Issue-Kommentar | DevOps | Deployment |
| **Phase 9** | Issue-Kommentar | Product Owner | Abschluss |

### Integration in Issue-Systeme
- **GitHub Issues**: Fragmente als Kommentare hinzufügen
- **Jira**: Fragmente in Kommentar-Felder kopieren
- **GitLab Issues**: Fragmente als Markdown-Kommentare
- **Andere Systeme**: Anpassung an spezifische Formate

## 🛠️ Bug-Formular Template

### Phase 1: Meldung
- **Version**: [Version]
- **Umgebung**: [DEV/TEST/REF/PROD]
- **Fehlerbeschreibung**: [Was erlebt der Nutzer?]
- **Erwartetes/Aktuelles Verhalten**: [Beschreibung]
- **Geschäftsbereich**: [Administration, Entwicklung, Fachanwender, Support]
- **Betroffene Kunden**: [Interne/Externe]

### Phase 2: Erstanalyse
- **Severity**: [CRITICAL/MAJOR/MINOR]
- **Priorität**: [EXTREME/HIGH/NORMAL/LOW/BACKLOG]
- **Zugewiesen an**: [Entwickler/Team]

### Phase 3-9: Weitere Phasen
Siehe entsprechende Markdown-Fragmente in den Phasen-Beschreibungen.

## 👥 Rollen und Verantwortlichkeiten

| Rolle | Verantwortlichkeiten | Phasen |
|-------|---------------------|--------|
| **Nutzer/Tester** | Bug melden, Informationen bereitstellen | Phase 1 |
| **Product Owner** | Priorisierung, Bewertung | Phase 2 |
| **Team Lead** | Koordination, Ressourcen | Phase 2, 9 |
| **Entwickler** | Technische Analyse, Implementierung | Phase 3, 5 |
| **Security Team** | Compliance & Security Review | Phase 4 |
| **QA Engineer** | Qualitätssicherung, Testing | Phase 6 |
| **Kunde** | Kundenabnahme (BzA) | Phase 7 |
| **DevOps** | Deployment, Monitoring | Phase 8 |

## 📈 Workflow-Metriken

### Messbare Kennzahlen
- **Durchschnittliche Bearbeitungszeit** pro Phase
- **Bug-Auflösungsrate** (gelöst vs. gemeldet)
- **Rücklaufquote** (Bugs die zurückkommen)
- **Kundenzufriedenheit** nach Bug-Fixes

### Qualitätsindikatoren
- **Vollständigkeit** der Bug-Reports
- **Genauigkeit** der Schweregrad-Bewertung
- **Effektivität** der Lösungsansätze
- **Regression-Rate** nach Fixes

## 📊 Erweiterte Metriken & KPIs

### Bug-Qualitäts-Metriken
- **MTTR (Mean Time To Resolution)**: Durchschnittliche Zeit bis zur Lösung
- **Bug Recurrence Rate**: Wie oft kommen Bugs zurück?
- **Customer Impact**: Downtime, betroffene Nutzer
- **Developer Productivity**: Bugs pro Developer/Sprint

### Process-Effektivität
- **Bug Triage Time**: Wie schnell werden Bugs bewertet?
- **Escalation Rate**: Wie oft wird eskaliert?
- **SLA Compliance**: Werden SLAs eingehalten?
- **Customer Satisfaction**: NPS nach Bug-Fixes

### Technical Metrics
- **Code Coverage**: Test-Coverage für Bug-Fixes
- **Deployment Success Rate**: Erfolgreiche Deployments
- **Rollback Frequency**: Wie oft muss zurückgerollt werden?
- **Performance Impact**: Performance-Verschlechterung nach Fixes

## 🔄 Workflow-Optimierung

### Regelmäßige Überprüfung
- **Workflow-Effektivität**: Funktioniert der Prozess gut?
- **Rollen-Klarheit**: Sind alle Verantwortlichkeiten klar?
- **Tool-Integration**: Sind alle Tools optimal eingebunden?
- **Best Practices**: Neue Erkenntnisse integrieren

### Feedback-Loops
- **Team-Feedback**: Was funktioniert gut/schlecht?
- **Prozess-Optimierung**: Wo können wir effizienter werden?
- **Dokumentation**: Ist alles klar verständlich?

## 🛠️ Automatisierung & CI/CD Integration

### Automated Testing
- **Unit Tests**: Automatische Tests bei jedem Commit
- **Integration Tests**: End-to-End Tests vor Deployment
- **Regression Tests**: Automatische Tests für bekannte Bug-Bereiche
- **Performance Tests**: Load Testing für kritische Pfade

### Monitoring & Alerting
- **Real-time Monitoring**: Automatische Alerts bei Issues
- **Performance Baselines**: Automatische Performance-Vergleiche
- **Error Tracking**: Automatische Error-Aggregation
- **User Impact Monitoring**: Real User Monitoring (RUM)

### Security Integration
- **Vulnerability Scanning**: Automatische Security-Scans
- **Dependency Updates**: Automatische Updates für bekannte CVEs
- **Security Testing**: SAST, DAST, Penetration Testing
- **Incident Response**: Security Incident Playbooks

## 🎯 Bug-Triage-Prozess

### Triage-Meeting
- **Frequenz**: Täglich für kritische Bugs, wöchentlich für andere
- **Teilnehmer**: Product Owner, Tech Lead, QA Lead
- **Agenda**: Priorisierung, Ressourcen-Zuweisung, SLA-Tracking
- **Output**: Sprint-Planung, Escalation-Entscheidungen

### Bug-Prevention Strategien
- **Code Reviews**: Obligatorisch für alle Änderungen
- **Automated Testing**: 80%+ Code Coverage
- **Static Analysis**: SonarQube, ESLint, etc.
- **Feature Flags**: Graduelle Rollouts für kritische Features

