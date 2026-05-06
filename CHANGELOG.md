# Changelog

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
