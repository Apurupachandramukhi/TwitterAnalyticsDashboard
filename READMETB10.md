## ✅ Task 10 – Engagement Rate Comparison: With vs Without App Opens

### 🎯 Objective:
Compare the average **Engagement Rate** for tweets:
- With **App Opens**
- Without **App Opens**

### 📊 Visual Used:
**Clustered Column Chart** showing:
- X-Axis: `AppOpenType` ("With App Opens", "Without App Opens")
- Y-Axis: Average of `EngagementRate`
- Tooltip: `Tweet` (optional)

### 📌 Filters Applied:
- **Impressions**: Even numbers only
- **Tweet Date**: Odd day only
- **Tweet Character Count**: > 30
- **Tweet Text**: Must **not contain** the letter **'D'**
- **Tweet Time (IST)**: Only between **9 AM and 5 PM**
- **Day of Week**: Only **Weekdays**

### ⏲️ Chart Visibility Conditions:
The chart is displayed **only** between:
- **12 PM – 6 PM IST**
- **7 AM – 11 AM IST**

(`ShowGraph = "Show"` controls visibility)

### ⚙️ DAX Columns Created:
- `EngagementRate`
- `CharacterCount`
- `OddDate`
- `EvenImpressions`
- `AppOpenType`
- `HourPost`
- `ShowGraph`

### 🎨 Formatting:
- Chart title: **"Engagement Rate Comparison: With vs Without App Opens (Filtered View)"**
- Data labels enabled
- Contrasting colors (optional for clarity)
