# Folder `data/`

**Project SEC-HTML-Logger** – reference data for the program.

Do not change the files in this folder without explicit permission (rule P03 in `CLAUDE.md`).

<br>

## Contents

```
data/
├── README.md                    # This file
├── sec-zip-list.csv             # Postal codes CH/FL with LV95 coordinates (derived, used by the program)
├── SEC2026_Relais-Liste.csv     # Relay list SEC 2026 (extracted from video)
├── SEC2026_Relais-Liste.md      # Same relay list as a Markdown table
└── raw/                         # Unchanged source files
    ├── ortschaftenverzeichnis_plz_2056.csv.zip    # swisstopo, LV95 (source of sec-zip-list.csv)
    ├── ortschaftenverzeichnis_plz_4326.csv.zip    # swisstopo, WGS84 (not used)
    └── SEC2026_relais-liste als video.mpg         # Source of the relay list (not in the repository)
```

<br>

## Postal code list `sec-zip-list.csv`

Postal codes (PLZ) of Switzerland and Liechtenstein with locality name and LV95 coordinates. Used for the fields MyZip (D058), ZIP Send (D026) and ZIP Rcvd (D074), and for the QRB distance calculation (D078).

| Column | Description |
|---|---|
| `zip` | 4-digit postal code |
| `town` | Locality name |
| `e` | LV95 east coordinate (E) in metres |
| `n` | LV95 north coordinate (N) in metres |

- Format: UTF-8 without BOM, `;`-separated, LF line endings, one header row.
- 4073 rows, sorted by `zip`, then `town`.
- One row per postal code + locality. A postal code can have several localities (e.g. `1000` with `Lausanne 25`, `Lausanne 26`, ...).
- If a locality spans several municipalities, the coordinates of the municipality with the largest address share (`Adressenanteil`) are used. On a tie, the first row of the source file wins.
- Coordinates are rounded to whole metres.

<br>

### Derivation

Source: `AMTOVZ_CSV_LV95.csv` in `raw/ortschaftenverzeichnis_plz_2056.csv.zip` (UTF-8 with BOM, `;`-separated, CRLF). Used source columns:

| Source column | Target column |
|---|---|
| `PLZ4` | `zip` |
| `Ortschaftsname` | `town` |
| `E` | `e` |
| `N` | `n` |
| `Adressenanteil` | only for selecting the municipality (see above) |

All other source columns (`Zusatzziffer`, `ZIP_ID`, `Gemeindename`, `BFS-Nr`, `Kantonskürzel`, `Sprache`, `Validity`) are dropped. Localities in Liechtenstein have no canton code in the source.

<br>

## Distance calculation (QRB)

LV95 coordinates are plane coordinates in metres (origin E = 2 600 000, N = 1 200 000 at the old observatory in Bern). Within Switzerland and Liechtenstein, the distance between two localities can therefore be calculated with Pythagoras:

- ΔE = difference of the two east coordinates
- ΔN = difference of the two north coordinates
- distance in metres = √(ΔE² + ΔN²)
- distance in kilometres = distance in metres / 1000

Example: `1003 Lausanne` (2 538 092 / 1 152 460) and `8001 Zürich` (2 683 368 / 1 247 416): ΔE = 145 276 m, ΔN = 94 956 m, distance = √(145 276² + 94 956²) ≈ 173 556 m ≈ 173.6 km.

The error of this plane calculation is negligible for contest purposes. The QRB is rounded to 0.1 km (D078 in `design/Funktionsbeschreibung.md`).

<br>

## Relay list `SEC2026_Relais-Liste.csv`

Relay list for SEC 2026, extracted by OCR from the video `raw/SEC2026_relais-liste als video.mpg`. `SEC2026_Relais-Liste.md` contains the same data as a Markdown table.

| Column | Description |
|---|---|
| `Route Name` | Relay name (call, location, frequency). Names ending with `...` are truncated as in the source. |
| `QRG TX` | Transmit frequency in MHz |
| `QRG RX` | Receive frequency in MHz |
| `Band Info` | Band (`2 m` or `70 cm`) |
| `UPS` | Flag `0` / `1` as given in the source |

- Format: UTF-8 without BOM, `,`-separated (names containing a comma are quoted), CRLF line endings, one header row, 166 relays.

<br>

## Source and license of the postal code data

**Source:** Federal Office of Topography swisstopo – *Amtliches Ortschaftenverzeichnis mit Postleitzahl und Perimeter*, https://www.swisstopo.admin.ch/de/amtliches-ortschaftenverzeichnis#Download

- `ortschaftenverzeichnis_plz_2056.csv.zip` (LV95): retrieved 2026-11-13.
- `ortschaftenverzeichnis_plz_4326.csv.zip` (WGS84): retrieved 2026-11-09.

The data is updated monthly by swisstopo.

**License:** Open Government Data – free use, source attribution required (© swisstopo).
