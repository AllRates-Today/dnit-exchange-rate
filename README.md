# Dirección Nacional de Ingresos Tributarios (DNIT) Exchange Rates API — dnit-exchange-rate

[![npm version](https://img.shields.io/npm/v/dnit-exchange-rate.svg)](https://www.npmjs.com/package/dnit-exchange-rate)
[![license](https://img.shields.io/npm/l/dnit-exchange-rate.svg)](https://github.com/AllRates-Today/dnit-exchange-rate/blob/main/LICENSE)
[![zero dependencies](https://img.shields.io/badge/dependencies-0-brightgreen.svg)](https://www.npmjs.com/package/dnit-exchange-rate)
[![TypeScript](https://img.shields.io/badge/TypeScript-types%20included-3178C6.svg)](https://www.typescriptlang.org/)
[![USD/PYG today](https://img.shields.io/badge/dynamic/json?url=https%3A%2F%2Fallratestoday.com%2Fapi%2Fopen%2Fcentral-bank%2Fdnit%3Fsource%3DUSD%26target%3DPYG&query=%24.rate&label=USD%2FPYG%20official%2C%20Direcci%C3%B3n%20Nacional%20de%20Ingresos%20Tributarios%20(DNIT)&color=0A7E8C&cacheSeconds=3600)](https://allratestoday.com/tax-authority-rates-api/dnit/)
[![rate date](https://img.shields.io/badge/dynamic/json?url=https%3A%2F%2Fallratestoday.com%2Fapi%2Fopen%2Fcentral-bank%2Fdnit%3Fsource%3DUSD%26target%3DPYG&query=%24.rate_date&label=rate%20date&color=555&cacheSeconds=3600)](https://allratestoday.com/tax-authority-rates-api/dnit/)

**Official Dirección Nacional de Ingresos Tributarios (DNIT) (Paraguay) daily exchange rates for Node.js and TypeScript. The published tax authority rates behind tax filings, customs valuations, audits, and compliant invoicing — not market estimates, but the numbers Dirección Nacional de Ingresos Tributarios (DNIT) itself prints, every business day.**

## 🚀 Why this client?

- 🏛️ **Official rates** — Dirección Nacional de Ingresos Tributarios (DNIT)'s own table, with the publisher's own `rate_date` on every response
- 📅 **History back to 1996** — point-in-time tables and daily series for any past date
- 🔀 **Official vs derived, always flagged** — computed inverse/cross pairs carry `derived: true`, never mixed with official prints
- ⚡ **Zero dependencies** — pure ESM + CJS over global `fetch`; Node 18+, Bun, Deno, and edge runtimes
- 🔷 **Type-safe** — full TypeScript definitions shipped with the package
- 🧾 **Compliance-grade metadata** — `rate_type`, publication date, and source disclaimer on every response

> **Official rate, not mid-market:** every value here is a number Dirección Nacional de Ingresos Tributarios (DNIT) itself published, fixed once printed and carrying the tax authority's own `rate_date` — what filings and audits require. Need the live mid-market rate for pricing or display instead? Use the [mid-market API](https://allratestoday.com/docs/) or [`@allratestoday/sdk`](https://www.npmjs.com/package/@allratestoday/sdk). The two can diverge by several percent.

## 🔑 Get your API key

Get a free API key at [allratestoday.com/register](https://allratestoday.com/register) — no credit card required. Latest rates are on every plan, including free.

## 📈 Latest official table

[![Latest Dirección Nacional de Ingresos Tributarios (DNIT) table](https://allratestoday.com/api/open/central-bank/dnit/table.svg)](https://allratestoday.com/tax-authority-rates-api/dnit/)

The image is rendered live from the keyless endpoint, so it follows the tax authority's publications on npm and on GitHub alike without a new release. The same table as text is folded below for search and copy-paste: on GitHub [a daily Action](.github/workflows/daily-table.yml) refreshes it whenever the tax authority publishes a new table; on npm it is as of the package's publish date.

<!-- daily-table:start -->
<details>
<summary>Table as text: published 2026-11-27 by Dirección Nacional de Ingresos Tributarios (DNIT) — 30 rates. Updated 2026-11-27.</summary>

| Base | Quote | Type | Rate |
| --- | --- | --- | ---: |
| AED | PYG | reference | 1751.84 |
| ARS | PYG | reference | 4.02 |
| AUD | PYG | reference | 4268.66 |
| BOB | PYG | reference | 542.53 |
| BRL | PYG | reference | 1122.6 |
| CAD | PYG | reference | 4516.72 |
| CHF | PYG | reference | 7713.4 |
| CLP | PYG | reference | 6.19 |
| CNY | PYG | reference | 966.14 |
| COP | PYG | reference | 1.83 |
| DKK | PYG | reference | 944.83 |
| EUR | PYG | reference | 7061.24 |
| GBP | PYG | reference | 8433.72 |
| HKD | PYG | reference | 821.03 |
| HUF | PYG | reference | 18.98 |
| INR | PYG | reference | 69.6 |
| JPY | PYG | reference | 40.39 |
| KRW | PYG | reference | 4.78 |
| MXN | PYG | reference | 326.81 |
| NOK | PYG | reference | 659.86 |
| NZD | PYG | reference | 3520.96 |
| PEN | PYG | reference | 1854.32 |
| SEK | PYG | reference | 629.57 |
| SGD | PYG | reference | 4985.68 |
| THB | PYG | reference | 188.91 |
| TRY | PYG | reference | 126.97 |
| TWD | PYG | reference | 195.29 |
| USD | PYG | reference | 6434.52 |
| UYU | PYG | reference | 158.21 |
| ZAR | PYG | reference | 367.04 |

</details>

Source: [Official rates published by DNIT, served by AllRatesToday](https://allratestoday.com/tax-authority-rates-api/dnit/). Rates are as printed by the tax authority; AllRatesToday is not affiliated with it.
<!-- daily-table:end -->

## 📦 Installation

```bash
npm install dnit-exchange-rate
```

```bash
yarn add dnit-exchange-rate
```

```bash
pnpm add dnit-exchange-rate
```

Requires Node 18+ (global `fetch`); also runs on Bun, Deno and edge runtimes. Also published under the org scope as [`@allratestoday/dnit-exchange-rate`](https://www.npmjs.com/package/@allratestoday/dnit-exchange-rate) — same code, same versions.

## 🏁 Quick start

```js
import { getRate } from 'dnit-exchange-rate';

const pair = await getRate('USD', 'PYG', { apiKey: 'art_live_...' });
console.log(pair.rate, pair.rate_date); // the official Dirección Nacional de Ingresos Tributarios (DNIT) rate, on the tax authority's own date
```

## 📚 API reference

- [Latest pair rate](#latest-pair-rate) — one pair from the latest official table
- [Full official table](#full-official-table) — everything the tax authority printed, in one call
- [Table for a date](#table-for-a-date) — the official table for an invoice or filing date
- [Daily time series](#daily-time-series) — one pair across a date range

---

### Latest pair rate

Free plan and up. Pairs the tax authority does not print directly are resolved from its table and flagged (see *Official vs derived rates* below).

```js
const pair = await getRate('USD', 'PYG', { apiKey: 'art_live_...' });
```

**Response:**

```javascript
{
  bank: 'dnit',
  name: 'Dirección Nacional de Ingresos Tributarios (DNIT)',
  rate_date: '2026-11-25',   // Dirección Nacional de Ingresos Tributarios (DNIT)'s own publication date
  source: 'USD',
  target: 'PYG',
  rate: 6426.98,
  rate_type: 'reference',
  derived: false,
  method: 'published',
  disclaimer: 'Official rates as published by the named central bank. On weekends/holidays the most recent published rate_date is returned.'
}
```

### Full official table

Free plan and up. The complete table for the latest publication date.

```js
import { getLatestRates } from 'dnit-exchange-rate';

const table = await getLatestRates({ apiKey: 'art_live_...' });
console.log(table.rate_date, table.rates.length);
```

**Response:**

```javascript
{
  bank: 'dnit',
  name: 'Dirección Nacional de Ingresos Tributarios (DNIT)',
  rate_date: '2026-11-25',
  rates: [
    { "base": "USD", "quote": "PYG", "type": "reference", "value": 6426.98 },
    // … the rest of the official table (30 currencies vs PYG)
  ],
  disclaimer: '…'
}
```

### Table for a date

Paid plans. The official table for any date since 1996 — weekends and holidays return the most recent published date, flagged via `published_on_requested_date`, which is exactly the in-force rate a filing needs.

```js
import { getRatesForDate } from 'dnit-exchange-rate';

const day = await getRatesForDate('2026-06-30', { apiKey: 'art_live_...' });
// Optionally narrow to one pair:
const one = await getRatesForDate('2026-06-30', { apiKey: 'art_live_...', source: 'USD', target: 'PYG' });
```

**Response:**

```javascript
{
  bank: 'dnit',
  requested_date: '2026-06-30',
  rate_date: '2026-06-30',                // the date actually published
  published_on_requested_date: true,      // false when a weekend/holiday fell back
  rates: [ /* the full table for that date */ ],
  disclaimer: '…'
}
```

### Daily time series

Paid plans. One resolved rate per publication date — ready for charting, revaluation runs, or audit workpapers.

```js
import { getHistory } from 'dnit-exchange-rate';

const series = await getHistory(
  { source: 'USD', target: 'PYG', from: '2026-01-01', to: '2026-11-25' },
  { apiKey: 'art_live_...' }
);
```

**Response:**

```javascript
{
  bank: 'dnit',
  source: 'USD',
  target: 'PYG',
  from: '2026-01-01',
  to: '2026-11-25',
  count: 152,
  rates: [
    // one entry per publication date
    { date: '2026-11-25', rate: 6426.98, rate_type: 'reference', derived: false, method: 'published' },
    // …
  ],
  disclaimer: '…'
}
```

Pass `{ symbol: 'USD' }` instead of `source`/`target` to get the raw published rows for one currency (all rate types, no pair resolution).

---

## 🗺️ Currencies covered

Dirección Nacional de Ingresos Tributarios (DNIT) currently publishes rates covering **30 currencies** against the PYG (as of the latest table):

🇦🇪 `AED` · 🇦🇷 `ARS` · 🇦🇺 `AUD` · 🇧🇴 `BOB` · 🇧🇷 `BRL` · 🇨🇦 `CAD` · 🇨🇭 `CHF` · 🇨🇱 `CLP` · 🇨🇳 `CNY` · 🇨🇴 `COP` · 🇩🇰 `DKK` · 🇪🇺 `EUR` · 🇬🇧 `GBP` · 🇭🇰 `HKD` · 🇭🇺 `HUF` · 🇮🇳 `INR` · 🇯🇵 `JPY` · 🇰🇷 `KRW` · 🇲🇽 `MXN` · 🇳🇴 `NOK` · 🇳🇿 `NZD` · 🇵🇪 `PEN` · 🇸🇪 `SEK` · 🇸🇬 `SGD` · 🇹🇭 `THB` · 🇹🇷 `TRY` · 🇹🇼 `TWD` · 🇺🇸 `USD` · 🇺🇾 `UYU` · 🇿🇦 `ZAR`

## 🏛️ Source

The daily exchange rates Paraguay's tax and customs authority (DNIT, Dirección Nacional de Aduanas) sets for converting declared foreign-currency values into guaraníes. Customs uses the rate in force on the declaration date to compute the taxable value of imports and exports.

- Publisher's own page: [Daily exchange rates for customs and tax](https://www.dnit.gov.py/web/portal-institucional/cotizaciones-aduaneras) · [www.dnit.gov.py](https://www.dnit.gov.py/)
- Publication: every business day; the exact schedule, freshness status and any current delay are on the [Dirección Nacional de Ingresos Tributarios (DNIT) rates page](https://allratestoday.com/tax-authority-rates-api/dnit/)
- Values are stored unmodified, with the publisher's own `rate_date` on every row — see the [methodology](https://allratestoday.com/official-rates-methodology/)

## 🧭 Reading the numbers

- `value` is always **quote currency per 1 unit of base currency** (`base: "EUR", quote: "USD", value: 1.15` means 1 EUR = 1.15 USD).
- Dirección Nacional de Ingresos Tributarios (DNIT) quotes **PYG per 1 unit of foreign currency** (e.g. `base: "USD", quote: "PYG"` means PYG per one US dollar).
- Need the other way round? Ask `getRate(target, source)` and the API inverts or crosses for you, flagged `derived: true` — never divide a published rate yourself in a compliance workflow.
- `rate_type` tells you which of the tax authority's series a row belongs to (`reference` here); some publishers print buy/sell or several fixings for the same pair.

## 🧩 ERP & accounting systems

Loading the official Dirección Nacional de Ingresos Tributarios (DNIT) rate into an accounting system is a supported workflow, not a hack. Step-by-step guides with the direction each system expects:

- [Dynamics 365 Business Central](https://allratestoday.com/docs/integrations/business-central/) — built-in Currency Exchange Rate Service, no code
- [Xero](https://allratestoday.com/docs/integrations/xero/) · [QuickBooks Online](https://allratestoday.com/docs/integrations/quickbooks/) · [SAP S/4HANA and ECC](https://allratestoday.com/docs/integrations/sap/) · [Odoo](https://allratestoday.com/docs/integrations/odoo/)

The same keyed endpoints return `?format=csv`, `?format=xml` and `?format=xlsx`, and accept the key as `?api_key=` on the URL for importers that cannot send headers:

```bash
curl "https://allratestoday.com/api/v1/central-bank/dnit/latest?format=xml&api_key=art_live_..."
```

## 🤖 AI agents

- MCP server: `npx -y @allratestoday/central-bank-mcp` (stdio) or the hosted endpoint `https://allratestoday.com/api/mcp` — tools for official rates, history, cross-bank comparison and publication calendars
- Already using the general SDK or MCP server? Since 2026-10-01 [`@allratestoday/sdk`](https://www.npmjs.com/package/@allratestoday/sdk) 1.4+ has `officialRates('dnit')` and [`@allratestoday/mcp-server`](https://www.npmjs.com/package/@allratestoday/mcp-server) 0.6+ has a `get_official_rates` tool — both return this source's latest table with no key, so you can add it without a second dependency
- Claude Code plugin (no key): `/plugin marketplace add AllRates-Today/claude-code-plugin` then `/plugin install allratestoday@allratestoday` — bundles both MCP servers plus an `/official-rate dnit ...` command
- Evaluating? Agents can self-issue a trial key with no signup: `POST https://allratestoday.com/api/agent/keys` (send `Content-Type: application/json`) returns a 100-call key valid 7 days that covers the free-plan methods (latest table, pairs); dated tables and history need a [paid plan](https://allratestoday.com/pricing/). The MCP servers expose it as `request_trial_key`
- Machine-readable site guide: [llms.txt](https://allratestoday.com/llms.txt) · [for-ai-agents](https://allratestoday.com/for-ai-agents/)

## ⚖️ Official vs derived rates

If Dirección Nacional de Ingresos Tributarios (DNIT) does not print a pair directly, the API resolves it from the tax authority's own table and says so — official and computed values are never confused:

| `method` | `derived` | Meaning |
| --- | --- | --- |
| `published` | `false` | The tax authority printed this pair directly |
| `inverse` | `true` | Computed as 1 ÷ the published opposite direction |
| `cross` | `true` | Computed via PYG from two published rates |

## 🛡️ Error handling

Errors are thrown as `Error` with `status` (HTTP code) and `body` (the API's JSON error) attached:

```js
try {
  const pair = await getRate('USD', 'XXX', { apiKey: 'art_live_...' });
} catch (err) {
  console.log(err.message); // human-readable reason
  console.log(err.status);  // e.g. 404
}
```

| Status | Meaning |
| ------ | ------- |
| — | Missing `apiKey` (thrown before any request) |
| `400` | Malformed date or parameters |
| `401` | Invalid API key |
| `403` | Endpoint needs a [paid plan](https://allratestoday.com/pricing/) (historical dates & series) |
| `404` | Pair or date range not covered by Dirección Nacional de Ingresos Tributarios (DNIT) |
| `429` | Monthly quota exceeded |

## 🔷 TypeScript

Full definitions ship with the package — no `@types` install:

```ts
import type { LatestRates, PairRate, DatedRates, RateEntry, HistoryQuery, RequestOptions } from 'dnit-exchange-rate';
```

## 📦 CommonJS

```javascript
const { getRate } = require('dnit-exchange-rate');

getRate('USD', 'PYG', { apiKey: 'art_live_...' }).then((pair) => console.log(pair.rate));
```

## 💡 Quota tips

- Rates change once per business day — cache the official table locally and a small monthly quota goes a long way.
- Every request counts toward your AllRatesToday quota, shared across all AllRatesToday endpoints on your key.

## 📖 Methods reference

| Method | Plan | Description |
| ------ | ---- | ----------- |
| `getRate(source, target, { apiKey })` | Free | Latest rate for one pair, resolved from the official table |
| `getLatestRates({ apiKey })` | Free | The tax authority's full latest official table |
| `getRatesForDate(date, { apiKey, source?, target? })` | Paid | The official table (or one pair) for a YYYY-MM-DD date |
| `getHistory({ symbol \| source+target, from?, to? }, { apiKey })` | Paid | Daily series since 1996 |

## 📥 Bulk data (no key)

Need the whole archive rather than an API call? The same official tables are mirrored daily as open data:

- Hugging Face: [AllRatesToday/central-bank-exchange-rates](https://huggingface.co/datasets/AllRatesToday/central-bank-exchange-rates) — one CSV per institution (`rates/dnit.csv`)
- Kaggle: [allratestoday/central-bank-exchange-rates](https://www.kaggle.com/datasets/allratestoday/central-bank-exchange-rates)
- Raw JSON on GitHub: `https://raw.githubusercontent.com/AllRates-Today/central-bank-exchange-rates/main/data/dnit/latest.json`

## 🔗 Links

- **Website:** [allratestoday.com](https://allratestoday.com)
- [Dirección Nacional de Ingresos Tributarios (DNIT) rates page](https://allratestoday.com/tax-authority-rates-api/dnit/) — live table, publication cadence, FAQ
- [All tax authority sources](https://allratestoday.com/tax-authority-rates-api/) · [Full list of 120+ central banks and 50+ tax authorities](https://allratestoday.com/central-bank-rates-api/institutions/) — one API, the same response shape for every source
- [Download central bank rates](https://allratestoday.com/download-central-bank-rates/) — every bank's latest table and history as Excel, CSV or JSON
- [Bank Exchange Rate API](https://allratestoday.com/bank-exchange-rate-api/) — live buy and sell rates from 1,200+ commercial banks in 120+ countries · [npm](https://www.npmjs.com/package/bank-exchange-rates) · [GitHub](https://github.com/AllRates-Today/bank-exchange-rates)
- [Package docs on the site](https://allratestoday.com/docs/sdk/dnit-exchange-rate/) · [ERP integration guides](https://allratestoday.com/docs/integrations/)
- [API documentation](https://allratestoday.com/docs/#central-bank) · [Interactive reference](https://allratestoday.com/api-reference/) · [Methodology](https://allratestoday.com/official-rates-methodology/)
- [Register (Free)](https://allratestoday.com/register) · [Dashboard](https://allratestoday.com/profile) · [Pricing](https://allratestoday.com/pricing/)
- [Status](https://allratestoday.com/status)
- [Postman collection](https://allratestoday.com/postman/)
- [ChatGPT app](https://chatgpt.com/plugins/plugin_asdk_app_6ae1e76098f48191a285ac3f5ab7a83b) — ask ChatGPT for live and official central bank rates
- [OpenAPI reference on Bump.sh](https://bump.sh/allratestoday/doc/allratestoday-api) — also on [SwaggerHub](https://app.swaggerhub.com/apis-docs/allratestoday/allratestoday-exchange-rate-central-bank-rates-api/2.2.0)
- [GitHub](https://github.com/AllRates-Today/dnit-exchange-rate)

## 📜 License

MIT
