# Alberta iGaming registry — monthly dataset snapshot

Monthly snapshots of Alberta's public iGaming register, one folder per registry-report issue.
Each folder is the deposit bundle for that issue: the brand-row registry and live-status layer
published on https://albertabookies.com/data, the AGLC gaming registrants database export
redistributed unmodified, a brand-to-legal-entity map, a generated changelog of every row and
directory-card change between consecutive archives, and the published report body. Sources: the
AGLC gaming registrants database export series (https://aglc.ca/gaming-registrants) and the
archived AiGC approved-sites directory
(https://www.abigaming.ca/operators/registered-igaming-sites/).

Two counts are easy to conflate and this bundle keeps them apart everywhere:

- **Brand row** — one consumer-facing brand. `registry-<period>.csv` and
  `brand-entity-map-<period>.csv` are counted in brand rows.
- **Legal entity** — one registered company in the AGLC register. A single entity may stand
  behind several brands, so the two numbers are never interchangeable.

In the AGLC export, `field_class_of_registration` is a **comma-separated list**: a registrant may
carry the operator class alongside supplier or platform classes. Membership must be tested against
the split list, not by string equality, or multi-class registrants are dropped from the count.

A third unit, used only in the changelogs: a **directory card** is one entry on the AiGC
approved-sites directory. One brand row can have several cards, so card counts are never brand-row
counts either.

## DOI and citation

https://doi.org/10.5281/zenodo.23387646

```
Vakoliuk, Aleksandr. "Alberta iGaming registry — month three." AlbertaBookies, registry report 2026-10, published 2026-10-15. https://albertabookies.com/registry-report/2026-10. Underlying dataset licensed CC BY 4.0.
```

## Licence

CC BY 4.0 — https://creativecommons.org/licenses/by/4.0/ (legal code in `LICENSE`). The AGLC and
AiGC source documents are the property of their respective publishers; the bundles redistribute
the AGLC export unmodified as the evidence behind the derived files, and the CC BY licence covers
the compilation and the derived files.

## Layout

| Folder     | Issue | Zenodo record                                                                                                           | What the folder holds                                                                            |
| ---------- | ----- | ----------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------ |
| `2026-08/` | 1     | none                                                                                                                    | Bundle built 2026-10-27; see the note below                                                      |
| `2026-09/` | 2     | Alberta iGaming registry — monthly dataset snapshot, September 2026 (Issue 2) · https://doi.org/10.5281/zenodo.22777635 | The deposited files, byte-identical to the record's zip (md5 `ff99f7acbea5fe98a217f5b487655a32`) |
| `2026-10/` | 3     | Alberta iGaming registry — monthly dataset snapshot, October 2026 (Issue 3) · https://doi.org/10.5281/zenodo.23387646   | The deposited files, byte-identical to the record's zip (md5 `b1ab839acb5ff9cc6150b4a71c031163`) |

Each folder holds `README.md` (that bundle's own description), `registry-<period>.csv`,
`live-status-<period>.json`, `aglc-registrants-<period>.csv`, `brand-entity-map-<period>.csv`,
`CHANGELOG-<period>.md` and `report-<period>.md`.

## Reproducibility

Every file is built by `scripts/zenodo-bundle.mjs <period>` in the albertabookies repository. The
AGLC export and the changelog are rebuilt from the dated archives and come out byte-identical on
any later run. `registry-<period>.csv`, `live-status-<period>.json`, `brand-entity-map-<period>.csv`
and the bundle `README.md` are copies of the site's data layer as it stood on the day the bundle
was built, so they reproduce only from the repository at that day's commit. `report-<period>.md`
is rendered from the issue as published at build time, so a later correction to the issue changes
a rebuild (issue 2's correction of 2026-10-15 is not in the deposited `2026-09/` copy). Issue 1 was never
deposited and its bundle was first built on 2026-10-27: those four files in `2026-08/` describe the
data layer of 2026-10-27, not of the 2026-08 reporting period.

Data page: https://albertabookies.com/data
