# Twitter Analytics Dashboard – Task 3

## ✅ Task 3: Average Engagement Rate and Total Impressions (3–5 PM IST)

### 🎯 Objective:
Create a Power BI report that displays the following metrics for tweets posted between **01-Jan-2020 and 30-Jun-2020**:  

- 📊 **Average Engagement Rate**  
- 📊 **Total Impressions**  

The report must meet the following requirements:  
1. Include only tweets:  
   - Posted between **01-Jan-2020 and 30-Jun-2020**  
   - With **impressions ≥ 100**  
   - Where **likes = 0**  
2. Display the visuals **only during 3 PM–5 PM IST**.  
3. Outside of this time window, the visuals should remain hidden.  

---

### 📊 **Implementation Details:**
- **Data Preparation (Power Query):**
  - Filtered tweets where `timestamp` is between `01-Jan-2020` and `30-Jun-2020`.
  - Applied filters:  
    - **Impressions ≥ 100**  
    - **Likes = 0**
  - Loaded the cleaned dataset into Power BI.

- **Visualizations:**
  - Two **Card visuals** created:  
    - **Card 1:** Average Engagement Rate  
    - **Card 2:** Total Impressions  
  - Cards are arranged side-by-side for a clean dashboard appearance.

- **Time-Based Visibility:**
  - Created a calculated column:  
    ```DAX
    ShowVisualColumn =
    IF(
        HOUR(NOW()) >= 15 && HOUR(NOW()) < 17,
        "Show",
        "Hide"
    )
    ```  
  - Applied a filter:  
    - `ShowVisualColumn = "Show"`
    - Ensures visuals are only visible between **3 PM–5 PM IST**.

---

### 📁 **Files Included:**
- `task3.pbix`: Power BI file for Task 3
- `README.md`: Documentation for Task 3

---

### 🚀 **How to Run:**
1. Open `task3.pbix` in Power BI Desktop.  
2. Verify:  
   - Visuals are visible **only from 3 PM–5 PM IST**.  
   - Filters and calculations are applied as per requirements.  

---

