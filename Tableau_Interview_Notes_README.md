# Tableau Interview Notes — Definitions & Concepts

> Quick-reference for interview rounds. Each concept has a clean definition first, then a practical note.

---

## 1. Fundamentals

**What is Tableau?**
Tableau is a data visualization and business intelligence tool that connects to various data sources and allows users to create interactive, shareable dashboards and reports through a drag-and-drop interface, without needing to write code.

**Tableau Products**

| Product | Definition |
|---|---|
| Tableau Desktop | The authoring application used to connect to data, build visualizations, and create dashboards |
| Tableau Server | An on-premises (or cloud-hosted) platform to publish, share, and manage dashboards within an organization |
| Tableau Cloud (Online) | Microsoft-hosted/SaaS equivalent of Tableau Server |
| Tableau Public | A free version where dashboards are published publicly on the web — used for portfolios |
| Tableau Prep | A tool used for data cleaning and transformation (ETL) before visualization |
| Tableau Reader | A free app to open and view dashboards created in Desktop, without editing rights |

**Interview answer:** "Tableau Desktop is where I build the visualizations and dashboards, and Tableau Server or Cloud is where I publish them so others in the organization can view and interact with them."

---

## 2. Data Connection Modes

| Mode | Definition |
|---|---|
| Live Connection | Tableau queries the data source directly in real time — always shows current data but performance depends on source speed |
| Extract | Tableau creates a compressed, in-memory snapshot (.hyper file) of the data — faster performance but needs scheduled refreshes to stay current |

**Interview answer:** "Live connection queries the source directly every time, so it's always up to date but can be slower on large datasets. An extract is a saved, compressed copy of the data that Tableau's engine can query much faster, at the cost of needing periodic refreshes."

---

## 3. Dimensions vs Measures

| Term | Definition |
|---|---|
| Dimension | Qualitative, categorical data used to slice and segment data — e.g., Region, Product Name, Date. Usually blue in Tableau's UI |
| Measure | Quantitative, numeric data that can be aggregated — e.g., Sales, Profit, Quantity. Usually green in Tableau's UI |

**Interview answer:** "Dimensions are categorical fields I use to group or slice my data — like region or category — while measures are numeric fields that get aggregated, like sum of sales or average profit."

---

## 4. Discrete vs Continuous

| Term | Definition | Color in UI |
|---|---|---|
| Discrete | Distinct, separate values treated as individual categories (headers on the axis) | Blue |
| Continuous | A range of values along a smooth, unbroken scale (creates an axis) | Green |

**Interview answer:** "Discrete fields create separate headers — like distinct category labels — while continuous fields create a continuous axis, like a trend line by date. Any field can technically be switched between discrete and continuous depending on how I want it displayed."

---

## 5. Filters (and Order of Operations)

**Definition:** Filters restrict the data shown in a view based on defined conditions. Tableau applies filters in a specific processing order, which affects the final result.

| Filter Type | Definition |
|---|---|
| Extract Filter | Applied before the extract is created — limits what data even gets pulled in |
| Data Source Filter | Applied to the entire data source before any worksheet-level filtering |
| Context Filter | An independent filter that other filters are then applied on top of — improves performance and changes filter dependency |
| Dimension Filter | Filters based on categorical field values |
| Measure Filter | Filters based on numeric/aggregated field values |
| Table Calculation Filter | Applied last, after all aggregations and table calculations are computed |

**Tableau's Order of Operations (simplified):**
Extract Filters → Data Source Filters → Context Filters → Dimension/Measure Filters → Table Calculation Filters

**Interview answer:** "Context filters are processed before regular dimension and measure filters, and every other filter is then applied within that context — that's useful both for performance and for controlling how filters interact with each other, like with Top N calculations."

---

## 6. Joins vs Blending

| Term | Definition |
|---|---|
| Join | Combines data at the row level from multiple tables within the **same data source**, using a common key (like SQL joins) |
| Data Blending | Combines data from **two different data sources** at an aggregated level, using a common linking field |

**Interview answer:** "Joins combine tables at the row level within a single data source, similar to SQL. Blending is used when I'm pulling from two completely different data sources — like Excel and a SQL database — and it combines the data at a summary/aggregate level instead of row level."

---

## 7. Calculated Fields

**Definition:** Custom fields created using formulas to derive new data from existing fields — used for calculations not directly available in the raw dataset, like profit ratio or custom categorization logic.

---

## 8. LOD (Level of Detail) Expressions

**Definition:** LOD expressions let you compute aggregations at a different level of granularity than the one currently in the view, independent of the visualization's dimensions.

| LOD Type | Definition |
|---|---|
| FIXED | Computes a value using only the specified dimensions, ignoring the view's other filters/dimensions |
| INCLUDE | Computes a value at a finer (more detailed) level than the view, then aggregates it back up |
| EXCLUDE | Removes a specific dimension from the level of detail, computing at a coarser level than the view |

**Interview answer:** "LOD expressions let me control the granularity of a calculation independent of what's in the view. For example, FIXED lets me calculate total sales per customer regardless of how the view is filtered, while EXCLUDE lets me remove a dimension — like removing 'month' to get a yearly total even when the view is broken down monthly."

---

## 9. Table Calculations

**Definition:** Calculations applied to the values already present in the visualization (post-aggregation), such as running totals, percent of total, rank, or moving averages — computed based on the structure of the table itself, not the underlying database.

---

## 10. Sets, Groups, Parameters, Bins, Hierarchies

| Term | Definition |
|---|---|
| Set | A custom field that defines a subset of data based on a condition (e.g., "Top 10 Customers") |
| Group | Combines multiple dimension members into a single category (e.g., grouping cities into regions manually) |
| Parameter | A user-controlled input value (number, string, date) that can dynamically drive calculated fields, filters, or reference lines |
| Bin | Groups a continuous measure into equal-sized intervals/buckets (e.g., age groups of 10 years) |
| Hierarchy | A nested structure of dimensions (e.g., Country → State → City) allowing drill-down in visualizations |

---

## 11. Dashboard Features

| Feature | Definition |
|---|---|
| Dashboard | A combination of multiple worksheets, visuals, and objects arranged together on a single canvas |
| Dashboard Action | Interactivity that lets one worksheet affect another — includes Filter Actions, Highlight Actions, and URL Actions |
| Story | A sequence of dashboards/worksheets arranged to narrate a data-driven story, step by step |

---

## 12. Common Chart Types

- **Bar/Line chart** – comparisons and trends
- **Heat map** – shows intensity/magnitude using color across a matrix
- **Treemap** – shows hierarchical, part-to-whole data using nested rectangles sized by value
- **Dual-axis chart** – combines two measures on the same view with independent axes
- **Bullet chart** – compares a measure against a target using a bar-in-bar format
- **Box plot** – shows the distribution and outliers of a dataset

---

## 13. Tableau vs Power BI

| Aspect | Tableau | Power BI |
|---|---|---|
| Visual customization | Best-in-class, highly flexible | Good, but more template-driven |
| Data modeling | Weaker — no native DAX equivalent | Strong — built-in DAX and relationship modeling |
| Learning curve | Steeper for advanced calculations (LOD) | Easier for those familiar with Excel |
| Pricing | Generally more expensive | Generally cheaper, bundled with Microsoft ecosystem |
| Best for | Deep exploratory visual analysis | Structured business reporting integrated with Microsoft tools |

---

## 14. Common Interview Q&A (Quick Fire)

**Q: What is the difference between a Join and a Blend?**
A: A join combines tables at the row level within one data source; a blend combines data from separate data sources at an aggregated level using a linking field.

**Q: What is the difference between FIXED and EXCLUDE LOD expressions?**
A: FIXED computes at exactly the dimensions specified, ignoring the view entirely. EXCLUDE takes the view's current dimensions and removes the specified one(s) before aggregating.

**Q: What is a Context Filter and why use it?**
A: A context filter is processed before other filters, creating an independent "context" that other filters then operate within — it's used to improve performance on large datasets and to make Top N-style filters work correctly alongside other filters.

**Q: What's the difference between a Table Calculation and an LOD Expression?**
A: A table calculation is applied after aggregation, based on what's visible in the table (e.g., running total across displayed rows). An LOD expression is computed at the data source level at a specified granularity, independent of what's in the view.

**Q: When would you use a Parameter?**
A: When I want the end user to dynamically control something in the dashboard — like switching between measures (Sales vs Profit) on a chart, or setting a custom threshold for a reference line.

**Q: What is the difference between Live Connection and Extract?**
A: Live connection queries the source in real time for the most current data but can be slower; an extract is a compressed, saved snapshot that performs faster but needs to be refreshed to reflect new data.

**Q: How do you handle a Many-to-Many relationship in Tableau?**
A: Typically by being cautious with blending/joins that create duplicate rows, using LOD expressions to control aggregation granularity, or restructuring the data model before importing.
