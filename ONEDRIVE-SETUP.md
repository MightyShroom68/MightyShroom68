# Putting the stock list on OneDrive (Family subscription)

One file. Everybody opens **the same** file. Nobody keeps their own copy.
That single rule is what makes this work.

Your Microsoft 365 **Family** plan can do this properly — you do not need the
business/enterprise version. Here is exactly how.

---

## Part 1 — Owner: set it up once (10 minutes)

### 0. Open it once in Excel first
Open `Verena-Diamond-Stock.xlsx` in Excel and save it (Ctrl+S / Cmd+S) **before**
you share it. The file was generated with the formulas in place but not yet
calculated, so until Excel has opened it once, OneDrive's little preview pane may
show the price columns as blank. Opening and saving fixes that permanently.

While it is open, sanity-check one row: `VD-001` should show a Retail Price of
**$2,733.50** and a Minimum Price of **$1,366.75** (Rp 43,736,000 and
Rp 21,868,000 in the reference columns). If you see those, every formula works.

### 1. Make a folder
In OneDrive on this computer, create a folder:

```
OneDrive ▸ Verena Stock
```

Put **`Verena-Diamond-Stock.xlsx`** inside it. Wait for the green tick / cloud
icon to show it has finished uploading.

### 2. Know which tab is for whom
Nothing is hidden — your staff can see cost, profit and margin, by design.
There is only one rule to teach them:

> **Customers get shown the `Customer View` tab. Never `Stock and Costing`.**

`Customer View` has no cost, no minimum price and no margin on it, and it is
already set up to print in landscape with the headings repeated on each page.

### 3. Share the folder — not the file
Right-click the **Verena Stock** folder ▸ **Share**.

- Click the settings/pencil icon and choose **Specific people** — *not* "Anyone
  with the link". This stops the price list leaking if someone forwards it.
- Make sure it says **Can edit**.
- Type each salesperson's email address.
- Send.

> Sharing the *folder* rather than the file means anything you add later
> (photos, certificates, next year's list) is automatically shared too.

### 4. Turn AutoSave on
Open the file from OneDrive and check **AutoSave** is **On** (top-left in Excel
on Windows/Mac). This is what makes everyone's changes appear for everyone else.

---

## Part 2 — Sales staff: get it on your phone (5 minutes, once)

1. Install the free **Microsoft Excel** app (App Store / Google Play).
2. Sign in with a free **Microsoft account** — use the email address the owner
   shared the folder with. If you do not have a Microsoft account, create one
   at [account.microsoft.com](https://account.microsoft.com) with that same email.
3. In the Excel app, tap **Open** ▸ **Shared** ▸ **Verena Stock** ▸
   **Verena-Diamond-Stock.xlsx**.
4. Tap the **★ / Add to favourites** so it is one tap away next time.

That's it. The file you see is the same one everyone else sees.

### On a computer
Just go to [onedrive.com](https://onedrive.com), sign in, open the file. It runs
in the browser — nothing to install. Or open it in desktop Excel if you have it.

### Finding a diamond on a phone
Tap any cell in the list ▸ the **filter funnel** icon ▸ tick the shape or status
you want. Or use the **magnifying glass** to search for a certificate number.

> The funnel on a phone is fiddly. If the counter has a tablet, the
> **Showroom Lookup** page (see README) is much faster for "do we have a 2ct
> oval?" — but it is look-up only.

---

## Part 3 — The rules that keep it working

| ✅ Do | ❌ Never |
|---|---|
| Open the file from OneDrive / Shared, every time | Email the file to anyone |
| Let AutoSave save for you | Use "Save As" or "Download a copy" |
| Type your change and move on | Keep your own version on your desktop |
| Ask the owner if a price says **ASK OWNER** | Quote below the Minimum Price (USD) |

If two people edit the same cell at the same moment, Excel keeps the last one
typed — it does not lose the row. What *does* break things is someone working
in a downloaded copy for a week and then saving it over the top.

---

## Honest limits of the Family plan

These are real, and worth knowing before you rely on it:

**1. Anyone with the link sees your cost and margin.**
Staff seeing cost is your decision and the file is built for it — but that makes
the *share link* the thing to guard. Use **Specific people**, never "Anyone with
the link", or a forwarded link hands a competitor your supplier prices and
margins. When someone leaves, remove their access: right-click the folder ▸
**Manage access**.

**2. Sheet protection has no password.**
The grey calculated columns are locked so the formulas cannot be damaged, but it
unlocks via Review ▸ Unprotect Sheet with no password — nothing stops a
determined person. Add a password if you want, and keep a note of it somewhere
safe.

**3. Editing on a big tablet may ask for a subscription.**
The Excel app edits for free on phones. On an iPad or a large Android tablet,
Microsoft may require a licence. Your Family plan covers 6 people, so you can
assign one to a shop device — or just use the browser at onedrive.com, which is
free to edit.

**4. This is a spreadsheet, not a database.**
It will be comfortable up to a few hundred stones. There is no audit trail of
who changed what, and no undo once AutoSave has written. Take a monthly copy
(File ▸ Save a Copy, name it `2026-08 backup`) and keep it in a **Backups**
subfolder.

**5. Version history is your safety net.**
If someone wrecks the file: open it on onedrive.com, right-click ▸ **Version
history**, and restore yesterday's copy. OneDrive keeps these automatically.
Show your staff this exists — it turns a disaster into a two-minute fix.

---

## If you outgrow this

The moment you want proper phone-first data entry, per-person permissions, and
a real audit trail, the upgrade is **Microsoft 365 Business Basic** (about
US$6/user/month). It unlocks **SharePoint Lists** and **Power Apps**, which give
you a genuine app — big buttons instead of a spreadsheet grid, a proper audit
trail of who changed what, and per-person control over who sees which columns.

Nothing you have built here is wasted: a SharePoint List imports directly from
this workbook.
