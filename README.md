# SalesPulse — Sales Decision Dashboard

A browser-based sales analytics dashboard built to go beyond charts: it automatically flags business problems (loss-making products, harmful discount thresholds, churn-risk customers) and lets you simulate pricing decisions before making them.

**Live demo:** https://aditisisodia143-ai.github.io/salespulse-dashboard/

## Why this project

Most sales dashboards stop at "here are the numbers." SalesPulse tries to answer the next question a manager actually asks: *what should I do about it?*

- **Problem Finder** — scans the filtered data and surfaces concrete issues (e.g. "Furniture margin is only 6%", "3 top customers have gone quiet") with a suggested action for each.
- **What-if simulator** — model a discount cap or price change and see projected sales/profit impact before proposing it, including an auto-search for the most profitable discount cap.
- **80/20 (Pareto) analysis** — identifies which products actually drive 80% of revenue.
- **3-month forecast** — linear trend with seasonality adjustment (when 13+ months of data are available).
- **Customer segmentation** — High/Mid/Low value tiers with at-risk (dormant) flags for top accounts.
- **One-click manager briefing** — auto-generates a plain-text summary of the numbers and open issues, ready to paste into an email.

## Tech

Plain HTML, CSS, and JavaScript — no build step, no backend, no package manager needed.
- **HTML** (`index.html`) — page structure and layout
- **CSS** (`style.css`) — all styling, including light/dark mode
- **JavaScript** (`script.js`) — data parsing, the problem-finder rules, charts, and the what-if simulator
- [Chart.js](https://www.chartjs.org/) for charts and [SheetJS/xlsx](https://sheetjs.com/) for reading uploaded Excel/CSV files — both vendored locally under `lib/` (not loaded from a CDN), so the app has no external runtime dependency and your data never leaves the browser

## Using it

Open `index.html` in any browser (or the deployed link). It loads with realistic sample data (~1,200 orders) so every tab works immediately.

To use your own data, click **Upload your sales file** (or drag a file anywhere on the page) with an `.xlsx`, `.xls`, or `.csv`. Required columns (names are matched automatically, case-insensitive): `Order Date`, `Region`, `Category`, `Product`, `Sales`, `Profit`. Optional: `Order ID`, `Customer`, `Quantity`, `Unit Price`, `Discount`.

Your file is read entirely client-side — nothing is uploaded to a server.

## Deploying

It's a static site (no server-side code), so any static host works:

- **GitHub Pages:** Settings → Pages → Deploy from branch → `main` / root. Your dashboard will be live at `https://<username>.github.io/<repo-name>/`.
- **Netlify / Vercel:** drag-and-drop the whole project folder, or connect the repo directly.

## Project structure

```
index.html          # page structure
style.css            # styling
script.js            # app logic (parsing, problem finder, charts, simulator)
lib/
  chart.umd.min.js   # Chart.js (vendored)
  xlsx.full.min.js   # SheetJS/xlsx (vendored)
README.md
```

## Possible next steps

- Persist uploaded data and problem-tracker checkmarks in a small backend/database for multi-user teams
- Export the manager briefing and charts to PDF
- Add role-based views (e.g. a regional manager sees only their region by default)
