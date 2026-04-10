# 🚰 Wasserschieber Kartierung

Eine mobile Web-App zur GPS-basierten Kartierung von Wasserschiebern bei Haushalten. Läuft direkt im Browser – keine Installation nötig.

## Features

- **GPS-Erfassung** mit kontinuierlicher Messung und gewichtetem Mittelwert für höhere Genauigkeit
- **Zielgenauigkeit** wählbar: ±10m / ±5m / ±3m / ±1m – App stoppt automatisch wenn Ziel erreicht
- **Live-Fortschrittsanzeige** mit Genauigkeit, Anzahl Samples und Mittelwert
- **Adress-Suche** via OpenStreetMap (Nominatim) – Adresse wird automatisch aus GPS befüllt
- **Kartenansicht** mit allen erfassten Schiebern (OpenStreetMap / Leaflet)
- **CSV-Export** mit Semikolon-Trennzeichen, UTF-8 BOM (direkt in Excel öffenbar)
- **Lokale Speicherung** im Browser (localStorage) – funktioniert auch offline
- **Smartphone-optimiert** mit Touch-Unterstützung und „Zum Homescreen hinzufügen"

## Verwendung

### Im Browser öffnen

Die App ist unter folgender URL erreichbar:

```
https://<benutzername>.github.io/<repository>/
```

### Wasserschieber erfassen

1. **Erfassen-Tab** öffnen
2. Zielgenauigkeit wählen (empfohlen: ±3m oder ±5m)
3. **„Messung starten"** tippen → Standorterlaubnis erteilen
4. Warten bis Zielgenauigkeit erreicht ist (grüne Anzeige) – App stoppt automatisch
5. Adresse wird automatisch befüllt, bei Bedarf anpassen
6. Optional eine Notiz eingeben (z.B. Tiefe, Deckelbeschaffenheit)
7. **„Schieber speichern"** tippen

### Karte anzeigen

Im **Karte-Tab** sind alle erfassten Schieber als Pins sichtbar. Tippen auf einen Pin zeigt Adresse, Datum und Notiz.

### Daten exportieren

Im **Liste-Tab**:
- **⬇ CSV exportieren** – lädt `wasserschieber_DATUM.csv` herunter
- **📋 Kopieren** – CSV-Inhalt in die Zwischenablage

Das CSV enthält folgende Spalten:

| Spalte | Beschreibung |
|---|---|
| ID | Zeitstempel der Erfassung |
| Adresse | Adresse oder Bezeichnung |
| Breitengrad | Latitude (8 Dezimalstellen) |
| Längengrad | Longitude (8 Dezimalstellen) |
| Genauigkeit_m | GPS-Genauigkeit in Metern |
| Anzahl_Samples | Anzahl der gemittelten GPS-Messungen |
| Notiz | Optionale Notiz |
| Erfasst_am | Datum und Uhrzeit (österreichisches Format) |
| ISO_Zeitstempel | Datum und Uhrzeit im ISO-8601-Format |

### Als App am Homescreen speichern

**Android (Chrome):** Menü → „Zum Startbildschirm hinzufügen"

**iPhone (Safari):** Teilen-Symbol → „Zum Home-Bildschirm"

## Genauigkeit

Die erreichbare GPS-Genauigkeit hängt vom Gerät und den Umgebungsbedingungen ab:

| Bedingung | Erreichbare Genauigkeit |
|---|---|
| Einzelmessung | ±15–30m |
| Nach 10–20 Sek. | ±5–10m |
| Mittelwert 30 Sek. | ±3–5m |
| Mittelwert 2–3 Min. | ±1–3m |
| Freier Himmel, modernes Gerät | ±1–2m |

**Tipps für beste Genauigkeit:**
- Smartphone ruhig halten (nicht schwingen)
- Im Freien messen, nicht unter Vordächern oder neben hohen Gebäuden
- Kurz warten bis das GPS-Signal stabil ist bevor die Messung gestartet wird

## Datenspeicherung

Alle Daten werden lokal im Browser gespeichert (`localStorage`). Die Daten bleiben beim Schließen des Browsers erhalten, sind aber **gerätegebunden** – ein Export per CSV wird empfohlen um Daten zu sichern oder zu übertragen.

## Technologie

- **Leaflet.js** – Kartendarstellung
- **OpenStreetMap** – Kartenmaterial
- **Nominatim** – Geocoding (Koordinaten ↔ Adresse)
- **Web Geolocation API** – GPS-Zugriff
- Kein Framework, kein Build-Prozess – eine einzelne HTML-Datei

## Lizenz

Zur freien Verwendung für interne Zwecke.
