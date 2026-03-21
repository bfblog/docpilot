# 1. Einführung und Ziele

## 1.1 Anforderungen

### Funktionale Anforderungen

**FR-1: Kanonisches Datenmodell**
- Die Datenplattform verwendet ein kanonisches Datenmodell als zentrale Datenstruktur.
- Alle Daten innerhalb der Plattform werden in diesem Format gespeichert.
- Services nutzen dieses Datenmodell zum Austausch von Daten.
- Durch den Modell-First Ansatz werden Redundanzen vermieden.

**FR-2: Modell-basierte Persistenz**
- Die Persistenz der Datenplattform nutzt genau das kanonische Datenmodell.
- Daten werden in diesem Format persistiert.
- Daten können in diesem Format wieder bezogen werden.

**FR-3: Datenintegration**
- Die Plattform bezieht Daten von externen Systemen.
- Daten werden im kanonischen Format gespeichert.
- Daten können bereinigt und veredelt werden.

**FR-4: Datenbereitstellung**
- Die Plattform stellt Daten über Services externen Diensten bereit.
- Daten werden im kanonischen Format bereitgestellt.

### Nicht-funktionale Anforderungen

**NFR-1: Container-basierte Architektur**
- Die Plattform ist container-basiert aufgebaut.
- Services sind als Container deploybar.

**NFR-2: Modell-First Ansatz**
- Das kanonische Datenmodell hat Priorität vor anderen Datenformaten.
- Redundanzen werden durch das zentrale Datenmodell vermieden.

### Geschäftsziele und -treiber

- **Zentrale Datenhaltung:** Einheitliches Datenmodell für alle Daten innerhalb der Plattform
- **Redundanzvermeidung:** Durch kanonisches Datenmodell werden Redundanzen vermieden
- **Datenqualität:** Bereinigung und Veredelung von Daten aus externen Systemen
- **Wiederverwendbarkeit:** Daten können zentral gespeichert und mehrfach verwendet werden

## 1.2 Qualitätsziele

[Noch nicht dokumentiert - wird iterativ ergänzt]

## 1.3 Stakeholder / Personas

[Noch nicht dokumentiert - wird iterativ ergänzt]
