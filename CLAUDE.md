# CLAUDE.md — Verena Jewellery price list

Project memory for Claude Code sessions in this repo. Read before touching the workbook.

## ⚠️ This repository is PUBLIC

`MightyShroom68/MightyShroom68` is the owner's GitHub **profile** repo (owner name == repo
name), so it has been public since 2021. It is being used as a working repo for Verena
Jewellery business files anyway.

Consequences for you:

- **Never write prices, cost basis, margins, supplier terms, tokens or customer data into a
  file you commit** — including this one. Describe structure, not numbers.
- The committed `.xlsx` files already contain all of that. That exposure predates this file
  and is the owner's call to resolve; do not quietly "fix" it by rewriting history.
- The owner intended to flip it to Private (Settings → General → Danger Zone). As of
  2026-11-17 that had not happened. Worth re-checking and re-raising once, not nagging.

## The deliverable

`TEST_13.08.26_Price_List_LM_VERENA_TEST.xlsx` — Verena Jewellery's gold bar (logam mulia)
price list. Branch: `claude/antam-price-comparison-x04pdy`, open as PR #1.

### Sheets

| Sheet | Role |
|---|---|
| `HARGA LM VERENA` | Master price engine. Computes each brand × weight from a base cost cell plus a per-size premium. |
| `HARGA LM VERENA CV` | Customer-facing mirror of the above; cells just reference it. |
| `Rumus Harga` | The premium/markup inputs. Yellow cells only — the sheet says so in B3. |
| `EMASKU RS CV` | Emasku comparison sheet: our price vs the brand's website price. |
| `Emasku Gold Price JSON LIVEDATA` | Hidden. Power Query feed, `hrtagold.id/api/v1/brandings/price/daily`. |
| `ANTAM RS CV` | **Built in this task.** Antam equivalent of `EMASKU RS CV`. |
| `Antam Gold Price JSON LIVEDATA` | **Built in this task.** Hidden. Placeholder for the Antam feed. |

### How `ANTAM RS CV` works

Rows 10–19 cover 0,5 g to 100 g (Verena stocks no Antam above 100 g; 4 g shows `-`).

- **C** — our price. `SUMPRODUCT('HARGA LM VERENA CV'!C<row>)-G<row>`. Column C of that sheet
  is Antam Certieye 2026, the variant that matches what logammulia.com actually sells.
- **D** — official website price, looked up **by weight**, never by row position:
  `IFERROR(INDEX(<livedata>!$D$2:$D$200, MATCH($H<row>, <livedata>!$C$2:$C$200, 0)), "-")`
- **E** — `IFERROR(C-D,"-")`. Negative means we are cheaper.
- **F, G, H** hidden: F = premium from `Rumus Harga`, G = reseller discount (**0** by owner's
  decision — column C is therefore the real CV price), H = numeric weight, the MATCH key.

The data sheet's contract is deliberately minimal: **weight in column C, price in column D,
from row 2 down.** Any source satisfying that works — hand-typed or query-driven.

## Traps — read before editing the workbook

1. **Never round-trip this file through openpyxl.** It silently destroys the Emasku Power
   Query (`xl/connections.xml`, `xl/queryTables/`), the in-cell product images
   (`xl/metadata.xml` + `xl/richData/*` — cells with `t="e" vm="N"`), and `customXml`.
   Edit the OPC zip directly instead. `scratchpad/build.py` in the session that created
   these sheets did exactly that; openpyxl is fine for *reading*.
2. **LibreOffice cannot open this workbook** in the cloud sandbox — it times out, on the
   original too. So `recalc.py` is unavailable. Verify formulas against Excel's own cached
   values (`load_workbook(data_only=True)` on the pre-edit file) instead.
3. **Locale.** The 0,5 g weight labels are the *text* `"0,5"`, and the master sheet
   multiplies by them. That only evaluates in a comma-decimal locale. The owner fixed this in
   Excel's advanced settings; don't "helpfully" force a recalculation without knowing that
   setting still holds. Lookups use hidden column H precisely to avoid depending on it.
4. **Weight-based lookup is load-bearing.** A Power Query rewrites its whole table on every
   refresh. Positional references would silently pair 1 g against the 10 g price.
5. Do not copy `EMASKU RS CV`'s sheet protection onto the Antam sheets; they were left
   unprotected deliberately.

## Open item: the Antam live feed

**Not built.** The prices in `Antam Gold Price JSON LIVEDATA` are hand-typed, dated
13 Aug 2026, and badly stale.

Why it was not wired from inside a Claude session:

- Antam publishes **no JSON API**. Emasku's feed works only because Hartadinata exposes one.
- The workbook's `DataMashup` blob (`customXml/item1.xml`) is laid out as
  `[version][package.zip][permissions][metadata][permission-bindings]`. That last section is
  ~294 bytes of **signed** data covering the package. Edit `Formulas/Section1.m` and it no
  longer matches; Excel then "repairs" the file and **drops every query, including the
  working Emasku one.** It cannot be regenerated offline. Hand the owner M text to paste
  through Excel's UI, which regenerates the bindings correctly.
- The sandbox's egress proxy blocks `logammulia.com` and every third-party gold API, so no
  endpoint can be tested from here.

**The page is scrapeable.** It is server-rendered HTML — confirmed from a maintained
open-source scraper that reads it with cheerio (a static parser that cannot run JavaScript):

```
table.table.table-bordered:nth-of-type(1) tbody tr
  td:nth-child(1) = Berat        ("0,5 gr")
  td:nth-child(2) = Harga Dasar
```

Rows 3–14 of that table are the "Emas Batangan" block (0,5 g → 1000 g). Gift Series, Imlek
and Batik blocks follow with **repeating weights**, so take the first 12 gram rows only.

Owner's route: Data → Get Data → **From Web** → `https://www.logammulia.com/id/harga-emas-hari-ini`
→ pick the gold table → load to `='Antam Gold Price JSON LIVEDATA'!$A$1` → tick "Refresh data
when opening the file".

**Rejected:** `logam-mulia-api.iamutaki.workers.dev/api/prices/logammulia`. Its config does
`(weightMatch?.[0] ?? '1')`, so a failed parse silently defaults weight to **1**. Their own
committed backup has the 0,5 g bar and the 1 g bar both recorded as weight 1, with different
prices. It would have mispaired the comparison.

## Decisions already made — don't relitigate

- **Reseller discount = 0.** The Emasku sheet marks down a flat 5.000/gram; the owner chose
  not to mirror that. Hence subtitle `-HARGA CV-`, not `-RESELLER PRICE-`.
- **Column E reads "Selisih Harga (- = Lebih Murah)"**, not Emasku's "Lebih Murah", because
  Verena is *more expensive* than the Antam website at 0,5 g and 1 g. Switching the header to
  match Emasku would put a positive number under a word promising a discount. If those two
  sizes ever get repriced, the header can change.
- **The live-data sheet is hidden**, mirroring Emasku.
- **Comparison stops at 100 g.** The 250/500/1000 g rows were all `-`.
- Git history is kept as-is; no purge.

## Open questions for the owner

1. Repo still public — flip to Private?
2. Do 0,5 g and 1 g get repriced so Verena is genuinely cheaper across the board?
3. Wire the Power Query, or keep updating the hidden sheet by hand?
