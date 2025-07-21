# Twitter Analytics Dashboard

## ✅ Task 2: Top 10% Tweets by Engagement Rate

### 📌 Objective:
Develop a chart that displays **tweets with the highest engagement rates (top 10%)** under specific conditions:
- Include only tweets that:
  - Have **more than 50 likes**.
  - Were posted on **weekdays (Monday–Friday)**.
  - Have a **tweet character count less than 30**.
- The chart should be visible **only between 3 PM IST to 5 PM IST**. Outside this time range, the graph will not appear on the dashboard.

---

### ⚙️ Implementation:
1. **Dataset Filters (Power Query):**
   - Filtered rows where `Likes > 50`.
   - Added a column for `DayOfWeek` to filter out Saturday and Sunday.
   - Added a column `TweetLength` to calculate character count and filtered where `TweetLength < 30`.

2. **Calculated Fields (DAX):**
   - **Engagement Rate:**
     ```dax
     EngagementRate = 
     ([Likes] + [Replies] + [Retweets]) / [Impressions]
     ```
   - **Top 10% Engagement Rate:**
     ```dax
     Top10Engagement =
     IF(
        [EngagementRate] >= PERCENTILEX.INC(ALL('YourTable'), [EngagementRate], 0.9),
        1,
        0
     )
     ```
   - **Time-based Visibility Filter:**
     ```dax
     ShowGraph =
     VAR CurrentTime = TIME(HOUR(NOW()), MINUTE(NOW()), 0)
     RETURN
        IF(
           CurrentTime >= TIME(15,0,0) && CurrentTime <= TIME(17,0,0),
           1,
           0
        )
     ```

3. **Visualization:**
   - Added a **Clustered Column Chart** showing:
     - **Axis:** Tweet ID
     - **Values:** Engagement Rate
   - Applied a filter: `Top10Engagement = 1`.
   - Applied a filter: `ShowGraph = 1` to restrict visibility to the specified time.

4. **Formatting:**
   - Customized chart title, axis labels, and colors for clarity.
   - Title: **“Top 10% Tweets by Engagement Rate (Weekdays, <30 Characters)”**

---

### 📁 File:
- `twitter_dashboard_task2.pbix`

---

### ✅ Outcome:
This visual displays only **top-performing tweets** meeting all criteria and ensures compliance with the time-bound visibility requirement for the dashboard.

