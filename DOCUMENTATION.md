# Documentation

**for the SEC-HTML-Logger-by-HB9EVT**

<br>

## Alpha version - software under development

**Status November 2026**: This log program is currently under development and is only available as an alpha version, which is still being tested thoroughly internally. Your feedback is very welcome once the beta test phase opens, hopefully soon.

<br>

## Background and motivation

The *Swiss Emergency Contest* (SEC) of the USKA is an amateur radio and CB contest.

The SEC contest rules contain a few exotic provisions that cannot be handled by the well-known contest logging programs. The USKA therefore provides its own log program for the SEC.

At the SEC 2026, the program provided caused a lot of frustration because it only worked sluggishly. This gave the author the idea of writing a log program for the SEC himself, as a possible alternative in the coming years.

<br>

## Purpose

The *SEC-HTML-Logger* is a log program for the *Swiss Emergency Contest* (SEC) of the USKA, based on the contest rules of 2026. The goal is a lean, easy-to-use, fast and safe log program tailored to the SEC.

<br>

## Requirements

- This log program runs exclusively in a **Chrome browser**. Other browsers are not supported.
- No internet connection is needed. The log program runs fully offline.

<br>

## Technology

- Plain HTML, CSS and JavaScript, without a build step and without libraries.
- Runs offline directly from the file system (`file://`) in a current version of Chrome.

<br>

## Restrictions

In the alpha phase, the user interface is available in German and English. In view of the beta phase, French and Italian will be added. These are the four languages planned.

<br>

## Spec-Driven Development with an AI

This project is built with an AI following the principle of "Spec-Driven Development":

First, a binding specification defines what the program must be able to do (see `design/Funktionsbeschreibung.md`). Building on this, the technical framework is defined (see `design/Technische-Umsetzung.md`). Based on both, the AI is then instructed to write the program code.

Every specification in the documents mentioned above has a number. Every implemented function refers to such a requirement number in the code, so that every part of the code can be traced back to the specification.

The basic working rules for the AI are laid down in the document `CLAUDE.md`.

The points still open are listed in chapter 17 "Offene Punkte" of the functional specification (numbers `D9nn`).

<br>

## External data and documents

- The postal codes of Switzerland and Liechtenstein with coordinates are in `data/sec-zip-list.csv`. Structure, source and license are described in `data/README.md`.

- External documents are in `docs/reference/` and are listed there in `README.md`:

  - `Reglement-SEC-2026-DE.pdf` - official contest rules SEC 2026 of the USKA.

  - `SEC26-Manual-de_V0003.pdf` - manual of the Windows log program. Local only, not in the repository.

<br>

## Operation

The program consists of the single file `SEC-Logger-by-HB9EVT.html`. It is opened in Google Chrome and runs fully offline. Chrome stores the data in the browser storage (IndexedDB).

For safety, a backup file must also be created. You are asked to do this before the contest, or before the first QSO.

<br>

### Views

**Tab "Log"**

Entry form at the top, the log below it. Above it is the message area, at the bottom the status bar. The language can be switched at the top right.

**Tab "Station"**

In the "Station" tab you enter your own details before the contest, or before the first QSO. These are:

- Own call sign (MyCall). A suffix such as /P is only accepted for single stations.

- Postal code (MyZip) of your own location, which must be in Switzerland or Liechtenstein.
- Group operation yes/no and, if applicable, the station number for group operation

**Tab "Administration"**

Export, backup file, import, etc.

<br>

### Logging a QSO

- "Live Logging": the program sets date and time itself. "Post Logging": date and time are entered by hand (logging after the contest).
- "Repeat Last": "Band", "Mode" and "TRX Route" are taken over from the previous QSO.
- Enter jumps to the next field that still has to be filled in. When everything is entered, Enter jumps to "Save"; another Enter saves the QSO.
- "ZIP Rcvd": type the postal code or the town name and choose from the list.
- Errors (e.g. a missing field) prevent saving. Warnings (e.g. dupe) appear in the message area and the affected field gets a coloured frame; the QSO can still be saved.
- In the log, the column "!" shows warnings:
  - **P** = This call sign was not always logged with the same postal code.
  - **C** = This call sign was not always logged identically. Check the prefixes and suffixes logged for this call sign in some QSOs (e.g. "/P" or "HB9/").
  - **X** = other warning. Click on the "X" to see the warning message.
  - **D** = "Dupe" (duplicate contact). You already had a contact with this call sign on the same band and via the same route (direct or via the same relay). **Tip**: if you are unsure, leave this dupe QSO in the log. In the evaluation, the QSO that also appears in the other station's log is counted automatically. The other one is cancelled without penalty.

<br>

### Changing or deleting a QSO

A double-click on a row in the log loads the QSO into the entry form (yellow background, focus on "Band", warnings are shown again). "Save changes" saves, "Discard" or the Esc key discards the change, "Delete" deletes the QSO after a confirmation question. In this question "No" is preselected; Enter always triggers the button highlighted in blue.

<br>

### Backup, import and export

- The backup file is mandatory (see "Data safety"). It is chosen via the hint above the entry form or under "Administration". "Download backup copy" also saves a copy in the download folder.
- Only backup files of this program can be read in ("Import: replace" or "Import: merge"). Before each import the log is saved; "Undo last import" restores it.
- "Export contest log (CSV)" creates the file for submission. According to the contest rules, its name must not be changed. "Export ADIF" creates a file for your own station log.

<br>

### Data safety

Chrome stores the log in the browser storage (IndexedDB). For files opened directly from the hard disk, Chrome usually does not grant persistent storage. The log can therefore be lost if the hard disk becomes full or if the browser data is deleted. The backup file provides the protection:

- Without a backup file, no QSO can be logged. It is best kept on a different storage device than Chrome, e.g. on a USB stick.
- The program writes the backup file after every saving, changing and deleting of a QSO. The status bar shows the time and the number of QSOs of the last write.
- After a restart of Chrome, writing must be confirmed once with "Enable backup file".
- At start-up, the program compares the log in the browser with the backup file. If QSOs are missing in the browser, it offers to add them from the backup file.
- If the backup file cannot be written (e.g. USB stick removed), logging continues. The status bar shows the error in red; "Retry" writes the whole log again.

<br>

### Notes

- The program may only be open in one tab. A second tab can only read.
- In an incognito window, the data is lost when the window is closed.
- The postal code data (© swisstopo) and the relay list are contained as a copy in the program file. If the files in `data/` change, a new version of the HTML file must be created.

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
with support from the AI Claude by Anthropic<br>(see chapter "Spec-Driven Development with an AI" above).
