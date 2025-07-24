# 📊 Task 9: Dual-Axis Chart – Media Views vs. Media Engagements by Day of Week

## 🎯 Objective

Create a **Dual-Axis Chart** in Power BI that shows:
- 📈 **Media Views** (as clustered columns)
- 📉 **Media Engagements** (as a line)

Both plotted by **Day of the Week** with multiple filters and time-based visibility rules.

---

## 🧮 Dataset Used

- **Table:** `Task9_Table` (duplicated from original `SocialMedia` table)

---

## ✅ Data Filters Applied

1. **Last Quarter Only**  
   - Created column: `TweetQuarter = QUARTER([date])`  
   - Filtered for latest quarter (e.g., Q2 if current is Q3)

2. **Tweet Impressions = Even Numbers**  
   - `EvenImpressions = IF(MOD([Impressions], 2) = 0, "Even", "Odd")`  
   - Filtered: `"Even"`

3. **Tweet Date = Odd Numbers**  
   - `OddTweetDate = IF(MOD(DAY([date]), 2) <> 0, "Odd", "Even")`  
   - Filtered: `"Odd"`

4. **Tweet Character Count > 30**  
   - `CharacterCount = LEN([Tweet])`  
   - Filtered: `> 30`

5. **Remove Tweets Containing Letter 'H'**  
   - In Power Query:  
     → Applied Text Filter → Does not contain `"H"`

---

## 📊 Visualization Details

- **Chart Type:** Line and Clustered Column Chart
- **X-Axis (Shared):** Day of the Week (e.g., Monday, Tuesday)
- **Y-Axis Left (Column):** Media Views
- **Y-Axis Right (Line):** Media Engagements

---

## 🎨 Conditional Formatting

- **Highlight spikes in Media Engagements**
  - Created `HighlightColor` column to show red for values **above average**
  - Applied conditional formatting to:
    - Line stroke color (Media Engagements)
    - Data labels

---

## ⏰ Time-Based Visibility (IST Time Filters)

1. **Created Column:** `HourIST = HOUR([time_clean] + TIME(5,30,0))`

2. **Created Column:**  
   ```DAX
   ShowGraph = IF(
       ([HourIST] >= 7 && [HourIST] < 11) || ([HourIST] >= 15 && [HourIST] < 17),
       "Show",
       "Hide"
   )
