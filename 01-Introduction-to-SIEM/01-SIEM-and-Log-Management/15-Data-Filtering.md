# 📘 Data Filtering in Splunk 

---

# 1️⃣ Learning Objective

By the end of this session, you will understand:

- How to filter data in Splunk
- How to apply multi-level filtering
- How to narrow large datasets efficiently
- How to display selected fields only
- Table formatting and display options

---

# 2️⃣ Starting Dataset

Example dataset:

`World_Airports.csv`

Total events:

~75,000 events

Search scope:

`All Time`

---

# 3️⃣ Basic Filtering

Filtering in Splunk is done using:

```
field_name=value
```

Example:

```
iso_region="US-TX"
```

This filters all airports in Texas.

Result:

~3,638 events

---

# 4️⃣ Second-Level Filtering

Now refine further:

```
iso_country="US"
```

This restricts data to the United States.

You can combine filters simply by space:

```
iso_country="US" iso_region="US-TX"
```

This acts as AND condition.

---

# 5️⃣ Multi-Level Filtering (More Precision)

Now filter even further:

```
iso_country="US" municipality="Houston"
```

Result:

~132 events

From:

75,000 → 3,638 → 132

This demonstrates layered filtration.

---

# 6️⃣ Creating a Table View

To display all fields:

```
| table *
```

This shows all columns.

---

# 7️⃣ Displaying Specific Fields Only

Instead of all fields:

```
| table host id iso_country iso_region local_code municipality name
```

This restricts output to selected columns.

This improves:

- Readability
- Performance
- Analysis clarity

---

# 8️⃣ Multi-Level Filtering with Table

Full example:

```
index=main iso_country="US" municipality="Houston"
| table id iso_country iso_region municipality name
```

---

# 9️⃣ Filtering Logic in Splunk

Splunk supports:

### 🔹 AND (default)
```
field1=value1 field2=value2
```

### 🔹 OR
```
field1=value1 OR field2=value2
```

### 🔹 NOT
```
field1=value1 NOT municipality="Houston"
```

---

# 🔟 Range Filtering

You can filter numeric ranges:

```
elevation_ft > 500
```

Or:

```
elevation_ft >= 1000 elevation_ft <= 5000
```

---

# 1️⃣1️⃣ Using Wildcards

Example:

```
municipality="San*"
```

Matches:

- San Antonio
- San Diego
- San Jose

---

# 1️⃣2️⃣ Display & Formatting Options in Search

Splunk allows you to customize view.

---

## 🔹 Events Per Page

Options:

- 10
- 20
- 50
- 100

Increasing per-page reduces number of pages.

---

## 🔹 Wrap vs No Wrap

- Wrap → Long text broken into lines
- No Wrap → Single horizontal scroll

---

## 🔹 Row Numbers

Enable row numbering for easier tracking.

---

## 🔹 Cell Selection

Clicking a cell:

- Highlights the value
- Enables quick filtering

---

## 🔹 Table Summary Options

You can enable:

- Totals
- Percentages
- Field summaries

---

## 🔹 Preview Mode

- Preview ON → Shows partial results while loading
- Preview OFF → Waits for full search completion

---

# 1️⃣3️⃣ Real-World Example

Imagine 10 million firewall logs.

You can filter:

```
action="blocked" src_country="Nepal" dest_port=443
```

From millions → only critical records.

This is why filtering is powerful.

---

# 1️⃣4️⃣ Performance Best Practices

✔ Always filter early  
✔ Avoid `All Time` unless necessary  
✔ Use specific fields  
✔ Limit displayed columns  
✔ Use time range wisely  

---

# 1️⃣5️⃣ Brief Explanation

Data filtering in Splunk allows analysts to narrow large datasets using field-value pairs, logical operators, and range conditions. Multi-level filtering can reduce millions of events to specific relevant records. Using the `table` command improves readability by limiting output to selected fields. Efficient filtering enhances performance and investigative accuracy.

---

# 🔥 Final Takeaway

Filtering transforms:

Massive Data → Targeted Insight

From:

75,000 events  
To  
132 specific records  

This is the power of Splunk filtering.


---

**✍️ Notes By Abhishek (Ez Abyss)**
