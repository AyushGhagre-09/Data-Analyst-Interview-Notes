# Power BI Interview Notes — Definitions & Concepts

> Quick-reference for interview rounds. Each concept has a clean definition first, then a practical note.

---

## 1. Fundamentals

**What is Power BI?**
Power BI is a business intelligence and data visualization tool by Microsoft that connects to multiple data sources, transforms and models data, and presents it through interactive reports and dashboards for business decision-making.

**Core Components**

| Component | Definition |
|---|---|
| Power BI Desktop | The application used to connect, transform, model data, and build reports |
| Power BI Service | The cloud platform (app.powerbi.com) used to publish, share, and collaborate on reports |
| Power BI Mobile | Mobile app to view dashboards/reports on the go |
| Power BI Gateway | A bridge that allows the Service to refresh data from on-premises sources securely |
| Power BI Report Server | An on-premises alternative to the cloud Service for organizations that can't use the cloud |

**Interview answer:** "Power BI Desktop is where I build the report and data model; Power BI Service is where I publish it for others to view, share, and schedule refreshes."

---

## 2. Power BI Workflow

**Definition:** Data flows through three stages — **Get Data** (connect to sources) → **Transform** (clean/shape in Power Query) → **Model** (define relationships and DAX measures) → **Visualize** (build reports) → **Publish/Share** (via Power BI Service).

---

## 3. Data Modeling

**Star Schema vs Snowflake Schema**

| Aspect | Star Schema | Snowflake Schema |
|---|---|---|
| Structure | One central fact table connected directly to denormalized dimension tables | Dimension tables are further split/normalized into sub-dimensions |
| Performance | Faster, simpler joins | More joins, slightly slower |
| Preference in Power BI | Recommended/default | Used only when normalization is necessary |

**Fact Table vs Dimension Table**

| Term | Definition |
|---|---|
| Fact Table | Contains measurable, numeric data (transactions, sales amount, quantity) and foreign keys linking to dimensions |
| Dimension Table | Contains descriptive attributes (product name, customer, date, region) used to filter and group facts |

**Relationships — Cardinality**

| Type | Definition |
|---|---|
| One-to-Many (1:*) | One row in Table A relates to many rows in Table B — the most common and recommended type |
| One-to-One (1:1) | Each row in Table A relates to exactly one row in Table B |
| Many-to-Many (*:*) | Multiple rows in Table A relate to multiple rows in Table B — used carefully, can cause ambiguity |

**Cross Filter Direction**
- **Single** – Filters flow in one direction only (dimension → fact); the default and recommended setting
- **Both** – Filters flow in both directions; used only when needed since it can create ambiguity or performance issues

**Interview answer:** "I always aim for a star schema with single-direction filtering from dimension to fact tables — it's simpler, faster, and avoids ambiguous relationship errors."

---

## 4. Power Query (M Language)

**Definition:** Power Query is the ETL (Extract, Transform, Load) engine inside Power BI used to connect to data sources, clean, reshape, and combine data before it's loaded into the data model. Each transformation step is recorded and can be edited, and it runs on the **M language** behind the scenes.

**Common transformations:** removing duplicates, changing data types, splitting/merging columns, pivoting/unpivoting, merging queries (joins), appending queries (unions), and creating custom columns.

---

## 5. DAX (Data Analysis Expressions)

**Definition:** DAX is a formula language used in Power BI to create custom calculations — calculated columns, measures, and calculated tables — built on top of the data model.

**Calculated Column vs Measure vs Calculated Table**

| Term | Definition | Calculated per | Stored in memory? |
|---|---|---|---|
| Calculated Column | A new column computed row-by-row, using values from the same row | Row context | Yes, physically stored |
| Measure | A dynamic aggregation calculated on the fly based on filters/slicers applied in the report | Filter context | No, computed at query time |
| Calculated Table | An entirely new table generated using a DAX expression | — | Yes, physically stored |

**Interview answer:** "A calculated column is computed once and stored in the table, evaluated row by row. A measure is calculated dynamically based on whatever filter context is applied — like a slicer or a visual — so it's more memory-efficient for aggregations."

**Row Context vs Filter Context**

| Term | Definition |
|---|---|
| Row Context | The context of the "current row" being evaluated — relevant to calculated columns and iterator functions like SUMX |
| Filter Context | The set of filters (from slicers, rows/columns in a visual, or CALCULATE) applied before a measure is evaluated |

**CALCULATE Function**
**Definition:** CALCULATE evaluates an expression in a modified filter context — it's the only DAX function that can change filter context, making it central to almost all advanced DAX.
`=CALCULATE(<expression>, <filter1>, <filter2>...)`

**Common DAX Functions**

| Function | Definition |
|---|---|
| SUM | Adds all values in a column |
| SUMX | An iterator — evaluates an expression row by row, then sums the result (used for row-level calculations before aggregating) |
| RELATED | Pulls a value from a related table (many-side to one-side) |
| RELATEDTABLE | Returns a table of related rows (one-side to many-side) |
| ALL | Removes filters from a table or column, used to calculate totals unaffected by slicers |
| ALLEXCEPT | Removes all filters except the ones specified |
| FILTER | Returns a filtered table based on a condition, often used inside CALCULATE |
| VALUES | Returns a list of distinct values in a column, respecting current filter context |

**Time Intelligence Functions**

| Function | Definition |
|---|---|
| TOTALYTD | Calculates the year-to-date total for a measure |
| SAMEPERIODLASTYEAR | Returns the same date/period shifted back one year, used for YoY comparisons |
| DATEADD | Shifts a date column forward/backward by a specified interval (day/month/year) |

**Interview answer (YoY example):** "To calculate YoY growth, I typically create a measure for the current period total, another using SAMEPERIODLASTYEAR or DATEADD to get last year's total, then calculate the percentage difference between the two — all wrapped inside CALCULATE to correctly shift the filter context on the Date table."

---

## 6. Storage Modes

| Mode | Definition |
|---|---|
| Import | Data is loaded and stored in Power BI's in-memory engine (VertiPaq) — fastest performance, but needs scheduled refreshes |
| DirectQuery | Power BI queries the source live, without storing data — always up to date, but slower and dependent on source performance |
| Live Connection | Connects directly to a live Analysis Services/Power BI dataset without importing or copying the model |
| Composite Model | Combines Import and DirectQuery tables within the same model |

---

## 7. Visualization Features

| Feature | Definition |
|---|---|
| Slicer | An on-report visual filter that lets users interactively filter data by a field |
| Bookmark | Captures the current state of a report page (filters, visibility, sort) so it can be recalled later, used for navigation or storytelling |
| Drill-through | Lets users click a data point to jump to a detailed report page filtered to that context |
| Tooltip (Custom) | A separate mini-report page shown as a hover tooltip on a visual |

---

## 8. Row-Level Security (RLS)

**Definition:** RLS restricts what data individual users can see within the same report, based on rules defined using DAX filters tied to their user role (e.g., a regional manager only sees their region's data).

---

## 9. Performance Optimization

- Prefer **Import mode** where possible; it's fastest
- Reduce cardinality of columns (avoid unnecessary high-uniqueness columns)
- Use **measures instead of calculated columns** where possible — they don't bloat model size
- Avoid unnecessary **bi-directional relationships**
- Disable unused **auto date/time** tables and build one shared **Date dimension table** instead
- Use **Performance Analyzer** to identify slow visuals/DAX queries

---

## 10. Power BI vs Tableau vs Excel

| Aspect | Power BI | Tableau | Excel |
|---|---|---|---|
| Primary use | BI & reporting at scale | Advanced visual analytics | General-purpose spreadsheet analysis |
| Data modeling | Strong (star schema, DAX) | Moderate | Limited (Power Pivot only) |
| Cost | Generally lower, tied to Microsoft ecosystem | Higher licensing cost | Included in Office |
| Visual flexibility | Good, template-driven | Best-in-class, highly customizable | Basic charting |
| Best for | Businesses using Microsoft stack, structured dashboards | Deep exploratory visual analysis | Ad-hoc analysis, smaller datasets |

---

## 11. Common Interview Q&A (Quick Fire)

**Q: Why use Power BI over Excel?**
A: Power BI handles much larger datasets efficiently through its VertiPaq compression engine, supports proper relational data modeling, and allows automated refresh and sharing through the Service — Excel isn't built for that scale.

**Q: What is the difference between a Measure and a Calculated Column?**
A: A measure is evaluated dynamically based on filter context and isn't stored; a calculated column is computed row-by-row at refresh time and physically stored in the model.

**Q: What is the difference between ALL and ALLEXCEPT?**
A: ALL removes every filter from a table/column; ALLEXCEPT removes all filters except the ones explicitly listed.

**Q: What is context transition in DAX?**
A: It's when row context is converted into filter context — this happens automatically inside CALCULATE, allowing a calculated column's row-level logic to behave like a filter for measures.

**Q: What's the difference between a slicer and a filter?**
A: A slicer is a visible, interactive visual on the report canvas; a filter (in the Filters pane) applies filtering behind the scenes and isn't necessarily visible to end users.

**Q: How do you handle many-to-many relationships in Power BI?**
A: By using a bridge table (a table containing the unique combination of keys) to break the many-to-many into two one-to-many relationships, or by carefully enabling many-to-many cardinality when unavoidable.

**Q: What is the difference between Import and DirectQuery?**
A: Import loads a compressed copy of the data into memory for fast performance but requires refreshes; DirectQuery queries the live source in real time, ensuring fresh data but at the cost of speed.
