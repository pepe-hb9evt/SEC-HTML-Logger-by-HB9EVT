# SEC-HTML-Logger

Browserbasiertes Logprogramm für den Swiss Emergency Contest (SEC) der USKA.

<br>

## Schnellstart

Das Programm ist in Entwicklung. Es gibt noch keine lauffähige Version.
Details zum Projekt stehen in `DOCUMENTATION_deutsch_german.md`.

Die Spezifikation (vgl. nachfolgendes Kapitel) der geplanten App umfasst 193 Positionen:

- 22 Projektregeln (siehe `CLAUDE.md`)
- 150 Positionen zur Funktionalität (siehe `design/Funktionsbeschreibung.md`)
- 21 Positionen bei den technischen Vorgaben (siehe `design/Technische-Umsetzung.md`).

Gestützt darauf wird die App nun programmiert.

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
├── CLAUDE.md                        # Regeln für Claude
├── README_deutsch_german.md         # Diese Datei
├── README.md                        # Englische Übersetzung dieser Datei
├── DOCUMENTATION_deutsch_german.md  # Ausführliche Dokumentation
├── DOCUMENTATION.md                 # Englische Übersetzung der Dokumentation
├── CHANGELOG_deutsch_german.md      # Änderungsprotokoll
├── LICENSE                          # Lizenz (MIT) und Fremdmaterial
├── .gitignore                       # Allow-List der Dateien im Repository
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
└── docs/
    └── reference/                   # Externe Dokumente (Dritte, nur lesen)
        ├── README.md
        ├── Reglement-SEC-2026-DE.pdf
        └── SEC26-Manual-de_V0003.pdf  # Nicht im Repository
```

<br>

## Lizenz

Der eigene Programmcode und die eigenen Dokumente stehen unter der MIT-Lizenz (siehe `LICENSE`).

Fremdmaterial ist davon ausgenommen und steht unter den Bedingungen der jeweiligen Rechteinhaber (Abschnitt „Third-party material“ in `LICENSE`):

- Postleitzahl-Daten in `data/`: Open Government Data von swisstopo, freie Nutzung mit Quellenangabe (© swisstopo).
- Relais-Liste SEC 2026 in `data/`: Rechte noch nicht geklärt.
- Dokumente in `docs/reference/`: Urheberrecht der jeweiligen Rechteinhaber.

<br>

## **Autor**

Pepe HB9EVT, https://github.com/pepe-hb9evt
mit Unterstützung durch die KI Claude von Anthropic<br>(vgl. Kapitel "Spec-Driven Development with an AI").
