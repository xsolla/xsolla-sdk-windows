# Changelog

## 3.1.17 — 2026-06-30

### Fixed

- Login widget close event no longer fires before the token is received
- Restore now consumes all owned units of a multi-unit SKU; previously one per launch without the Events API
- `XsollaStoreClientPurchaseArgs.developerPayload` is now applied per purchase; previously the per-call override was ignored for the global payload
- A failed fetch no longer marks its SKUs as loaded (recorded only on success); the dedup cache is cleared on `Deinitialize` so a re-initialized client refetches

### Added

- `collapseRestoredMultiUnitPurchases` on `XsollaClientSettings` — collapse restored multi-unit SKUs into one quantity notification (`true`) or one per unit (`false`, default)
- `XsollaStoreClientExtensionsSettings.Builder.SetProductFetchSettings(...)` — per-SKU fetch tunables `maxItemsPerRequest`, `maxParallelRequests`, `cacheTtlMillis` (defaults 50 / 4 / 1h); `cacheTtlMillis` is ignored on standalone (no cache)
- `XsollaClientConfiguration.Builder.SetSkipMissingProductsOnFetch(bool)` — when `true` (default), skips backend-reported non-existent SKUs and fails only if all are missing

### Changed

- Per-SKU fetch retries transient failures (transport, 408/429/5xx) per the `QueryProducts` retry profile; a slow or failing batch no longer blocks sibling batches

## 3.1.14 — 2026-05-06

### Changed

- Improved auth token refreshing (takes social claims into account)

### Added

- Added `SetCustomPayStationProductionDomain` and `SetCustomPayStationSandboxDomain` builder methods — allow overriding the Pay Station domain for a single environment without affecting the other

### Fixed

- Fixed malformed URL when using custom PayStation domain

## 3.1.2 — 2026-03-11

- Initial public release of Xsolla SDK for Windows (C#)
- Targets: .NET 6.0, 7.0, 8.0, 9.0, .NET Standard 2.1
