# SalesPulse — Sales Decision Dashboard

A browser-based sales analytics dashboard built to go beyond charts: it automatically flags business problems (loss-making products, harmful discount thresholds, churn-risk customers) and lets you simulate pricing decisions before making them.

**Live demo:** add your published link here (see "Deploying" below)

## Why this project

Most sales dashboards stop at "here are the numbers." SalesPulse tries to answer the next question a manager actually asks: *what should I do about it?*

- **Problem Finder** — scans the filtered data and surfaces concrete issues (e.g. "Furniture margin is only 6%", "3 top customers have gone quiet") with a suggested action for each.
- **What-if simulator** — model a discount cap or price change and see projected sales/profit impact before proposing it, including an auto-search for the most profitable discount cap.
- **80/20 (Pareto) analysis** — identifies which products actually drive 80% of revenue.
- **3-month forecast** — linear trend with seasonality adjustment (when 13+ months of data are available).
- **Customer segmentation** — High/Mid/Low value tiers with at-risk (dormant) flags for top accounts.
- **One-click manager briefing** — auto-generates a plain-text summary of the numbers and open issues, ready to paste into an email.

## Tech

Single self-contained `index.html` — no build step, no backend, no dependencies to install.
- [Chart.js](https://www.chartjs.org/) for charts
- [SheetJS/xlsx](https://sheetjs.com/) for reading uploaded Excel/CSV files, parsed entirely in the browser

## Using it

Open `index.html` in any browser (or the deployed link). It loads with realistic sample data (~1,200 orders) so every tab works immediately.

To use your own data, click **Upload your sales file** (or drag a file anywhere on the page) with an `.xlsx`, `.xls`, or `.csv`. Required columns (names are matched automatically, case-insensitive): `Order Date`, `Region`, `Category`, `Product`, `Sales`, `Profit`. Optional: `Order ID`, `Customer`, `Quantity`, `Unit Price`, `Discount`.

Your file is read entirely client-side — nothing is uploaded to a server.

## Deploying

Since it's a single static HTML file, any static host works:

- **GitHub Pages:** Settings → Pages → Deploy from branch → `main` / root. Your dashboard will be live at `https://<username>.github.io/<repo-name>/`.
- **Netlify / Vercel:** drag-and-drop the `index.html` file, or connect the repo directly.

## Project structure

```
index.html   # the entire app — markup, styles, and logic
README.md
```

## Possible next steps

- Persist uploaded data and problem-tracker checkmarks in a small backend/database for multi-user teams
- Export the manager briefing and charts to PDF
- Add role-based views (e.g. a regional manager sees only their region by default)
