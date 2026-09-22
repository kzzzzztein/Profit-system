# 🍉 Lexcel — Sales & Profit Tracker

A simple, spreadsheet-free way for a fruits & sweets shop to log sales and see **profit** at a glance — built for people who don't want to fight with Excel formulas.

This is a **prototype**: one self-contained web page (`index.html`), no server, no account, no database to set up. It runs entirely in the browser and saves data on the device it's used on.

---

## 1. Try it right now

Just double-click **`index.html`**. It opens in your browser and works immediately — sample fruit & sweets products and two weeks of sample sales are pre-loaded so you can see it in action. Clear them anytime from **Backup & Data → Erase all data**.

## 2. Put it online for free (GitHub Pages)

1. Create a new GitHub repository (e.g. `lexcel`).
2. Upload `index.html` (and this `README.md`) to it.
3. Go to the repo's **Settings → Pages**.
4. Under **Build and deployment → Source**, choose **Deploy from a branch**, pick the `main` branch and `/ (root)` folder, then **Save**.
5. GitHub gives you a live link within a minute or two, usually:
   `https://YOUR-USERNAME.github.io/lexcel/`
6. Share that link — anyone can open and use it on their phone or computer. Each person's data stays on their own device (see the note on storage below).

No build step, no npm install, no server to pay for.

## 3. How profit is calculated

Lexcel ships with a standard formula turned on by default:

```
Profit per sale = Quantity × (Sell Price − Cost Price) − Discount
```

From **Profit Formula** in the sidebar, a shop owner can switch on, without touching any code:

- **Packaging cost** — subtracts a per-item packaging/container cost you set per product
- **Tax** — subtracts a percentage of revenue
- **Other operating expenses** — a fixed amount (rent share, ice, gas, spoilage) subtracted once per period, not per sale

For advanced users, there's an optional **custom formula** field that accepts a real expression (using [math.js](https://mathjs.org)) built from `quantity`, `sellPrice`, `costPrice`, `discount`, `packaging`, `revenue`, `cogs`, and `tax`. Leave it blank and the standard formula above is always used — nothing breaks if someone doesn't touch it.

Dashboard "Total Profit" = sum of every sale's profit in the selected period, minus operating expenses if set. Margin % = profit ÷ revenue.

## 4. Where the data lives (and how to back it up)

This prototype uses the browser's built-in storage (`localStorage`) — think of it as a free, zero-setup database that lives only on one device/browser. That means:

- ✅ Nothing to configure, nothing to pay for, works offline
- ⚠️ Clearing browser data, or switching devices/browsers, loses it
- ⚠️ Two people on two devices do **not** see the same data

**Back up regularly** from **Backup & Data**:
- **Download backup (.json)** — a full copy you can restore later or move to another device
- **Download sales as spreadsheet (.csv)** — opens directly in Excel/Google Sheets

## 5. When you're ready for a real (still free) database

If the shop grows past one device, upgrade to one of these free tiers — no rewrite of the UI needed, just swap where data is read/written:

| Option | Why it's a good fit |
|---|---|
| **Google Sheets + Sheets API** | Free, and the shop owner can still see/edit raw data in a spreadsheet they already understand |
| **Supabase** | Free hosted Postgres database with a simple REST API; easiest real upgrade path |
| **Firebase (Firestore)** | Google's free tier, syncs in real time across devices — good if multiple staff log sales at once |

Any of these lets several devices share one live set of sales data instead of each browser having its own copy.

## 6. Files

```
lexcel/
├── index.html   ← the whole app (open this)
└── README.md    ← this file
```

## 7. Customizing

- **Products**: fruits and sweets are just the starting categories — add, edit, or delete any product from the **Products** tab.
- **Branding**: change the business name and currency symbol under **Profit Formula → Business details**.
- **Colors/fonts**: all defined as CSS variables at the top of `index.html` (`--berry`, `--mango`, `--leaf`, etc.) if you want to restyle it.
