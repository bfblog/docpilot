---
typ: artefakt
name: Deployment Operations Canvas
kontext: Hilfsvorlage zur strukturierten Erfassung von Deployment, Skalierung, Monitoring, Verfügbarkeit, Betriebsaufwand und betrieblichen Risiken — realistische Betriebsperspektive, kein Idealbild
rollen:
  - Softwarearchitekt
  - Operativer Betrieb
artefakte:
  - Architekturdokumentation nach arc42
  - Systemhandbuch
  - Integration Canvas
  - Quality Attribute Canvas
  - Risk Technical Debt Canvas
workflows: []
---

# Artefakt: Deployment / Operations Canvas

## Über den Deployment / Operations Canvas

Der **Deployment / Operations Canvas** strukturiert, **wie** ein System **betrieben** wird: **Deployment- und Verteilungsstruktur**, **Skalierung** und Engpässe, **Logging, Monitoring und Alerting**, **Verfügbarkeit und Resilienz** (Redundanz, Failover, Recovery), **Betriebsaufwand** (Komplexität, Skills) sowie **betriebliche Risiken** und Single Points of Failure. Ziel ist eine **ehrliche, operative Sicht** — **keine** idealisierte Referenzarchitektur auf dem Whiteboard.

**Typischer Anschluss:** Inhalte fließen in **arc42** (u. a. **Verteilungssicht**, Randbedingungen, Risiken), in das **Systemhandbuch** und **Betriebshandbuch**, und ergänzen **Integration Canvas** (Laufzeit/Protokolle) sowie **Quality Attribute Canvas** (Verfügbarkeit, Performance-Ziele). Überschneidungen mit dem **Risk / Technical Debt Canvas** bewusst nutzen oder verlinken.

---

## Sinn und Zweck

- **Gemeinsames Bild** zwischen Entwicklung, Architektur und Betrieb
- **Skalierungsgrenzen** und **Engpässe** früh benennen
- **Observability** (Logs, Metriken, Traces, Alerts) **planvoll** statt improvisiert
- **Betriebskomplexität** und **Skill-Bedarf** sichtbar machen
- **Schwachstellen** und **SPOFs** ohne Beschönigung dokumentieren

---

## Eingabe (für die Sitzung / den Prompt)

| Platzhalter | Bedeutung |
|-------------|-----------|
| System | Was wird betrieben? |
| Infrastruktur (optional) | Cloud, On-Prem, Kubernetes, VMs, PaaS, … |
| Anforderungen (optional) | SLAs, Compliance, Datenresidenz, Budget |

---

## Ablage (außerhalb der Bibliothek)

Typisch unter `{DOCS}/` oder als Teil von System-/Betriebshandbuch, z. B. `docs/betrieb/deployment-operations-[system].md`.

---

## Vorlage (Markdown)

```markdown
# Deployment / Operations Canvas: [Systemname]

**Datum:** [Datum]  
**Owner:** [Softwarearchitekt / Betrieb — gemeinsam]  
**Status:** [Entwurf | Vereinbart | Überholt]

## 1. Deployment-Struktur

Zu dokumentieren:
- [HIER: **Wie** ist das System **verteilt**? — Umgebungen (Dev/Test/Prod), Regionen, Netzsegmente]
- [HIER: **Komponenten / Nodes / Cluster** — wer läuft wo, grobe Topologie]

| Komponente / Service | Umgebung | Laufzeit / Host / Cluster | Bemerkung |
|----------------------|----------|---------------------------|-----------|
| … | … | … | … |

## 2. Skalierung

Zu dokumentieren:
- [HIER: **Horizontal** vs. **vertikal** — was ist vorgesehen, was ist Grenze?]
- [HIER: **Engpässe** — Datenbank, zentraler Broker, Lizenz, API-Quota, …]

| Dimension | Mechanismus | Bekannte Grenze / Engpass |
|-----------|---------------|---------------------------|
| … | … | … |

## 3. Betrieb & Monitoring

Zu dokumentieren:
- [HIER: **Logging** — zentral, Retention, PII, Correlation IDs]
- [HIER: **Monitoring** — Metriken, Dashboards, SLIs]
- [HIER: **Alerting** — wann wird wen benachrichtigt, Runbooks?]

| Bereich | Werkzeug / Ort | Was wird überwacht? |
|---------|----------------|---------------------|
| … | … | … |

## 4. Verfügbarkeit & Resilienz

Zu dokumentieren:
- [HIER: **Redundanz** — active/active, active/passive, single AZ?]
- [HIER: **Failover** — automatisch, manuell, RTO/RPO falls bekannt]
- [HIER: **Recovery** — Backup, Restore-Tests, Disaster-Übungen]

| Szenario | Vorgehen | Annahme / Lücke |
|----------|----------|-----------------|
| … | … | … |

## 5. Betriebsaufwand

Zu dokumentieren:
- [HIER: **Komplexität** — viele bewegliche Teile, manuelle Schritte, Ausnahmen]
- [HIER: **Notwendige Skills** — Kubernetes, DB-Admin, Netzwerk, Security, …]

| Thema | Aufwand (grob: niedrig/mittel/hoch) | Skills / Verantwortung |
|-------|-------------------------------------|-------------------------|
| … | … | … |

## 6. Risiken

Zu dokumentieren:
- [HIER: **Betriebliche Schwachstellen** — undokumentierte Abhängigkeiten, fehlende Überwachung]
- [HIER: **Single Points of Failure** — technisch und organisatorisch (Bus-Faktor)]

| Risiko | Art (SPOF / Komplexität / …) | Mitigation / nächster Schritt |
|--------|------------------------------|-------------------------------|
| … | … | … |

## Verknüpfung arc42 / Handbücher

Zu dokumentieren:
- [HIER: arc42 Verteilungssicht / relevante Kapitel; `{OPERATIONS-MANUAL.MD}` / Systemhandbuch]
```

---

## Anforderungen an die Ausfüllung

- **Realistische Betriebsperspektive** — was passiert bei 3 Uhr nachts, bei Deployment, bei Lastspitzen?
- **Fokus auf Risiken und Komplexität**, nicht auf Marketing-Diagramme
- **Keine idealisierte Architektur** — bekannte Kompromisse und Schulden benennen
- **Annahmen** explizit (z. B. „Restore nie getestet“)

---

## Zu dokumentieren (Kurz-Checkliste)

```
Kritischster SPOF: [HIER]
Schwächstes Monitoring / blindes Fleck: [HIER]
Größter manueller Betriebsschritt: [HIER]
Ein Skalierungs-Engpass: [HIER]
```
