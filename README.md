# SEC-HTML-Logger

Browser-based log program for the Swiss Emergency Contest (SEC) of the USKA.

<br>

## Alpha version - software under development

This log program is currently under development and is only available as an alpha version, which is still being tested thoroughly internally. Your feedback is very welcome once the beta test phase opens, hopefully soon.

<br>

## Quick start

1. Open `SEC-Logger-by-HB9EVT.html` in Google Chrome (double-click, no installation needed).
2. Under "Station", enter your own call sign (MyCall) and your own postal code (MyZip).
3. Above the entry form, choose the backup file, ideally on a USB stick (mandatory).
4. Log the QSOs under "Log".
5. After the contest, export the contest log as a CSV file under "Administration".

Operation is described in `DOCUMENTATION.md`.

<br>

## Documentation

For all details, see the file `DOCUMENTATION.md`.

<br>

## Spec-Driven Development with an AI

This project is built with an AI following the principle of "Spec-Driven Development":

First, a binding specification defines what the program must be able to do (see `design/Funktionsbeschreibung.md`). Building on this, the technical framework is defined (see `design/Technische-Umsetzung.md`). Based on both, the AI is then instructed to write the program code.

Every specification in the documents mentioned above has a number. Every implemented function refers to such a requirement number in the code, so that every part of the code can be traced back to the specification.

The basic working rules for the AI are laid down in the document `CLAUDE.md`.

<br>

## Folder structure

```
SEC-HTML-Logger/
├── SEC-Logger-by-HB9EVT.html        # The program (one single file)
├── CLAUDE.md                        # Rules for Claude
├── README_deutsch_german.md         # German original of this file
├── README.md                        # This file (English translation)
├── DOCUMENTATION_deutsch_german.md  # Detailed documentation
├── DOCUMENTATION.md                 # English translation of the documentation
├── CHANGELOG_deutsch_german.md      # Changelog. Not in the repository
├── LICENSE                          # License (MIT) and third-party material
├── .gitignore                       # Allow-list of the files in the repository
├── .gitattributes                   # Git settings (line endings)
├── SEC-HTML-Logger-Testdaten-3000-QSOs.json  # Backup file with 3000 test QSOs. Not in the repository
├── data/                            # Reference data used by the app (do not modify)
│   ├── README.md
│   ├── sec-zip-list.csv             # Postal codes CH/FL with LV95 coordinates (derived)
│   ├── SEC2026_Relais-Liste.csv     # Relay list SEC 2026
│   ├── SEC2026_Relais-Liste.md      # Relay list as a Markdown table
│   └── raw/                         # Unmodified source data
│       ├── ortschaftenverzeichnis_plz_2056.csv.zip
│       ├── ortschaftenverzeichnis_plz_4326.csv.zip
│       └── SEC2026_relais-liste als video.mpg  # Not in the repository
├── design/                          # Own specifications
│   ├── Funktionsbeschreibung.md     # Functional specification with numbers Dnnn
│   └── Technische-Umsetzung.md      # Technical implementation with numbers Tnnn
├── docs/
│   └── reference/                   # External documents (third-party, read-only)
│       ├── README.md
│       ├── Reglement-SEC-2026-DE.pdf
│       └── SEC26-Manual-de_V0003.pdf  # Not in the repository
└── tests/                           # Tests of the program logic (Node.js). Not in the repository
    ├── test-logic.js
    └── reference/                   # Reference files with fictitious test data
```

<br>

## License

The own program code and the own documents are licensed under the MIT License (see `LICENSE`).

Third-party material is excluded from this and remains under the terms of the respective rights holders (section "Third-party material" in `LICENSE`):

- Postal code data in `data/`: Open Government Data from swisstopo (Swiss Federal Office of Topography), free use with source attribution (© swisstopo).
- Relay list SEC 2026 in `data/`: rights not yet clarified.
- Documents in `docs/reference/`: copyright of the respective rights holders.

<br>

## **Author**

Pepe HB9EVT, https://github.com/pepe-hb9evt<br>
with support from the AI Claude by Anthropic<br>(see chapter "Spec-Driven Development with an AI").
