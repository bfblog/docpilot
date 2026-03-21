# 3. Kontextabgrenzung / Systemkontext

## Systemübersicht

Die Datenplattform ist ein zentrales System, das:
- Daten von externen Systemen bezieht
- Daten im kanonischen Format speichert (ggf. bereinigt/veredelt)
- Daten über Services externen Diensten bereitstellt

## Nachbarsysteme

### Externe Datenquellen
- **Beschreibung:** Systeme, die Daten an die Plattform liefern
- **Schnittstelle:** [Zu definieren: Protokoll, Format]
- **Richtung:** Externe Systeme → Datenplattform
- **Datenfluss:** Rohdaten werden bezogen und im kanonischen Format gespeichert

### Externe Dienste
- **Beschreibung:** Systeme, die Daten von der Plattform beziehen
- **Schnittstelle:** [Zu definieren: Protokoll, Format]
- **Richtung:** Datenplattform → Externe Dienste
- **Datenfluss:** Daten werden im kanonischen Format bereitgestellt

## Benutzer

[HIER: Benutzerrollen definieren, falls vorhanden]

## Schnittstellen

### Schnittstelle: Datenimport
- **Angeboten von:** Datenplattform (Import-Service)
- **Genutzt von:** Externe Datenquellen
- **Protokoll:** [Zu definieren]
- **Format:** [Zu definieren - wird zu kanonischem Format transformiert]
- **Verantwortlichkeit:** Empfang von Daten aus externen Systemen

### Schnittstelle: Datenexport
- **Angeboten von:** Datenplattform (Export-Service)
- **Genutzt von:** Externe Dienste
- **Protokoll:** [Zu definieren]
- **Format:** Kanonisches Datenmodell
- **Verantwortlichkeit:** Bereitstellung von Daten im kanonischen Format
