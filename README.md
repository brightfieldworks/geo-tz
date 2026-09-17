# geo-tz (PHP)

A PHP 8.2+ port of the `node-geo-tz` public API for finding the timezone at a GPS coordinate.

Original project: `node-geo-tz` by Evan Siroky (https://github.com/evansiroky/node-geo-tz).

## Licensing: MIT code, ODbL data

This package ships code and a database under **two different licences**:

- **Code** — the PHP sources in `src/`, `scripts/` and `tests/` are MIT
  licensed; see `LICENSE.md`.
- **Bundled timezone boundary data** — the files in `data/` are **not** MIT.
  They are derived from OpenStreetMap and licensed under the Open Data Commons
  Open Database License (ODbL) v1.0; see `DATA_LICENSE` for the full text.

Using or redistributing the `data/` files requires the ODbL attribution:

> Timezone boundary data (c) OpenStreetMap contributors, available under the
> Open Database License (ODbL v1.0).
> https://www.openstreetmap.org/copyright

`NOTICE.md` carries that attribution together with the full provenance chain
(OpenStreetMap -> timezone-boundary-builder -> node-geo-tz -> this mirror),
the upstream revisions and the SHA-256 of every bundled data file. All three
files (`LICENSE.md`, `DATA_LICENSE`, `NOTICE.md`) are included in the
distributed package archive, not only here on the web.

## Install

```bash
composer require mamluk/geo-tz
```

## Usage

Default dataset (1970 timezones):

```php
use GeoTz\GeoTz;

$tzids = GeoTz::find(47.650499, -122.35007);

// Optional: preload all features into memory
GeoTz::preCache();

// Optional: control caching
GeoTz::setCache(['preload' => true]);

// Optional: provide a Symfony cache pool or PSR-16 cache
use Symfony\Component\Cache\Adapter\FilesystemAdapter;
use Symfony\Component\Cache\Psr16Cache;

$pool = new FilesystemAdapter('geo_tz');
GeoTz::setCache(['store' => $pool]);

$psr16 = new Psr16Cache($pool);
GeoTz::setCache(['store' => $psr16]);
```

Full dataset (all timezones):

```php
use GeoTz\All\GeoTz as AllGeoTz;

$tzids = AllGeoTz::find(12.826174, 45.036933);
```

"Now" dataset (latest distinct zones):

```php
use GeoTz\Now\GeoTz as NowGeoTz;

$tzids = NowGeoTz::find(12.826174, 45.036933);
```

## Data updates

The data files are vendored under `data/`. `data/SOURCE.json` records the
`node-geo-tz` commit they were taken from, and `NOTICE.md` traces that commit
back to the timezone-boundary-builder release and its IANA tz release.

`composer update-data` refreshes them, but it downloads whatever currently
sits on the upstream `master` branch, so its result is not reproducible and it
must not be run as part of a build or deployment. Update the data by
reviewing a specific upstream revision, then committing the refreshed files
and `NOTICE.md` provenance and hashes together.

## Environment

Set `GEO_TZ_DATA_PATH` to point at an alternate directory containing the
`*.geo.dat` files if you want to store them outside the package.
