# LottoLens — Lottery Analyzer

LottoLens analyzes lottery draw history in the browser. You give it past winning numbers. It shows how often each number came up, which numbers are hot, cold or overdue, and which pairs appeared together. It can also generate number sets using one of several strategies.

> **Disclaimer:** Lottery draws are independent random events. LottoLens describes patterns in past data. It does **not** predict future draws, and no strategy improves your odds.

## Getting started

LottoLens is a single HTML file with nothing to install and no build step.

1. Open `index.html` in any modern browser.
2. Sample draws are preloaded (28 draws in 6/49 format), so you can try every page right away.

The only external resource is Google Fonts. Without internet access the app still works, but it falls back to system fonts.

## Pages

| Page | What it does |
|------|--------------|
| **Analyze** | Frequency chart for every number, hot/cold/overdue lists, and the most common number pairs. |
| **Heatmap** | Color-coded grid of the whole number pool, so frequent and rare numbers stand out at a glance. |
| **Generate** | Generates 1–10 number sets of 5–7 numbers using the selected strategy. Each set shows its sum (Σ). |
| **History** | Add, delete, import (CSV) and export (CSV) past draws. Analysis updates immediately. |
| **Settings** | Set the number pool and pick count, adjust thresholds, and import/export/reset data. |
| **Help** | Built-in guide to every feature. |

### Lottery presets

Settings includes presets for common formats: **6/49**, **6/59**, **5/45** and **5/70**. You can also set a custom pool size and pick count.

## Generation strategies

| Strategy | How it picks numbers |
|----------|----------------------|
| 🔥 **Hot picks** | Favors the numbers drawn most often. |
| ❄️ **Cold picks** | Favors the numbers drawn least often. |
| ⚖️ **Balanced** | Mixes hot, cold and overdue numbers. |
| ⏱️ **Overdue** | Favors numbers that haven't appeared for a long time. |
| 🎲 **Random** | Ignores history and picks uniformly at random. Useful as a baseline. |

## Key concepts

- **Hot:** drawn more than *average × hot threshold* times (default ×1.3).
- **Cold:** drawn fewer than *average × cold threshold* times (default ×0.5).
- **Overdue:** not seen in the last *N* draws (default 10).
- **Pair frequency:** how often two numbers appeared in the same draw.
- **Set sum (Σ):** the total of a set's numbers. In 6/49, winning sums usually fall between 100 and 200.

You can change all thresholds in **Settings**.

## Importing draws (CSV)

**History → Import CSV** accepts `.csv` or `.txt` files with one draw per line. Each line starts with the date, followed by a comma, semicolon or tab. The numbers come after that, separated by spaces, commas, semicolons or tabs:

```csv
2025-01-04, 5 12 21 31 38 47
2025-01-08,7,14,21,28,35,42
2025-01-15;3;11;21;33;40;47
```

- Numbers outside the configured pool, and duplicate numbers within a row, are dropped.
- Rows with fewer than 2 valid numbers are skipped.
- Draws are sorted by date after import.

## Saving your data

LottoLens does **not** save anything automatically, so reloading the page resets to the sample data. To keep your work:

- **Settings → Export JSON** saves draws, configuration and thresholds. Load the file again with **Import JSON**.
- **Export CSV** saves just the draw list.

## Tech

- Plain HTML, CSS and JavaScript in one file (`index.html`), with no frameworks or dependencies.
- Responsive layout for desktop and mobile.
- Fonts: [Syne](https://fonts.google.com/specimen/Syne) and [DM Mono](https://fonts.google.com/specimen/DM+Mono).
