# Verena Jewellery — Diamond Stock Book

A dead-simple stock tracker for our lab-grown diamonds, built to replace the
Excel sheet. It runs in any web browser (shop computer, laptop, tablet, or
phone). **No installation, no login, no internet needed after it's opened.**

---

## For sales staff — how to use it (60 seconds)

Open **`index.html`** (double-click it, or tap the bookmark on the counter
tablet). That's it — everything is on one screen.

| I want to… | Do this |
|---|---|
| **Find a diamond** | Type in the search box (stock number, shape, certificate, customer name…). |
| **See only what's available** | Use the **All statuses** dropdown → *In Stock*. |
| **Add a new diamond** | Tap the gold **＋ Add Diamond** button, fill it in, **Save**. |
| **Sell a diamond** | Tap **Mark Sold** on its row, add the price/customer, **Confirm**. |
| **Hold one for a customer** | Tap **Reserve**. Tap **Un-reserve** to release it. |
| **Fix a mistake** | Tap **Edit** on the row. |

The coloured tiles at the top always show: how many are **in stock**,
**reserved**, **sold this month**, and the **total value** of current stock.

Colour on the left edge of each row = where it's listed:
🔵 Website · 🟡 Retail shop · 🟣 Both.

---

## For the shop owner — setup & housekeeping

### Bring in the current Excel list
1. In Excel, choose **File → Save As → CSV**.
2. In the app, tap **☰ More → ⬆️ Bring in my Excel file** and pick that CSV.

The importer matches columns automatically (Stock No, Carat, Colour, Clarity,
Cut, Lab, Certificate, Price, Status, etc.), so your existing headings usually
just work. See **`sample-import.csv`** for the ideal column layout.

### Back up your data (do this regularly!)
Tap **☰ More → ⬇️ Save a backup**. This downloads a CSV you can open in Excel
or keep as a safety copy.

> ⚠️ **Important:** the app saves diamonds *on the device/browser you use it in*
> (like notes saved on that computer). It does **not** automatically sync
> between the shop computer and the website. Pick **one main device** as the
> master stock book, and use the backup/import buttons to move data around or
> keep copies. A regular backup means you never lose anything.

### Try it first
Tap **☰ More → ✨ Load example diamonds** to see how it looks with data, then
**🗑️ Delete everything** when you're ready to start real entries.

### Print a stock list
Tap **☰ More → 🖨️ Print stock list** for a clean printout (buttons hidden).

---

## What's tracked per diamond
Stock number · Shape · Carat · Cut · Colour · Clarity · Lab (IGI/GIA/…) ·
Certificate number · Price · Where it's listed (Website / Retail / Both) ·
Status (In Stock / Reserved / Sold) · Customer & sold price when sold · Notes.

---

## Good to know
- **Nothing is uploaded anywhere** — your stock data stays on your own device.
- Works offline. No subscription, no accounts.
- To put it on the counter tablet: open the file once, then add it to the home
  screen / bookmarks bar for one-tap access.
