# Excel Interview Notes — Definitions & Concepts

> Quick-reference for interview rounds. Each concept has a clean definition first, then a practical note.

---

## 1. Fundamentals

**What is Excel?**
Excel is a spreadsheet application used to store, organize, calculate, and visualize tabular data using rows, columns, formulas, and built-in analytical tools like PivotTables and charts.

**Workbook vs Worksheet**
| Term | Definition |
|---|---|
| Workbook | The entire Excel file (.xlsx), which can contain multiple worksheets |
| Worksheet (Sheet) | A single page/tab inside a workbook made up of rows and columns |

**Cell, Row, Column**
A **cell** is the intersection of a row and column (e.g., A1). A **row** runs horizontally (numbered), a **column** runs vertically (lettered).

---

## 2. Cell References

| Type | Symbol | Definition | Example |
|---|---|---|---|
| Relative | A1 | Changes automatically when copied to another cell, based on relative position | Copying `A1` from row 1 to row 2 becomes `A2` |
| Absolute | $A$1 | Locked reference — row and column never change when copied | `$A$1` stays `$A$1` everywhere |
| Mixed | $A1 or A$1 | Either row or column is locked, not both | `$A1` locks column only |

**Interview answer:** "Relative references adjust based on the position of the formula, while absolute references (using `$`) stay fixed regardless of where the formula is copied. Mixed references lock only the row or only the column."

---

## 3. Formula vs Function

| Term | Definition |
|---|---|
| Formula | A user-defined expression that performs a calculation, e.g. `=A1+B1` |
| Function | A predefined, built-in formula that performs a specific task, e.g. `=SUM(A1:A10)` |

**Interview answer:** "A formula is any expression I write to calculate a value, while a function is a built-in, predefined formula provided by Excel that I use inside my formulas."

---

## 4. Lookup Functions

**VLOOKUP** — VLOOKUP searches vertically in the first column and returns a value from a specified column to its right in the same row.
`=VLOOKUP(lookup_value, table_array, col_index_num, [range_lookup])`

**HLOOKUP** — Same as VLOOKUP but searches **horizontally** across the first row.

**INDEX-MATCH** — A combination where `MATCH` finds the position of a value, and `INDEX` returns the value at that position. Unlike VLOOKUP, it can look in any direction (left or right) and doesn't break if columns are inserted.
`=INDEX(return_range, MATCH(lookup_value, lookup_range, 0))`

**XLOOKUP** — The modern replacement for VLOOKUP/HLOOKUP. Can search in any direction, returns exact matches by default, and handles errors natively.
`=XLOOKUP(lookup_value, lookup_array, return_array, [if_not_found])`

| Function | Direction | Can look left? | Breaks if column inserted? |
|---|---|---|---|
| VLOOKUP | Vertical only | No | Yes |
| HLOOKUP | Horizontal only | No | Yes |
| INDEX-MATCH | Both | Yes | No |
| XLOOKUP | Both | Yes | No |

**Interview answer:** "VLOOKUP only searches left to right and breaks if a column is inserted in between. INDEX-MATCH and XLOOKUP are more robust since they reference columns independently and can search in any direction."

---

## 5. Logical Functions

- **IF** – Returns one value if a condition is true, another if false: `=IF(condition, value_if_true, value_if_false)`
- **IFS** – Handles multiple conditions without nesting multiple IFs
- **AND / OR** – Combine multiple logical conditions
- **IFERROR** – Returns a specified value if a formula results in an error, otherwise returns the formula result
- **IFNA** – Same as IFERROR but specific to `#N/A` errors

---

## 6. Aggregate & Conditional Functions

| Function | Definition |
|---|---|
| SUM | Adds all numbers in a range |
| SUMIF | Adds values that meet a single condition |
| SUMIFS | Adds values that meet multiple conditions |
| COUNTIF / COUNTIFS | Counts cells meeting one/multiple conditions |
| AVERAGEIF / AVERAGEIFS | Averages values meeting one/multiple conditions |

---

## 7. Text Functions

- **LEFT / RIGHT / MID** – Extract characters from the left, right, or middle of a text string
- **CONCATENATE / CONCAT / TEXTJOIN** – Combine multiple text strings into one; TEXTJOIN also allows a delimiter and ignores blanks
- **TRIM** – Removes extra spaces from text
- **LEN** – Returns the number of characters in a string
- **FIND / SEARCH** – Locate the position of a substring (FIND is case-sensitive, SEARCH is not)

---

## 8. Date & Time Functions

- **TODAY() / NOW()** – Return the current date / current date and time
- **DATEDIF** – Calculates the difference between two dates in days, months, or years
- **EOMONTH** – Returns the last day of the month, a specified number of months before/after a date
- **NETWORKDAYS** – Counts working days between two dates, excluding weekends (and optional holidays)

---

## 9. PivotTable

**Definition:** A PivotTable is a data summarization tool that lets you dynamically group, sort, filter, and aggregate large datasets without writing formulas — by dragging fields into Rows, Columns, Values, and Filters.

**Interview answer:** "A PivotTable lets me quickly summarize large datasets — for example, totaling sales by region and month — by simply dragging fields into rows and values, without writing manual formulas like SUMIFS."

---

## 10. Power Query

**Definition:** Power Query is Excel's data connection and transformation engine (ETL tool) that lets you import, clean, reshape, and combine data from multiple sources before loading it into the worksheet or data model.

**Interview answer:** "Power Query is used for the ETL process — Extract, Transform, Load. I use it to pull data from sources like CSVs or databases, clean and reshape it using its step-based interface, and then load it into Excel."

---

## 11. Data Validation

**Definition:** A feature that restricts the type of data or values users can enter into a cell (e.g., dropdown lists, number ranges, date ranges), reducing data entry errors.

---

## 12. Conditional Formatting

**Definition:** A feature that automatically applies formatting (color, icons, data bars) to cells based on their values or a custom rule, making patterns and outliers visually easy to spot.

---

## 13. What-If Analysis

**Definition:** What-If Analysis is a set of Excel tools that lets you test different values in a formula to see how they affect the outcome, or work backward from a desired outcome to find the input needed to achieve it — without manually changing and recalculating each time. It comes in three forms: Goal Seek, Data Tables, and Scenario Manager.

**Interview answer:** "What-If Analysis is used when I want to see how changing one or more inputs affects a result — for example, checking how many units I'd need to sell to hit a target profit. Excel gives three tools for this: Goal Seek for single-variable backward calculation, Data Tables for testing a range of input values at once, and Scenario Manager for comparing multiple named sets of assumptions."

| Tool | Definition |
|---|---|
| Goal Seek | Works backward — finds the input value needed to achieve a desired formula result |
| Data Table | Shows how a formula's result changes with different values of one or two input variables |
| Scenario Manager | Lets you create and compare multiple sets of input values (scenarios) and see their different outcomes |

---

## 14. Charts

**Definition:** Visual representations of data (bar, line, pie, combo, etc.) used to identify trends, comparisons, and patterns more intuitively than raw numbers.

---

## 15. Macros & VBA (Basics)

**Macro** – A recorded or coded sequence of actions that automates repetitive tasks in Excel.
**VBA (Visual Basic for Applications)** – The programming language used to write and customize macros beyond what the macro recorder can capture.

---

## 16. Dynamic Array Functions (Newer Excel)

- **UNIQUE** – Returns a list of unique values from a range
- **FILTER** – Returns rows that match specified criteria
- **SORT** – Sorts a range or array
- **SEQUENCE** – Generates a list of sequential numbers

---

## 17. Common Interview Q&A (Quick Fire)

**Q: Difference between COUNT and COUNTA?**
A: COUNT counts only numeric cells; COUNTA counts all non-blank cells (numbers, text, dates).

**Q: What is a Named Range?**
A: A user-defined name assigned to a cell or range, making formulas more readable (e.g., `=SUM(SalesData)` instead of `=SUM(A2:A100)`).

**Q: Freeze Panes vs Split?**
A: Freeze Panes locks specific rows/columns in place while scrolling; Split divides the window into separate scrollable sections.

**Q: What is the difference between .xls and .xlsx?**
A: .xls is the older binary format (Excel 97-2003); .xlsx is the newer XML-based format, smaller in size and default since Excel 2007.

**Q: What's the difference between a Table and a normal Range in Excel?**
A: A Table (Ctrl+T) auto-expands with new data, supports structured references, and integrates directly with PivotTables and Power Query — a plain range does not.

**Q: How do you handle duplicate data?**
A: Using Conditional Formatting to highlight duplicates, the Remove Duplicates tool, or COUNTIF-based formulas to flag them.

**Q: Explain the difference between absolute and relative referencing with an example.**
A: If `=A1*B1` is in cell C1 and copied to C2, a relative reference becomes `=A2*B2`. If written as `=$A$1*B1`, the A1 stays fixed while B1 still adjusts.
