# Verena Jewellery — Lab Grown Diamond Stock Tracking

Replaces `2026_LGD_Costing.xlsx`. Built to live on **OneDrive** so the shop and
the website team work from one list, on a computer or a phone.

**Every selling price is in Rupiah.** US dollars appear in one place only:
what we pay the supplier.

| File | What it is | Who uses it |
|---|---|---|
| **`Verena-Diamond-Stock.xlsx`** | The stock book. **The only place stock is recorded.** | Everyone |
| **`ONEDRIVE-SETUP.md`** | How to put it on OneDrive and open it on a phone | Owner, once |
| `showroom-lookup.html` | Optional fast search for a counter tablet — **look-up only** | Sales, optional |
| **`LIVE-RATE.md`** | Connecting the USD rate to a live feed (2 minutes) | Owner, once |
| `sample-import.csv` | Example of the column layout | Reference |

---

## Nothing is locked

There is no password and no protection on any sheet. Type in any cell, add
stones, change any price. The colour of a heading tells you what a column does:

| Heading colour | Meaning |
|---|---|
| **Gold** | The columns you type in most — Your Price, Set Into / Frame, Notes, Base Cost |
| Green | Other things you type — status, specs, sale details |
| Dark green | The two prices staff quote — calculated |
| Grey | Works itself out — a formula |

If you type over a grey column you replace its formula for that stone. To repair
it: copy the same cell from the row above and paste it back, or use Undo. If it
already saved, OneDrive keeps **Version history** (right-click the file on
onedrive.com) — that's your real undo.

---

## Where do I type?

The **Stock and Costing** tab has a gold line above the headings naming the exact
column for each job:

| I want to… | Column |
|---|---|
| Set the selling price (Rp) | **L — `Your Price (Rp)`** |
| Add a comment | **M — `Notes`** |
| Note a stone set into a mount | **N — `Set Into / Frame`** |
| Fill in a supplier cost (USD) | **O — `Base Cost (USD)`** |
| Lock a stone's exchange rate | **P — `Rate Used (IDR/USD)`** |
| Mark something sold | **C — `Status`**, then **Q — `Price Sold (Rp)`** |

Everything you type regularly is now within the first 18 columns. Cost workings
and profit analysis sit off to the right, out of the way.

---

## Setting a price

| Column | What it does |
|---|---|
| `Suggested Price (Rp)` | Automatic: cost in Rupiah × 5. |
| **`Your Price (Rp)`** | **Type the selling price here** — column L, gold heading. |
| `Retail Price (Rp)` | The price in force — what staff quote and customers see. |
| `Minimum Price (Rp)` | The floor: cost in Rupiah × 2.5, exactly as your original sheet. |

- **Leave `Your Price (Rp)` empty** → priced automatically at cost × 5.
- **Type a Rupiah figure** → that becomes the Retail Price, and it is **fixed**.
  Changing the exchange rate will not move it.
- **Delete it** → back to the automatic price.
- **Type below the Minimum** → the cell turns red, and the Profit Summary counts
  how many stones are under their floor.

You can price a stone before its supplier invoice arrives — type into
`Your Price (Rp)` and it is sellable today. Its Minimum Price stays `ASK OWNER`
until you enter `Base Cost (USD)`, and it stays out of the profit totals.

---

## Currency — the rule

**Rupiah is the money customers pay us. Dollars are the money we pay suppliers.**
The file now enforces that:

| In Rupiah — everything the customer touches | In USD — only what we pay suppliers |
|---|---|
| Retail Price · Minimum Price · Your Price | Base Cost |
| Suggested Price · Price Sold · Profit | Adjusted Cost |
| Everything on the Customer View | Price per Carat (a buying yardstick) |

There is **no dollar selling price anywhere** — the ones an earlier draft carried
have been removed.

The two currencies meet in exactly one column: **`Adj. Cost (Rp)`**, which
converts the supplier cost into Rupiah at the Settings rate so profit and margin
can compare the Rupiah you took against the Rupiah that stone cost you. That is
precisely what your original sheet did.

### The rate can be live, and history stays frozen

Each stone carries its own **`Rate Used (IDR/USD)`** (column P). All 21 existing
stones are locked at **16,000** — the rate their figures were built on — so
changing the live rate on Settings **cannot move a finished sale**.

Without that lock, switching to today's rate would have cut your recorded profit
by **Rp 5,359,563** on sales already banked. Now:

| | |
|---|---|
| Existing stones (`Rate Used` = 16,000) | frozen — profit never changes |
| New stones (`Rate Used` blank) | follow the live rate on Settings |
| A selling price you typed | never moves, ever |

When a new stone is settled, type the rate into column P to lock it too.

**Settings B7** records when the rate was last updated and **B8 turns red** once
it is more than 30 days old.

---

## The six tabs

| Tab | Purpose |
|---|---|
| **Stock and Costing** | Every stone, one row. Specs, prices, cost, profit, margin. All typing happens here. Gold headings = what you type most; grey = calculated. |
| **Customer View** | Same stones, with cost, minimum price and margin stripped out. Price in Rupiah. Show or print **this** for customers. |
| **Profit Summary** | Cost tied up, revenue, profit, margin, best/weakest sale, per-supplier breakdown — in Rupiah, with a USD column only for money paid to suppliers. |
| **Settings** | Exchange rate, the two multipliers, and the dropdown lists. |
| **How To Use** | Plain-language instructions, starting with how to set a price. |
| **Notes & Fixes** | Every problem found in the old file and what was done. |

Nothing is hidden — staff can see cost and margin, as you asked. The only rule to
teach them: **show customers the Customer View tab.**

### The two profitability measures — both kept

| Column | Formula | VD-009 reads |
|---|---|---|
| **Margin (Cost to Revenue)** — yours, unchanged | Price Sold ÷ Cost | **740%** (sold for 7.4× cost) |
| **Profit Margin %** — new | (Price Sold − Cost) ÷ Price Sold | **86.5%** (86.5 sen of every Rupiah is profit) |

---

## Your original data is untouched

Every figure from `2026_LGD_Costing.xlsx` was compared field by field against
this workbook — purchase dates, shapes, carats, colours, clarities, certificate
numbers, suppliers, statuses, base costs, adjustments and all five recorded sale
amounts. **Nothing differs.** The Rupiah cost and minimum-price figures compute
to exactly the same numbers as your original (VD-001 → Rp 8,747,200 cost and
Rp 21,868,000 minimum, and so on for all 21 stones).

Two cosmetic edits I had made — `SOLD` → `Sold`, and `Marquies Shape` →
`Marquise Shape` — have been **reverted**. Your spellings stand exactly as you
typed them. Totals are unaffected either way, because Excel matches text without
regard to case.

> The shape dropdown still offers the corrected spelling "Marquise Shape". If you
> ever want the two old rows standardised, say so — I won't change them otherwise.

---

## ⚠️ Nine stones still have no cost

Items 13–21 had an empty **Base Cost**, so your old file calculated their minimum
price as **Rp 0** — a salesperson reading that could have given a stone away.

VD-013 (Heart 2.09ct) · VD-014 (Oval 1.59ct) · VD-015 (Princess 2.10ct) ·
VD-016 (Round 1.19ct) · VD-017 (Round 1.09ct) · VD-018 (Round 1.10ct) ·
VD-019 (Oval 1.06ct) · VD-020 (Princess 1.55ct) · VD-021 (Princess 1.55ct)

They read `ASK OWNER`, are excluded from the Profit Summary, and show "On request"
to customers. You can price them now via `Your Price (Rp)`; you still need the
cost for margins to work.

## ⚠️ Your exchange rate is about 12% stale

The rate carried over from the old sheet is **16,000**. The real rate in late
July 2026 is around **17,900–18,000**. Because the minimum price is cost × 2.5,
your floor is currently ~12% lower than it should be:

| | at 16,000 | at ~17,935 |
|---|---|---|
| VD-001 minimum | Rp 21,868,000 | **Rp 24,512,061** |
| VD-003 minimum | Rp 41,228,000 | **Rp 46,214,011** |

See **`LIVE-RATE.md`** to connect it to a live feed — about two minutes.

---

## What the numbers should say today

Check these when you open it — if they match, every formula is working:

| | Rupiah | USD paid to supplier |
|---|---|---|
| VD-001 retail price | **Rp 43,736,000** | — |
| VD-001 minimum price | **Rp 21,868,000** | — |
| Revenue (5 stones sold) | **Rp 190,000,000** | — |
| Cost of those stones | Rp 44,316,800 | $2,769.80 |
| **Total profit** | **Rp 145,683,200** | — |
| Overall profit margin | 76.7% | — |
| Cost tied up in stock | Rp 77,211,200 | $4,825.70 |
| Retail value of stock | Rp 386,056,000 | — |
| Profit if all sold at retail | Rp 308,844,800 | — |

Stock figures cover the 7 unsold stones that have a cost.

---

## Adding new stock

One row on **Stock and Costing**:

> Stock No (`VD-022`…), Status, Shape, Carat, Colour, Clarity, Lab,
> Certificate No, Purchased Date, Supplier, Base Cost (USD), Adjustment —
> plus `Your Price (Rp)` if you already know what it should sell for.

Everything else follows automatically — the Customer View row and the Profit
Summary update themselves. **You don't need to insert rows**; the next empty row
already has every formula and dropdown. There's room for **200 stones** (to row
207). When you need more, copy the last row and paste it into the rows below.

Changing availability is just the **Status** column: In Stock → Reserved → Sold.

The dropdowns are a shortcut, not a rule — if a new shape isn't listed, type it
in anyway. To make it permanent, add it to the bottom of that column on
**Settings**.

---

## The optional showroom lookup

`showroom-lookup.html` — a search screen for a counter tablet, faster than
filtering a spreadsheet on a touchscreen. **Read-only on purpose** so it can never
disagree with the master file. Export **Stock and Costing** ▸ **Save As ▸ CSV**,
then load that CSV into the page. It shows the data's age and warns after 3 days.

---

## Formulas

Unchanged from your original sheet:

```
Adjusted Cost (USD)      = Base Cost × (1 + Adjustment)
Adj. Cost (Rp)           = Adjusted Cost × exchange rate
Suggested Price (Rp)     = Adj. Cost (Rp) × 5        ← was "RRP", in USD
Minimum Price (Rp)       = Adj. Cost (Rp) × 2.5      ← identical to yours
Price per Carat (USD)    = Adjusted Cost ÷ Carat
Profit (Rp)              = Price Sold − Adj. Cost (Rp)
Margin (Cost to Revenue) = Price Sold ÷ Adj. Cost (Rp)
```

New:

```
Retail Price (Rp)  = Your Price (Rp) if set, otherwise Suggested Price (Rp)
Profit Margin %    = (Price Sold − Adj. Cost (Rp)) ÷ Price Sold
```

The minimum price is now literally your original formula: Adj. Cost in Rp × 2.5.

See **Notes & Fixes** for the seven issues found in the old file, including
`#VALUE!` on every unsold row, `#DIV/0!` on placeholders, a hard-coded exchange
rate in two cells, and a customer price list covering only 16 of 28 stones.
