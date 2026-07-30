# Verena Jewellery — Lab Grown Diamond Stock Tracking

Replaces `2026_LGD_Costing.xlsx`. Built to live on **OneDrive** so the shop and
the website team work from one list, on a computer or a phone.

**Prices are in US dollars. Rupiah is a reference conversion only.**

| File | What it is | Who uses it |
|---|---|---|
| **`Verena-Diamond-Stock.xlsx`** | The stock book. **The only place stock is recorded.** | Everyone |
| **`ONEDRIVE-SETUP.md`** | How to put it on OneDrive and open it on a phone | Owner, once |
| `showroom-lookup.html` | Optional fast search for a counter tablet — **look-up only** | Sales, optional |
| `sample-import.csv` | Example of the column layout | Reference |

---

## Setting a price — the answer to "how do I add prices?"

Four columns work together on the **Stock and Costing** tab:

| Column | What it does |
|---|---|
| `Suggested Price (USD)` | Automatic: adjusted cost × 5, exactly as your original sheet. |
| **`Your Price (USD)`** | **Type your own price here.** Cream = you type. |
| `Retail Price (USD)` | The price in force — what staff quote and customers see. |
| `Minimum Price (USD)` | The floor: adjusted cost × 2.5. |

- **Leave `Your Price` empty** → the stone is priced automatically at cost × 5.
- **Type a number into `Your Price`** → that becomes the Retail Price immediately.
  The Rupiah column, the Customer View and the Profit Summary all follow.
- **Delete what you typed** → back to the automatic price.
- **Type below the Minimum** → the cell turns red, and the Profit Summary counts
  how many stones are below their floor.

You can price a stone that has no cost recorded yet — type into `Your Price` and
it is sellable straight away. Its Minimum Price stays `ASK OWNER` until you enter
the Base Cost, and it stays out of the profit totals, so fill the cost in when
you know it.

---

## Currency

Every price, cost and profit figure is in **USD**. Beside each is a Rupiah
column, converted at the rate on the **Settings** tab, marked as reference.

A useful consequence: **your USD prices no longer depend on the exchange rate.**
In the old sheet a stale rate silently changed the minimum price you'd accept.
Now the rate only moves the reference columns.

**Recording a sale** stays in Rupiah — `Price Sold (Rp)` — because that is what
the shop actually takes and how your five existing sales are recorded.
`Price Sold (USD)` converts automatically. Say the word if you'd rather type sales
in USD instead.

---

## The six tabs

| Tab | Purpose |
|---|---|
| **Stock and Costing** | Every stone, one row. Specs, prices, cost, profit, margin. All typing happens here. Cream = type; grey = calculated; green = the two prices staff use. |
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

Everything else follows automatically. Rows are ready down to row 127.

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
