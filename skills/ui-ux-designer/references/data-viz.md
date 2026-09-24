# Data visualization & charts

Load only for data products. When the product shows data, specify charts deliberately (HIGH priority for data products).

- **Match chart type to data type:** trend over time → line/area; compare categories → bar (sort descending); proportion → pie/donut (**only ≤5 categories**, else bar); relationship → scatter; part-to-whole over time → stacked.
- **Accessibility is mandatory, not optional:** never rely on color alone — differentiate series by line style/pattern/shape; provide a **data-table fallback** and a text/`aria` summary of the key insight; ensure interactive marks are keyboard-reachable with ≥44pt tap area.
- **Readability:** show legends near the chart; tooltips/labels on hover (web) or tap (mobile) with exact values; label axes with units; keep grid lines low-contrast so they don't compete with data; use tabular figures and locale-aware number/date/currency formatting.
- **States:** skeleton while loading; meaningful empty state ("No data yet" + guidance) instead of a blank axis frame; error state with retry instead of a broken chart.
- **Responsive & scale:** charts reflow or simplify on small screens (fewer ticks, horizontal bars); for 1000+ points, aggregate/sample and offer drill-down rather than rendering everything.
