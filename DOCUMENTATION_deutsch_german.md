# Dokumentation

**zum SEC-HTML-Logger-by-HB9EVT**

<br>

## Alpha-Version - Software in Entwicklung

**Stand November 2026**: Dieses Log-Programm ist aktuell in Entwicklung und liegt erst in einer Alpha-Version vor, die noch eingehend intern getestet wird. Deine Rückmeldungen sind herzlich willkommen, wenn hoffentlich in Kürze die Beta-Testphase eröffnet wird.

<br>

## Ausgangslage und Motivation

Der *Swiss Emergency Contest* (SEC) der USKA ist ein Amateurfunk- und CB-Contest.

Der SEC hat in seinem Contest-Reglement ein paar exotische Bestimmungen, die mit den allgemein bekannten Contest-Logging-Programmen nicht abgebildet werden können. Daher stellt die USKA ein eigenes Log-Programm für den SEC zur Verfügung.

Beim SEC 2026 hat das zur Verfügung gestellte Programm für viel Unmut gesorgt, weil es nur harzig funktioniert hat. Das hat den Autor auf die Idee gebracht, selbst ein Log-Programm für den SEC zu programmieren, als mögliche Alternative in den kommenden Jahren.

<br>

## Zweck

Der *SEC-HTML-Logger* ist ein Log-Programm für den *Swiss Emergency Contest* (SEC) der USKA, gestützt auf das Contest-Reglement von 2026. Ziel ist ein schlankes, einfach bedienbares, schnelles und sicheres Log-Programm, das massgeschneidert für den SEC ist.

<br>

## Voraussetzungen

- Dieses Log-Programm läuft ausschliesslich in einem **Chrome-Browser**. Andere Browser werden nicht unterstützt.
- Eine Internetverbindung wird nicht benötigt. Das Log-Programm läuft vollständig offline.

<br>

## Technik

- Reines HTML, CSS und JavaScript, ohne Build-Schritt und ohne Bibliotheken.
- Läuft offline direkt aus dem Dateisystem (`file://`) in einer aktuellen Version von Chrome.

<br>

## Restriktionen

In der Alpha-Phase erfolgt die Benutzerführung in den Sprachen Deutsch und Englisch. Im Hinblick auf die Beta-Phase werden dann noch Französisch und Italienisch ergänzt. Das sind die vier Sprachen, die geplant sind.

<br>

## Spec-Driven Development with an AI

Dieses Projekt wird nach dem Prinzip „Spec-Driven Development“ (spezifikationsgetriebene Entwicklung) mit einer AI erstellt:

Zuerst wird in einer verbindlichen Spezifikation festgelegt, was das Programm können muss (siehe `design/Funktionsbeschreibung.md`). Darauf aufbauend werden technische Rahmenbedingungen festgelegt (siehe `design/Technische-Umsetzung.md`). Gestützt darauf wird anschliessend die AI beauftragt, den Programmcode zu schreiben.

Jede Spezifikation in den oben genannten Dokumenten trägt eine Nummer. Jede umgesetzte Funktion verweist im Code auf eine solche Anforderungsnummer, sodass sich jede Codestelle auf die Spezifikation zurückführen lässt.

Grundlegende Arbeitsregeln für die AI sind im Dokument `CLAUDE.md` geregelt.

Die aktuell noch offenen Punkte stehen in der Funktionsbeschreibung in Kapitel 17 „Offene Punkte“ (Nummern `D9nn`).

<br>

## Externe Daten und Dokumente

- Die Postleitzahlen der Schweiz und Liechtensteins mit Koordinaten liegen in `data/sec-zip-list.csv`. Aufbau, Quelle und Lizenz sind in `data/README.md` beschrieben.

- Externe Dokumente liegen in `docs/reference/` und sind dort in `README.md` aufgeführt:

  - `Reglement-SEC-2026-DE.pdf` - offizielles Reglement SEC 2026 der USKA.

  - `SEC26-Manual-de_V0003.pdf` - Handbuch des Windows-Log-Programms. Nur lokal, nicht im Repository.

<br>

## Bedienung

Das Programm besteht aus der einen Datei `SEC-Logger-by-HB9EVT.html`. Sie wird in Google Chrome geöffnet und läuft vollständig offline. Die Daten speichert Chrome im Browser-Speicher (IndexedDB).

Zur Sicherheit muss zusätzlich eine Sicherungsdatei angelegt werden. Dazu wird man vor dem Contest, beziehungsweise vor dem ersten QSO aufgefordert.

<br>

### Ansichten

**Reiter „Log“**

Eingabemaske oben, darunter das Log. Darüber liegt der Meldungsbereich, unten die Statuszeile. Die Sprache kann oben rechts umgestellt werden.

**Reiter „Station“**

Im Reiter "Station" erfasst man vor dem Contest, beziehungsweise vor dem ersten QSO, die eigenen Angaben. Diese sind:

- eigenes Rufzeichen (MyCall). Ein Zusatz wie z. B. /P wird nur bei Einzelstationen akzeptiert.

- Postleitzahl (MyZip) des eigenen Standorts, welcher in der Schweiz oder in Liechtenstein liegen muss.
- Gruppenbetrieb Ja/Nein und ggf. Stationsnummer bei Gruppenbetrieb

**Reiter „Administration“**

Export, Sicherungsdatei, Import, usw.

<br>

### QSO erfassen

- „Live Logging“: Das Programm setzt Datum und Zeit selbst. „Post Logging“: Datum und Zeit werden von Hand erfasst (Nacherfassung).
- „Repeat Last“: „Band“, „Mode“ und „TRX Route“ werden vom vorherigen QSO übernommen.
- Enter springt zum nächsten Feld, das noch ausgefüllt werden muss. Ist alles erfasst, springt Enter auf „Save“; ein weiteres Enter speichert das QSO.
- „ZIP Rcvd“: Postleitzahl oder Ortsnamen eintippen und aus der Liste wählen.
- Fehler (z. B. ein fehlendes Feld) verhindern das Speichern. Warnungen (z. B. Dupe) erscheinen im Meldungsbereich, das betroffene Feld ist farbig umrahmt; gespeichert werden kann trotzdem.
- Im Log zeigt die Spalte „!“ Warnungen an:
  - **P** = Dieses Rufzeichen wurde nicht immer mit der gleichen Postleitzahl geloggt.
  - **C** = Dieses Rufzeichen wurde nicht immer identisch geloggt. Prüfe die teilweise geloggten Vor- und Zusätze bei diesem Rufzeichen (z. B. "/P" oder "HB9/").
  - **X** = andere Warnung. Klicke auf das „X“, um dir die Warnmeldung anzeigen zu lassen.
  - **D** = "Dupe" (doppelt erfasste Verbindung). Mit diesem Rufzeichen hattest du auf dem gleichen Band und über den gleichen Verbindungsweg (direkt oder über dasselbe Relais) bereits eine Verbindung. **Tipp**: Wenn du unsicher bist, lass dieses Dupe-QSO im Log. Bei der Auswertung wird automatisch jenes QSO gewertet, welches auch im Log des Gesprächspartners steht. Das andere wird straffrei annulliert.

<br>

### QSO ändern oder löschen

Doppelklick auf eine Zeile im Log übernimmt das QSO in die Eingabemaske (gelber Hintergrund, Fokus auf „Band“, Warnungen werden wieder angezeigt). „Save changes“ speichert, „Discard“ oder die Taste Esc verwirft die Änderung, „Delete“ löscht das QSO nach einer Rückfrage. Bei dieser Rückfrage ist „No“ vorgewählt; Enter löst immer den blau hinterlegten Knopf aus.

<br>

### Sicherung, Import und Export

- Die Sicherungsdatei ist Pflicht (siehe „Datensicherheit“). Gewählt wird sie über den Hinweis über der Eingabemaske oder unter „Administration“. „Download backup copy“ legt zusätzlich eine Kopie im Download-Ordner ab.
- Eingelesen werden können nur Sicherungsdateien dieses Programms („Import: replace“ oder „Import: merge“). Vor jedem Import wird das Log gesichert; „Undo last import“ stellt es wieder her.
- „Export contest log (CSV)“ erzeugt die Datei für die Einreichung. Ihr Name darf nach dem Reglement nicht verändert werden. „Export ADIF“ erzeugt eine Datei für das eigene Stationslog.

<br>

### Datensicherheit

Chrome speichert das Log im Browser-Speicher (IndexedDB). Für Dateien, die direkt von der Festplatte geöffnet werden, gewährt Chrome in der Regel keinen dauerhaften Speicher. Das Log kann darum verloren gehen, wenn die Festplatte voll wird oder wenn die Browserdaten gelöscht werden. Den Schutz bietet die Sicherungsdatei:

- Ohne Sicherungsdatei kann kein QSO erfasst werden. Sie liegt am besten auf einem anderen Datenträger als Chrome, z. B. auf einem USB-Stick.
- Das Programm schreibt die Sicherungsdatei nach jedem Speichern, Ändern und Löschen eines QSO. Die Statuszeile zeigt Zeit und Anzahl QSOs des letzten Schreibens.
- Nach einem Neustart von Chrome muss das Schreiben einmal mit „Enable backup file“ bestätigt werden.
- Beim Start vergleicht das Programm das Log im Browser mit der Sicherungsdatei. Fehlen im Browser QSOs, bietet es an, sie aus der Sicherungsdatei zu ergänzen.
- Kann die Sicherungsdatei nicht geschrieben werden (z. B. USB-Stick entfernt), läuft die Erfassung weiter. Die Statuszeile zeigt den Fehler rot; mit „Retry“ wird das ganze Log nachgetragen.

<br>

### Hinweise

- Das Programm darf nur in einem Tab offen sein. Ein zweiter Tab kann nur lesen.
- Im Inkognito-Fenster gehen die Daten beim Schliessen verloren.
- Die Postleitzahl-Daten (© swisstopo) und die Relais-Liste sind als Kopie in der Programmdatei enthalten. Ändern sich die Dateien in `data/`, muss eine neue Version der HTML-Datei erstellt werden.

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
mit Unterstützung durch die KI Claude von Anthropic<br>(vgl. oben im Kapitel "Spec-Driven Development with an AI").
