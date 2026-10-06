# Pandas Interview Questions

A collection of **Pandas interview questions** organized by difficulty level, with concise answers and examples.

---

# 🟢 Beginner Level

## 1. What is Pandas?

Pandas is a Python library used for **data manipulation and data analysis**. Its main data structures are **Series** and **DataFrame**.

## 2. How do you import Pandas?

```python
import pandas as pd
```

## 3. What is a Series?

A Series is a **one-dimensional labeled array**.

```python
s = pd.Series([10, 20, 30])
```

## 4. What is a DataFrame?

A DataFrame is a **two-dimensional labeled data structure** with rows and columns.

```python
df = pd.DataFrame({
    "Name": ["A", "B", "C"],
    "Age": [20, 25, 30]
})
```

## 5. Difference between Series and DataFrame?

| Series | DataFrame |
|---|---|
| 1-D | 2-D |
| Single labeled column | Multiple rows and columns |

## 6. How do you read a CSV file?

```python
df = pd.read_csv("data.csv")
```

## 7. How do you read an Excel file?

```python
df = pd.read_excel("data.xlsx")
```

## 8. How do you inspect the first few rows?

```python
df.head()
```

## 9. How do you inspect the last few rows?

```python
df.tail()
```

## 10. How do you check the shape?

```python
df.shape
```

Returns `(rows, columns)`.

## 11. How do you check column names?

```python
df.columns
```

## 12. How do you check data types?

```python
df.dtypes
```

## 13. What does `info()` do?

```python
df.info()
```

It shows column names, non-null counts, data types, and memory information.

## 14. What does `describe()` do?

```python
df.describe()
```

It provides descriptive statistics for numeric columns.

## 15. How do you select a column?

```python
df["Age"]
```

Multiple columns:

```python
df[["Name", "Age"]]
```

---

# 🟡 Intermediate Level

## 16. What is `loc`?

`loc` is **label-based indexing**.

```python
df.loc[2, "Age"]
```

## 17. What is `iloc`?

`iloc` is **integer-position-based indexing**.

```python
df.iloc[2, 1]
```

## 18. Difference between `loc` and `iloc`?

```text
loc  → labels
iloc → integer positions
```

## 19. What are `at` and `iat`?

They are used for accessing a **single value**.

```python
df.at[2, "Age"]
df.iat[2, 1]
```

## 20. What is filtering?

```python
df[df["Age"] > 25]
```

## 21. How do you filter with multiple conditions?

```python
df[(df["Age"] > 20) & (df["Age"] < 30)]
```

```text
& → AND
| → OR
~ → NOT
```

## 22. What is `.isin()`?

```python
df[df["City"].isin(["Pune", "Mumbai"])]
```

## 23. How do you sort a DataFrame?

```python
df.sort_values("Age")
```

Descending:

```python
df.sort_values("Age", ascending=False)
```

## 24. What is `sort_index()`?

```python
df.sort_index()
```

Sorts by the DataFrame index.

## 25. How do you rename columns?

```python
df.rename(columns={"Age": "Years"}, inplace=True)
```

## 26. How do you remove a column?

```python
df.drop(columns=["Age"])
```

## 27. What does `inplace=True` mean?

It modifies the existing object rather than returning a separate modified object.

```python
df.drop(columns=["Age"], inplace=True)
```

## 28. How do you check missing values?

```python
df.isna().sum()
```

## 29. Difference between `isna()` and `isnull()`?

They are effectively equivalent in Pandas.

```python
df.isna()
df.isnull()
```

## 30. How do you remove missing values?

```python
df.dropna()
```

## 31. How do you replace missing values?

```python
df.fillna(0)
```

Example:

```python
df["Age"] = df["Age"].fillna(df["Age"].mean())
```

## 32. Does `dropna()` remove empty strings?

**No.** `""` is not the same as `NaN`.

```python
df["Column"] = df["Column"].replace("", np.nan)
df = df.dropna()
```

## 33. What is `replace()`?

```python
df["City"] = df["City"].replace("Pune ", "Pune")
```

## 34. What is `apply()`?

```python
df["Age"] = df["Age"].apply(lambda x: x + 1)
```

## 35. What is `lambda`?

A lambda is a small anonymous function.

```python
lambda x: x * 2
```

## 36. What is `groupby()`?

```python
df.groupby("Department")["Salary"].mean()
```

It groups data and allows aggregation.

## 37. What is aggregation?

Common aggregation functions include:

```python
sum()
mean()
min()
max()
count()
```

Example:

```python
df.groupby("Department")["Salary"].agg(["mean", "max", "min"])
```

## 38. What is `value_counts()`?

```python
df["City"].value_counts()
```

Counts the frequency of unique values.

## 39. What is `query()`?

```python
df.query("Age > 25")
```

Filters rows using a readable expression.

## 40. What is `reset_index()`?

```python
df.reset_index()
```

Resets the index to the default integer index.

## 41. What is `set_index()`?

```python
df.set_index("Name")
```

Sets a column as the index.

## 42. What is `concat()`?

```python
pd.concat([df1, df2])
```

Combines Pandas objects along rows or columns.

## 43. What is `merge()`?

```python
pd.merge(df1, df2, on="customer_id")
```

Combines DataFrames using matching keys, similar to a SQL join.

## 44. Difference between `concat()` and `merge()`?

```text
concat → combines by rows or columns
merge  → combines using matching keys
```

## 45. What is a pivot table?

```python
pd.pivot_table(
    df,
    values="Sales",
    index="Region",
    columns="Product",
    aggfunc="sum"
)
```

It summarizes data across rows and columns.

---

# 🔴 Advanced Level

## 46. What is a MultiIndex?

A MultiIndex allows multiple levels of indexes.

```python
df.set_index(["Department", "Employee"])
```

## 47. Difference between `merge()`, `join()`, and `concat()`?

```text
merge  → joins using keys
join   → commonly joins using indexes
concat  → combines along an axis
```

## 48. What is `rolling()`?

`rolling()` performs calculations over a moving window.

```python
df["rolling_sum"] = df["Sales"].rolling(3).sum()
```

## 49. What is `cumsum()`?

Calculates cumulative sum.

```python
df["Cumulative_Sales"] = df["Sales"].cumsum()
```

## 50. What is `rank()`?

Assigns ranks to values.

```python
df["Rank"] = df["Salary"].rank(ascending=False)
```

## 51. Difference between `rank()` and `sort_values()`?

```text
rank        → assigns a rank
sort_values → rearranges rows
```

## 52. What is `drop_duplicates()`?

```python
df.drop_duplicates()
```

For a specific column:

```python
df.drop_duplicates(subset=["Email"])
```

## 53. How do you find duplicate rows?

```python
df.duplicated()
```

Count duplicates:

```python
df.duplicated().sum()
```

## 54. What is `pivot()`?

```python
df.pivot(
    index="Date",
    columns="Product",
    values="Sales"
)
```

It reshapes data without aggregation. Duplicate index/column combinations can cause an error.

## 55. Difference between `pivot()` and `pivot_table()`?

```text
pivot       → reshapes data, no aggregation
pivot_table → reshapes data and supports aggregation
```

## 56. What is `melt()`?

`melt()` converts wide data into long format.

```python
pd.melt(
    df,
    id_vars=["Name"],
    var_name="Metric",
    value_name="Value"
)
```

## 57. How do you convert a column to datetime?

```python
df["Date"] = pd.to_datetime(df["Date"])
```

## 58. How do you extract year, month, and day?

```python
df["Year"] = df["Date"].dt.year
df["Month"] = df["Date"].dt.month
df["Day"] = df["Date"].dt.day
```

## 59. What is vectorization in Pandas?

Vectorization means operating on an entire Series/DataFrame instead of using explicit Python loops.

```python
df["Salary"] = df["Salary"] * 1.10
```

## 60. What is `SettingWithCopyWarning`?

It can occur when Pandas is unsure whether an operation is modifying a view or a copy.

Prefer explicit `.loc` assignment:

```python
df.loc[df["Age"] > 25, "Category"] = "Senior"
```

## 61. How do you slice rows?

```python
df[1:5]
```

## 62. How do you slice rows and columns with `loc`?

```python
df.loc[0:5, ["Name", "Age", "Salary"]]
```

## 63. How do you slice rows and columns with `iloc`?

```python
df.iloc[0:5, 0:3]
```

## 64. How do you check for empty strings?

```python
(df["Column"] == "").sum()
```

For whitespace-only strings:

```python
(df["Column"].astype(str).str.strip() == "").sum()
```

## 65. How do you remove leading and trailing spaces?

```python
df["Column"] = df["Column"].str.strip()
```

For all object columns:

```python
for col in df.select_dtypes(include="object").columns:
    df[col] = df[col].str.strip()
```

## 66. How do you replace empty strings with `0`?

```python
df["Column"] = df["Column"].replace("", 0)
```

For whitespace-only strings:

```python
df["Column"] = df["Column"].replace(r"^\s*$", 0, regex=True)
```

---

# ⭐ Most Important Pandas Interview Topics

- Series vs DataFrame
- `head()`, `tail()`, `info()`, `describe()`
- `shape`, `columns`, `dtypes`
- `loc`, `iloc`, `at`, `iat`
- Indexing and slicing
- Filtering and `.isin()`
- `.query()`
- `sort_values()`
- `drop()` and `rename()`
- Missing values: `isna()`, `dropna()`, `fillna()`
- Empty strings vs `NaN`
- `replace()`
- `apply()` and `lambda`
- `groupby()` and aggregation
- `value_counts()`
- `concat()` vs `merge()`
- `pivot()` vs `pivot_table()`
- `melt()`
- `reset_index()` / `set_index()`
- `rolling()`, `cumsum()`, `rank()`
- `drop_duplicates()`
- Datetime operations
- Vectorization
- `SettingWithCopyWarning`

---

# 📌 Suggested Preparation Order

```text
Beginner
   ↓
Series & DataFrame
   ↓
Reading Data
   ↓
Indexing & Slicing
   ↓
Intermediate
   ↓
Filtering
   ↓
Sorting
   ↓
Missing Values
   ↓
GroupBy & Aggregation
   ↓
Merge & Concatenate
   ↓
Advanced
   ↓
Pivot / Melt
   ↓
Window Operations
   ↓
Datetime
   ↓
Performance & Copy/View Concepts
```

> **Interview Tip:** For each topic, prepare the definition, syntax, a small example, and one common interview follow-up question.
