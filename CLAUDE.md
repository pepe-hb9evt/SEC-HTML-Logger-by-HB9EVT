# Project rules for Claude - SEC-HTML-Logger

Browser-based log program for the Swiss Emergency Contest (SEC) of the USKA.

<br>


| Project phase                      |                                   |
| ---------------------------------- | --------------------------------- |
| We are in **"Beta testing phase"** | (only the user changes this line) |

<br>

# General rules

## Rule format

- C01 -- Every rule or specification has a unique number:
  - general rules `C01`, `C02`, ...
  - project rules `P01`, `P02`, ...
  - design specifications/requirements `D001`, `D002`, ...
  - technical specification `T001`, `T002`, ...
- C02 -- Rules or specifications added later are either appended at the end with the next free number, or inserted at a suitable place. When inserted, they get the number of the preceding entry with a letter appended (example: an entry inserted after `C01` becomes `C01A`, the next one inserted after it becomes `C01B`, and so on). Existing numbers never change; removed entries are marked as removed.
- C03 -- Exception to C02: during the early development phase (see project phase), renumbering is allowed. It needs the user's approval.
- C04 -- In a rule definition document, the rule number is followed by " -- " and the rule itself (example: `C05 -- Communicate with the user in German.`).

<br>

## Communication

- C05 -- Communicate with the user in German.
- C06 -- Address the user informally with "du" (duzen), never with "Sie".
- C07 -- "Mache einen Vorschlag" (or similar) -> work out a plan for approval, do not change files.
- C08 -- "Erstellen", "Ausführen" -> implement the approved plan, or carry out the requested task immediately.

<br>

## File handling

- C09 -- Files are also edited outside of Claude. Before changing a file, ALWAYS read its current version from the project folder and base the planned changes on that version. Never rebuild a file from an older copy, a previous tool result or memory.
- C10 -- If a file changed since Claude last read it, keep the user's changes and merge Claude's changes into them. Never silently overwrite edits made by the user.
- C11 -- After creating or changing a file in the project folder, wait one second, read the file again and verify that it actually contains the new content. Report any mismatch.
- C12 -- Do not rename or move the user's folders or files without approval.
- C13 -- Code and Markdown files: UTF-8 without BOM, LF line endings, no trailing spaces, exactly one final newline.
- C13A -- In Markdown files no line endings in the middle of a paragraph.
- C14 -- Keep Windows line endings (CRLF) in `.bat` and `.ps1` files.

<br>

## Specification

- C15 -- Every implemented function refers to its requirement number(s) in a code comment.
- C16 -- Open points in the specification are decided by the user. Do not implement an assumption for them without approval.

<br>

## Code

- C17 -- Helper scripts: Python 3.8+, standard library only - no extra packages without the user's approval. Exception: tests of JavaScript code are written in JavaScript and run with Node.js, using only its built-in modules.

<br>

## Security and privacy

- C18 -- Never use real URLs, names or e-mail addresses in README, documentation or example files, except for author or license declarations. Use fictitious ones based on the NATO alphabet (`example-alpha`, `example-bravo`, ...), no Greek letters.
- C19 -- `.gitignore` is an allow-list: every new file that belongs in the repository must be added explicitly. Files with personal data or secrets must never be added.

<br>

## Testing

- C20 -- Before reporting a change as done, test it and state what was tested.

<br>

## Git and releases

- C21 -- Claude does not access Git: no `git` commands (no init, add, commit, push, pull, tag, ...), no changes inside the `.git` folder. The user handles Git himself. Never build or publish a release without asking the user.

<br>

# Project rules

## Folders and data

- P01 -- Do not make any change in the folder `data/` and all its subfolders without explicit permission for each single case.
- P02 -- `docs/reference/` holds third-party documents. Never edit them; only replace them with newer versions on the user's request.

<br>

## App language

- P03 -- During the early development phase (see project phase), only English is used in the user interface.
- P04 -- Later the program must be multilingual (German, French, Italian, English). Design for this from the start: keep all user interface texts in one central place, no hard-coded texts in the code.

<br>

## Languages of files

- P05 -- In code documents, all variable names, function names and code comments are in English.
- P06 -- READMEs in subfolders are in English.
- P07 -- Plans and design documents are in German.

<br>

## Documentation

- P08 -- `README_deutsch_german.md` is in German and gives a short overview, folder structure and quick start only. `README.md` is only its English translation.
- P09 -- `DOCUMENTATION_deutsch_german.md` is in German and contains all information that is not in the READMEs and is relevant for a new user. `DOCUMENTATION.md` is only its English translation.
- P10 -- Applies only to the document pairs in the project folder (`README_deutsch_german.md` / `README.md`, `DOCUMENTATION_deutsch_german.md` / `DOCUMENTATION.md`): make changes in the German document first. Then ask the user for approval before updating the English translation.
- P11 -- If the German document and its English translation differ in content, point this out to the user.
- P12 -- When files or folders are added, moved or removed, update the folder tree in `README_deutsch_german.md` and the affected READMEs in subfolders in the same step (`README.md` see P10).
- P13 -- In documentation and communication use "webpage" instead of "website" or "site".
- P14 -- Put a deliberate blank line `<br>` before every heading. Exceptions: a heading directly below its parent heading, and the first heading of the file.
- P15 -- A changelog is kept in `CHANGELOG_deutsch_german.md` in German. Every change to project files gets an entry.

<br>

## Specification

- P16 -- The design documents are `design/Funktionsbeschreibung.md` (functional specification, requirements `Dnnn`) and `design/Technische-Umsetzung.md` (technical implementation, knowledge blocks `Tnnn`).
- P17 -- Requirement references in code comments use the form `// D111 dupe check`.

<br>

## Code

- P18 -- Plain HTML, CSS and JavaScript, no build step, no frameworks or libraries without the user's approval.
- P19 -- The app runs fully offline from the local file system (`file://`) in current Chrome: no CDN links, no web fonts, no network requests.

<br>

## Security and privacy

- P20 -- Never use call signs of real persons in documentation or example files, except for author or license declarations (see C18).
- P21 -- Logs of real contests must never be added to the repository.

<br>

## Testing

- P22 -- Test changes in the browser (Chrome) before reporting them as done.
