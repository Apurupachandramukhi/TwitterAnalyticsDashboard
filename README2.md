# Twitter Analytics Dashboard – Task 2

## ✅ Task 2: Top 10% Tweets by Engagement Rate

### 🎯 Objective:
Create a Power BI report that displays tweets with the highest engagement rates (Top 10%).  
The chart must meet the following conditions:  

- Only include tweets that:  
  - Have more than **50 likes**  
  - Were posted on **weekdays (Monday–Friday)**  
  - Were posted between **3 PM IST and 5 PM IST**  
  - Have a tweet character count **less than 30**  
- Apply **time-based visibility**: The chart should only be visible during **3 PM–5 PM IST**.  

---

### 📊 **Implementation Details:**
- **Data Preparation (Power Query):**
  - Filtered tweets with more than 50 likes.  
  - Extracted and filtered tweets posted only on weekdays (Mon–Fri).  
  - Adjusted UTC timestamps to IST and filtered tweets between 3 PM–5 PM IST.  
  - Filtered tweets with character count <30.  
  - Calculated **Engagement Rate** using:  
    ```
    Engagement Rate = (Likes + Retweets + Replies + Quotes) / Impressions
    ```
  - Selected **Top 10% tweets** based on Engagement Rate.  

- **Report Visualization:**
  - Created a **Bar Chart**:  
    - **X-axis:** tweet_text  
    - **Y-axis:** Engagement Rate  
  - Enabled Data Labels for clear visualization.  
  - Applied time-based visibility using a DAX measure:  
    ```DAX
    ShowChart = IF(HOUR(NOW()) >= 15 && HOUR(NOW()) < 17, 1, 0)
    ```  
    Filtered the chart to show only when `ShowChart = 1`.  

---

### 📁 **Files Included:**
