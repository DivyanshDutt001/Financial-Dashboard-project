# FinFlow — Financial Dashboard

A clean, production-quality financial dashboard built for the frontend internship assignment.

---

## Overview

FinFlow is an all-in-one, single-page financial tracker that allows users to check their financial inputs, update transactions, switch between roles and have insights into spending trends — without the need for a backend or other build tools.

Built with: **Vanilla HTML + CSS + JavaScript** and **Chart.js** for data visualizations.

---

## Getting Started

### Run locally

No build step required. Well, just open the file in a browser.

```bash
# Option 1 — open directly
open index.html

# Option 2 — run a simple dev server (recommended to avoid localStorage restrictions)
npx serve .
# or
python3 -m http.server 8080
# then visit http://localhost:8080
```

That's it. No npm install, no Webpack, no framework setup.

---

## Features

### 1. Dashboard Overview
- **Summary cards** — Total Balance, Total Income, Total Expenses, Transaction Count
- **Balance Trend Chart** —Line chart net balance last 3 or 6 months (toggle)
- **Spending Breakdown Donut** — Current month expenses by category with a custom legend
- **Recent Transactions** — Quick preview of latest 5 entries

### 2. Transactions
- Full table with Date, Description, Category, Type, Amount
- **Search** — real-time text filtering across description and category
- **Filters** — by category, type (income/expense), and month
- **Sorting** — click any column header to sort ascending/descending
- **Pagination** — 8 per page with navigation controls
- **Add/Edit/Delete** — modal form for admins to manage transactions

### 3. Role-Based UI
Switch roles using the dropdown in the top bar:
- **Admin** — can add, edit, and delete transactions; action buttons are visible
- **Viewer** — read-only access; all editing UI is hidden

No backend or auth required — role is simulated in frontend state.

### 4. Insights
- Highest spending category with percentage share
- Month-over-month expense change (percentage delta)
- Savings rate (income minus expenses as % of income)
- Average transaction value
- Monthly Income vs Expenses bar chart (6 months)
- Category-wise spending progress bars

### 5. State Management
All state is managed in a single plain JavaScript `state` object:
```js
{
  transactions: [],   // all transaction records
  role: 'admin',      // current user role
  filters: { ... },   // active filter values
  sort: { ... },      // sort key and direction
  page: 1,            // current transactions page
  editingId: null,    // id of transaction being edited
}
```
This keeps the code modular and predictable without any external library.

---

## Optional Enhancements Included

| Feature | Status |
|---|---|
| Dark mode | ✅ Toggle button in topbar, persisted to localStorage |
| Data persistence | ✅ Transactions saved to localStorage on every change |
| CSV export | ✅ One-click export from sidebar |
| Animations | ✅ Progress bars, toast notifications, hover states |
| Advanced filtering | ✅ Multi-field filter (search + category + type + month) |

---

## Design Decisions

- **Typography**: DM Serif Display (headings) + DM Sans (body) — gives a refined financial product feel
- **Color**: Muted earth tones with a forest green accent; avoids the overused purple-on-white AI aesthetic
- **Responsive**: Sidebar collapses to a mobile overlay on screens < 768px; all grids use auto-fit
- **Empty States**: Every list/chart handles the no-data case gracefully
- **Seed Data**: Pre-loaded with realistic Indian rupee transactions across 3 months so the dashboard looks populated out of the box

---

## File Structure

```
finance-dashboard/
└── index.html      # Everything: HTML, CSS, JavaScript in one self-contained file
```

Single-file architecture was a deliberate choice — demonstrates that clean, maintainable code doesn't require a complex build pipeline for a project of this scope.

---

## Author

Built as part of a frontend internship assignment. All code is original.
