# Fluid Network Studio verification benchmark set

Thirty-one benchmark cases for pipe network solvers, each with a cited reference value, the value
computed by [Fluid Network Studio](https://www.fluidnetworkstudio.com), the deviation and a pre-declared acceptance band.
Version 1.1, 18 November 2026.

This repository holds data only: the case table and this description. It is maintained by Haimi
Jordaan, the developer of Fluid Network Studio, so the computed values come from the software's
own solver. The solver itself is not open source. The full report, with the method and the
discussion of every deviation, is on Zenodo.

- **Report and data on Zenodo:** https://doi.org/10.5281/zenodo.22080506 (all versions)
- **Interactive version, solved live:** https://www.fluidnetworkstudio.com/verification

## The case table

`fluid-network-studio-verification-cases.csv` has one row per case:

| Column | Meaning |
|---|---|
| `case_id` | Stable identifier |
| `title` | What the case is |
| `group` | The section it sits in on the verification page |
| `reference_class` | Where the reference value comes from (below) |
| `comparison_leg` | `same-family` or `cross-code` (below) |
| `unit` | Unit of both values |
| `reference_value` | The reference |
| `computed_value` | What Fluid Network Studio computes |
| `abs_deviation` | The absolute difference |
| `rel_deviation_pct` | The difference as a percentage of the reference |
| `acceptance_band_pct` | The band the case must stay inside, declared in advance |
| `within_band` | `yes` when it does |
| `description` | The problem, in a sentence or two |

## Where the reference values come from

| Class | Cases | Leg |
|---|---|---|
| Closed-form analytical solution | 15 | same-family |
| Separate reference implementation | 2 | same-family |
| Independent engine (OWA-EPANET 2.2) | 4 | same-family |
| Independent engine (NASA GFSSP, published example) | 4 | cross-code |
| Published element coefficient | 4 | cross-code |
| Published textbook network benchmark | 1 | same-family |
| Published limiting correlation (von Karman fully rough limit) | 1 | cross-code |

The OWA-EPANET 2.2 and NASA GFSSP comparisons are independent checks, and the published classes
are as good as their publications.

The separate reference implementation, and the code that evaluates the closed-form references,
were written by the same author as the solver. They catch coding errors, but they are not
third-party checks.

## Two legs, never pooled

- **Same-family** (22 cases): the reference shares the solver's formulation. Largest deviation
  0.32%.
- **Cross-code** (9 cases): a different numerical method or an independently published
  correlation. Largest deviation 2.61%.

Every case is inside its band. This is verification, not validation: no case compares against
physical measurement.

## Citing it

See `CITATION.cff`, or cite the Zenodo record: Jordaan, H. (2026). *Verification of Fluid Network Studio: 31 benchmark cases against closed-form solutions, OWA-EPANET 2.2 and NASA GFSSP*
(Version 1.1). Zenodo. https://doi.org/10.5281/zenodo.22080506

## Licence

[CC BY 4.0](https://creativecommons.org/licenses/by/4.0/). See `LICENSE`.
