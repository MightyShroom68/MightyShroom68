# Connecting the USD → IDR rate to a live feed

**Do this once. It takes about two minutes.**

---

## First, why this matters right now

Your sheet carried over a rate of **16,000** from the old file. The actual rate
in late July 2026 is around **17,900–18,000** — roughly **12% higher**.

That gap has a direct cost. Your minimum price is the stone's cost × 2.5, so at
a stale rate the floor is set ~12% too low:

| | at 16,000 (stale) | at ~17,935 (real) |
|---|---|---|
| VD-001 minimum price | Rp 21,868,000 | **Rp 24,512,061** |
| VD-003 minimum price | Rp 41,228,000 | **Rp 46,214,011** |

Every new stone you buy is being costed with the wrong rate too.

---

## Before you connect anything — your history is already protected

There is a column on **Stock and Costing** called **`Rate Used (IDR/USD)`**
(column P). Every one of your 21 existing stones is locked to **16,000** in it.

That means when you change the live rate, **nothing that already happened
moves**. Your five completed sales keep exactly the profit they have now:

| | | |
|---|---|---|
| VD-003 | Rp 33,508,800 | unchanged |
| VD-009 | Rp 64,862,400 | unchanged |
| **Total profit** | **Rp 145,683,200** | **unchanged** |

Without that lock, going live would have quietly cut your recorded profit by
**Rp 5,359,563** — money you have already banked. That would be wrong: you paid
those suppliers in 2024, at 2024's rate.

**New stones** you add have `Rate Used` blank, so they pick up the live rate
automatically. Once a stone is priced and settled, type the rate into that
column to lock it too.

---

## Method A — Currencies data type  ★ recommended

Works in Excel on Windows, Mac **and in the browser**, with your Microsoft 365
Family subscription.

1. Open the **Settings** tab. Cell **D5** already contains the text `USD/IDR`.
2. Click **D5**, then go to **Data ▸ Data Types ▸ Currencies**.
   A small bank icon appears in the cell.
3. Click cell **B3** and type:

   ```
   =D5.Price
   ```

   Press Enter. B3 now shows the live rate.
4. To update it later: **Data ▸ Refresh All**. Do this whenever you add stock.

> On phones the Excel app shows the last refreshed value rather than fetching a
> new one. That is fine — refresh on a computer now and then.

---

## Method B — Power Query  (auto-refreshes every time the file opens)

Windows Excel only, but it updates itself with no clicking.

1. **Data ▸ Get Data ▸ From Other Sources ▸ From Web**
2. Paste this address:

   ```
   https://api.frankfurter.app/latest?from=USD&to=IDR
   ```

3. Load the result, then point cell **B3** at the IDR value in the loaded table.
4. Right-click the query in the **Queries & Connections** pane ▸ **Properties**
   ▸ tick **"Refresh data when opening the file"**.

Frankfurter is a free service based on European Central Bank rates and needs no
account or API key.

---

## Method C — just type it

Perfectly fine if the other two are awkward.

1. Look up the rate (search "USD to IDR").
2. Type it into **Settings B3**.
3. Put today's date into **Settings B7**.

Cell **B8** shows how old the rate is and **turns red past 30 days**, so nobody
has to remember.

---

## After connecting: check nothing moved

Open **Profit Summary** and confirm **Total profit is still Rp 145,683,200**.
If it is, your history is intact and only new stock is using the live rate.

If it did change, something overwrote the `Rate Used` column — restore from
OneDrive **Version history** and check that column P still reads 16,000 for
VD-001 to VD-021.

---

## Should the minimum price move with the rate?

Right now it does not, for stones you already own — their floor is based on what
you actually paid.

There is an argument the other way: if you had to *replace* that stone today it
would cost ~12% more, so the floor arguably should rise. If you want that, the
simplest approach is to update `Rate Used` for unsold stones only, leaving sold
ones locked. Say the word and I can add a separate "replacement rate" that
drives minimum prices while keeping historical profit frozen.
