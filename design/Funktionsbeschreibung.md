# Funktionsbeschreibung für den SEC-HTML-Logger

## 1. Zu diesem Dokument

| Nr. | Funktion |
|---|---|
| D001 | Dieses Dokument ist die Grundlage für die Realisierung der Software und allfälliger ergänzender Tools. Es wurde zu Projektbeginn erstellt, bevor auch nur eine Zeile Programmcode geschrieben wurde. |
| D002 | Während der Entwicklung, der Beta-Tests und der Weiterentwicklung sind Anpassungen und Ergänzungen möglich. Bei Anpassungen im Rahmen der Weiterentwicklung ist jeweils anzugeben, ab welcher Programmversion sie gelten. |
| D003 | Programmversion: Sie hat die Form `MAJOR.MINOR.PATCH`; MINOR und PATCH sind von Beginn an zweistellig. Vor der ersten Contest-tauglichen Version gilt `0.xx.yy` (erste Version `0.01.00`), danach `1.xx.yy`. |
| D004 | MAJOR wird erhöht, wenn sich das Format der Sicherungsdatei so ändert, dass ältere Sicherungsdateien nicht mehr eingelesen werden können. MINOR wird bei neuen Funktionen erhöht, PATCH bei Fehlerkorrekturen. |
| D005 | Die Versionsnummer steht an genau einer Stelle im Programmcode. Sie wird in der Administrations-Ansicht und in der Statuszeile angezeigt und in die Sicherungsdatei, in den ADIF-Export (Feld `PROGRAMVERSION`) und in jeden Eintrag des Changelogs geschrieben. Git-Tags setzt der Benutzer selbst (vgl. C21). |
| D006 | In diesem Dokument hat jede Bestimmung eine eindeutige Nummer `Dnnn` (oder `DnnnX`). Sie dient zur Referenzierung in Begleitdokumenten und im Code. |
| D007 | Dieses Dokument setzt voraus, dass der Leser die üblichen Fachbegriffe des Amateurfunks kennt, Contest-Erfahrung hat und mit dem Swiss Emergency Contest (SEC) und seinem eigenartigen Regelwerk (HBT anstatt UTC, CSV-Datei anstatt ADIF- oder Cabrillo-Datei, usw.) vertraut ist. |
| D008 | Bestimmungen mit dem Vermerk (Wunsch) beschreiben eine erwünschte, aber nicht zwingende Funktion. Alle übrigen Bestimmungen sind Pflicht. |

---

<br>

## 2. Zweck der Software

| Nr. | Funktion |
|---|---|
| D009 | Das Programm dient zur Erfassung der Funkverbindungen (QSOs) im Swiss Emergency Contest (SEC) der USKA. |
| D010 | Das Programm ist schlank. Es enthält nur Funktionen, die D009 dienen. |
| D011 | Das Programm erzeugt eine Log-Datei, die ohne Nachbearbeitung zur Auswertung eingereicht werden kann. |
| D012 | Grundlagen sind das Manual V4 (2026-10-23) der SEC-App von Leander HB9RMW, das Contest-Reglement SEC 2026 der USKA (beide in `docs/reference/` abgelegt) sowie die eigenen Erfahrungen des Autors am SEC. |

---

<br>

## 3. Technische Rahmenbedingungen

| Nr. | Funktion |
|---|---|
| D013 | Das Programm ist eine reine HTML-Lösung (HTML, CSS und JavaScript). Es braucht weder eine Installation noch einen Server. |
| D014 | Das Programm läuft vollständig offline. Es lädt keine Daten und keine Programmteile aus dem Internet. |
| D015 | Unterstützt wird der Browser Google Chrome in einer aktuellen Version. |
| D016 | Die Bedienung muss flüssig vonstattengehen. Typische Tätigkeiten während eines laufenden Contests (z. B. QSO erfassen, QSO ändern, QSO speichern, Dupe-Erkennung) vertragen keine Wartezeiten. Näheres regelt D041. |
| D017 | Programmdatei: `SEC-Logger-by-HB9EVT.html` im Projekt-Hauptordner. |
| D018 | Regelungen zur Sprache der Benutzeroberfläche sind in P03 und P04 in `CLAUDE.md` festgelegt. |

---

<br>

## 4. Darstellung

| Nr. | Funktion |
|---|---|
| D019 | Die Hauptansicht besteht aus der Eingabemaske für ein QSO im oberen Bereich, dem Log mit den bereits erfassten QSOs darunter, einem Meldungsbereich und einer Statuszeile. |
| D020 | Neben der Hauptansicht gibt es die Ansicht Stationseinstellungen (Kapitel 6) und die Administrations-Ansicht, u. a. mit den Funktionen für Import und Export. |
| D021 | Die Statuszeile zeigt die Anzahl QSOs, die Gesamtpunktzahl (nur bei Einzelstationen, vgl. D123), ob die letzte Speicherung erfolgreich war, den Status der Sicherungsdatei (D044), die gewählten Erfassungsmodi (Kapitel 9) und die Programmversion (D005). |
| D022 | Die Darstellung passt sich der Breite des Browser-Tabs an. |
| D023 | Die Eingabemaske für ein QSO steht auf einer Zeile. Ist das Fenster zu schmal, wird sie auf zwei oder drei Zeilen verteilt. |
| D024 | Im Log steht jedes QSO auf einer Zeile. Ist das Fenster zu schmal, erscheint ein horizontaler Scrollbalken, mit dem man das Log seitlich verschieben kann. |
| D025 | Spalten des Logs in dieser Reihenfolge: "Nr.", "Date", "Time", "Band", "Mode", "TRX Route", "His Call", "RST Send", "ZIP Send", "RST Rcvd", "ZIP Rcvd", "Points", "QRB". |
| D026 | "ZIP Send" ist die eigene Postleitzahl ("MyZip", D072). In der Eingabemaske wird sie nur angezeigt und ist nicht veränderbar. |
| D027 | Das Log ist nach Datum und Zeit sortiert. |
| D028 | Ein neues oder geändertes QSO wird im Log an der richtigen Stelle nach Datum und Zeit einsortiert. |
| D029 | Jedes QSO hat eine Nummer, die sog. QSO-Nummer. Sie gibt an, der wievielte Eintrag im Log das QSO ist (1 = ältestes QSO gemäss Datum- und Zeitfeld). |
| D030 | Die QSO-Nummer wird nur vom Programm verwaltet. Der Benutzer kann sie nicht ändern. |
| D031 | Beim Erfassen eines neuen QSO zeigt die Eingabemaske die Nummer an, die das QSO erhalten wird. |
| D032 | Beim Ändern eines QSO zeigt die Eingabemaske die Nummer an, die das QSO vor dem erneuten Speichern hatte. |
| D033 | Im Log steht die QSO-Nummer am linken Rand. |
| D034 | Nach jedem Hinzufügen, Ändern oder Löschen eines QSO nummeriert das Programm das Log neu durch. |
| D035 | Beim Start steht eine leere Eingabemaske bereit. Der Fokus liegt auf dem Feld "Band". |
| D035A | Die Administrations-Ansicht zeigt die Quellenangabe für die Postleitzahl-Daten: „© swisstopo – Amtliches Ortschaftenverzeichnis mit Postleitzahl und Perimeter“. Sie ist nach den Nutzungsbedingungen von swisstopo (Open Government Data) Pflicht. |

---

<br>

## 5. Datenhaltung

| Nr. | Funktion |
|---|---|
| D036 | Sind noch keine Daten gespeichert (z. B. beim ersten Start), zeigt das Programm ein leeres Log an. |
| D037 | Notfunkgruppen führen pro Station ein eigenes Log, unterschieden durch die Stationsnummer (D060). |
| D038 | Jedes QSO wird sofort nach dem Erfassen dauerhaft gespeichert, als eigener Datensatz. |
| D039 | Erst wenn das Speichern abgeschlossen ist, meldet das Programm „gespeichert“ und legt das nächste QSO zur Erfassung bereit. Bei einer Panne geht höchstens das QSO verloren, das gerade erfasst wird. |
| D040 | Die Speicherdauer (vom Ende der Eingabe bis zur Meldung „gespeichert“) wird gemessen und in geeigneter Form in der Administrations-Ansicht angezeigt (z. B. Verlauf der letzten 20 Messungen). |
| D041 | Wird das erfasste QSO zum Speichern freigegeben, muss die Eingabemaske innert höchstens 0.4 Sekunden wieder für die Eingabe bereitstehen. Kann diese Limite nicht dauernd eingehalten werden, sind zwingend Lösungen zu suchen. |
| D042 | Zusätzliche Sicherungsdatei (optional): Der Benutzer kann eine Sicherungsdatei auf einem Datenträger wählen. Das Programm führt sie nach jedem QSO nach. |
| D043 | Format der Sicherungsdatei: JSON, UTF-8 ohne BOM, mit Formatversion, den Stationseinstellungen und allen QSOs. |
| D044 | Nach einem Neustart von Chrome muss das Schreiben der Sicherungsdatei einmal bestätigt werden. Bis dahin zeigt das Programm einen Hinweis an. |
| D045 | Beim Start lädt das Programm das gespeicherte Log. Ist kein Log vorhanden, aber eine Sicherungsdatei, bietet das Programm an, das Log daraus wiederherzustellen. |
| D046 | In der Administrations-Ansicht kann eine Sicherungsdatei (D042, D043) eingelesen werden. Andere Dateien (z. B. die CSV-Datei, D128 und folgende) können nicht eingelesen werden. |
| D047 | Für den Import gibt es zwei Knöpfe: „Ersetzen“ ersetzt das bestehende Log durch die Sicherungsdatei. „Ergänzen“ fügt die QSOs der Sicherungsdatei dem bestehenden Log hinzu; dabei gelten die Dupe-Prüfung (D111) und die Neunummerierung (D034). |
| D048 | Vor jedem Import sichert das Programm das aktuelle Log automatisch. |
| D049 | Ist die Datei ungültig, zeigt das Programm eine Fehlermeldung mit der Zeilennummer an. Das bestehende Log bleibt unverändert. |
| D050 | Das Programm fordert bei Chrome dauerhaften Speicher an. Wird er nicht gewährt, zeigt das Programm eine Warnmeldung an. |
| D051 | Läuft das Programm in einem Inkognito-Fenster, zeigt das Programm eine Warnmeldung an, weil die Daten beim Schliessen verloren gehen. |
| D052 | Ist die Eingabemaske nicht leer oder wird gerade ein QSO geändert, warnt der Browser beim Schliessen des Tabs. |
| D053 | Ist das Programm bereits in einem anderen Tab geöffnet, zeigt es einen Hinweis an und lässt keine Erfassung zu. |

---

<br>

## 6. Stationseinstellungen

| Nr. | Funktion |
|---|---|
| D054 | In der Ansicht Stationseinstellungen (D020) werden die Einstellungen zur eigenen Station vorgenommen. |
| D055 | Das Programm speichert die Stationseinstellungen dauerhaft. Sie stehen nach einem Neustart wieder zur Verfügung. |
| D056 | "MyCall": Das eigene Rufzeichen wird ohne Zusätze wie `/P` oder `/M` erfasst. |
| D057 | "MyZip": Die vierstellige Postleitzahl des Standorts wird aus der PLZ-Tabelle gewählt. |
| D058 | "Gruppenbetrieb": Mit einer Ja/Nein-Einstellung wird festgelegt, ob die Station als Teil einer Notfunkgruppe arbeitet. |
| D059 | "SEC Group Number": Bei Gruppenbetrieb erhält jede Station eine eigene Stationsnummer (1…n). |
| D060 | Die Oberfläche schlägt folgende Stationsnummern vor: 1 = 80 m, 2 = 40 m, 3 = VHF bzw. VHF/UHF, 4 = UHF, 5 = CB. |
| D061 | D056 bis D058 sind Pflichtfelder. Sind diese nicht vollständig ausgefüllt, kann kein QSO geloggt oder geändert werden. Ein Hinweistext macht darauf aufmerksam. Der Import ist hingegen möglich (siehe D046). |
| D062 | "used in Log": Das Programm bildet aus den Einstellungen das Rufzeichen für das Log: `MyCall` bei Einzelstationen, `MyCall/Nummer` bei Gruppenstationen (z. B. `MyCall/1`). |
| D063 | Das Rufzeichen für den Funkbetrieb bleibt bei Gruppenstationen gleich. Die Stationsnummer dient nur dazu, die Logs bei der Auswertung zu unterscheiden. |

---

<br>

## 7. QSO-Felder

| Nr. | Funktion |
|---|---|
| D064 | Pflichtfelder sind "Date", "Time", "Band", "Mode", "TRX Route", "His Call", "RST Send", "RST Rcvd" und "ZIP Rcvd". Sie müssen ausgefüllt sein. "MyCall" und "MyZip" werden automatisch gesetzt, "Points" und "QRB" werden berechnet. |
| D065 | "Date": Datum des QSO. |
| D066 | "Time": Uhrzeit des QSO. |
| D067 | "Band": Band des QSO, gewählt aus der Band-Tabelle. |
| D068 | "Mode": Betriebsart des QSO, gewählt aus der Mode-Tabelle. |
| D069 | "TRX Route": Verbindungsweg, entweder `DIRECT` oder ein Relais aus der Relais-Tabelle. |
| D070 | "His Call": Rufzeichen der Gegenstation, manuell erfasst. |
| D071 | "RST Send": Rapport, den man der Gegenstation gibt (z. B. `59`). |
| D072 | "MyZip": Eigene Postleitzahl. Wird automatisch aus den Stationseinstellungen übernommen. |
| D073 | "RST Rcvd": Rapport, den man von der Gegenstation erhält. |
| D074 | "ZIP Rcvd": Postleitzahl der Gegenstation, gewählt aus der PLZ-Tabelle. |
| D075 | "RST Send" und "RST Rcvd" sind auf `59` voreingestellt. |
| D076 | "MyCall": Eigenes Rufzeichen ("used in Log"). Wird automatisch aus den Stationseinstellungen übernommen. |
| D077 | "Points": Punktwerte des QSO. Werden berechnet (siehe Kapitel 12). |
| D078 | "QRB": Distanz zur Gegenstation in km, gerundet auf 0.1 km. Sie wird nach Pythagoras aus den LV95-Koordinaten der eigenen Postleitzahl ("MyZip") und der Postleitzahl der Gegenstation ("ZIP Rcvd") berechnet. Datenquelle und Formel: `data/sec-zip-list.csv` und `data/README.md`. |

---

<br>

## 8. Stammdaten

| Nr. | Funktion |
|---|---|
| D079 | Die Stammdaten sind fest vorgegeben. |
| D080 | Band-Tabelle: Enthält die zulässigen Bänder 80 m, 40 m, 11 m (CB), 2 m und 70 cm. |
| D081 | Mode-Tabelle: Enthält die zulässigen Betriebsarten SSB, FM und AM, je mit Bezeichnung und Punktfaktor. |
| D082 | Relais-Tabelle: Enthält die zulässigen FM-Relais in CH/FL mit Name (Call, Standort, Frequenz), Sendefrequenz und Empfangsfrequenz sowie den Eintrag `DIRECT`. |
| D083 | PLZ-Tabelle: Enthält alle Postleitzahlen der Schweiz und Liechtensteins mit Ortsname. |
| D084 | Für Relais-Verbindungen dürfen nur Relais aus der Relais-Tabelle verwendet werden. |
| D085 | Die Relais-Tabelle kann nur in einem Admin-Bereich geändert werden. Vor unbedachten Änderungen wird gewarnt. |

---

<br>

## 9. Erfassung

| Nr. | Funktion |
|---|---|
| D086 | Live Logging (Standard): Datum, Zeit, "MyCall" und "MyZip" werden beim Anlegen eines QSO automatisch gesetzt. Gedacht für die Erfassung live während des Contests. |
| D087 | Im Live Logging werden Datum und Zeit aus der lokalen Systemzeit genommen. Ändert sich etwas im Feld "His Call", werden sie neu gesetzt. |
| D088 | Post Logging: Alle Felder, auch Datum und Zeit, sind frei editierbar. Gedacht für die Nacherfassung von Papiernotizen nach dem Contest. |
| D089 | Repeat Last (Standard): Beim Bestätigen eines leeren Feldes wird der Wert aus dem vorherigen QSO übernommen. Das gilt vor allem für "Band", "Mode", "TRX Route" und die Rapporte. |
| D090 | No Repeat: Es werden keine Werte aus dem vorherigen QSO übernommen. |
| D091 | Auto Next (Standard): Nach dem letzten Pflichtfeld ("ZIP Rcvd") wird das QSO gespeichert und sofort ein neues angelegt. |
| D092 | Manual Next: Ein neues QSO wird erst auf ausdrücklichen Befehl angelegt. |
| D093 | Das Programm merkt sich, welche Erfassungsmodi zuletzt gewählt waren. |
| D094 | Die Route `DIRECT` kann direkt gewählt werden, ohne Suche in der Relais-Tabelle. |
| D095 | Eingabe bereinigen: Leerzeichen am Anfang und am Ende einer Eingabe werden entfernt. Das Feld "His Call" wird in Grossbuchstaben umgewandelt. Vorsätze (z. B. `HB0/`) und Zusätze (z. B. `/P`) sind im Feld "His Call" erlaubt. |

---

<br>

## 10. Datensatz-Operationen

| Nr. | Funktion |
|---|---|
| D096 | Ein neues QSO kann hinzugefügt werden. Es wird gemäss D028 einsortiert. |
| D097 | Ein bestehendes QSO kann bearbeitet werden. Die Änderung kann gespeichert oder verworfen werden. Dafür gibt es anklickbare Knöpfe. Verwerfen ist zudem mit der Taste Esc möglich. |
| D098 | Mit einem Doppelklick auf eine Zeile im Log wird das QSO in die Eingabemaske übernommen und kann dort bearbeitet werden. |
| D099 | Es ist klar erkennbar, ob in der Eingabemaske ein bestehendes QSO geändert oder ein neues QSO erfasst wird: Beim Ändern hat die Eingabemaske eine andere Hintergrundfarbe und zeigt die Nummer des QSO an. |
| D100 | Beim Ändern eines bestehenden QSO werden Datum und Zeit nicht automatisch neu gesetzt, auch nicht im Live Logging. |
| D101 | Ein QSO kann gelöscht werden. Das geschieht nach einer Rückfrage. |
| D102 | Im Log kann man navigieren: zum ersten, letzten, vorherigen oder nächsten QSO sowie seitenweise. |
| D103 | Das Programm zeigt die aktuelle Position und die Anzahl der QSOs an („QSO n of N“). |
| D104 | Das Log kann nach Spalten gruppiert und mit einer Volltextsuche durchsucht werden. |

---

<br>

## 11. Prüfungen und Warnmeldungen

| Nr. | Funktion |
|---|---|
| D105 | Fehler verhindern das Speichern, z. B. ein fehlendes Pflichtfeld (D064) oder ein Wert, der nicht in den Stammdaten (Kapitel 8) steht. |
| D106 | Fehler werden schon während der Eingabe direkt beim betroffenen Feld angezeigt. |
| D107 | Warnungen erscheinen gut sichtbar in roter Schrift. Sie verhindern das Weiterarbeiten nicht, z. B. das Speichern und das Erfassen des nächsten QSO. |
| D108 | Verstösse gegen die Plausibilitätsregeln (Kapitel 13) sind Warnungen. |
| D109 | Alle Meldungen und Rückfragen des Programms erscheinen im Meldungsbereich (D019), nicht in eigenen Fenstern. Einzige Ausnahme ist die Warnung des Browsers beim Verlassen (D052). |
| D110 | Eine offene Rückfrage verfällt, sobald der Benutzer etwas anderes macht. |
| D111 | Das Programm meldet „Dupe“, wenn ein QSO mit derselben Kombination aus "Band", "TRX Route" und "His Call" bereits existiert. |
| D112 | Erscheint die Warnmeldung „Dupe“, springt das Log zum bereits vorhandenen QSO und hebt dessen Zeile farbig hervor. |
| D113 | Reglement, Direktverbindungen: Jede Station darf pro Band nur einmal direkt gearbeitet werden. |
| D114 | Reglement, Relaisverbindungen: Jede Station darf pro Relais nur einmal gearbeitet werden. Über ein anderes Relais oder direkt darf sie nochmals gearbeitet werden. |
| D115 | Das Programm warnt, wenn eine Verbindung keine neuen Punkte einbringt (vgl. D116 ff.). |

---

<br>

## 12. Punkteberechnung

| Nr. | Funktion |
|---|---|
| D116 | Es zählen nur QSOs mit Gegenstationen, deren Standort in CH/FL liegt. Das heisst: Das Rufzeichen muss mit `HB` beginnen, entweder der eigene Präfix oder der Gastlandpräfix (z. B. `HB9/…`). Sonst gibt es keine Punkte. |
| D117 | Jedes gültige QSO ergibt 1 Punkt, auf allen Bändern. |
| D118 | SSB-Bonus: SSB-QSOs auf 11 m, 2 m und 70 cm zählen 2 Punkte. Auf 80 m und 40 m gibt es keinen Bonus. |
| D119 | Multiplikator: Jede verschiedene Postleitzahl ("ZIP Rcvd") pro Band ergibt einen Multiplikatorpunkt. |
| D120 | Bandergebnis: QSO-Punkte des Bandes × Anzahl verschiedener Postleitzahlen auf diesem Band. |
| D121 | Gesamtpunktzahl: Summe der Bandergebnisse von 2 m, 70 cm, 80 m, 40 m und 11 m. |
| D122 | Bei Notfunkgruppen werden die Punkte aller Stationsnummern unter demselben Rufzeichen zusammengezählt. Das geschieht bei der Auswertung, nicht im Programm. |
| D123 | Bei Notfunkgruppen zeigt das Programm keine Gesamtpunktzahl an (Folge aus D122). |

---

<br>

## 13. Plausibilitätsregeln

| Nr. | Funktion |
|---|---|
| D124 | HB3-Stationen dürfen nicht auf 40 m arbeiten. |
| D125 | Relais dürfen nur auf 2 m und 70 cm verwendet werden, und nur in FM. |
| D126 | Erlaubte Modes pro Band: 80 m und 40 m nur SSB; 11 m AM, FM und SSB; 2 m und 70 cm direkt SSB und FM; über Relais nur FM. |
| D127 | Die eigene Postleitzahl darf sich während des Contests nicht ändern. |

---

<br>

## 14. Export

| Nr. | Funktion |
|---|---|
| D128 | Contest-Log: Das Programm exportiert das Log als CSV-Datei. |
| D129 | CSV-Format: keine Kopfzeile, eine Zeile pro QSO, Trennzeichen `;`, Zeilenende CRLF, Zeichensatz ASCII. |
| D130 | CSV-Spalten in dieser Reihenfolge: 1 QSO-Nummer (D029); 2 Datum `TT.MM.JJJJ`; 3 Zeit `HH:MM:SS`; 4 "Band" (z. B. `80 m`, `70 cm`); 5 "Mode" (`SSB`, `FM` oder `AM`); 6 "TRX Route" (`DIRECT` oder Relaisname „Call Standort Frequenz“); 7 "His Call"; 8 "RST Send"; 9 "MyZip"; 10 "RST Rcvd"; 11 "ZIP Rcvd"; 12 QSO-Punkt (immer `1`); 13 leer; 14 Punktwert des Mode (`1`, SSB-Bonus `2`); 15 leer; 16 "MyCall" ("used in Log"); 17 Relais-Kennung (z. B. `<Relais-Call>-04`), nur bei Relais-QSOs. |
| D131 | Bei QSOs ohne Relais bleibt Feld 17 leer, die Zeile endet mit `;`. |
| D132 | Der Name der CSV-Datei wird automatisch erzeugt: `<MyCall>.CSV`, bei Gruppen `<MyCall>_<Nr>.CSV` (z. B. `MyCall_1.CSV`). |
| D133 | ADIF: Das Programm exportiert das Log zusätzlich als ADIF-Datei (v3.x) für die Übernahme ins eigene Stationslog. |
| D134 | Der Name der ADIF-Datei ist `<MyCall>[_<Nr>].ADI`. |
| D135 | Erfasste Felder, die es in der ADIF-Norm nicht gibt, werden zusammen mit dem Contest-Kurznamen ins ADIF-Feld `NOTES` geschrieben: `SEC 2026; MyPLZ = 0000; HisPLZ = 0000`. |
| D136 | Zum Speichern einer CSV- oder ADIF-Datei öffnet das Programm den Speichern-Dialog des Browsers bzw. des Betriebssystems. Der Dateiname nach D132 bzw. D134 wird darin vorgeschlagen. |
| D137 | Vor dem Speichern weist das Programm darauf hin, dass der Name der CSV-Datei nach dem Reglement nicht verändert werden darf. Wird im Speichern-Dialog ein anderer Name gewählt, zeigt das Programm eine Warnmeldung an. |
| D138 | Nach dem Export meldet das Programm, ob er erfolgreich war oder nicht. |

---

<br>

## 15. Einbindung ins Projekt

| Nr. | Funktion |
|---|---|
| D139 | README und DOCUMENTATION im Projektordner erhalten einen Abschnitt zur Bedienung. |
| D140 | Die Programmdatei (D017) wird in die Allow-Liste von `.gitignore` aufgenommen. |
| D141 | Beispiele verwenden nur fiktive Rufzeichen. |

---

<br>

## 16. Test

| Nr. | Funktion |
|---|---|
| D142 | Getestet wird nur mit eigens erstellten Testdaten oder mit Testdaten, die der Benutzer zur Verfügung stellt, nie mit echten Logs (P21 in `CLAUDE.md`). |
| D143 | Die Logik (Punkte, Dupe-Prüfung, Plausibilität, CSV- und ADIF-Export) wird ohne Oberfläche gegen Referenzdateien getestet. |
| D144 | Pannen werden simuliert: Speicherfehler, verweigerte Berechtigung, Import einer defekten Datei. |
| D145 | Die Grenze von 0.4 Sekunden (D041) wird mit einem grossen Log gemessen, z. B. 2000 QSOs. |
| D146 | Die Oberfläche prüft der Benutzer selbst in Chrome. |

---

<br>

## 17. Offene Punkte

| Nr. | Funktion |
|---|---|
| D901 | Zu D130: Herkunft bzw. Format der Relais-Kennung in CSV-Spalte 17 klären. Solange dies ungeklärt ist (und der Punkt deshalb hier aufgeführt ist), wird Spalte 17 im CSV mit `unbekannt gemaess D901` ausgefüllt. |
| D902 | Zu D069: Darf im SEC jedes Relais aus der SEC-Relais-Liste verwendet werden oder nur jene mit dem Eintrag UPS = 1?<br />Solange dies ungeklärt ist (und der Punkt deshalb hier aufgeführt ist), darf jedes Relais aus der Liste verwendet werden. |
| D903 | Zu D111: Gemäss SEC-Reglement (Kap. 7) besteht eine Doppelverbindung, wenn Rufzeichen, Band und Verbindungsweg (direkt oder über welches Relais) übereinstimmen. So macht es auch die SEC26-Logging-App von Leander HB9RMW. Im Manual V4 (2026-10-23) zu dieser App steht hingegen, eine Doppelverbindung liege nur dann vor, wenn zudem auch der Mode (FM, SSB, AM) übereinstimmt.<br />Im Hinblick auf den SEC 2027 ist abzuklären, wie es künftig sein soll.<br />Solange dies ungeklärt ist (und der Punkt deshalb hier aufgeführt ist), gilt D111. |
