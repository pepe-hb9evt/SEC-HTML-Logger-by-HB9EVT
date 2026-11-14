# SEC-HTML-Logger - Documentation

<br>

## Purpose

The SEC-HTML-Logger is a log program for the Swiss Emergency Contest (SEC) of the USKA.
It runs in the browser, fully offline, and is meant to replace the Windows log program of the USKA.
It records the radio contacts (QSOs), checks for duplicate contacts, calculates the theoretically possible points and
exports the log for submission.

<br>

## Specification

All functions are described in `design/Funktionsbeschreibung.md`. Each requirement has
a unique number `Dnnn`. The program code refers to these numbers in comments.

The open points are listed in chapter 17 "Offene Punkte" of the functional specification (numbers `D9nn`).

<br>

## Technology

- Plain HTML, CSS and JavaScript, without a build step and without libraries.
- Runs offline directly from the file system (`file://`) in a current version of Chrome.
- During the development phase the user interface is in English. Later the program will be
  multilingual (German, French, Italian, English). All user interface texts are therefore kept
  in one central place.

<br>

## Data

The postal codes of Switzerland and Liechtenstein with coordinates are in
`data/sec-zip-list.csv`. Structure, source and license are described in `data/README.md`.
The files in the folder `data/` are not modified.

<br>

## Reference documents

The external documents are in `docs/reference/` and are listed there in `README.md`:

- `Reglement-SEC-2026-DE.pdf` - official contest rules SEC 2026 of the USKA.
- `SEC26-Manual-de_V0003.pdf` - manual of the Windows log program. Local only, not in the repository.

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
with support from the AI Claude by Anthropic<br>(see chapter "Spec-Driven Development with an AI" in the README).
