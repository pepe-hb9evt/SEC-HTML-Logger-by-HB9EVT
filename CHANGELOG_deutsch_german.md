# Änderungsprotokoll

zu Projekt SEC-HTML-Logger

<br>

## 2026-11-10

- CLAUDE.md, C01: Nummerierung der technischen Spezifikation von `P001` auf `T001` korrigiert (passend zu P05).
- CLAUDE.md, C02: Tippfehler "specificatons" korrigiert.
- CLAUDE.md, C05A: neue Regel, der Benutzer wird geduzt.
- CLAUDE.md: Leerzeichen am Zeilenende nach `<br>` entfernt (C23).

<br>

## 2026-11-13

- design/Funktionsbeschreibung.md: ergänzt um Versionierung, Vermerk (Wunsch), Programmdatei, Sprachregelung (Verweis auf CLAUDE.md), Aufbau der Hauptansicht, Statuszeile, Spalten des Logs inkl. ZIP Send, Startzustand, Import nur von Sicherungsdateien (Ersetzen/Ergänzen), Format der Sicherungsdatei, Warnung beim Verlassen, zweiter Tab, Bereinigung der Eingabe, Unterscheidung Fehler/Warnung, Meldungsbereich ohne Pop-ups.
- design/Funktionsbeschreibung.md: neue Kapitel 15 „Einbindung ins Projekt“ und 16 „Test“; Kapitel 11 heisst neu „Prüfungen und Warnmeldungen“; Offene Punkte (jetzt Kapitel 17) um D902 und D903 ergänzt.
- design/Funktionsbeschreibung.md: alle Bestimmungen in der bestehenden Reihenfolge neu nummeriert (D001–D147, C03); doppelte Nummern und Platzhalter (`D0`, `D1`, leer) behoben; Verweis in der Bestimmung zu Notfunkgruppen korrigiert (Stationsnummer statt MyCall).
- design/Technische-Umsetzung.md: Verweise auf die neue Nummerierung angepasst, falsche Verweise in T015 und T016 korrigiert.
- data/sec-zip-list.csv: neu erzeugt aus `ortschaftenverzeichnis_plz_2056.csv.zip` (PLZ, Ortschaft, LV95-Koordinaten E/N, 4073 Zeilen).
- data/README.md: bereinigt, vervollständigt und ins Englische übersetzt (Inhalt, Postleitzahlliste, Herleitung, Distanzberechnung, Relais-Liste, Quelle und Lizenz).
- README_deutsch_german.md: Ordnerstruktur von `data/` nachgeführt.
- CLAUDE.md, C13: präzisiert, die Regel gilt nur für die Dokumentpaare README und DOCUMENTATION im Projektordner.
- design/Funktionsbeschreibung.md, D077: Berechnung der QRB festgelegt (LV95, Pythagoras, gerundet auf 0.1 km); offener Punkt D903 entfernt.

<br>

## 2026-11-14

- CLAUDE.md: Verweise korrigiert (P12 auf P10, P20 auf C18, Beispiel in P17 auf D111), Überschrift „Specification“ und Leerzeichen-Fehler in C02 und „App language“ bereinigt.
- design/Funktionsbeschreibung.md: neu durchnummeriert (D001–D145), Querverweise auf D-, C- und P-Nummern geprüft und korrigiert (u. a. D026, D105, D141), Fettschrift entfernt, Feldnamen in Anführungszeichen gesetzt, sprachlich überarbeitet, leere Tabellenzeilen entfernt.
- data/README.md: Rundung der QRB auf 0.1 km (D078) eingetragen, D-Verweise nachgeführt, Video als nicht im Repository markiert.
- README_deutsch_german.md, README.md: Ordnerstruktur von `data/` nachgeführt, Baumzeichen bei `design/` korrigiert; im englischen README die nicht mehr vorhandene Datei `old_SEC26-Funktionsbeschreibung.md` entfernt.
- .gitignore: Allow-Liste für `data/` nachgeführt (2056-ZIP, Relais-Listen neu, `AMTOVZ_CSV_WGS84.csv` entfernt; Video nicht im Repository).
- design/Funktionsbeschreibung.md: Feldnamen vereinheitlicht ("Date", "Time", "Band", "Mode", "His Call"), Regel „1 Punkt pro gültigem QSO“ als D116A wieder aufgenommen, Manual-Bezeichnung in D903 auf V4 (2026-10-23) vereinheitlicht, D901 ohne Umlaut (`unbekannt gemaess D901`), D902 korrigiert (UPS = 1), leere Tabellenzeile entfernt.
- design/Funktionsbeschreibung.md: ab D116A neu durchnummeriert (D117–D146), Querverweise nachgeführt.
- README_deutsch_german.md: neues Kapitel „Spec-Driven Development“.
- LICENSE: neu, MIT-Lizenz für eigenes Material mit Abschnitt „Third-party material“ (swisstopo-Daten, Relais-Liste, Referenzdokumente).
- README_deutsch_german.md: neuer Abschnitt „Lizenz“, `LICENSE` in die Ordnerstruktur aufgenommen, fehlendes Leerzeichen vor `design/Technische-Umsetzung.md` ergänzt.
- design/Funktionsbeschreibung.md: neue Bestimmung D035A zur Quellenangabe von swisstopo in der Administrations-Ansicht.
- .gitignore: `LICENSE` in die Allow-Liste aufgenommen.
- README.md, DOCUMENTATION.md: vollständig neu aus den deutschen Fassungen übersetzt.
