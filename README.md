# Verena Jewellery — Lab Grown Diamond Stock Tracking

Replaces `2026_LGD_Costing.xlsx`. Built to live on **OneDrive** so the shop and
the website team work from one list, on a computer or a phone.

| File | What it is | Who uses it |
|---|---|---|
| **`Verena-Diamond-Stock.xlsx`** | The stock book. **The only place stock is recorded.** | Everyone |
| **`ONEDRIVE-SETUP.md`** | How to put it on OneDrive and open it on a phone | Owner, once |
| `showroom-lookup.html` | Optional fast search for a counter tablet — **look-up only** | Sales, optional |
| `sample-import.csv` | Example of the column layout | Reference |

---

## Start here

1. Read **`ONEDRIVE-SETUP.md`** and do Part 1 (10 minutes).
2. Send your sales staff Part 2 (5 minutes each).
3. Open the workbook's **How To Use** tab — written for someone who has never
   used Excel.

---

## The six tabs

| Tab | Purpose |
|---|---|
| **Stock and Costing** | Every stone, one row each. Specs, prices, cost, profit, margin. All typing happens here. Cream columns = type; grey = calculated and locked. |
| **Customer View** | The same stones with cost, minimum price and margin stripped out. Show or print **this** one for customers. Fills itself in. |
| **Profit Summary** | Cost tied up, revenue, profit, margin %, best and weakest sale, breakdown by supplier. All formulas. |
| **Settings** | Exchange rate and the two multipliers, plus the dropdown lists. |
| **How To Use** | Plain-language instructions for staff and for you. |
| **Notes & Fixes** | Every problem found in the old file and what was done about it. |

Nothing is hidden — your staff can see cost and margin, as you asked. The
customer-facing list is a separate tab rather than a separate permission, so the
only thing to remember is: **show customers the Customer View tab.**

### The two profitability measures — both kept

| Column | Formula | VD-009 reads |
|---|---|---|
| **Margin (Cost to Revenue)** — yours, unchanged | Price Sold ÷ Cost | **740%** (sold for 7.4× cost) |
| **Profit Margin %** — new | (Price Sold − Cost) ÷ Price Sold | **86.5%** (86.5 sen of every rupiah is profit) |

Your original column measures revenue *against* cost, which is why it reads in
the hundreds of percent. The new one is what most people mean by "margin". Both
sit side by side so nothing you had is lost.

### What staff quote
- **Retail Price (Rp)** — quote this.
- **Minimum Price (Rp)** — the floor, cost × 2.5 exactly as your original sheet.
- **`ASK OWNER`** in red — no cost recorded, so no safe price. Do not quote.

---

## ⚠️ Nine stones still have no cost

Items 13–21 had an empty **Base Cost** column, so your old file calculated their
minimum price as **Rp 0** — a salesperson reading that sheet could have given a
stone away.

| Stock No | Shape | Carat |
|---|---|---|
| VD-013 | Heart Brilliant | 2.09 |
| VD-014 | Oval Brilliant | 1.59 |
| VD-015 | Princess Cut | 2.10 |
| VD-016 | Round Brilliant | 1.19 |
| VD-017 | Round Brilliant | 1.09 |
| VD-018 | Round Brilliant | 1.10 |
| VD-019 | Oval Brilliant | 1.06 |
| VD-020 | Princess Cut | 1.55 |
| VD-021 | Princess Cut | 1.55 |

They now read `ASK OWNER`, are excluded from every Profit Summary total, and show
as "On request" to customers. **Filling in their Base Cost is the one thing needed
before the file is complete.**

Also confirm the **exchange rate** on Settings (still 16,000 IDR/USD from your
original). Every Rupiah figure depends on it.

---

## What the Profit Summary should say today

Check these when you open it — if they match, every formula is working:

| | |
|---|---|
| Stones sold | 5 |
| Revenue | Rp 190,000,000 |
| Cost of those stones | Rp 44,316,800 |
| **Total profit** | **Rp 145,683,200** |
| Overall profit margin | 76.7% |
| Margin (Cost to Revenue) | 428.73% |
| Best single profit | Rp 64,862,400 (VD-009) |
| Weakest margin | 63.4% (VD-006) |
| Cost tied up in stock | Rp 77,211,200 |
| Retail value of stock | Rp 386,056,000 |

Stock figures cover the 7 unsold stones that have a cost; the 9 without one are
excluded until you fill them in.

---

## Adding new stock

One row on **Stock and Costing** — that's it:

> Stock No (`VD-022`…), Status, Shape, Carat, Colour, Clarity, Lab,
> Certificate No, Purchased Date, Supplier, Base Cost (USD), Adjustment

Prices, profit, the Customer View row and the Profit Summary all follow
automatically. Rows are pre-formatted with dropdowns and formulas down to row 127
(120 stones).

---

## The optional showroom lookup

`showroom-lookup.html` is a search screen for a counter tablet — type "2ct oval"
and get it instantly, faster than filtering a spreadsheet on a touchscreen.

It is **read-only on purpose** so it can never disagree with the master file. To
use it: **Stock and Costing** tab ▸ **File ▸ Save As ▸ CSV**, then load that CSV
into the page. It shows how old the data is and warns you after 3 days.

Reserving and selling always happens in the workbook.

> An earlier draft of this project stored stock in the browser itself. It was
> removed: browser storage does not sync through OneDrive, so every device would
> have held a different stock list.

---

## Formulas — unchanged from your original sheet

```
Adjusted Cost (USD) = Base Cost × (1 + Adjustment)
RRP (USD)           = Adjusted Cost × 5
Price per Carat     = Adjusted Cost ÷ Carat
Adj. Cost (Rp)      = Adjusted Cost × exchange rate
Minimum Price (Rp)  = Adj. Cost (Rp) × 2.5
Profit (Rp)         = Price Sold − Adj. Cost (Rp)
Margin (Cost to Revenue) = Price Sold ÷ Adj. Cost (Rp)
```

Two columns are new:

```
Retail Price (Rp) = RRP (USD) × exchange rate      (= 2 × minimum price)
Profit Margin %   = (Price Sold − Adj. Cost (Rp)) ÷ Price Sold
```

See **Notes & Fixes** for the six bugs found in the old file — `#VALUE!` on every
unsold row, `#DIV/0!` on placeholders, a hard-coded exchange rate in two cells,
and a customer price list that only covered 16 of 28 stones.
