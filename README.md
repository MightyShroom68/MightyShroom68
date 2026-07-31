# Verena Jewellery — Lab Grown Diamond Stock Tracking

Replaces `2026_LGD_Costing.xlsx`. Built to live on **OneDrive** so the shop and
the website team work from one list, on a computer or a phone.

**Customers pay in Rupiah. Costs are in US dollars.** You can set a price in
either currency, and whichever you type is the real price — it never moves when
the exchange rate changes.

| File | What it is | Who uses it |
|---|---|---|
| **`Verena-Diamond-Stock.xlsx`** | The stock book. **The only place stock is recorded.** | Everyone |
| **`ONEDRIVE-SETUP.md`** | How to put it on OneDrive and open it on a phone | Owner, once |
| `showroom-lookup.html` | Optional fast search for a counter tablet — **look-up only** | Sales, optional |
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
| Set the Rupiah selling price | **N — `Your Price (Rp)`** |
| Set it in dollars instead | **O — `Your Price (USD)`** |
| Add a comment | **P — `Notes`** |
| Note a stone set into a mount | **Q — `Set Into / Frame`** |
| Fill in a missing cost | **R — `Base Cost (USD)`** |
| Mark something sold | **C — `Status`** |

Everything you type regularly is now within the first 18 columns. Cost workings
and profit analysis sit off to the right, out of the way.

---

## Setting a price — the answer to "how do I add prices?"

Four columns work together on the **Stock and Costing** tab:

| Column | What it does |
|---|---|
| `Suggested Price (USD)` | Automatic: adjusted cost × 5, exactly as your original sheet. |
| **`Your Price (Rp)`** | **Type the Rupiah price here** — column N, gold heading. |
| **`Your Price (USD)`** | Or set it in dollars — column O. |
| `Retail Price (Rp)` / `(USD)` | The price in force — what staff quote and customers see. |
| `Minimum Price (Rp)` / `(USD)` | The floor: adjusted cost × 2.5. |

- **Leave both `Your Price` columns empty** → priced automatically at cost × 5.
- **Type into `Your Price (Rp)`** → that exact Rupiah figure becomes the Retail
  Price, permanently, and the USD column shows today's equivalent.
- **Type into `Your Price (USD)`** → same the other way round.
- **Delete what you typed** → back to the automatic price.
- **Type below the Minimum** → the cell turns red, and the Profit Summary counts
  how many stones are below their floor.

You can price a stone that has no cost recorded yet — type into `Your Price` and
it is sellable straight away. Its Minimum Price stays `ASK OWNER` until you enter
the Base Cost, and it stays out of the profit totals, so fill the cost in when
you know it.

---

## Currency — and why a set price never drifts

Your costs are in USD (that's how you buy). Your customers pay in Rupiah.
Both are first-class here:

| Column | |
|---|---|
| **`Your Price (Rp)`** | The Rupiah price the customer actually pays. **Type it and it is fixed** — changing the rate on Settings will not move it. |
| **`Your Price (USD)`** | Set the price in dollars instead, if that's how you think about it. |
| `Retail Price (Rp)` / `(USD)` | The prices in force — what staff quote and the Customer View shows. |

The rule: **whichever currency you type in becomes the real price.** The other
one is worked out at the current rate. If you type neither, both come from
cost × 5.

So for a stone with a Rupiah price tag on it, type the Rupiah figure into
`Your Price (Rp)`. That number is then yours permanently — no rate change,
now or in a year, can alter it.

**Recording a sale** stays in Rupiah — `Price Sold (Rp)` — because that is what
the shop actually takes. `Price Sold (USD)` converts automatically.

**The minimum price does still move with the rate**, and that is deliberate:
it is your cost × 2.5, and your cost is genuinely in dollars. If the rupiah
weakens, the Rupiah figure you must clear to stay profitable really does rise.

---

## The six tabs

| Tab | Purpose |
|---|---|
| **Stock and Costing** | Every stone, one row. Specs, prices, cost, profit, margin. All typing happens here. Gold headings = what you type most; grey = calculated. |
| **Customer View** | Same stones, with cost, minimum price and margin stripped out. Price in USD with Rupiah beside it. Show or print **this** for customers. |
| **Profit Summary** | Cost tied up, revenue, profit, margin, best/weakest sale, per-supplier breakdown — USD with Rupiah alongside. |
| **Settings** | Exchange rate, the two multipliers, and the dropdown lists. |
| **How To Use** | Plain-language instructions, starting with how to set a price. |
| **Notes & Fixes** | Every problem found in the old file and what was done. |

Nothing is hidden — staff can see cost and margin, as you asked. The only rule to
teach them: **show customers the Customer View tab.**

### The two profitability measures — both kept

| Column | Formula | VD-009 reads |
|---|---|---|
| **Margin (Cost to Revenue)** — yours, unchanged | Price Sold ÷ Cost | **740%** (sold for 7.4× cost) |
| **Profit Margin %** — new | (Price Sold − Cost) ÷ Price Sold | **86.5%** (86.5¢ of every dollar is profit) |

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
to customers. You can price them now via `Your Price (USD)`; you still need the
cost for margins to work.

Also confirm the **exchange rate** on Settings (16,000 IDR/USD from your original).

---

## What the numbers should say today

Check these when you open it — if they match, every formula is working:

| | USD | Rupiah reference |
|---|---|---|
| VD-001 retail price | **$2,733.50** | Rp 43,736,000 |
| VD-001 minimum price | **$1,366.75** | Rp 21,868,000 |
| Revenue (5 stones sold) | **$11,875.00** | Rp 190,000,000 |
| Cost of those stones | $2,769.80 | Rp 44,316,800 |
| **Total profit** | **$9,105.20** | Rp 145,683,200 |
| Overall profit margin | 76.7% | — |
| Cost tied up in stock | $4,825.70 | Rp 77,211,200 |
| Retail value of stock | $24,128.50 | Rp 386,056,000 |
| Profit if all sold at retail | $19,302.80 | Rp 308,844,800 |

Stock figures cover the 7 unsold stones that have a cost.

---

## Adding new stock

One row on **Stock and Costing**:

> Stock No (`VD-022`…), Status, Shape, Carat, Colour, Clarity, Lab,
> Certificate No, Purchased Date, Supplier, Base Cost (USD), Adjustment —
> plus `Your Price (USD)` if you already know what it should sell for.

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
Suggested Price (USD)    = Adjusted Cost × 5          ← was "RRP"
Minimum Price (USD)      = Adjusted Cost × 2.5        ← was computed in Rupiah
Price per Carat (USD)    = Adjusted Cost ÷ Carat
Profit                   = Price Sold − Adjusted Cost
Margin (Cost to Revenue) = Price Sold ÷ Adjusted Cost
```

New:

```
Retail Price (USD) = Your Price if set, otherwise Suggested Price
Profit Margin %    = (Price Sold − Adjusted Cost) ÷ Price Sold
<anything> (Rp)    = the USD figure × exchange rate     (reference only)
```

The minimum price is arithmetically identical to your original — it applied ×2.5
to the Rupiah cost; this applies ×2.5 to the USD cost and converts. Same number.

See **Notes & Fixes** for the seven issues found in the old file, including
`#VALUE!` on every unsold row, `#DIV/0!` on placeholders, a hard-coded exchange
rate in two cells, and a customer price list covering only 16 of 28 stones.
