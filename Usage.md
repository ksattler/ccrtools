# Checklisten in CCRtools — Benutzerhandbuch

CCRtools verwaltet Tauch-Checklisten als JSON-Dateien. Jede Checkliste besteht aus **Abschnitten** (z. B. „Computer", „Scrubber"), die jeweils beliebig viele **Einträge** enthalten. Einträge können drei verschiedene Typen haben:

| Typ | Beschreibung |
|-----|-------------|
| **Check** | Einfaches Häkchen — antippen zum Abhaken |
| **Wert (Value)** | Texteingabe für Messwerte (z. B. Millivolt-Werte der O₂-Zellen) |
| **Timer** | Countdown-Timer für zeitkritische Schritte (z. B. Negativtest) |

---

## Checklisten-Bibliothek

Der Tab **Checklist** zeigt alle gespeicherten Checklisten. Beim ersten Start kopiert die App die mitgelieferte KISS Sidewinder Pre-Dive Checkliste automatisch in den Dokumentenordner.

### Checkliste starten

Checkliste in der Liste antippen — sie öffnet sich auf dem ersten Abschnitt. Abschnitte werden nacheinander durchgearbeitet; am Ende erscheint eine **Zusammenfassung** mit dem Erfüllungsgrad jedes Abschnitts (grün = vollständig, rot = unvollständig). Von der Zusammenfassung aus kann jeder Abschnitt nochmals aufgerufen werden.

### Sprachausgabe (TTS)

In der aktiven Checkliste erscheint oben rechts ein Lautsprecher-Symbol. Bei aktivierter Sprachausgabe liest die App jeden Eintrag vor und springt nach dem Abhaken automatisch zum nächsten. Die Sprache richtet sich nach dem in den Info-Metadaten hinterlegten Sprachcode der Checkliste.

---

## Checkliste erstellen

1. Toolbar-Schaltfläche **+** (oben rechts) antippen.
2. Namen eingeben und mit **OK** bestätigen — die leere Checkliste erscheint sofort in der Bibliothek.
3. Checkliste nach links wischen → **Edit** antippen, um Abschnitte und Einträge hinzuzufügen (siehe [Checkliste bearbeiten](#checkliste-bearbeiten)).

Namen müssen eindeutig sein; leere Namen werden abgelehnt.

---

## Checkliste bearbeiten

Checkliste in der Bibliothek nach links wischen → **Edit** antippen. Der Editor zeigt die hierarchische Struktur (Checkliste → Abschnitte → Einträge).

### Bearbeitungsmodus aktivieren

Oben links auf **Edit** tippen, um den Bearbeitungsmodus zu aktivieren. Damit können Abschnitte und Einträge per Drag-and-drop umsortiert werden.

### Abschnitt hinzufügen

**+**-Schaltfläche (oben rechts) antippen → Typ **Section** wählen → Titel eingeben → zurücknavigieren. Der Abschnitt wird am Ende der Checkliste eingefügt.

### Eintrag hinzufügen

**+**-Schaltfläche antippen → Typ **Item** wählen → Felder ausfüllen:

- **Description**: Text des Eintrags
- **Type**: Check / Value / Timer
  - Bei **Value**: Sensor-Spalte auswählen (Ambient 1–5, Oxygen 1–5, Scrubber, Battery 1–2) — dies verknüpft den Eintrag mit dem O₂-Sensor-Log
  - Bei **Timer**: Dauer in Minuten (1–10 min) festlegen

Der neue Eintrag wird dem zuletzt ausgewählten Abschnitt hinzugefügt.

### Eintrag oder Abschnitt bearbeiten

Zeile nach links wischen → **Edit** antippen. Typ und Beschreibung können geändert werden. Beim Zurücknavigieren werden die Änderungen gespeichert.

### Eintrag verschieben (in anderen Abschnitt)

Zeile nach rechts wischen → **Move** antippen → Zielabschnitt auswählen. Die Schaltfläche erscheint nur, wenn mindestens zwei Abschnitte vorhanden sind.

### Eintrag oder Abschnitt löschen

Zeile nach links wischen → **Delete** antippen → Sicherheitsabfrage bestätigen. Das Löschen eines Abschnitts entfernt alle darin enthaltenen Einträge.

### Checkliste umbenennen

Im Editor die oberste Zeile (mit dem Haus-Symbol und dem Namen) nach links wischen → **Rename** antippen → neuen Namen eingeben → **Save**. Namen müssen eindeutig sein.

### Abschnitt umbenennen

Abschnittszeile nach links wischen → **Rename** antippen → neuen Namen eingeben → **Save**.

---

## Metadaten bearbeiten

Checkliste in der Bibliothek nach links wischen → **Info** antippen. Dort können folgende Felder gepflegt werden:

| Feld | Bedeutung |
|------|-----------|
| **Author** | Ersteller der Checkliste |
| **Version** | Versionsnummer (freie Texteingabe) |
| **Description** | Kurzbeschreibung |
| **Language** | Sprache für die Sprachausgabe (Deutsch / English) |

Beim Zurücknavigieren werden die Metadaten automatisch gespeichert.

---

## Checkliste importieren

Checklisten werden als `.json`-Dateien ausgetauscht. Es gibt zwei Import-Wege:

### Aus einer Datei (lokal / AirDrop / Files-App)

Toolbar-Schaltfläche **Importieren** (Pfeil-mit-Häkchen-Symbol, oben links) antippen → JSON-Datei auswählen. Bei Namenskollision wird automatisch ein eindeutiger Name vergeben (z. B. „Meine Liste (2)").

### Aus dem Internet herunterladen

Toolbar-Schaltfläche **Download** (iCloud-Symbol, oben links) antippen → verfügbare Checklisten auswählen → **Download**. Die Checklisten werden direkt in die Bibliothek importiert.

---

## Checkliste exportieren / teilen

Checkliste in der Bibliothek nach **rechts** wischen → Teilen-Symbol antippen. Die Checkliste wird als `.json`-Datei über das iOS-Teilen-Menü weitergegeben (AirDrop, Mail, Dateien usw.).

---

## Checkliste löschen

Checkliste nach links wischen → **Delete** antippen → Sicherheitsabfrage bestätigen. Die Löschung ist endgültig.

---

## Sensor Logging

Der Tab **Sensor Log** zeigt eine chronologische Tabelle der O₂-Sensor-Messwerte, die beim Abschluss einer Checkliste automatisch gespeichert werden.

### Wann wird eine Messung gespeichert?

Ein Checklist-Eintrag trägt nur dann zum Sensor-Log bei, wenn er **beide** folgenden Bedingungen erfüllt:

1. Der Typ des Eintrags ist **Value** (Texteingabe).
2. Der Eintrag ist mit einer **Sensor-Spalte** verknüpft — also einem der folgenden Werte:
   `Ambient 1`–`Ambient 5`, `Oxygen 1`–`Oxygen 5`, `Scrubber`, `Battery 1`–`Battery 2`.

Einträge vom Typ **Check** oder **Timer** sowie Value-Einträge ohne Sensor-Zuweisung werden **nicht** geloggt. Beim Speichern der Checkliste wird aus allen verknüpften Value-Einträgen genau eine `SensorReading`-Zeile erzeugt.

### Ambient vs. Oxygen — Bedeutung der Spalten

| Spaltengruppe | Messvorgang | Beschreibung |
|---------------|-------------|--------------|
| **Ambient 1–5** | Sensor in Umgebungsluft (21 % O₂) | mV-Wert des Sensors an der Luft vor dem Tauchgang |
| **Oxygen 1–5** | Sensor in reinem O₂ (100 %) | mV-Wert des Sensors im O₂-Flush |
| **Scrubber** | Restlaufzeit Scrubber | verbleibende Scrubber-Zeit in Minuten |
| **Battery 1–2** | Akkuspannung | Spannung der Steuereinheit in Volt |

Die Nummerierung 1–5 entspricht den physischen Sensoren des Geräts. Für die Linearitätsauswertung muss derselbe Sensor-Index sowohl mit einem `Ambient`- als auch einem `Oxygen`-Eintrag erfasst werden.

### Linearitätsberechnung

Die Linearität eines Sensors gibt an, wie linear er auf unterschiedliche O₂-Partialdrücke anspricht. Sie wird aus dem Quotienten des Oxygen-mV-Werts und des erwarteten Oxygen-mV-Werts (hochgerechnet aus dem Ambient-Wert) berechnet:

```
Linearität (%) = (Oxygen-mV / (Ambient-mV × 4,77)) × 100
```

Der Faktor **4,77** ergibt sich aus dem theoretischen Verhältnis von reinem Sauerstoff (100 % O₂) zu Umgebungsluft (21 % O₂): 100 ÷ 21 ≈ 4,77. Ein perfekt linearer Sensor liefert 100 %. Abweichungen deuten auf Alterung oder Fehlfunktion hin.

Die Linearität wird nur berechnet, wenn für denselben Sensor-Index **sowohl** ein Ambient- als auch ein Oxygen-Wert vorliegen. Fehlt einer der beiden Werte, bleibt die Spalte leer.

### Sensor-Log-Ansicht

- **Tabelle**: Datum und Linearität (%) je Sensor, sortiert nach Datum (neueste zuerst).
- **Sensor tauschen** (Pfeil-Symbol je Sensor): Erfasst einen Sensor-Wechsel ohne Messwerte — die Zeile erscheint mit dem Eintrag „Change".
- **Diagramm** (Linien-Symbol oben rechts): Zeigt den Linearitätsverlauf aller Sensoren über die Zeit.
- **CSV-Export** (Teilen-Symbol oben links): Exportiert alle Einträge als `.csv`-Datei mit Datum, Ambient-mV, Oxygen-mV, Linearität, Akkustand, Scrubber-Restzeit und Sensor-Wechsel-Kennzeichen.

---

## JSON-Format (für manuelle Erstellung)

Checklisten können auch mit einem Texteditor erstellt und anschließend importiert werden. Minimales Beispiel:

```json
{
  "name": "Meine Checkliste",
  "info": {
    "author": "Max Mustermann",
    "version": "1.0",
    "description": "Beispiel-Checkliste",
    "language": "de"
  },
  "sections": [
    {
      "id": 1,
      "name": "Computer",
      "items": [
        { "id": 11, "text": "Akkuspannung prüfen (> 1,3 V)", "type": "check" },
        { "id": 12, "text": "Zelle 1 (mV Ambient)", "type": "value" },
        { "id": 13, "text": "Negativtest", "type": "timer", "time": 300 }
      ]
    }
  ]
}
```

**Wichtige Regeln:**
- `name` muss eindeutig sein und dem Dateinamen (ohne `.json`) entsprechen.
- Alle `id`-Werte müssen innerhalb der gesamten Checkliste eindeutig sein.
- `time` wird in Sekunden angegeben (300 = 5 Minuten).
- Das Feld `language` akzeptiert `"de"` oder `"en"`.

### Sensor-Logging verknüpfen

Um einen Value-Eintrag mit dem O₂-Sensor-Log zu verbinden, muss ein `logging`-Array auf Checklisten-Ebene ergänzt werden:

```json
"logging": [
  { "column": "Ambient 1", "value": { "section": 1, "item": 12 } },
  { "column": "Oxygen 1",  "value": { "section": 1, "item": 14 } },
  { "column": "Scrubber",  "value": { "section": 2, "item": 21 } }
]
```

Gültige Spaltennamen: `Ambient 1`–`Ambient 5`, `Oxygen 1`–`Oxygen 5`, `Scrubber`, `Battery 1`–`Battery 2`. Nach Abschluss der Checkliste wird aus diesen Werten automatisch eine Sensor-Ablesung im Tab **Sensor Log** gespeichert.
