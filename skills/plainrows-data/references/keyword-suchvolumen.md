# Keyword Suchvolumen Tool & API: Google Keyword-Recherche (`plainrows/keyword-suchvolumen`)

Keyword Suchvolumen prüfen für Google Deutschland, Österreich, Schweiz und 91 weitere Länder: monatliches Suchvolumen, CPC, Wettbewerb, Keyword Difficulty, Suchintention und Verlauf für bis zu 10.000 Keywords. Keyword Planner Alternative, auch als MCP-Tool. Nur Keywords mit Daten + 0,021 $ Start.

Store page and full documentation: https://apify.com/plainrows/keyword-suchvolumen

## Input fields

| Field | Type | Default | What it does |
|---|---|---|---|
| `keywords` (required) | array |  | Keywords, eines pro Eintrag, bis zu 10.000 pro Lauf (je max. 80 Zeichen und 10 Wörter), z. B. "kaffeemaschine". Am besten echte Suchbegriffe (1 bis 4 Wörter): sehr lange, falsch geschriebene oder ganz neue Begriffe... |
| `mode` | string: `volume`, `ideas` | "volume" | "Suchvolumen": Kennzahlen für jedes eingegebene Keyword, z. B. "volume". "Keyword-Ideen" ("ideas"): jedes Keyword ist ein Start-Keyword, der Lauf liefert verwandte Keyword-Ideen mit denselben Kennzahlen (plus... |
| `country` | string (94 codes, see the Store page) | "DE" | Land, dessen Google-Suchdaten Sie wollen (94 Länder), z. B. "DE" für Deutschland, "AT" für Österreich, "CH" für die Schweiz. |
| `languageCode` | string |  | Sprachcode, z. B. "de", "fr" oder "en". Leer lassen = Hauptsprache des Landes (Deutsch für DE, AT und CH). Nur Sprachen, die die Datenquelle für das Land anbietet; andere stoppen den Lauf mit einer klaren Meldung und... |
| `historyMonths` | integer | 12 | Wie viele Monate Suchvolumen pro Keyword, neueste zuerst, z. B. 12. 0 = keiner. Bis 96 Monate (meist ab 2018). Ohne Aufpreis. Im Ideen-Modus liefert die Quelle höchstens 12 Monate. |
| `includeAiSearchVolume` | boolean | false | Nur im Suchvolumen-Modus, z. B. true: fügt aiSearchVolume (geschätzte monatliche Nutzung des Keywords in KI-Tools und Chat-Assistenten) mit Monatsverlauf hinzu. Berechnet pro Keyword mit positivem KI-Volumen (siehe... |
| `maxIdeasPerSeed` | integer | 50 | Nur Ideen-Modus, z. B. 50: höchstens so viele verwandte Keyword-Ideen pro Start-Keyword, relevanteste zuerst. Eine Idee, die schon für ein anderes Start-Keyword geliefert wurde, wird nicht erneut geliefert oder... |

## Example input

```json
{
  "keywords": [
    "kaffeemaschine",
    "siebträgermaschine",
    "kaffeevollautomat"
  ],
  "mode": "volume",
  "country": "DE"
}
```

## Price per event (Apify plan: Free / Starter / Scale / Business)

- **Keyword**: $0.01 / $0.008 / $0.007 / $0.006. Ein Keyword mit Daten: Suchvolumen, CPC, Wettbewerb, Keyword Difficulty, Suchintention, Trends und Monatsverlauf. Keywords ohne Daten, Duplikate und ungültige Keywords kosten nie etwas. Dazu eine Startgebühr pro Lauf (Actor Start).
- **KI-Suchvolumen**: $0.005 / $0.004 / $0.0035 / $0.003. Optional, standardmäßig aus: ein Keyword mit KI-Suchvolumen (wie oft es in KI-Assistenten vorkommt, mit Monatsverlauf). Nur berechnet, wenn „KI-Suchvolumen einbeziehen“ an ist und ein Volumen gefunden wird.
- **Actor Start**: $0.021 / $0.021 / $0.021 / $0.021. Charged when the Actor starts running. Number of events charged depends on Actor memory (one event per GB, minimum one event).
