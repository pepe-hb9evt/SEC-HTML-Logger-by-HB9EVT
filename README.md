# SEC-HTML-Logger

Browser-based log program for the Swiss Emergency Contest (SEC) of the USKA.

<br>

## Quick start

The program is under development. There is no working version yet.
Details about the project are in `DOCUMENTATION.md`.

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
├── CLAUDE.md                        # Rules for Claude
├── README_deutsch_german.md         # German original of this file
├── README.md                        # This file (English translation)
├── DOCUMENTATION_deutsch_german.md  # Detailed documentation
├── DOCUMENTATION.md                 # English translation of the documentation
├── CHANGELOG_deutsch_german.md      # Changelog
├── LICENSE                          # License (MIT) and third-party material
├── .gitignore                       # Allow-list of the files in the repository
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
└── docs/
    └── reference/                   # External documents (third-party, read-only)
        ├── README.md
        ├── Reglement-SEC-2026-DE.pdf
        └── SEC26-Manual-de_V0003.pdf  # Not in the repository
```

<br>

## License

The own program code and the own documents are licensed under the MIT License (see `LICENSE`).

Third-party material is excluded from this and remains under the terms of the respective rights holders (section "Third-party material" in `LICENSE`):

- Postal code data in `data/`: Open Government Data from swisstopo, free use with source attribution (© swisstopo).
- Relay list SEC 2026 in `data/`: rights not yet clarified.
- Documents in `docs/reference/`: copyright of the respective rights holders.

<br>

## **Author**

Pepe HB9EVT, https://github.com/pepe-hb9evt
with support from the AI Claude by Anthropic<br>(see chapter "Spec-Driven Development with an AI").
