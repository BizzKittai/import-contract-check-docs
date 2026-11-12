# Import Contract Check

**Release preparation:** the plugin is not yet available for purchase. Marketplace review and a real paid/trial activation test are still pending.

Check a CSV delivery against an explicit JSON contract inside IntelliJ IDEA. Find column drift, missing values, duplicate keys and type errors, navigate to the source location, and export a report with input hashes. Validation is local; no file upload, AI API, Python installation or database connection is required.

## Quick start

After installing the supported Marketplace release and activating a valid license or available trial:

1. Open **Tools → Import Contract Check** (also available from the project file context menu).
2. Select a saved UTF-8 CSV and its JSON contract. A neighbouring `filename.csv.icc.json` is selected automatically when opening the action for that CSV.
3. Select **Check import**. Results apply to the captured files; changed inputs need a new check.
4. Select an issue and **Open selected issue** to navigate to its line and column.
5. Use **Export JSON report** to save at a destination you choose. Input files remain unchanged.

Try the fictional [examples](examples). `products.csv` with `products.csv.icc.json` passes with two records and no issues. `products-invalid.csv` produces four issues on line 3: minimum price, invalid boolean, invalid date and duplicate key. These examples were tested in the private evaluation build; they do not demonstrate a Marketplace-activated paid license.

Read the [contract specification](CONTRACT.md), [privacy notice](PRIVACY.md) and [license terms](EULA.md).

## Scope and compatibility

Header drift; required values; integers, decimals, booleans and calendar dates; allowed values; numeric bounds; unique fields and composite keys of up to eight fields. UTF-8 with optional BOM; comma, semicolon, pipe or tab separators.

Maximum 10 MiB CSV, 100,000 data records, 128 columns, 1,000,000 cells and 100,000 characters per cell. Up to 500 issues; reaching a limit marks the result incomplete. Reports omit data-cell values and input paths but include headers, positions and hashes, which may still be sensitive.

Tested by hand in **IntelliJ IDEA Community Edition 2025.2.6.4, build 252.28539.149, on macOS ARM64**. From version 1.0.1 the plugin installs in IntelliJ-based IDEs from 2025.2 onwards; that version was checked with the JetBrains Plugin Verifier against IntelliJ IDEA 2025.2.6.4, 2025.3.6.2, 2026.1.5.1, 2026.2.4 and 2026.3. Other products and operating systems have not been tested by hand. Passing declared rules does not establish business correctness or guarantee that an importer will accept the file.

No spreadsheet import, automatic schema inference, automatic data repair, remote validation or CI service is included.

## Support and vendor

Email **hello@bizzkitt.ai** with the plugin version, IDE build, rule identifier and a minimal fictional example. Do not post production data, credentials or bank information. Response targets: critical requests within two business days; other requests within five business days. These are response targets, not guaranteed fix times.

BizzKitt BV, Frederikstraat 67, 3034 LD Rotterdam, Netherlands. Dutch business register number 42149345. [Marketplace vendor](https://plugins.jetbrains.com/vendor/bizzkitt).

This repository contains public documentation and fictional examples. It does not contain the proprietary plugin source or a license bypass. Documentation and examples © 2026 BizzKitt BV. You may copy and adapt the fictional examples for your own contracts.
