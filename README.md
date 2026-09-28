
# 📊 SQL Analysis: International Student Mental Health by Length of Stay

## Business Question

**How does the length of stay impact the mental health condition of international students?**

The objective of this analysis is to understand whether the duration of stay in a new country influences international students' mental health outcomes.

The analysis focuses on three key mental health indicators:

- Depression symptoms
- Suicide-related concerns
- Acculturative stress

---

# 🧮 SQL Query

```sql
SELECT
    stay,
    COUNT(*) AS count_int,
    ROUND(AVG(todep),2) AS average_phq,
    ROUND(AVG(tosc),2) AS average_scs,
    ROUND(AVG(toas),2) AS average_as
FROM students
WHERE inter_dom = 'Inter'
GROUP BY stay
ORDER BY stay DESC;
```

---

# 🔍 Analysis Steps Performed

## Step 1: Data Filtering

### Action Taken

The dataset was filtered to include only international students.

```sql
WHERE inter_dom = 'Inter'
```

### Why This Filter Was Applied?

International students experience unique challenges while adapting to a new environment, including:

- Cultural differences
- Language barriers
- Academic pressure
- Social adjustment challenges

Analyzing only international students helps identify their specific mental health patterns.

---

# Step 2: Data Grouping

### Action Taken

Students were grouped based on their length of stay.

```sql
GROUP BY stay
```

### Column Used:

`stay`

### Actual Meaning:

**Length of Stay**

This column represents the number of years an international student has stayed in the country.

Example:

| stay | Meaning |
|---|---|
| 1 | Student stayed for 1 year |
| 3 | Student stayed for 3 years |
| 10 | Student stayed for 10 years |

---

## Why Was `stay` Selected for Analysis?

Length of stay can influence a student's adjustment process.

Over time, students may experience changes in:

- Cultural adaptation
- Language skills
- Social relationships
- Sense of belonging
- Mental health condition

This analysis helps answer:

> "Does mental health change as international students spend more time in a new environment?"

---

# Step 3: Calculate Mental Health Metrics

## 1. International Student Count

### SQL Function:

```sql
COUNT(*) AS count_int
```

### Action:

Counted the number of international students in each stay duration group.

### Result Meaning:

Shows how many students belong to each length-of-stay category.

Example:

| stay | count_int |
|---|---|
| 1 | 95 |

Interpretation:

95 international students have stayed for 1 year.

---

# 2. Average Depression Score (PHQ)

### SQL Function:

```sql
ROUND(AVG(todep),2) AS average_phq
```

### Column Used:

`todep`

### Full Meaning:

**Total Depression Score**

### Purpose:

Measures the average depression symptoms among international students.

### Result Interpretation:

- Higher score → Higher depression symptoms
- Lower score → Lower depression symptoms

This helps compare depression levels across different stay durations.

---

# 3. Average Suicide Concern Score (SCS)

### SQL Function:

```sql
ROUND(AVG(tosc),2) AS average_scs
```

### Column Used:

`tosc`

### Full Meaning:

**Total Suicide Concern Score**

### Purpose:

Measures suicide-related concerns among students.

### Result Interpretation:

Shows whether suicide concern levels vary depending on the duration of stay.

---

# 4. Average Acculturative Stress Score (AS)

### SQL Function:

```sql
ROUND(AVG(toas),2) AS average_as
```

### Column Used:

`toas`

### Full Meaning:

**Total Acculturative Stress Score**

### Purpose:

Measures stress caused by adapting to a different cultural environment.

### Result Interpretation:

Shows whether cultural adjustment stress changes as students spend more time in the country.

---

# Step 4: Sorting the Results

### Action Taken:

Results were sorted by length of stay in descending order.

```sql
ORDER BY stay DESC
```

### Purpose:

Displays students with the longest stay duration first, making comparison easier.

---

# 📈 Output Generated

The final output contains five analytical columns:

| Column | Description |
|---|---|
| `stay` | Length of stay group |
| `count_int` | Number of international students |
| `average_phq` | Average depression score |
| `average_scs` | Average suicide concern score |
| `average_as` | Average acculturative stress score |

---

# 💡 Business Value / Insights

This analysis helps educational institutions understand:

- How mental health indicators vary among international students
- Whether students with shorter or longer stays require different levels of support
- How cultural adaptation may influence student wellbeing

The findings can support:

- Student counselling programs
- International student support services
- Mental health awareness initiatives

---

# 🛠️ SQL Skills Demonstrated

| SQL Concept | Usage |
|---|---|
| `SELECT` | Selected required columns |
| `WHERE` | Filtered international students |
| `GROUP BY` | Created stay duration groups |
| `COUNT()` | Counted students |
| `AVG()` | Calculated average scores |
| `ROUND()` | Rounded decimal values |
| `ORDER BY` | Sorted final output |

---

# 📌 Key Learning

This analysis demonstrates the complete SQL analytical workflow:

**Business Question → Data Filtering → Data Grouping → Aggregation → Insight Generation**
