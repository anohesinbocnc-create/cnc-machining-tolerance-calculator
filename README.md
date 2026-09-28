# CNC Machining Tolerance Calculator (ISO 2768)

A free, dependency-free web tool for **general tolerances on CNC-machined parts**:

- **ISO 2768-1** — permissible deviations for linear dimensions, classes **f / m / c / v**
- **ISO 2768-2** — straightness & flatness tolerances, classes **H / K / L**

Enter a nominal dimension, pick a class, and the tool returns the ±deviation and the accepted
size range. It also highlights the matching row in the full reference table. Everything runs
client-side in a single `index.html` — no build step, no dependencies, no tracking.

**Live demo:** <https://anohesinbocnc-create.github.io/cnc-machining-tolerance-calculator/>
(enable GitHub Pages: *Settings → Pages → Deploy from branch → main / root*)

## Why ISO 2768?

Drawings that carry a general note such as `ISO 2768-mK` don't need every dimension individually
toleranced. This tool answers the everyday shop-floor question: *"for a 45.6 mm dimension under
ISO 2768-m, what deviation applies?"* — and shows the boundary case where the answer changes
(e.g. 120 mm belongs to the 30–120 mm range, not 120–400 mm).

ISO 2768 does **not** apply to mating features (use ISO 286 hole/shaft fits), individually
toleranced features, or chamfers/radii unless stated.

## Reference table — ISO 2768-1, linear dimensions (permissible deviations in mm)

| Nominal size range (mm) | f | m | c | v |
|---|---|---|---|---|
| 0.5 – 3 | ±0.05 | ±0.1 | ±0.2 | — |
| 3 – 6 | ±0.05 | ±0.1 | ±0.3 | ±0.5 |
| 6 – 30 | ±0.1 | ±0.2 | ±0.5 | ±1.0 |
| 30 – 120 | ±0.15 | ±0.3 | ±0.8 | ±1.5 |
| 120 – 400 | ±0.2 | ±0.5 | ±1.2 | ±2.5 |
| 400 – 1000 | ±0.3 | ±0.8 | ±2.0 | ±4.0 |
| 1000 – 2000 | ±0.5 | ±1.2 | ±3.0 | ±6.0 |
| 2000 – 4000 | — | ±2.0 | ±4.0 | ±8.0 |

Range convention: lower bound exclusive, upper bound inclusive.

## Reference table — ISO 2768-2, straightness & flatness (mm)

| Nominal length range (mm) | H | K | L |
|---|---|---|---|
| ≤ 10 | 0.05 | 0.10 | 0.20 |
| 10 – 30 | 0.10 | 0.20 | 0.40 |
| 30 – 100 | 0.20 | 0.40 | 0.80 |
| 100 – 300 | 0.30 | 0.60 | 1.20 |
| 300 – 1000 | 0.40 | 0.80 | 1.60 |
| 1000 – 3000 | 0.50 | 1.00 | 2.00 |

## Machine-readable data

For scripts, spreadsheets and AI/LLM tooling, the same tables ship as plain data files:

- [`data/iso-2768-1-linear.csv`](data/iso-2768-1-linear.csv)
- [`data/iso-2768-2-flatness.csv`](data/iso-2768-2-flatness.csv)
- [`data/iso-2768.json`](data/iso-2768.json) (both tables, with range semantics documented)

## Files

```
index.html                      # the whole app — open it locally, no server needed
data/iso-2768-1-linear.csv     # table 1 as CSV
data/iso-2768-2-flatness.csv   # table 2 as CSV
data/iso-2768.json             # both tables as JSON
```

## Sources & scope

Data transcribed from the published tables of **ISO 2768-1:1989** and **ISO 2768-2:1989**
(General tolerances). ISO standards are copyrighted; buy the official text from
[iso.org](https://www.iso.org/) if you need the full standard. This repository provides the
public summary tables and a calculation convenience tool, not the standard itself.

## Maintained by

[Sinbo Precision](https://www.sinbo-machining.com/) — CNC machining and precision
manufacturing in Dongguan, China (IATF 16949 / ISO 9001 / ISO 14001).

Related references on our site:

- [ISO 2768 general tolerances explained](https://www.sinbo-machining.com/wiki/tolerances/iso-2768)
- [GD&T fundamentals](https://www.sinbo-machining.com/wiki/tolerances/gdt)
- [515+ machined part families directory](https://www.sinbo-machining.com/parts/)

## Contributing

Found an error, or want more tables (ISO 2768-1 external radii & chamfer heights, ISO 286 fits)?
Open an issue or a pull request.

## License

[MIT](LICENSE)
