# SEC-HTML-Logger - Dokumentation

<br>

## Zweck

Der SEC-HTML-Logger ist ein Logprogramm für den Swiss Emergency Contest (SEC) der USKA. Es läuft im Browser, vollständig offline, und soll das Windows-Logprogramm der USKA ersetzen. Es erfasst die Funkverbindungen (QSOs), prüft Doppelverbindungen, berechnet die theoretisch möglichen Punkte und exportiert das Log für die Einreichung.

<br>

## Spezifikation

Alle Funktionen sind in `design/Funktionsbeschreibung.md` beschrieben. Jede Bestimmung hat eine eindeutige Nummer `Dnnn`. Der Programmcode verweist in Kommentaren auf diese Nummern.

Die offenen Punkte stehen in Kapitel 17 „Offene Punkte“ der Funktionsbeschreibung (Nummern `D9nn`).

<br>

## Technik

- Reines HTML, CSS und JavaScript, ohne Build-Schritt und ohne Bibliotheken.
- Läuft offline direkt aus dem Dateisystem (`file://`) in einer aktuellen Version von Chrome.
- In der Entwicklungsphase ist die Oberfläche englisch. Später wird das Programm mehrsprachig (Deutsch, Französisch, Italienisch, Englisch). Alle Texte der Oberfläche liegen darum an einer zentralen Stelle.

<br>

## Daten

Die Postleitzahlen der Schweiz und Liechtensteins mit Koordinaten liegen in `data/sec-zip-list.csv`. Aufbau, Quelle und Lizenz sind in `data/README.md` beschrieben. Die Dateien im Ordner `data/` werden nicht verändert.

<br>

## Referenzdokumente

Die externen Dokumente liegen in `docs/reference/` und sind dort in `README.md` aufgeführt:

- `Reglement-SEC-2026-DE.pdf` - offizielles Reglement SEC 2026 der USKA.
- `SEC26-Manual-de_V0003.pdf` - Handbuch des Windows-Logprogramms. Nur lokal, nicht im Repository.

<br>

## Bedienung

Das Programm besteht aus der einen Datei `SEC-Logger-by-HB9EVT.html`. Sie wird in Google Chrome geöffnet und läuft vollständig offline. Die Daten speichert Chrome im Browser-Speicher (IndexedDB).

<br>

### Ansichten

- „Log“: Eingabemaske oben, darunter das Log. Darüber liegt der Meldungsbereich, unten die Statuszeile.
- „Station“: eigenes Rufzeichen (MyCall), eigene Postleitzahl (MyZip), Gruppenbetrieb und Stationsnummer (SEC Group Number, 1 bis 9). Das Rufzeichen oder der Gastlandpräfix beginnt mit HB (oder bei Sonderrufzeichen ev. auch mit HE). Ohne gültige Angaben kann kein QSO erfasst werden; bei jedem Feld steht, was fehlt oder falsch ist. Einzelstationen dürfen Zusätze wie `/P` verwenden, Gruppenstationen nicht.
- „Administration“: Export, Sicherungsdatei, Import, Speicherdauer, Relais-Tabelle, Quellenangaben.
- Sprache: Die Auswahl rechts neben „Live Logging“ schaltet zwischen Deutsch und Englisch um. Beim ersten Start gilt die Sprache des Browsers, sonst Englisch. Die Feldnamen des Contest-Logs bleiben englisch. Die Knopfnamen in dieser Dokumentation sind die englischen.

<br>

### QSO erfassen

- Für ein neues QSO steht der Fokus bei „Live Logging“ im ersten leeren Feld, bei „Post Logging“ im Feld „Time“. Mit „Repeat Last“ sind „Band“, „Mode“ und „TRX Route“ mit den Werten des vorherigen QSO vorbelegt.
- Enter springt zum nächsten Feld, das leer ist oder einen Fehler hat (nach dem letzten Feld geht es vorne weiter), oder zu einem folgenden Feld mit Warnung. Hat das aktuelle Feld einen Fehler, bleibt der Fokus vorerst dort; ein zweites Enter ohne Änderung springt weiter. Gibt es nichts mehr zu tun, springt Enter auf „Save“; ein weiteres Enter speichert das QSO, danach steht eine neue Eingabemaske bereit. Ausgefüllte Felder erreicht man mit Tab oder per Mausklick.
- Mit „Repeat Last“ übernimmt Enter in einem leeren Feld den Wert aus dem vorherigen QSO. Mit Tab springt der Fokus vom letzten Knopf zurück zu „Date“.
- Ein Rufzeichen (ohne Vor- und Zusätze wie `HB9/` oder `/P`) hat mindestens drei Zeichen, nur Buchstaben und Ziffern, eine Ziffer an zweiter oder dritter Stelle und als letztes Zeichen einen Buchstaben. Sonst erscheint eine Warnung (bei „His Call“ und bei „MyCall“). Unzulässige Zeichen und eine fehlende Ziffer an zweiter oder dritter Stelle werden schon beim Tippen gemeldet, die übrigen Regeln nach drei Sekunden Tipp-Pause oder beim Verlassen des Feldes.
- Auf 11 m (CB) muss das Rufzeichen nicht mit HB oder HE beginnen und zählt normal Punkte; geprüft wird nur, dass es aus Buchstaben und Ziffern besteht.
- Bei einem Dupe heisst der Knopf „Save Dupe“. Bei der Warnung zu einer abweichenden Postleitzahl setzt der Knopf „… übernehmen“ die bisherige Postleitzahl ein.
- Mit „Live Logging“ setzt das Programm Datum und Zeit selbst. Mit „Post Logging“ werden sie von Hand erfasst (Nacherfassung nach dem Contest).
- Bei „ZIP Rcvd“ genügt die vierstellige Postleitzahl; man kann auch den Ortsnamen eintippen. Die Liste unter dem Feld zeigt zuerst die Einträge, die mit der Eingabe beginnen, und unter einem Strich jene, die sie nur enthalten. Pfeil nach unten und Enter (oder ein Klick) übernehmen einen Eintrag, Esc schliesst die Liste. Fehlermeldungen erscheinen erst nach drei Sekunden Tipp-Pause oder beim Verlassen des Feldes. Wurde die Gegenstation früher schon erfasst, nennt die Meldung deren Postleitzahl; der Knopf „… übernehmen“ setzt sie ein.
- Fehler (z. B. fehlendes Pflichtfeld) verhindern das Speichern und werden beim Feld angezeigt. Warnungen (z. B. „Dupe“ oder „Mode AM is not allowed on 80 m“) erscheinen rot im Meldungsbereich, sobald die betroffenen Felder ausgefüllt sind. Sie verhindern das Speichern nicht.
- Felder, die eine Warnung auslösen, haben einen farbigen Rahmen: blau bei einem Dupe („His Call“, „Band“, „TRX Route“), sonst rot, z. B. „ZIP Rcvd“ bei einer abweichenden Postleitzahl oder „His Call“ bei einem anderen Zusatz.
- „Save“ ist blau, wenn alle Pflichtfelder ausgefüllt sind und keine Warnung vorliegt. Gespeichert werden kann auch ohne blauen Knopf.
- In der Spalte „!“ des Logs steht ein rotes „P“ bei allen QSOs einer Station, wenn ihre Postleitzahlen nicht übereinstimmen, ein rotes „C“, wenn ihr Rufzeichen mit verschiedenen Vor- oder Zusätzen erfasst wurde (z. B. `/P`), ein rotes „X“ bei einer anderen Warnung und ein blaues „D“ bei einem Dupe. Treffen mehrere zu, stehen alle in dieser Reihenfolge, z. B. „P,C,D“. Im Meldungsbereich stehen nur die Warnungen des QSO in der Eingabemaske. Ein Klick auf die Buchstaben zeigt die Warnungen des betreffenden QSO an, ohne es zu öffnen.

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
- Die Postleitzahl-Daten (© swisstopo) und die Relais-Liste sind als Kopie in der Programmdatei enthalten. Ändern sich die Dateien in `data/`, muss diese Kopie nachgeführt werden.

<br>

## Test

Die Programmlogik (Punkte, Dupe-Prüfung, Plausibilität, CSV- und ADIF-Export, Sicherungsdatei) wird mit `tests/test-logic.js` gegen die Referenzdateien in `tests/reference/` geprüft:

```
node tests/test-logic.js
```

Die Referenzdateien enthalten nur fiktive Rufzeichen. Die Zeiten im ADIF-Export werden nach UTC umgerechnet; der Test geht darum von der Zeitzone Europe/Zurich aus (unter Windows die Standardeinstellung in der Schweiz).

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
mit Unterstützung durch die KI Claude von Anthropic<br>(vgl. Kapitel "Spec-Driven Development with an AI" im README).
