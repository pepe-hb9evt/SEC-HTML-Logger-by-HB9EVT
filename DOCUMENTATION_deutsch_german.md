# SEC-HTML-Logger - Dokumentation

<br>

## Zweck

Der SEC-HTML-Logger ist ein Logprogramm für den Swiss Emergency Contest (SEC) der USKA.
Es läuft im Browser, vollständig offline, und soll das Windows-Logprogramm der USKA ersetzen.
Es erfasst die Funkverbindungen (QSOs), prüft Doppelverbindungen, berechnet die theoretisch möglichen Punkte und
exportiert das Log für die Einreichung.

<br>

## Spezifikation

Alle Funktionen sind in `design/Funktionsbeschreibung.md` beschrieben. Jede Bestimmung hat
eine eindeutige Nummer `Dnnn`. Der Programmcode verweist in Kommentaren auf diese Nummern.

Die offenen Punkte stehen in Kapitel 17 „Offene Punkte“ der Funktionsbeschreibung (Nummern `D9nn`).

<br>

## Technik

- Reines HTML, CSS und JavaScript, ohne Build-Schritt und ohne Bibliotheken.
- Läuft offline direkt aus dem Dateisystem (`file://`) in einer aktuellen Version von Chrome.
- In der Entwicklungsphase ist die Oberfläche englisch. Später wird das Programm mehrsprachig
  (Deutsch, Französisch, Italienisch, Englisch). Alle Texte der Oberfläche liegen darum an
  einer zentralen Stelle.

<br>

## Daten

Die Postleitzahlen der Schweiz und Liechtensteins mit Koordinaten liegen in
`data/sec-zip-list.csv`. Aufbau, Quelle und Lizenz sind in `data/README.md` beschrieben.
Die Dateien im Ordner `data/` werden nicht verändert.

<br>

## Referenzdokumente

Die externen Dokumente liegen in `docs/reference/` und sind dort in `README.md` aufgeführt:

- `Reglement-SEC-2026-DE.pdf` - offizielles Reglement SEC 2026 der USKA.
- `SEC26-Manual-de_V0003.pdf` - Handbuch des Windows-Logprogramms. Nur lokal, nicht im Repository.

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
mit Unterstützung durch die KI Claude von Anthropic<br>(vgl. Kapitel "Spec-Driven Development with an AI" im README).
