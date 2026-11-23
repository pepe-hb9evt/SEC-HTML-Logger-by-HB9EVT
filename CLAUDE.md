# Project rules for Claude - SEC-HTML-Logger

Browser-based log program for the Swiss Emergency Contest (SEC) of the USKA.

<br>


| Project phase                       |                                   |
| ----------------------------------- | --------------------------------- |
| We are in **"Alpha testing phase"** | (only the user changes this line) |

<br>

## General project rules

### Rule format

- G01 -- Every rule or specification has a unique number:
  - general project rules `G01`, `G02`, ...
  - specific project rules `P01`, `P02`, ...
  - design specifications/requirements `D001`, `D002`, ...
  - technical specification `T001`, `T002`, ...
- G02 -- Rules or specifications added later are either appended at the end with the next free number, or inserted at a suitable place. When inserted, they get the number of the preceding entry with a letter appended (example: an entry inserted after `G01` becomes `G01A`, the next one inserted after it becomes `G01B`, and so on). Existing numbers never change; removed entries are marked as removed.
- G03 -- Exception to G02: during the early development phase (see project phase), renumbering is allowed. It needs the user's approval.
- G04 -- In a rule definition document, the rule number is followed by " -- " and the rule itself (example: `G07 -- In code documents, all variable names, function names and code comments are in English.`).

<br>

### Shared rules

@../CLAUDE.md

- G05 -- Also follow the rules in the CLAUDE.md of the parent folder `Pepe-AI-Aera` (imported above), which are numbered B01 to B99.
- G06 -- If a basic rule (`Bnn`) conflicts with a rule in this file (`Gnn` or `Pnn`), the rule in this file takes precedence.

<br>

### Languages of files

- G07 -- In code documents, all variable names, function names and code comments are in English.
- G08 -- Every subfolder directly below the project folder that belongs to the repository, except `.github/`, has a README.md and is always in English with no need of a translation in any other language.
- G09 -- Any other documents and data files in subfolders can be in German or in English with no need of a translation in any other language.

<br>

### Documentation

- G10 -- `README_deutsch_german.md` is in German and gives a short overview, folder structure and quick start only. `README.md` is only its English translation.
- G11 -- If the project has a `DOCUMENTATION_deutsch_german.md`, it is in German and contains all information that is not in the READMEs and is relevant for a new user. `DOCUMENTATION.md` is only its English translation.
- G12 -- Applies only to the document pairs in the project folder (`README_deutsch_german.md` / `README.md`, `DOCUMENTATION_deutsch_german.md` / `DOCUMENTATION.md`): make changes in the German document first. Then ask the user for approval before updating the English translation.
- G13 -- If the German document and its English translation differ in content, point this out to the user.
- G14 -- When files or folders are added, moved or removed, update the folder tree in `README_deutsch_german.md` and the affected READMEs in subfolders in the same step (`README.md` see G12).
- G15 -- Put a deliberate blank line `<br>` before every heading. Exceptions: a heading directly below its parent heading, and the first heading of the file.
- G16 -- A changelog is kept in `CHANGELOG_deutsch_german.md` in German. Every change to project files gets an entry.

<br>

### Git

- G17 -- `.gitignore` is an allow-list: every new file that belongs in the repository must be added explicitly. Files with personal data or secrets must never be added.

<br>

## Specific project rules

### Folders and data

- P01 -- Do not make any change in the folder `data/` and all its subfolders without explicit permission for each single case.
- P02 -- `docs/reference/` holds third-party documents. Never edit them; only replace them with newer versions on the user's request.

<br>

### App language

- P03 -- During the early development phase (see project phase), only English is used in the user interface.
- P04 -- Later the program must be multilingual (German, French, Italian, English). Design for this from the start: keep all user interface texts in one central place, no hard-coded texts in the code.

<br>

### Specification

- P05 -- Every implemented function refers to its requirement number(s) in a code comment in the form `// Dnnn short description`.
- P06 -- Open points in the specification are decided by the user. Do not implement an assumption for them without approval.
- P07 -- The design documents are `design/Funktionsbeschreibung.md` (functional specification, requirements `Dnnn`) and `design/Technische-Umsetzung.md` (technical implementation, knowledge blocks `Tnnn`).

<br>

### Code

- P08 -- Plain HTML, CSS and JavaScript, no build step, no frameworks or libraries without the user's approval.
- P09 -- The app runs fully offline from the local file system (`file://`) in current Chrome: no CDN links, no web fonts, no network requests.
- P10 -- Tests of JavaScript code are written in JavaScript and run with Node.js, using only its built-in modules (exception to B22).

<br>

### Security and privacy

- P11 -- Logs of real contests must never be added to the repository.

<br>

### Testing

- P12 -- Test changes in the browser (Chrome) before reporting them as done.
