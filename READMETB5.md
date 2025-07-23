# 📊 Twitter Analytics Dashboard – Task 5

This task creates a clustered bar chart to analyze clicks by tweet category, filtered by date, word count, and with time-based visibility on the dashboard.

---

## ✅ Task Objective
- Plot a **Clustered Bar Chart** showing:
  - 📊 **Sum of URL Clicks**
  - 📊 **Sum of User Profile Clicks**
  - 📊 **Sum of Hashtag Clicks**
- Break down by **Tweet Category**:
  - Tweets with Media
  - Tweets with Links
  - Tweets with Hashtags
- Apply filters:
  - Include tweets with **at least one interaction type (URL/User Profile/Hashtag Clicks > 0)**
  - **Tweet Date** is an **even-numbered day**
  - **Tweet Word Count > 40**
- Display the chart **only between 3PM to 5PM IST**.

---

## 📝 Steps Implemented
1. **Duplicated Table**
   - Duplicated unpivoted table as `Task5_Unpivoted` to keep original dataset clean.

2. **Applied Dataset Filters**
   - Unpivoted Click Columns:
     - Selected `URL Clicks`, `User Profile Clicks`, `Hashtag Clicks`
     - Applied **Unpivot Columns** in Power Query
     - Resulted in:
       - `Click Type`: URL, Profile, Hashtag
       - `Click Count`: Numeric values
   - Even Date Filter:
     ```DAX
     IsEvenDate = IF(MOD(DAY('Task5_Unpivoted'[date]), 2) = 0, 1, 0)
     ```
   - Word Count Filter:
     ``
