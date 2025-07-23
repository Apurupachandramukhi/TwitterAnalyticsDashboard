# 📊 Twitter Analytics Dashboard – Task 7

This task creates a line chart to show the trend of average engagement rate over each month of the year, separated by media content, with multiple filters and time-based visibility.

---

## ✅ Task Objective
- Plot a **Line Chart** showing:
  - 📊 **Monthly Average Engagement Rate**
  - Separate lines for:
    - Tweets **with media content**
    - Tweets **without media content**
- Apply filters:
  - **Engagement Rate = even numbers**
  - **Tweet Date = odd numbers**
  - **Tweet Character Count > 20**
  - **Exclude Tweets containing the letter ‘C’**
- Display the chart **only between 3PM–5PM and 7AM–11AM IST**

---

## 📝 Steps Implemented

---

### 🟢 **Step 1: Open and Save File**
📍 **Where:** Power BI Desktop  
📍 **Table Used:** `project1.pbix`

- Opened `project1.pbix` in Power BI Desktop.
- Saved as `twitter_dashboard_task7.pbix`.

---

### 🟢 **Step 2: Duplicate Table**
📍 **Where:** Power Query Editor → Queries Pane  
📍 **Table Used:** `SocialMedia`

- Duplicated table and renamed it as `Task7_Table`.
- Clicked **Close & Apply** to load the table into Power BI.

---

### 🟢 **Step 3: Apply Dataset Filters**
📍 **Where:** Power BI → Modeling Tab  
📍 **Table Used:** `Task7_Table`

1. **Engagement Rate Filter (Even Numbers):**
   ```DAX
   EvenEngagement =
   IF(MOD(ROUND('Task7_Table'[Engagement Rate]*100,0), 2) = 0, "Even", "Odd")
   ```
   ✅ Applied filter: `EvenEngagement = "Even"`

2. **Tweet Date Filter (Odd Numbers):**
   ```DAX
   OddTweetDate =
   IF(MOD(DAY('Task7_Table'[date]), 2) <> 0, "Odd", "Even")
   ```
   ✅ Applied filter: `OddTweetDate = "Odd"`

3. **Tweet Character Count (> 20):**
   ```DAX
   CharacterCount = LEN('Task7_Table'[Tweet])
   ```
   ✅ Applied filter: `CharacterCount > 20`

---

### 🟢 **Step 4: Remove Tweets Containing Letter 'C'**
📍 **Where:** Power Query Editor → Transform Tab  
📍 **Table Used:** `Task7_Table`

- Applied a text filter on `Tweet`:  
  ```
  Does Not Contain "C" (case-insensitive)
  ```
- Clicked **Close & Apply** to load the cleaned table.

---

### 🟢 **Step 5: Create Media Content Flag**
📍 **Where:** Power BI → Modeling Tab → New Column  
📍 **Table Used:** `Task7_Table`

```DAX
MediaContent =
IF('Task7_Table'[Media Views] > 0, "With Media", "Without Media")
```

---

### 🟢 **Step 6: Create Visual**
📍 **Where:** Power BI Report View (Canvas)  
📍 **Table Used:** `Task7_Table`

- Inserted a **Line Chart** from Visualizations Pane.  
- Assigned fields:

| **Field**               | **Assign To** |
|-------------------------|----------------|
| Month (from Date)       | X-Axis         |
| Average Engagement Rate | Y-Axis         |
| MediaContent            | Legend         |

---

### 🟢 **Step 7: Add Time-Based Visibility**
📍 **Where:** Power BI → Modeling Tab  
📍 **Table Used:** `Task7_Table`

1. **Created HourIST Column:**
   ```DAX
   HourIST =
   HOUR('Task7_Table'[time_clean] + TIME(5,30,0))
   ```

2. **Created ShowGraph Column:**
   ```DAX
   ShowGraph =
   IF(
       ([HourIST] >= 7 && [HourIST] < 11) || ([HourIST] >= 15 && [HourIST] < 17),
       "Show",
       "Hide"
   )
   ```

3. **Applied Visual Filter:**
   - In Filters Pane → Dragged `ShowGraph`.
   - Applied filter: `ShowGraph = "Show"`

✅ The chart now appears **only between 7AM–11AM and 3PM–5PM IST**.

---

### 🟢 **Step 8: Format Chart**
📍 **Where:** Power BI → Report View  
📍 **Table Used:** `Task7_Table`

- Set Chart Title:
  ```
  "Monthly Average Engagement Rate (With/Without Media, Time Filtered)"
  ```
- Adjusted Axis Titles:
  - X-Axis: *“Month”*
  - Y-Axis: *“Average Engagement Rate”*
- Enabled Data Labels and formatted legend.

---

## 📁 Output File
- **File Name:** `twitter_dashboard_task7.pbix`
- **Location:** Uploaded in this repository.

---

## 🚀 Commit Message
```
Task 7: Added Line Chart for Average Engagement Rate with media separation and dual time filters (3PM–5PM, 7AM–11AM IST)
```
