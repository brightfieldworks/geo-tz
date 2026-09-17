# NOTICE — code and bundled data are licensed differently

This package distributes two kinds of material under two different licences.
Both notices must be preserved in redistributions.

## Code — MIT

The PHP source (`src/`, `scripts/`, `tests/`) and the package metadata are
licensed under the MIT License. The full text is in `LICENSE.md`.

## Bundled timezone boundary data — ODbL v1.0

The files under `data/` are a database, not code, and are **not** covered by
the MIT licence. They are derived from OpenStreetMap and are licensed under
the Open Data Commons Open Database License (ODbL) v1.0. The full text is in
`DATA_LICENSE`.

Required attribution:

> Timezone boundary data © OpenStreetMap contributors, available under the
> Open Database License (ODbL v1.0).
> <https://www.openstreetmap.org/copyright>

Redistributing this package, or publicly using a work produced from the
`data/` files, carries the ODbL obligations: keep this attribution and the
licence text, and offer any publicly used adapted version of the database
under the ODbL.

## Provenance of the bundled data

| Stage | Source | Revision |
| --- | --- | --- |
| Boundary geometry | OpenStreetMap contributors | as consumed by the builder release below |
| Boundary builder | `evansiroky/timezone-boundary-builder` | release `2025c`, commit `932baf12f1df6fa0f2c387ba96e54e9cd5dfca26`, IANA tz release `2025c` |
| Geobuf packaging | `evansiroky/node-geo-tz` | commit `ed663141f27ffa7057c3cfd1a1c7438150631e9f` ("Update to 2025c data", 2026-01-13) |
| This mirror | `brightfieldworks/geo-tz` | data copied unchanged; recorded in `data/SOURCE.json` |

Every file under `data/` in this revision is byte-identical to the file at the
same path in `evansiroky/node-geo-tz` at
`ed663141f27ffa7057c3cfd1a1c7438150631e9f`. SHA-256 of each:

| File | SHA-256 |
| --- | --- |
| `data/SOURCE.json` | `2aec5ea26a3b2d7af857a28ba96e486c90514eea51db04098ad0e0b2db8cda38` |
| `data/timezones.geojson.geo.dat` | `8031d7f2376faa5a403cc5855341286dca68a1a1fbefdb43865ff821596d1036` |
| `data/timezones.geojson.index.json` | `d70bfdb766bfa8214c156b335f87342e2ad4bf97edecedf6d834f8b6d9dda9c1` |
| `data/timezones-1970.geojson.geo.dat` | `c79907aa8110109e0c3d95d41b119c068caaf22e8ba19a01d86618b3dd005334` |
| `data/timezones-1970.geojson.index.json` | `b4c7f798aef133b9325c2b625e49059585316a4cbf887221338642d5f649affc` |
| `data/timezones-now.geojson.geo.dat` | `400e47fa66a67cfd13044aafd6c3180d071c075ec26bc0c187c94df4762f81ae` |
| `data/timezones-now.geojson.index.json` | `64a23284daec1c8055a2d3668f7dc3769beef2c6a2d57427d164f9d4a07c2bff` |

`DATA_LICENSE` is a verbatim copy of `DATA_LICENSE` from
timezone-boundary-builder `2025c` (SHA-256
`064dbcd9fdd0ffdf36742c40718a23596be8a51838cb43b397f45d383ba42440`).

Upstream licence statements:

- <https://github.com/evansiroky/timezone-boundary-builder#licenses> — MIT code,
  ODbL output data.
- <https://github.com/evansiroky/node-geo-tz> — MIT code, redistributing the
  same ODbL data.
- <https://github.com/mamluk/geo-tz> — MIT PHP port this repository mirrors.
