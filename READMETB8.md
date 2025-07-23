# 📊 Twitter Analytics Dashboard – Task 8

This task creates a visualization comparing the number of replies, retweets, and likes for tweets that have received media engagements greater than the median value. It applies multiple filters and time-based visibility on the dashboard.

---

## ✅ Task Objective
- Plot a **Clustered Bar Chart** showing:
  - 📊 **Replies, Retweets, and Likes** for selected tweets
- Apply filters:
  - **Media Engagements > Median Value**
  - **Date between June–August 2020**
  - **Tweet Date = odd numbers**
  - **Media Views = even numbers**
  - **Tweet Character Count > 20**
  - **Exclude Tweets containing the letter ‘S’**
- Display the chart **only between 3PM–5PM and 7AM–11AM IST**

---

## 📝 Steps Implemented

---

### 🟢 **Step 1: Open and Save File**
📍 **Where:** Power BI Desktop  
📍 **Table Used:** `project1.pbix`

- Opened `project1.pbix` in Power BI Desktop.
- Saved as `twitter_dashboard_task8.pbix`.

---

### 🟢 **Step 2: Duplicate Table**
📍 **Where:** Power Query Editor → Queries Pane  
📍 **Table Used:** `SocialMedia`

- Duplicated table and renamed it as `Task8_Table`.
- Clicked **Close & Apply** to load the table into Power BI.

---

### 🟢 **Step 3: Apply Dataset Filters**
📍 **Where:** Power BI → Modeling Tab & Power Query  
📍 **Table Used:** `Task8_Table`

1. **Media Engagements > Median Value:**
   - Created measure:
     ```DAX
     MedianMediaEngagement =
     MEDIAN('Task8_Table'[Media Engagements])
     ```
   - Created column:
     ```DAX
     MediaAboveMedian =
     IF('Task8_Table'[Media Engagements] > [MedianMediaEngagement], "Above Median", "Below Median")
     ```
   ✅ Filter: `MediaAboveMedian = "Above Median"`

2. **Date Range (June–August 2020):**
   ✅ Applied filter in Filters Pane:
   ```
   Date >= 01-Jun-2020 AND Date <= 31-Aug-2020
   ```

3. **Tweet Date Filter (Odd Numbers):**
   ```DAX
   OddTweetDate =
   IF(MOD(DAY('Task8_Table'[date]), 2) <> 0, "Odd", "Even")
   ```
   ✅ Filter: `OddTweetDate = "Odd"`

4. **Media Views Filter (Even Numbers):**
   ```DAX
   EvenMediaViews =
   IF(MOD('Task8_Table'[Media Views], 2) = 0, "Even", "Odd")
   ```
   ✅ Filter: `EvenMediaViews = "Even"`

5. **Tweet Character Count (> 20):**
   ```DAX
   CharacterCount = LEN('Task8_Table'[Tweet])
   ```
   ✅ Filter: `CharacterCount > 20`

6. **Removed Tweets Containing Letter ‘S’:**
📍 **Where:** Power Query Editor → Transform Tab  
   - Applied text filter on `Tweet`:  
     ```
     Does Not Contain "S" (case-insensitive)
     ```
   - Clicked **Close & Apply** to load the cleaned table.

---

### 🟢 **Step 4: Create Visual**
📍 **Where:** Power BI Report View (Canvas)  
📍 **Table Used:** `Task8_Table`

- Inserted a **Clustered Bar Chart** from Visualizations Pane.  
- Assigned fields:

| **Field**         | **Assign To** |
|---------------------|----------------|
| Tweet ID           | X-Axis         |
| Replies            | Y-Axis         |
| Retweets           | Y-Axis         |
| Likes              | Y-Axis         |
| MediaAboveMedian   | Legend         |

---

### 🟢 **Step 5: Add Time-Based Visibility**
📍 **Where:** Power BI → Modeling Tab  
📍 **Table Used:** `Task8_Table`

1. **Created HourIST Column:**
   ```DAX
   HourIST =
   HOUR('Task8_Table'[time_clean] + TIME(5,30,0))
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

### 🟢 **Step 6: Format Chart**
📍 **Where:** Power BI → Report View  
📍 **Table Used:** `Task8_Table`

- Set Chart Title:
  ```
  "Comparison of Replies, Retweets, and Likes (Filtered by Median Media Engagement)"
  ```
- Adjusted Axis Titles:
  - X-Axis: *“Tweet ID”*
  - Y-Axis: *“Count”*
- Enabled Data Labels and formatted legend.

---

## 📁 Output File
- **File Name:** `twitter_dashboard_task8.pbix`
- **Location:** Uploaded in this repository.

---

## 🚀 Commit Message
```
Task 8: Added Chart for Replies, Retweets, and Likes comparison with median filter and dual time visibility (3PM–5PM, 7AM–11AM IST)
```
