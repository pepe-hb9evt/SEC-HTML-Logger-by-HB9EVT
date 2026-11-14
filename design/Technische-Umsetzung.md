# SEC26 Log – Technische Umsetzung

Dieses Dokument beschreibt, wie die Anforderungen aus `Funktionsbeschreibung.md` technisch umgesetzt werden.
Jeder Wissensblock hat eine eindeutige Nummer `Tnnn` (oder `TnnnX`). Sie dient zur Referenzierung in Begleitdokumenten und im Code.

---

<br>

## 1. Rahmenbedingungen

| Nr. | Inhalt |
|---|---|
| T001 | Das Programm ist eine reine HTML-Lösung (HTML, CSS und JavaScript), läuft vollständig offline direkt aus dem Dateisystem (`file://`) und unterstützt nur Google Chrome (D013, D014, D015). |
| T002 | Ziel der Datenhaltung: Jedes QSO wird sofort gespeichert. Bei einer Panne geht höchstens das QSO verloren, das gerade erfasst wird (D038, D039). |

---

<br>

## 2. Speicherarten im Vergleich

| Nr. | Inhalt |
|---|---|
| T003 | **IndexedDB** (Datenbank im Browser): sehr sicher. Mit der Option `durability: 'strict'` meldet Chrome eine Transaktion erst als abgeschlossen, wenn die Daten auf der Festplatte stehen. Funktioniert auch über `file://`. Die Speichergrenzen spielen für ein Log keine Rolle. |
| T004 | **localStorage:** einfach, aber weniger sicher. Chrome schreibt die Daten verzögert auf die Festplatte. Bei einem Stromausfall können die letzten Sekunden verloren gehen. Wird nicht verwendet. |
| T005 | **Sicherungsdatei** über die Chrome-Funktion *File System Access*: sehr sicher. Chrome schreibt zuerst in eine temporäre Datei und ersetzt die alte Datei erst danach. Die Datei ist darum nie halb geschrieben. Die Datei wird einmal gewählt; nach jedem Neustart von Chrome muss das Schreiben mit einem Klick erneut erlaubt werden. |
| T006 | **Gewählte Lösung:** IndexedDB als Hauptspeicher (T007), Sicherungsdatei als optionale zweite Sicherung (T010). |

---

<br>

## 3. Hauptspeicher IndexedDB

| Nr. | Inhalt |
|---|---|
| T007 | Datenbankname `sec-html-logger`. Alle lokalen HTML-Dateien teilen sich in Chrome denselben Speicherbereich; der eindeutige Name verhindert Konflikte mit anderen lokalen Programmen. |
| T008 | Jedes QSO ist ein eigener Datensatz. Beim Speichern wird nur das neue bzw. geänderte QSO geschrieben, nie das ganze Log (D038). Die Stationsnummer bei Notfunkgruppen ist Teil des Datensatzes, damit jede Station ihr eigenes Log hat (D037). |
| T009 | **Ablauf beim Speichern eines QSO:** (1) Datensatz in einer Transaktion mit `durability: 'strict'` schreiben. (2) Auf das Ereignis „Transaktion abgeschlossen“ warten. (3) Erst dann „gespeichert“ anzeigen und das nächste QSO anlegen (D039). (4) Schlägt das Speichern fehl, bleibt das QSO in der Eingabe und das Programm zeigt eine Warnmeldung an. |

---

<br>

## 4. Sicherungsdatei

| Nr. | Inhalt |
|---|---|
| T010 | Der Benutzer wählt die Sicherungsdatei einmal über den Speichern-Dialog von Chrome (`showSaveFilePicker`). Der Verweis auf die Datei wird in IndexedDB abgelegt (D042). |
| T011 | Nach jedem gespeicherten QSO schreibt das Programm das ganze Log in die Sicherungsdatei. Bei der Grösse eines Contest-Logs ist das unproblematisch. |
| T012 | Nach einem Neustart von Chrome ist die Schreibberechtigung aufgehoben. Sie kann nur nach einem Klick des Benutzers erneut angefordert werden (`requestPermission`). Bis dahin zeigt das Programm einen Hinweis an (D044). |
| T013 | Die Sicherungsdatei schützt auch dann, wenn die Browserdaten gelöscht werden. Liegt sie auf einem USB-Stick, schützt sie zusätzlich bei einem Festplattendefekt. |

---

<br>

## 5. Start und Wiederherstellung

| Nr. | Inhalt |
|---|---|
| T014 | Beim Start liest das Programm das Log aus IndexedDB. Ist IndexedDB leer und ist eine Sicherungsdatei bekannt, bietet das Programm an, das Log daraus wiederherzustellen (D045). |
| T015 | Das Programm ruft `navigator.storage.persist()` auf. Ohne dauerhaften Speicher darf Chrome die Daten löschen, wenn die Festplatte voll wird. Wird die Anfrage abgelehnt, erscheint eine Warnmeldung (D050). |
| T016 | Ein Inkognito-Fenster lässt sich nur indirekt erkennen, z. B. an einem auffällig kleinen Speicherkontingent (`navigator.storage.estimate()`). Die Erkennung ist nicht garantiert zuverlässig (D051). |

---

<br>

## 6. Verhalten bei Pannen

| Nr. | Inhalt |
|---|---|
| T017 | **Tab oder Chrome stürzt ab:** Verlust höchstens des QSO in Eingabe. |
| T018 | **PC-Absturz oder Stromausfall:** Verlust höchstens des QSO in Eingabe (dank `durability: 'strict'`). |
| T019 | **Browserdaten gelöscht:** ohne Sicherungsdatei geht das ganze Log verloren; mit Sicherungsdatei kein Verlust, das Log wird daraus wiederhergestellt. |
| T020 | **Festplatte defekt:** das ganze Log geht verloren, ausser die Sicherungsdatei liegt auf einem anderen Datenträger. |

---

<br>

## 7. Zu prüfen

| Nr. | Inhalt |
|---|---|
| T021 | In einem Prototyp prüfen, dass IndexedDB, `durability: 'strict'`, `navigator.storage.persist()` und `showSaveFilePicker` in der aktuellen Chrome-Version über `file://` wie beschrieben funktionieren. |
