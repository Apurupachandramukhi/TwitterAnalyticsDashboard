# 📊 Twitter Analytics Dashboard – Task 4

This task creates a scatter chart to analyze the relationship between media engagements and media views for filtered tweets, with time-based visibility on the dashboard.

---

## ✅ Task Objective
- Plot a **Scatter Chart** showing:
  - 📈 **X-Axis:** Media Views
  - 📊 **Y-Axis:** Media Engagements
- Highlight tweets where:
  - **Engagement Rate > 5%**
- Apply filters:
  - Tweets with **more than 10 replies**
  - **Tweet Date** is an **odd-numbered day**
  - **Tweet Word Count > 50**
- Display the chart **only between 6PM to 11PM IST**.

---

## 📝 Steps Implemented
1. **Opened Project File**
   - Opened `project1.pbix` in Power BI Desktop.
   - Saved as `twitter_dashboard_task4.pbix`.

2. **Applied Dataset Filters**
   - Replies Filter: `Replies > 10`
   - Odd Date Filter:
     ```DAX
     IsOddDate = IF(MOD(DAY([date]), 2) = 1, 1, 0)
     ```
     Filter: `IsOddDate = 1`
   - Tweet Word Count Filter:
     ```DAX
     WordCount = LEN(TRIM([Tweet])) - LEN(SUBSTITUTE(TRIM([Tweet]), " ", "")) + 1
     ```
     Filter: `WordCount > 50`

3. **Created Scatter Chart**
   - X-Axis: `Media Views`
   - Y-Axis: `Media Engagements`
   - Highlighted tweets:
     ```DAX
     HighlightTweet = IF([Engagement Rate] > 0.05, "High Engagement", "Normal")
     ```
   - Used `HighlightTweet` as Legend.

4. **Added Time-Based Visibility**
   - Created DAX Measure:
     ```DAX
     ShowScatterChart = 
     VAR CurrentTime = TIME(HOUR(NOW())+5, MINUTE(NOW()), SECOND(NOW()))
     RETURN
     IF(CurrentTime >= TIME(18,0,0) && CurrentTime <= TIME(23,0,0), 1, 0)
     ```
   - Applied as visual-level filter: `ShowScatterChart = 1`.

5. **Formatted Chart**
   - Axis Titles:
     - X-Axis: *“Media Views”*
     - Y-Axis: *“Media Engagements”*
   - Chart Title:
     > **“Media Engagements vs Media Views (Odd Dates, Word Count >50)”**

---

## 📁 Output File
- **File Name:** `twitter_dashboard_task4.pbix`
- **Location:** Uploaded in this repository.

---

## 🗓 Filters Applied
| Filter Type          | Condition                              |
|----------------------|------------------------------------------|
| **Replies**          | More than 10                            |
| **Odd Dates**        | Tweet date day is odd                   |
| **Word Count**       | More than 50 words                      |
| **Highlight Tweets** | Engagement Rate > 5%                    |
| **Time Visibility**  | Chart visible 6PM–11PM IST only         |

---

## 🚀 Commit Message
```
Task 4: Added Scatter Chart for Media Engagements vs Media Views with odd-date and word count filters, time visibility (6PM–11PM IST)
```
