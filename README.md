# Praxisbesuchs-Planer – Version 2

Deutschsprachige, responsive Web-App für den Dental-Außendienst. Sie läuft vollständig im Browser und kann über GitHub Pages auf iPad und iPhone wie eine App installiert werden.

## Funktionen

- Praxen und Apotheken anlegen, bearbeiten und löschen
- Excel-Dateien (`.xlsx`, `.xls`, `.csv`) importieren
- Automatische Zuordnung der Spalten aus der Kundendatei, unter anderem Firma, Kundennummer, Straße, Hausnummer, PLZ, Ort, Telefon und E-Mail
- Dublettenerkennung über Kundennummer beziehungsweise Name und Adresse
- Suche und Filter nach Status, Ort und Wiedervorlagedatum
- Google-Maps-Route und Websuche je Kunde
- Gesprächsnotizen, Ansprechpartner, Interessen und Besuchsdaten
- Lokale Datenspeicherung und JSON-Datensicherung
- PWA-Unterstützung für die Installation auf dem Home-Bildschirm

## Start

Für einen schnellen lokalen Test kann `index.html` geöffnet werden. Zuverlässiger ist ein lokaler Webserver:

```bash
python3 -m http.server 8000
```

Danach im Browser `http://localhost:8000` öffnen.

## GitHub Pages

1. Dateien in ein GitHub-Repository hochladen.
2. `Settings` → `Pages` öffnen.
3. `Deploy from a branch`, Branch `main`, Ordner `/root` wählen.
4. Die erzeugte GitHub-Pages-Adresse in Safari öffnen.
5. Teilen → `Zum Home-Bildschirm` → hinzufügen.

## Excel-Import

Die Datei wird ausschließlich im Browser verarbeitet. Sie wird nicht an einen Server hochgeladen. Bestehende Datensätze werden nicht automatisch überschrieben. Mögliche Dubletten werden beim Import übersprungen.

Hinweis: Für das Lesen von Excel-Dateien wird SheetJS über ein CDN geladen. Beim ersten Excel-Import ist deshalb eine Internetverbindung notwendig. Die übrige App kann nach dem ersten Laden über den Service Worker weitgehend offline genutzt werden.

## Datenschutz und technische Grenzen

Die Daten liegen in `localStorage` des jeweiligen Browsers. Sie werden nicht zwischen Geräten synchronisiert. Beim Löschen der Safari-Websitedaten können sie verloren gehen. Deshalb regelmäßig über „Sicherung exportieren“ eine JSON-Sicherung erstellen.

Für eine spätere produktive Mehrgeräte-Lösung empfiehlt sich eine EU-gehostete Datenbank mit Anmeldung, rollenbasiertem Zugriff und verschlüsselter Übertragung.

## Prüfung

- JavaScript-Syntaxprüfung mit Node.js
- Prüfung aller referenzierten lokalen Dateien
- Responsives Layout für Smartphone, iPad und Desktop
- Importlogik für die vorhandenen deutschen Excel-Spalten
