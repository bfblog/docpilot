product-backlog.md# Prompt-Bibliothek

Diese Bibliothek enthält strukturierte Prompts für verschiedene Anwendungsfälle.

## 📁 Struktur

```
/prompt/
├── README.md                    # Diese Datei
├── _koordinator.md              # Hauptrolle: Koordinator aller Rollen
└── rollen/
    └── prompt-coach.md          # Rolle: Prompt-Coach
```

## 🎯 Verwendung

### Koordinator - Hauptrolle (Empfohlen)

Der `_koordinator.md` ist die Hauptrolle, die alle anderen Rollen koordiniert.

**Funktionen:**
- Kennt alle Rollen im Verzeichnis `./rollen`
- Interagiert direkt mit dem Nutzer
- Berät den Nutzer und schlägt die passende Rolle vor
- Macht jeden Rollenwechsel explizit und meldet ihn in der Konsole

**Verwendung:**
1. Den kompletten Inhalt von `_koordinator.md` kopieren
2. Als Startprompt in die KI-Session einfügen
3. Der Koordinator führt dich zu den passenden Rollen

**Beispiel:**
```
🔄 Ich agiere nun in der Rolle: prompt-coach
```

### Einzelne Rollen verwenden

Du kannst auch einzelne Rollen direkt verwenden:

**Prompt-Coach:**
1. Den kompletten Inhalt von `rollen/prompt-coach.md` kopieren
2. Als Startprompt in die KI-Session einfügen
3. Die KI arbeitet dann nach den definierten Regeln und Strukturen

## 📝 Prompt-Entwicklung

### Qualitätskriterien

Ein guter Prompt sollte:
- ✅ Eindeutig sein
- ✅ Kurz und verständlich sein
- ✅ Keine unnötigen Adjektive oder Prosa enthalten
- ✅ Klare Ziele definieren
- ✅ W-Fragen beantworten (Wer? Warum? Wie? Was? Wann? Wo?)
- ✅ Rollen, Kontext und Grenzen benennen
- ✅ Klare Handlungen oder Anforderungen vorgeben
- ✅ Spätere Fehler vermeiden
- ✅ Für Menschen und KI gleichermaßen lesbar sein

### Entwicklungsprozess

1. **Verständnisfragen stellen** - Was soll der Prompt erreichen?
2. **Ziel definieren** - Klare Zielsetzung formulieren
3. **Promptstruktur erzeugen** - W-Fragen beantworten
4. **Promptvorschlag erstellen** - Erste Version formulieren
5. **Kompaktheits-Check durchführen** - Auf Wesentliches reduzieren
6. **Zustimmung einholen oder nachbessern** - Iterative Verbesserung

## 🔄 Erweiterung der Bibliothek

Neue Prompts können hinzugefügt werden:
- Klare, beschreibende Dateinamen verwenden
- Strukturierte Formatierung (Markdown)
- Dokumentation der Verwendung im README ergänzen

## 📚 Weitere Ressourcen

- [Prompt Engineering Guide](https://platform.openai.com/docs/guides/prompt-engineering)
- [Best Practices für Prompts](https://help.openai.com/en/articles/6654000-best-practices-for-prompt-engineering-with-openai-api)

