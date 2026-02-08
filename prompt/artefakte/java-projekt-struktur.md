---
typ: artefakt
name: Java-Projektstruktur
kontext: Template zur Beschreibung der Struktur und Dokumentation von Java-Projekten mit Maven
rollen:
  - Softwarearchitekt
  - Dev-Team
artefakte: []
workflows: []
---

# Artefakt: Java-Projektstruktur

## Über Java-Projektdokumentation

Ein **Java-Projekt** folgt einer standardisierten Struktur, die durch Maven als Build-Tool definiert wird. Die Dokumentation eines Java-Projekts beginnt mit der README.md im Projektverzeichnis und kann bei komplexeren Projekten durch weitere Markdown-Dateien ergänzt werden.

**Kernprinzipien:**
- Maven als Build-Tool (pom.xml)
- Standardisierte Verzeichnisstruktur
- README.md als zentrale Dokumentation
- Modularer Aufbau bei Multi-Modul-Projekten
- Klare Trennung zwischen Root-Projekt und Sub-Modulen

---

## Projektstruktur

### Wurzelverzeichnis

**Standard:** `/java` als Basis-Verzeichnis (wenn nichts anderes vereinbart ist)

**Inhalt des Wurzelverzeichnisses:**
- `pom.xml` (Master-POM für Multi-Modul-Projekte)
- `README.md` (Projektübersicht und Einstiegspunkt)
- Unterverzeichnisse für Sub-Module
- Weitere Konfigurationsdateien (z.B. `.gitignore`, `LICENSE`)

**Struktur:**
```
/java
├── pom.xml                    # Master-POM
├── README.md                   # Projektübersicht
├── .gitignore
├── LICENSE
├── module1/                   # Sub-Modul 1
│   ├── pom.xml
│   ├── README.md
│   └── src/
├── module2/                   # Sub-Modul 2
│   ├── pom.xml
│   ├── README.md
│   └── src/
└── docs/                      # Weitere Dokumentation (optional)
    ├── architektur.md
    ├── deployment.md
    └── ...
```

### Master-POM (Root pom.xml)

**Zweck:** Definiert das Multi-Modul-Projekt und gemeinsame Konfigurationen.

**Inhalt:**
- Projekt-Metadaten (groupId, artifactId, version)
- Modul-Deklarationen (`<modules>`)
- Gemeinsame Dependencies
- Build-Plugins (für alle Module)
- Properties (Java-Version, Encoding, etc.)

**Zu dokumentieren:**
```
[HIER: Master-POM beschreiben]

Die Master-POM im Root-Verzeichnis:
- Definiert das Multi-Modul-Projekt
- Listet alle Sub-Module auf
- Enthält gemeinsame Dependencies und Plugins
- Definiert gemeinsame Properties

**Wichtige Elemente:**
- `<modules>`: Liste aller Sub-Module
- `<dependencyManagement>`: Zentral verwaltete Dependency-Versionen
- `<pluginManagement>`: Zentral verwaltete Plugin-Konfigurationen
- `<properties>`: Gemeinsame Properties (Java-Version, Encoding, etc.)
```

### Sub-Module

**Struktur:** Jedes Sub-Modul ist ein eigenständiges Verzeichnis mit eigener pom.xml

**Inhalt eines Sub-Moduls:**
- `pom.xml` (Modul-spezifische POM)
- `README.md` (Modul-Dokumentation)
- `src/main/java/` (Java-Quellcode)
- `src/main/resources/` (Ressourcen)
- `src/test/java/` (Test-Code)
- `src/test/resources/` (Test-Ressourcen)
- `target/` (Build-Artefakte, wird beim Build erstellt)

**Struktur eines Sub-Moduls:**
```
module1/
├── pom.xml                    # Modul-POM
├── README.md                  # Modul-Dokumentation
├── src/
│   ├── main/
│   │   ├── java/             # Java-Quellcode
│   │   │   └── com/example/module1/
│   │   └── resources/         # Ressourcen (Properties, XML, etc.)
│   └── test/
│       ├── java/              # Test-Code
│       │   └── com/example/module1/
│       └── resources/         # Test-Ressourcen
└── target/                    # Build-Artefakte (wird erstellt)
    ├── classes/
    ├── test-classes/
    └── ...
```

---

## pom.xml - Projekt Object Model

### Aufbau einer pom.xml

**Zweck:** Beschreibt alle Abhängigkeiten, Module, Build-Plugins und Konfigurationen des Projekts.

**Hauptabschnitte:**
- Projekt-Metadaten
- Dependencies
- Build-Konfiguration
- Plugins
- Properties

**Zu dokumentieren:**
```
[HIER: pom.xml-Struktur beschreiben]

### Projekt-Metadaten

```xml
<groupId>com.example</groupId>
<artifactId>project-name</artifactId>
<version>1.0.0</version>
<packaging>pom</packaging>  <!-- oder jar, war, etc. -->
```

**Erklärung:**
- `groupId`: Organisations- oder Projekt-Gruppe
- `artifactId`: Name des Artefakts
- `version`: Versionsnummer
- `packaging`: Art des Artefakts (pom für Parent, jar für Library, war für Web-App)

### Dependencies

```xml
<dependencies>
    <dependency>
        <groupId>...</groupId>
        <artifactId>...</artifactId>
        <version>...</version>
    </dependency>
</dependencies>
```

**Erklärung:**
- Externe Bibliotheken, die das Projekt benötigt
- Werden automatisch heruntergeladen und zum Classpath hinzugefügt
- Versionen sollten zentral im `dependencyManagement` verwaltet werden

### Build-Konfiguration

```xml
<build>
    <plugins>
        <plugin>
            <groupId>...</groupId>
            <artifactId>...</artifactId>
            <version>...</version>
        </plugin>
    </plugins>
</build>
```

**Erklärung:**
- Build-Plugins (Compiler, Surefire für Tests, etc.)
- Konfiguration des Build-Prozesses
- Source- und Target-Versionen

### Properties

```xml
<properties>
    <maven.compiler.source>17</maven.compiler.source>
    <maven.compiler.target>17</maven.compiler.target>
    <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
</properties>
```

**Erklärung:**
- Java-Version
- Encoding
- Weitere projektweite Properties
```

### Master-POM vs. Modul-POM

**Master-POM (Root):**
- `packaging`: `pom`
- Enthält `<modules>`-Liste
- Definiert gemeinsame Dependencies und Plugins
- Verwaltet Dependency-Versionen zentral

**Modul-POM:**
- `packaging`: `jar`, `war`, etc.
- Vererbt von Parent-POM (Master-POM)
- Definiert modul-spezifische Dependencies
- Kann modul-spezifische Plugins haben

**Zu dokumentieren:**
```
[HIER: Unterschiede erklären]

### Master-POM (Root)

**Besonderheiten:**
- `<packaging>pom</packaging>`: Definiert Multi-Modul-Projekt
- `<modules>`: Liste aller Sub-Module
- `<dependencyManagement>`: Zentral verwaltete Dependency-Versionen
- `<pluginManagement>`: Zentral verwaltete Plugin-Konfigurationen

**Zweck:**
- Zentrale Verwaltung gemeinsamer Konfigurationen
- Einheitliche Versionsverwaltung
- Vereinfachte Wartung

### Modul-POM

**Besonderheiten:**
- `<parent>`: Verweis auf Master-POM
- `<packaging>jar</packaging>` (oder war, etc.)
- Modul-spezifische Dependencies
- Kann modul-spezifische Plugins überschreiben

**Zweck:**
- Modul-spezifische Konfiguration
- Modul-spezifische Dependencies
- Unabhängige Entwicklung einzelner Module
```

---

## README.md - Zentrale Dokumentation

### Zweck der README.md

**Die README.md ist:**
- Der Einstiegspunkt für neue Teammitglieder
- Erklärt Sinn und Zweck des Projekts
- Beschreibt, was das Projekt tut
- Vermittelt notwendiges Wissen für die Arbeit am Quellcode
- **Verpflichtend** für jedes Projekt und Sub-Modul
- Das Minimum der Projektdokumentation

**Zielgruppe:**
- Neue Teammitglieder
- Entwickler, die am Projekt arbeiten
- Externe, die das Projekt verstehen wollen

### Aufbau der README.md

**Minimale Struktur:**
1. Projektübersicht
2. Zweck und Funktion
3. Voraussetzungen
4. Build und Ausführung
5. Projektstruktur
6. Weitere Informationen (Links)

**Zu dokumentieren:**
```
[HIER: README-Struktur beschreiben]

# [Projektname]

## Überblick

**Was ist dieses Projekt?**
[Kurze Beschreibung des Projekts und seines Zwecks]

**Warum existiert dieses Projekt?**
[Geschäftszweck, Problem, das gelöst wird]

**Was tut dieses Projekt?**
[Hauptfunktionen und Fähigkeiten]

## Voraussetzungen

**Technische Voraussetzungen:**
- Java [Version]
- Maven [Version]
- [Weitere Tools/Software]

**Kenntnisse:**
- [Welche Kenntnisse sind hilfreich?]

## Build und Ausführung

### Projekt bauen

```bash
mvn clean install
```

**Erklärung:**
- Baut das gesamte Projekt inklusive aller Sub-Module
- Führt Tests aus
- Erstellt Artefakte im `target/`-Verzeichnis

### Einzelnes Modul bauen

```bash
cd module1
mvn clean install
```

### Projekt ausführen

[Anleitung zur Ausführung, falls anwendbar]

## Projektstruktur

```
/java
├── pom.xml                    # Master-POM
├── README.md                  # Diese Datei
├── module1/                   # [Beschreibung]
├── module2/                   # [Beschreibung]
└── ...
```

**Erklärung der Module:**
- **module1:** [Zweck und Funktion]
- **module2:** [Zweck und Funktion]

## Weitere Informationen

- [Architektur-Dokumentation](./docs/architektur.md)
- [Deployment-Anleitung](./docs/deployment.md)
- [Entwickler-Guide](./docs/entwickler-guide.md)
```

### Inhalt der README.md im Detail

#### 1. Projektübersicht

**Zweck:** Schneller Überblick über das Projekt.

**Inhalt:**
- Projektname
- Kurzbeschreibung
- Status (in Entwicklung, produktiv, etc.)
- Version

**Zu dokumentieren:**
```
[HIER: Projektübersicht schreiben]

# [Projektname]

[Kurze Beschreibung in 1-2 Sätzen]

**Status:** [In Entwicklung | Produktiv | Wartung]
**Version:** [Version]
**Letzte Aktualisierung:** [Datum]
```

#### 2. Zweck und Funktion

**Zweck:** Erklärt, warum das Projekt existiert und was es tut.

**Inhalt:**
- Geschäftszweck
- Problem, das gelöst wird
- Hauptfunktionen
- Zielgruppe

**Zu dokumentieren:**
```
[HIER: Zweck und Funktion beschreiben]

## Zweck und Funktion

### Warum existiert dieses Projekt?

[Detaillierte Erklärung des Geschäftszwecks und des Problems, das gelöst wird]

### Was tut dieses Projekt?

**Hauptfunktionen:**
- [Funktion 1]: [Beschreibung]
- [Funktion 2]: [Beschreibung]
- [Funktion 3]: [Beschreibung]

### Zielgruppe

[Wer nutzt dieses Projekt? Wer entwickelt daran?]
```

#### 3. Voraussetzungen

**Zweck:** Information über technische und fachliche Voraussetzungen.

**Inhalt:**
- Technische Voraussetzungen (Java, Maven, Tools)
- Systemanforderungen
- Benötigte Kenntnisse
- Externe Abhängigkeiten

**Zu dokumentieren:**
```
[HIER: Voraussetzungen beschreiben]

## Voraussetzungen

### Technische Voraussetzungen

**Erforderlich:**
- Java [Version] oder höher
- Maven [Version] oder höher
- [Weitere Tools]

**Optional:**
- [Tool 1]: [Zweck]
- [Tool 2]: [Zweck]

### Systemanforderungen

- Betriebssystem: [Unterstützte OS]
- Arbeitsspeicher: [Empfehlung]
- Festplattenspeicher: [Empfehlung]

### Kenntnisse

**Empfohlene Kenntnisse:**
- [Kenntnis 1]
- [Kenntnis 2]
- [Kenntnis 3]

### Externe Abhängigkeiten

- [Abhängigkeit 1]: [Beschreibung, wie beschafft?]
- [Abhängigkeit 2]: [Beschreibung, wie beschafft?]
```

#### 4. Build und Ausführung

**Zweck:** Anleitung zum Bauen und Ausführen des Projekts.

**Inhalt:**
- Build-Befehle
- Ausführungsanleitung
- Test-Ausführung
- Deployment (falls relevant)

**Zu dokumentieren:**
```
[HIER: Build-Anleitung schreiben]

## Build und Ausführung

### Projekt bauen

**Gesamtes Projekt (inklusive aller Module):**
```bash
mvn clean install
```

**Erklärung:**
- `clean`: Löscht vorherige Build-Artefakte
- `install`: Kompiliert, testet und installiert Artefakte im lokalen Repository
- Baut alle Sub-Module in der richtigen Reihenfolge

**Nur kompilieren (ohne Tests):**
```bash
mvn clean compile
```

**Nur Tests ausführen:**
```bash
mvn test
```

**Einzelnes Modul bauen:**
```bash
cd module1
mvn clean install
```

### Projekt ausführen

[Falls anwendbar: Anleitung zur Ausführung]

**Beispiel für ausführbare JAR:**
```bash
java -jar target/project-name-1.0.0.jar
```

**Beispiel für Web-Anwendung:**
```bash
mvn spring-boot:run
```

### Build-Artefakte

Nach dem Build finden Sie die Artefakte in:
- `target/`: Kompilierte Klassen
- `target/[modulname]-[version].jar`: JAR-Datei
- `target/[modulname]-[version]-sources.jar`: Quellcode-JAR
- `target/[modulname]-[version]-javadoc.jar`: JavaDoc-JAR
```

#### 5. Projektstruktur

**Zweck:** Übersicht über die Verzeichnisstruktur.

**Inhalt:**
- Verzeichnisbaum
- Erklärung wichtiger Verzeichnisse
- Beschreibung der Module

**Zu dokumentieren:**
```
[HIER: Projektstruktur beschreiben]

## Projektstruktur

### Verzeichnisstruktur

```
/java
├── pom.xml                    # Master-POM für Multi-Modul-Projekt
├── README.md                   # Projektübersicht (diese Datei)
├── .gitignore                  # Git-Ignore-Regeln
├── LICENSE                     # Lizenz
├── module1/                    # Modul 1: [Beschreibung]
│   ├── pom.xml                # Modul-POM
│   ├── README.md              # Modul-Dokumentation
│   └── src/
│       ├── main/
│       │   ├── java/          # Java-Quellcode
│       │   └── resources/     # Ressourcen
│       └── test/
│           ├── java/          # Test-Code
│           └── resources/     # Test-Ressourcen
├── module2/                    # Modul 2: [Beschreibung]
│   ├── pom.xml
│   ├── README.md
│   └── src/
└── docs/                       # Weitere Dokumentation
    ├── architektur.md
    ├── deployment.md
    └── ...
```

### Wichtige Verzeichnisse

**Root-Verzeichnis:**
- `pom.xml`: Master-POM, definiert Multi-Modul-Projekt
- `README.md`: Projektübersicht und Einstiegspunkt

**Modul-Verzeichnisse:**
- `pom.xml`: Modul-spezifische POM
- `README.md`: Modul-Dokumentation
- `src/main/java/`: Java-Quellcode
- `src/main/resources/`: Ressourcen (Properties, XML, etc.)
- `src/test/java/`: Test-Code
- `src/test/resources/`: Test-Ressourcen
- `target/`: Build-Artefakte (wird beim Build erstellt)

### Modul-Beschreibungen

**module1: [Name]**
- **Zweck:** [Wofür ist dieses Modul?]
- **Hauptfunktionen:** [Liste]
- **Abhängigkeiten:** [Von welchen Modulen/Externen abhängig?]

**module2: [Name]**
- **Zweck:** [Wofür ist dieses Modul?]
- **Hauptfunktionen:** [Liste]
- **Abhängigkeiten:** [Von welchen Modulen/Externen abhängig?]
```

#### 6. Weitere Informationen

**Zweck:** Verweise auf zusätzliche Dokumentation.

**Inhalt:**
- Links zu weiterführender Dokumentation
- Externe Ressourcen
- Kontakte

**Zu dokumentieren:**
```
[HIER: Weitere Informationen auflisten]

## Weitere Informationen

### Dokumentation

- [Architektur-Dokumentation](./docs/architektur.md): Systemarchitektur und Design
- [Deployment-Anleitung](./docs/deployment.md): Anleitung zum Deployment
- [Entwickler-Guide](./docs/entwickler-guide.md): Guide für Entwickler
- [API-Dokumentation](./docs/api.md): API-Dokumentation

### Externe Ressourcen

- [Link 1]: [Beschreibung]
- [Link 2]: [Beschreibung]

### Kontakte

- Projekt-Owner: [Name/Kontakt]
- Tech Lead: [Name/Kontakt]
- Support: [Kontakt]
```

### README.md für Sub-Module

**Zweck:** Modul-spezifische Dokumentation.

**Inhalt:**
- Modul-Übersicht
- Zweck des Moduls
- Abhängigkeiten
- Verwendung
- Verweis auf Root-README

**Zu dokumentieren:**
```
[HIER: Modul-README-Struktur beschreiben]

# [Modulname]

## Überblick

**Zweck:** [Wofür ist dieses Modul?]

**Was tut dieses Modul?**
[Kurze Beschreibung der Hauptfunktionen]

**Teil von:** [Verweis auf Root-Projekt]

## Abhängigkeiten

**Externe Dependencies:**
- [Dependency 1]: [Zweck]
- [Dependency 2]: [Zweck]

**Interne Abhängigkeiten:**
- [Modul 1]: [Warum benötigt?]
- [Modul 2]: [Warum benötigt?]

## Verwendung

**Wie wird dieses Modul verwendet?**
[Anleitung zur Verwendung des Moduls]

**Beispiel:**
```java
[Code-Beispiel]
```

## Build

```bash
mvn clean install
```

## Weitere Informationen

- [Root-Projekt-README](../README.md)
- [Modul-spezifische Dokumentation](./docs/modul-doku.md)
```

---

## Weitere Dokumentation

### Wann weitere Dokumentation?

**Weitere Markdown-Dateien werden erstellt, wenn:**
- Das Projekt komplex ist
- Spezielle Themen vertieft werden müssen
- Die README.md zu lang wird
- Spezifische Zielgruppen angesprochen werden sollen

**Organisation:**
- Weitere Dokumentation in `docs/`-Verzeichnis
- README.md leitet mit Links auf spezielle Dokumentation weiter
- Jede Dokumentation hat einen klaren Zweck

### Mögliche Dokumentationsdateien

**Zu dokumentieren:**
```
[HIER: Mögliche Dokumentationsdateien auflisten]

### docs/architektur.md
**Zweck:** Systemarchitektur und Design-Entscheidungen
**Zielgruppe:** Entwickler, Architekten
**Inhalt:**
- Architektur-Übersicht
- Design-Entscheidungen
- Komponenten-Beschreibungen
- Datenflüsse

### docs/deployment.md
**Zweck:** Anleitung zum Deployment
**Zielgruppe:** DevOps, Operations
**Inhalt:**
- Deployment-Prozess
- Konfiguration
- Umgebungen
- Troubleshooting

### docs/entwickler-guide.md
**Zweck:** Guide für Entwickler
**Zielgruppe:** Neue Entwickler
**Inhalt:**
- Entwicklungsumgebung einrichten
- Coding-Standards
- Git-Workflow
- Testing-Guidelines

### docs/api.md
**Zweck:** API-Dokumentation
**Zielgruppe:** API-Nutzer
**Inhalt:**
- API-Endpoints
- Request/Response-Formate
- Authentifizierung
- Beispiele

### docs/contributing.md
**Zweck:** Beitragsrichtlinien
**Zielgruppe:** Externe Contributor
**Inhalt:**
- Wie kann man beitragen?
- Code-Standards
- Pull-Request-Prozess
- Code-Review-Richtlinien

### docs/changelog.md
**Zweck:** Änderungshistorie
**Zielgruppe:** Alle
**Inhalt:**
- Versionshistorie
- Änderungen pro Version
- Breaking Changes
```

### Verknüpfung in README.md

**Zu dokumentieren:**
```
[HIER: Verknüpfung beschreiben]

Die README.md sollte am Ende einen Abschnitt "Weitere Informationen" enthalten, 
der auf spezielle Dokumentation verweist:

```markdown
## Weitere Informationen

### Dokumentation

- [Architektur](./docs/architektur.md): Systemarchitektur und Design-Entscheidungen
- [Deployment](./docs/deployment.md): Anleitung zum Deployment
- [Entwickler-Guide](./docs/entwickler-guide.md): Guide für Entwickler
- [API-Dokumentation](./docs/api.md): API-Dokumentation
- [Contributing](./docs/contributing.md): Beitragsrichtlinien
- [Changelog](./docs/changelog.md): Änderungshistorie
```

**Prinzip:**
- README.md bleibt übersichtlich
- Spezielle Themen werden ausgelagert
- Klare Verweise auf weitere Dokumentation
- Jede Dokumentation hat einen klaren Zweck
```

---

## Build-Prozess

### Maven Build

**Zweck:** Beschreibung des Build-Prozesses.

**Inhalt:**
- Wie funktioniert der Build?
- Abhängigkeiten zwischen Modulen
- Build-Artefakte
- Build-Phasen

**Zu dokumentieren:**
```
[HIER: Build-Prozess beschreiben]

## Build-Prozess

### Maven Build-Phasen

**Standard-Build-Phasen:**
1. `validate`: Validiert Projekt-Struktur
2. `compile`: Kompiliert Quellcode
3. `test`: Führt Tests aus
4. `package`: Erstellt Artefakt (JAR, WAR, etc.)
5. `install`: Installiert Artefakt im lokalen Repository
6. `deploy`: Deployt Artefakt in Remote-Repository

### Multi-Modul-Build

**Reihenfolge:**
1. Maven liest Master-POM
2. Identifiziert alle Module aus `<modules>`-Liste
3. Baut Module in der richtigen Reihenfolge (abhängig von Dependencies)
4. Installiert Module im lokalen Repository
5. Verfügbare Module können von anderen Modulen verwendet werden

**Beispiel:**
```bash
mvn clean install
```

**Was passiert:**
- `clean`: Löscht `target/`-Verzeichnisse in allen Modulen
- `install`: Baut alle Module in der richtigen Reihenfolge
- Module werden nacheinander gebaut (abhängig von Dependencies)

### Build-Artefakte

**Nach dem Build finden Sie:**

**In jedem Modul:**
- `target/classes/`: Kompilierte Klassen
- `target/test-classes/`: Kompilierte Test-Klassen
- `target/[modulname]-[version].jar`: Haupt-JAR
- `target/[modulname]-[version]-sources.jar`: Quellcode-JAR
- `target/[modulname]-[version]-javadoc.jar`: JavaDoc-JAR

**Im Root:**
- Keine eigenen Artefakte (packaging: pom)
- Dient nur als Container für Module
```

### Abhängigkeiten zwischen Modulen

**Zu dokumentieren:**
```
[HIER: Modul-Abhängigkeiten beschreiben]

## Modul-Abhängigkeiten

### Abhängigkeitsstruktur

**Wie werden Module-Abhängigkeiten definiert?**

In der `pom.xml` eines Moduls:

```xml
<dependencies>
    <dependency>
        <groupId>com.example</groupId>
        <artifactId>module1</artifactId>
        <version>${project.version}</version>
    </dependency>
</dependencies>
```

**Build-Reihenfolge:**
- Maven analysiert Dependencies automatisch
- Module werden in der richtigen Reihenfolge gebaut
- Abhängige Module werden vor abhängigen Modulen gebaut

**Beispiel:**
- `module1` hat keine internen Abhängigkeiten → wird zuerst gebaut
- `module2` hängt von `module1` ab → wird nach `module1` gebaut
- `module3` hängt von `module1` und `module2` ab → wird zuletzt gebaut

### Externe Dependencies

**Zentral verwaltet in Master-POM:**

```xml
<dependencyManagement>
    <dependencies>
        <dependency>
            <groupId>org.springframework</groupId>
            <artifactId>spring-core</artifactId>
            <version>5.3.21</version>
        </dependency>
    </dependencies>
</dependencyManagement>
```

**Verwendung in Modulen:**

```xml
<dependencies>
    <dependency>
        <groupId>org.springframework</groupId>
        <artifactId>spring-core</artifactId>
        <!-- Version wird von dependencyManagement übernommen -->
    </dependency>
</dependencies>
```
```

---

## Verzeichnisstruktur im Detail

### Standard Maven-Verzeichnisstruktur

**Zu dokumentieren:**
```
[HIER: Verzeichnisstruktur detailliert beschreiben]

## Verzeichnisstruktur im Detail

### src/main/java/

**Zweck:** Java-Quellcode des Moduls

**Struktur:**
```
src/main/java/
└── com/
    └── example/
        └── module1/
            ├── Main.java
            ├── Service.java
            └── util/
                └── Helper.java
```

**Konvention:**
- Paketstruktur spiegelt Verzeichnisstruktur wider
- Standard: `com.[organisation].[projekt].[modul]`
- Klassen werden in entsprechenden Paketen organisiert

### src/main/resources/

**Zweck:** Ressourcen, die zur Laufzeit benötigt werden

**Inhalt:**
- Properties-Dateien (`application.properties`)
- XML-Konfigurationsdateien
- Templates
- Statische Dateien (Bilder, etc.)

**Struktur:**
```
src/main/resources/
├── application.properties
├── log4j.xml
└── templates/
    └── template.html
```

### src/test/java/

**Zweck:** Test-Code

**Struktur:**
- Spiegelt die Struktur von `src/main/java/` wider
- Test-Klassen haben meist `Test`-Suffix
- JUnit oder TestNG werden verwendet

**Beispiel:**
```
src/test/java/
└── com/
    └── example/
        └── module1/
            └── ServiceTest.java
```

### src/test/resources/

**Zweck:** Test-Ressourcen

**Inhalt:**
- Test-Konfigurationsdateien
- Test-Daten
- Mock-Daten

### target/

**Zweck:** Build-Artefakte (wird beim Build erstellt)

**Wichtig:**
- Wird beim Build erstellt
- Sollte in `.gitignore` stehen
- Kann gelöscht werden (`mvn clean`)

**Inhalt:**
- `classes/`: Kompilierte Klassen
- `test-classes/`: Kompilierte Test-Klassen
- `[modulname]-[version].jar`: Haupt-Artefakt
- Weitere Build-Artefakte
```

---

## Best Practices

### README.md Best Practices

**Zu dokumentieren:**
```
[HIER: Best Practices für README.md]

## Best Practices für README.md

### Klarheit und Verständlichkeit

✅ **Gut:**
- Klare, prägnante Sprache
- Strukturierte Gliederung
- Verständlich für neue Teammitglieder
- Praktische Beispiele

❌ **Schlecht:**
- Zu technisch oder zu oberflächlich
- Unstrukturiert
- Veraltete Informationen
- Fehlende Beispiele

### Aktualität

✅ **Gut:**
- Regelmäßig aktualisiert
- Reflektiert aktuellen Stand des Projekts
- Version wird dokumentiert

❌ **Schlecht:**
- Veraltete Informationen
- Inkonsistente Versionsangaben
- Nicht aktualisiert nach Änderungen

### Vollständigkeit

✅ **Gut:**
- Enthält alle wichtigen Informationen
- Erklärt Zweck und Funktion
- Beschreibt Build-Prozess
- Verweist auf weitere Dokumentation

❌ **Schlecht:**
- Fehlen wichtige Informationen
- Unvollständige Beschreibungen
- Fehlende Verweise

### Struktur

✅ **Gut:**
- Klare Gliederung
- Logische Reihenfolge
- Einheitliche Formatierung
- Verweise auf weitere Dokumentation

❌ **Schlecht:**
- Unstrukturiert
- Schwer navigierbar
- Inkonsistente Formatierung
```

### Projektstruktur Best Practices

**Zu dokumentieren:**
```
[HIER: Best Practices für Projektstruktur]

## Best Practices für Projektstruktur

### Modul-Organisation

✅ **Gut:**
- Klare Trennung der Verantwortlichkeiten
- Module sind unabhängig entwickelbar
- Minimale Abhängigkeiten zwischen Modulen
- Jedes Modul hat klaren Zweck

❌ **Schlecht:**
- Zu viele Abhängigkeiten zwischen Modulen
- Unklare Verantwortlichkeiten
- Zirkuläre Abhängigkeiten
- Module ohne klaren Zweck

### Verzeichnisstruktur

✅ **Gut:**
- Folgt Maven-Standards
- Konsistente Struktur über alle Module
- Klare Namenskonventionen
- Logische Organisation

❌ **Schlecht:**
- Abweichung von Maven-Standards ohne Grund
- Inkonsistente Struktur
- Unklare Namenskonventionen
- Unorganisierte Struktur

### Dokumentation

✅ **Gut:**
- README.md in jedem Modul
- Aktuelle Dokumentation
- Klare Verweise auf weitere Dokumentation
- Dokumentation ist Teil des Projekts

❌ **Schlecht:**
- Fehlende README.md
- Veraltete Dokumentation
- Dokumentation nicht im Repository
- Unklare Verweise
```

### pom.xml Best Practices

**Zu dokumentieren:**
```
[HIER: Best Practices für pom.xml]

## Best Practices für pom.xml

### Master-POM

✅ **Gut:**
- Zentrale Verwaltung von Dependency-Versionen
- Gemeinsame Plugin-Konfigurationen
- Einheitliche Properties
- Klare Modul-Deklaration

❌ **Schlecht:**
- Versionen in jedem Modul einzeln
- Inkonsistente Plugin-Konfigurationen
- Fehlende zentrale Verwaltung
- Unklare Modul-Struktur

### Modul-POM

✅ **Gut:**
- Vererbt von Master-POM
- Nur modul-spezifische Dependencies
- Klare Abhängigkeiten
- Konsistente Konfiguration

❌ **Schlecht:**
- Duplizierte Konfigurationen
- Inkonsistente Versionsverwaltung
- Unklare Abhängigkeiten
- Abweichungen ohne Grund

### Dependencies

✅ **Gut:**
- Versionen zentral verwaltet
- Nur notwendige Dependencies
- Klare Scope-Definitionen (compile, test, etc.)
- Regelmäßige Updates

❌ **Schlecht:**
- Versionen in jedem Modul
- Überflüssige Dependencies
- Unklare Scopes
- Veraltete Versionen
```

---

## Checkliste für neue Projekte

**Zu dokumentieren:**
```
[HIER: Checkliste erstellen]

## Checkliste für neue Projekte

### Projekt-Setup

- [ ] Wurzelverzeichnis erstellt (`/java` oder vereinbartes Verzeichnis)
- [ ] Master-POM (`pom.xml`) erstellt
- [ ] README.md im Root erstellt
- [ ] `.gitignore` erstellt (inkl. `target/`)
- [ ] `LICENSE` hinzugefügt (falls erforderlich)

### Modul-Setup

Für jedes Modul:
- [ ] Modul-Verzeichnis erstellt
- [ ] Modul-POM (`pom.xml`) erstellt
- [ ] Modul in Master-POM eingetragen
- [ ] README.md im Modul erstellt
- [ ] Standard-Verzeichnisstruktur erstellt (`src/main/java`, etc.)

### Dokumentation

- [ ] Root-README.md enthält:
  - [ ] Projektübersicht
  - [ ] Zweck und Funktion
  - [ ] Voraussetzungen
  - [ ] Build-Anleitung
  - [ ] Projektstruktur
  - [ ] Verweise auf weitere Dokumentation

- [ ] Modul-README.md enthält:
  - [ ] Modul-Übersicht
  - [ ] Zweck des Moduls
  - [ ] Abhängigkeiten
  - [ ] Verwendung

### Build

- [ ] Projekt baut erfolgreich (`mvn clean install`)
- [ ] Tests laufen erfolgreich
- [ ] Artefakte werden korrekt erstellt
- [ ] Modul-Abhängigkeiten funktionieren

### Weitere Dokumentation (falls erforderlich)

- [ ] `docs/`-Verzeichnis erstellt
- [ ] Weitere Dokumentationsdateien erstellt
- [ ] Verweise in README.md eingefügt
```

---

## Zusammenfassung

Ein **Java-Projekt** folgt einer standardisierten Struktur:

**Kern-Elemente:**
- **Wurzelverzeichnis:** `/java` (Standard) mit Master-POM
- **Build-Tool:** Maven (pom.xml)
- **Struktur:** Multi-Modul-Projekt mit Sub-Modulen
- **Dokumentation:** README.md als zentrale Dokumentation (verpflichtend)

**Jedes Projekt/Modul enthält:**
- `pom.xml`: Projekt-Konfiguration
- `README.md`: Dokumentation (verpflichtend)
- `src/main/java/`: Java-Quellcode
- `src/test/java/`: Test-Code
- `target/`: Build-Artefakte (wird erstellt)

**README.md ist:**
- Der Einstiegspunkt für neue Teammitglieder
- Erklärt Sinn und Zweck des Projekts
- Beschreibt, was das Projekt tut
- Vermittelt notwendiges Wissen
- **Verpflichtend** für jedes Projekt und Modul

**Weitere Dokumentation:**
- Wird in `docs/`-Verzeichnis ausgelagert
- README.md verweist auf spezielle Dokumentation
- Jede Dokumentation hat einen klaren Zweck

Ein gut strukturiertes und dokumentiertes Java-Projekt ermöglicht es neuen Teammitgliedern, schnell zu verstehen, was das Projekt tut und wie sie daran arbeiten können.
