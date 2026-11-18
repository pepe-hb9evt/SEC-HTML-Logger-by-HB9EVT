# SEC-HTML-Logger

Browserbasiertes Log-Programm für den Swiss Emergency Contest (SEC) der USKA.

<br>

## Alpha-Version - Software in Entwicklung

Dieses Log-Programm ist aktuell in Entwicklung und liegt erst in einer Alpha-Version vor, die noch eingehend intern getestet wird. Deine Rückmeldungen sind herzlich willkommen, wenn hoffentlich in Kürze die Beta-Testphase eröffnet wird.

<br>

## Schnellstart

1. `SEC-Logger-by-HB9EVT.html` in Google Chrome öffnen (Doppelklick, keine Installation nötig).
2. Unter „Station“ das eigene Rufzeichen (MyCall) und die eigene Postleitzahl (MyZip) erfassen.
3. Über der Eingabemaske die Sicherungsdatei wählen, am besten auf einem USB-Stick (Pflicht).
4. Unter „Log“ die QSOs erfassen.
5. Nach dem Contest unter „Administration“ das Contest-Log als CSV-Datei exportieren.

Die Bedienung ist in `DOCUMENTATION_deutsch_german.md` beschrieben.

<br>

## Dokumentation

Für alle Details konsultiere die Datei `DOCUMENTATION_deutsch_german.md`.

<br>

## Spec-Driven Development with an AI

Dieses Projekt wird nach dem Prinzip „Spec-Driven Development“ (spezifikationsgetriebene Entwicklung) mit einer AI erstellt:

Zuerst wird in einer verbindlichen Spezifikation festgelegt, was das Programm können muss (siehe `design/Funktionsbeschreibung.md`). Darauf aufbauend werden technische Rahmenbedingungen festgelegt (siehe `design/Technische-Umsetzung.md`). Gestützt darauf wird anschliessend die AI beauftragt, den Programmcode zu schreiben.

Jede Spezifikation in den oben genannten Dokumenten trägt eine Nummer. Jede umgesetzte Funktion verweist im Code auf eine solche Anforderungsnummer, sodass sich jede Codestelle auf die Spezifikation zurückführen lässt.

Grundlegende Arbeitsregeln für die AI sind im Dokument `CLAUDE.md` geregelt.

<br>

## Ordnerstruktur

```
SEC-HTML-Logger/
├── SEC-Logger-by-HB9EVT.html        # Das Programm (eine einzige Datei)
├── CLAUDE.md                        # Regeln für Claude
├── README_deutsch_german.md         # Diese Datei
├── README.md                        # Englische Übersetzung dieser Datei
├── DOCUMENTATION_deutsch_german.md  # Ausführliche Dokumentation
├── DOCUMENTATION.md                 # Englische Übersetzung der Dokumentation
├── CHANGELOG_deutsch_german.md      # Änderungsprotokoll. Nicht im Repository
├── LICENSE                          # Lizenz (MIT) und Fremdmaterial
├── .gitignore                       # Allow-List der Dateien im Repository
├── .gitattributes                   # Git-Einstellungen (Zeilenenden)
├── SEC-HTML-Logger-Testdaten-3000-QSOs.json  # Sicherungsdatei mit 3000 Test-QSOs. Nicht im Repository
├── data/                            # Referenzdaten für die App (nicht verändern)
│   ├── README.md
│   ├── sec-zip-list.csv             # Postleitzahlen CH/FL mit LV95-Koordinaten (abgeleitet)
│   ├── SEC2026_Relais-Liste.csv     # Relais-Liste SEC 2026
│   ├── SEC2026_Relais-Liste.md      # Relais-Liste als Markdown-Tabelle
│   └── raw/                         # Unveränderte Quelldaten
│       ├── ortschaftenverzeichnis_plz_2056.csv.zip
│       ├── ortschaftenverzeichnis_plz_4326.csv.zip
│       └── SEC2026_relais-liste als video.mpg  # Nicht im Repository
├── design/                          # Eigene Spezifikationen
│   ├── Funktionsbeschreibung.md     # Funktionsbeschreibung mit Nummern Dnnn
│   └── Technische-Umsetzung.md      # Technische Umsetzung mit Nummern Tnnn
├── docs/
│   └── reference/                   # Externe Dokumente (Dritte, nur lesen)
│       ├── README.md
│       ├── Reglement-SEC-2026-DE.pdf
│       └── SEC26-Manual-de_V0003.pdf  # Nicht im Repository
└── tests/                           # Tests der Programmlogik (Node.js). Nicht im Repository
    ├── test-logic.js
    └── reference/                   # Referenzdateien mit fiktiven Testdaten
```

<br>

## Lizenz

Der eigene Programmcode und die eigenen Dokumente stehen unter der MIT-Lizenz (siehe `LICENSE`).

Fremdmaterial ist davon ausgenommen und steht unter den Bedingungen der jeweiligen Rechteinhaber (Abschnitt „Third-party material“ in `LICENSE`):

- Postleitzahl-Daten in `data/`: Open Government Data von swisstopo (Schweizer Bundesamt für Landestopografie), freie Nutzung mit Quellenangabe (© swisstopo).
- Relais-Liste SEC 2026 in `data/`: Rechte noch nicht geklärt.
- Dokumente in `docs/reference/`: Urheberrecht der jeweiligen Rechteinhaber.

<br>

## **Autor**

Pepe HB9EVT, https://github.com/pepe-hb9evt<br>
mit Unterstützung durch die KI Claude von Anthropic<br>(vgl. Kapitel "Spec-Driven Development with an AI").
