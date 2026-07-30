# Verena Jewellery — Lab Grown Diamond Stock Tracking

Replaces `2026_LGD_Costing.xlsx`. Built to live on **OneDrive** so the shop and
the website team work from one list, on a computer or a phone.

| File | What it is | Who uses it |
|---|---|---|
| **`Verena-Diamond-Stock.xlsx`** | The stock list. **This is the only place stock is recorded.** | Everyone |
| **`ONEDRIVE-SETUP.md`** | How to put it on OneDrive and open it on a phone | Owner, once |
| `showroom-lookup.html` | Optional fast search screen for a counter tablet — **look-up only** | Sales, optional |
| `sample-import.csv` | Example of the column layout | Reference |

---

## Start here

1. Read **`ONEDRIVE-SETUP.md`** and do Part 1 (10 minutes).
2. Send your sales staff Part 2 (5 minutes each).
3. Open the workbook's **How To Use** tab — it is written for someone who has
   never used Excel.

---

## What's inside the workbook

| Tab | Purpose |
|---|---|
| **Stock List** | What staff use all day. Green headings = type here. Grey = calculated. |
| **Costing** | *Hidden.* Base cost, supplier, profit, margin. Owner only. |
| **Settings** | Exchange rate and the two mark-up multipliers. Change one number, every price updates. |
| **How To Use** | Plain-language instructions for staff and for you. |
| **Notes & Fixes** | Every problem found in the old file and what was done about it. |

### The two numbers sales staff need
- **Retail Price (Rp)** — what to quote.
- **Minimum Price (Rp)** — the floor. Never sell below it without your approval.
  It is cost × 2.5, exactly as in your original sheet.

If either shows **`ASK OWNER`** in red, that stone has no cost recorded yet, so
there is no safe price. Staff are told not to quote it.

---

## ⚠️ Nine stones currently have no price

Items 13–21 of the old sheet had an empty **Base Cost** column, so the old file
was calculating their minimum price as **Rp 0**. A salesperson reading that sheet
could have given a stone away.

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

They now show `ASK OWNER` instead of Rp 0. **Please fill in their Base Cost on
the Costing tab** — that is the one thing needed before the file is complete.

Also confirm the **exchange rate** on the Settings tab (still 16,000 IDR/USD
from your original sheet). Every Rupiah price depends on it.

---

## Adding new stock

1. **Stock List** — next empty row: Stock No (`VD-022`…), Status, Shape, Carat,
   Colour, Clarity, Lab, Certificate No.
2. **Costing** — same Stock No in column A, then Purchased Date, Supplier,
   Base Cost (USD), Adjustment.

Prices appear by themselves. Rows are pre-formatted down to row 127 (120 stones);
the dropdowns and formulas are already there.

---

## The optional showroom lookup

`showroom-lookup.html` is a search screen for a counter tablet — type "2ct oval"
and get it instantly, which is much faster than filtering a spreadsheet on a
touchscreen.

It is **read-only on purpose**, so it can never disagree with the master file.
To use it: open the **Stock List** tab ▸ **File ▸ Save As ▸ CSV**, then load that
CSV into the page. It shows how old the data is and warns you after 3 days.

Reserving and selling always happens in the workbook.

> An earlier draft of this project was a browser app that stored stock in the
> browser itself. It was removed: browser storage does not sync through OneDrive,
> so every device would have held a different stock list. One file on OneDrive is
> the correct answer for a Family subscription.

---

## Formulas — unchanged from your original sheet

```
Adjusted Cost (USD) = Base Cost × (1 + Adjustment)
RRP (USD)           = Adjusted Cost × 5
Price per Carat     = Adjusted Cost ÷ Carat
Adj. Cost (Rp)      = Adjusted Cost × exchange rate
Minimum Price (Rp)  = Adj. Cost (Rp) × 2.5
Profit (Rp)         = Price Sold − Adj. Cost (Rp)
Margin              = Price Sold ÷ Adj. Cost (Rp)
```

One column is new: **Retail Price (Rp)** = RRP (USD) × exchange rate. Your old
sheet quoted retail in USD but the floor in Rupiah, so staff had to convert in
their heads. It works out to exactly 2× the minimum price.

See the **Notes & Fixes** tab for the six bugs found in the old file, including
`#VALUE!` errors on every unsold row and a hard-coded exchange rate in two cells.
