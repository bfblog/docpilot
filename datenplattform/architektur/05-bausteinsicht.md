# 5. Bausteinsicht

## Level 1: Fachliche Bausteine (Domänen/Bounded Contexts)

Die Datenplattform besteht aus folgenden fachlichen Bausteinen:

### Persistenz / Datenspeicher
- **Fachliche Verantwortlichkeit:** 
  - Speicherung von Daten im kanonischen Datenmodell
  - Persistenz der Datenplattform nutzt genau das kanonische Datenmodell
  - Daten werden in diesem Format persistiert und können so wieder bezogen werden
- **Fachliche Abhängigkeiten:** 
  - Wird von Systemadaptern genutzt (zum Speichern importierter Daten)
  - Wird von Data-Providern genutzt (zum Abrufen von Daten)
  - Wird von Datenquellenverwaltung genutzt (Metadaten zu Datenquellen)
  - Wird von Datenangebotsverwaltung genutzt (Metadaten zu Datenangeboten)

### Systemadapter
- **Fachliche Verantwortlichkeit:** 
  - Beziehen Daten von externen Quellen
  - Transformation von externen Datenformaten in das kanonische Datenmodell
  - Bereinigung und Veredelung von Daten
- **Fachliche Abhängigkeiten:** 
  - Nutzt Persistenz zum Speichern der transformierten Daten
  - Nutzt Message Broker für asynchrone Kommunikation (z.B. bei Datenimport-Ereignissen)
  - Nutzt Datenquellenverwaltung für Konfiguration der Datenquellen
  - Nutzt Konfiguration für Adapter-spezifische Einstellungen
  - Nutzt Identity Management für Authentifizierung bei externen Quellen

### Data-Provider
- **Fachliche Verantwortlichkeit:** 
  - Stellen Daten für externe Dienste zur Verfügung
  - Bereitstellung von Daten im kanonischen Datenmodell
  - Transformation von Daten für externe Formate (falls erforderlich)
- **Fachliche Abhängigkeiten:** 
  - Nutzt Persistenz zum Abrufen von Daten
  - Nutzt Message Broker für asynchrone Kommunikation (z.B. bei Datenänderungen)
  - Nutzt Datenangebotsverwaltung für Konfiguration der Datenangebote
  - Nutzt Konfiguration für Provider-spezifische Einstellungen
  - Nutzt Identity Management für Autorisierung von externen Diensten

### Konfiguration
- **Fachliche Verantwortlichkeit:** 
  - Speicherung von Konfigurationen als Key-Value Paare
  - Key-Value Paare werden unter einem Namen abgelegt
  - Verschiedene Namen erlauben getrennte Konfigurationspaare
- **Fachliche Abhängigkeiten:** 
  - Wird von allen anderen Bausteinen genutzt für ihre spezifischen Konfigurationen
  - Nutzt Persistenz für die Speicherung der Konfigurationen

### Zeitgeber
- **Fachliche Verantwortlichkeit:** 
  - Löst zu konfigurierbaren Zeiten Ereignisse aus
  - Zeitgesteuerte Ausführung von Aufgaben (z.B. periodische Datenimporte)
- **Fachliche Abhängigkeiten:** 
  - Nutzt Konfiguration für Zeitplan-Konfigurationen
  - Nutzt Message Broker zum Auslösen von Ereignissen
  - Kann Systemadapter triggern (z.B. für periodische Datenimporte)

### Message Broker
- **Fachliche Verantwortlichkeit:** 
  - Asynchrone Kommunikation zwischen Diensten
  - Unterstützt Publish-Subscribe Zugriffsmuster
  - Event-basierte Kommunikation
- **Fachliche Abhängigkeiten:** 
  - Wird von allen Bausteinen genutzt, die asynchrone Kommunikation benötigen
  - Nutzt Persistenz für Event-Persistenz (falls erforderlich)

### Identity Management
- **Fachliche Verantwortlichkeit:** 
  - Verwaltung von Rechten und Rollen
  - Unterstützung von Protokollen wie OAuth 2.0
  - Authentifizierung und Autorisierung
- **Fachliche Abhängigkeiten:** 
  - Nutzt Konfiguration für Identity-Konfigurationen
  - Nutzt Persistenz für Speicherung von Benutzern, Rollen und Berechtigungen
  - Wird von Systemadaptern genutzt (Authentifizierung bei externen Quellen)
  - Wird von Data-Providern genutzt (Autorisierung von externen Diensten)

### Datenquellenverwaltung
- **Fachliche Verantwortlichkeit:** 
  - Verwaltung von Metadaten zu externen Datenquellen
  - Konfiguration von Datenquellen
  - Verwaltung von Verbindungsinformationen zu externen Systemen
- **Fachliche Abhängigkeiten:** 
  - Nutzt Persistenz für Speicherung von Datenquellen-Metadaten
  - Nutzt Konfiguration für Datenquellen-Konfigurationen
  - Wird von Systemadaptern genutzt (für Konfiguration der zu importierenden Quellen)
  - Nutzt Identity Management für Authentifizierungsinformationen zu externen Quellen

### Datenangebotsverwaltung
- **Fachliche Verantwortlichkeit:** 
  - Verwaltung von Metadaten zu Datenangeboten
  - Konfiguration von Datenangeboten für externe Dienste
  - Verwaltung von Zugriffsrechten auf Datenangebote
- **Fachliche Abhängigkeiten:** 
  - Nutzt Persistenz für Speicherung von Datenangebots-Metadaten
  - Nutzt Konfiguration für Datenangebots-Konfigurationen
  - Wird von Data-Providern genutzt (für Konfiguration der bereitzustellenden Angebote)
  - Nutzt Identity Management für Autorisierungsinformationen zu externen Diensten

## Level 2: Technische Bausteine (Komponenten/Services)

[Wird iterativ ergänzt, sobald technische Details verfügbar sind]

Die technischen Bausteine werden die fachlichen Bausteine implementieren. Jeder fachliche Baustein kann auf einen oder mehrere technische Bausteine (Services, Komponenten) gemappt werden.

## Schnittstellenbeschreibung

[Wird iterativ ergänzt, sobald Schnittstellendetails verfügbar sind]

Die Schnittstellen zwischen den Bausteinen werden hier detailliert beschrieben, sobald technische Details (Protokolle, Formate) verfügbar sind.
