# 📊 Twitter Analytics Dashboard – Task 3

This task creates a visual to analyze Twitter engagement rates and impressions with filters for specific date ranges, impressions, likes, and time-based visibility.

---

## ✅ Task Objective
- Create a chart showing:
  - 📈 **Average Engagement Rate**
  - 📊 **Total Impressions**
- Apply filters:
  - Tweets posted between **01-Jan-2020** and **30-Jun-2020**.
  - Only include tweets where:
    - **Impressions > 100**
    - **Likes ≠ 0**
- Display the chart **only between 3PM to 5PM IST** on the dashboard.

---

## 📝 Steps Implemented
1. **Opened Project File**
   - Opened `project1.pbix` in Power BI Desktop.
   - Saved as `twitter_dashboard_task3.pbix`.

2. **Filtered Dataset**
   - Applied a **date range filter** on `date` column:
     - Start Date: **01-Jan-2020**
     - End Date: **30-Jun-2020**.
   - Added additional filters:
     - **Impressions > 100**
     - **Likes ≠ 0**.

3. **Created Chart**
   - Added a **Clustered Column Chart** visual.
   - Fields used:
     - Axis: `Tweet ID`
     - Values:
       - `Engagement Rate` → Average
       - `Impressions` → Sum

4. **Added Time-Based Visibility**
   - Created a DAX Measure:

     ```DAX
     ShowChart = 
     VAR CurrentTime = TIME(HOUR(NOW())+5, MINUTE(NOW()), SECOND(NOW()))
     RETURN
     IF(CurrentTime >= TIME(15,0,0) && CurrentTime <= TIME(17,0,0), 1, 0)
     ```
   - Applied this measure as a **visual-level filter** to ensure the chart appears **only between 3PM–5PM IST**.

5. **Formatted Chart**
   - Added data labels, axis titles, and appropriate colors for clarity.
   - Chart Title:
     > **“Avg Engagement Rate & Total Impressions (Jan–Jun 2020)”**

---

## 📁 Output File
- **File Name:** `twitter_dashboard_task3.pbix`
- **Location:** Uploaded in this repository.

---

## 🗓 Filters Applied
| Filter Type         | Condition                        |
|---------------------|-------------------------------------|
