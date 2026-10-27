# Alberta iGaming registry — monthly dataset snapshot, 2026-08

Deposit bundle for registry report issue 1, reporting period 13 July – 13 August 2026.
Report: https://albertabookies.com/registry-report/2026-08 · Live dataset: https://albertabookies.com/data

## Unit definitions

Two counts are easy to conflate and this bundle keeps them apart everywhere:

- **Brand row** — one consumer-facing brand. `registry-<period>.csv` and
  `brand-entity-map-<period>.csv` are counted in brand rows.
- **Legal entity** — one registered company in the AGLC register. A single entity may stand
  behind several brands, so the two numbers are never interchangeable.

As of 2026-10-18 the register holds **55 brand rows across 41 legal entities** in class `iGaming - Operator`.

In the AGLC export, `field_class_of_registration` is a **comma-separated list**: a registrant may
carry the operator class alongside supplier or platform classes. Membership must be tested against
the split list, not by string equality, or multi-class registrants are dropped from the count.

Gaming vertical (sportsbook / casino / both) is an editorial classification of each brand's
publicly advertised products; AGLC's register lists every entry under the single operator class.

## Files

| File | What it is | Provenance |
| --- | --- | --- |
| `registry-2026-08.csv` | Brand-row registry with ownership and live-status columns, exactly as published on https://albertabookies.com/data | copied byte-for-byte from `public/data/aglc-operators-2026-10-18.csv` |
| `live-status-2026-08.json` | Live-status layer: per-brand state, source URL and as-of date | copied byte-for-byte from `src/data/live-status.json` |
| `aglc-registrants-2026-08.csv` | The AGLC registrants database export, unmodified — last archive inside the period | copied byte-for-byte from `sources/aglc/gaming_registrants_db_2026-08-13.csv` |
| `brand-entity-map-2026-08.csv` | Brand to registered legal entity | derived from `src/data/aglc-registry.json` |
| `CHANGELOG-2026-08.md` | Every row added, removed or changed between consecutive archives, and every directory card added or removed | generated diff, no hand-written text |
| `report-2026-08.md` | The published report body | generated from the published issue |

## Sources

- AGLC gaming registrants database — https://aglc.ca/gaming-registrants
- AiGC approved-sites directory — https://www.abigaming.ca/operators/registered-igaming-sites/

Snapshots of both are archived with the date they were taken. The registrants export is the record
for registration; the directory is the record for whether a brand is taking Alberta play. The two
are separate facts and are never merged.

## Two-pass rules

Both directions require two consecutive daily passes before the dataset moves, because one pass is
not evidence:

- **Removal** — a row missing from a single export is treated as an export artifact. It is recorded
  as a removal only after it is absent on two consecutive passes.
- **Addition** — a new directory card is a candidate on first sight and is recorded live only after
  it is present on two consecutive passes.

## Licence and citation

Licensed CC BY 4.0 — https://creativecommons.org/licenses/by/4.0/

```
Vakoliuk, Aleksandr. "Alberta iGaming registry — month one." AlbertaBookies, registry report 2026-08, published 2026-08-13. https://albertabookies.com/registry-report/2026-08. Underlying dataset licensed CC BY 4.0.
```

The AGLC and AiGC source documents are the property of their respective publishers; this bundle
redistributes the AGLC export unmodified as the evidence behind the derived files, and the CC BY
licence covers the compilation and the derived files.
