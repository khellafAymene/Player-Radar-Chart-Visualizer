# 🕸️ Player Radar Chart Visualizer

A customizable **polar/radar chart** tool for visualizing football (soccer) player statistics, built with Python and Matplotlib. Designed to produce clean, professional-looking player performance visuals.

---

## 📊 Example Output

The chart displays each player's statistics as a polar bar chart, with:
- **Outer segments** showing the maximum possible value (lightly colored)
- **Inner segments** showing the actual player value (fully colored)
- **Value labels** displayed inside each segment
- **Category legend** at the top with color coding
- **Player name** as the chart title

---

## 📁 Project Structure

```
├── Player.py            # Main script for generating the chart
├── DATA.xlsx            # Excel file containing player statistics (sheet: PLAYER)
└── README.md
```

---

## 📋 Excel File Format (`DATA.xlsx` → Sheet: `PLAYER`)

The script reads from the `PLAYER` sheet with the following required columns:

| Column     | Description                              | Example         |
|------------|------------------------------------------|-----------------|
| `PLAYER`   | Player name                              | Lionel Messi    |
| `METRIC`   | Statistic name (add `%` for percentages) | Goals, Pass%    |
| `VALUE`    | Player's value for this metric           | 25              |
| `MAX`      | Maximum possible value for this metric   | 40              |
| `CATEGORY` | Group/category name for color coding     | Attacking       |
| `COLOR`    | Hex color for this category              | #e63946         |

> **Note:** Each row represents one metric. All rows for the same player share the same `PLAYER` value.

---

## ⚙️ Requirements

### Python Libraries

```bash
pip install pandas matplotlib numpy openpyxl ANIS_HAJJAJI
```

### Custom Module

This project depends on `ANIS_HAJJAJI.py`, which must be in the same directory. It provides three helper functions:

| Function              | Description                                      |
|-----------------------|--------------------------------------------------|
| `make_lighter(color, alpha)` | Lightens a hex color by the given factor  |
| `percent_to_number(value)`   | Strips `%` sign and converts to float     |
| `auto_split(text, max_len)`  | Splits long metric names across two lines |

### Font

The script uses a custom Arabic-compatible font (**Almarai**). Download it from [Google Fonts](https://fonts.google.com/specimen/Almarai) and update the path in the script:

```python
Path = r"path\to\Almarai-Regular.ttf"
```

---

## 🚀 Usage

1. Fill in `DATA.xlsx` with your player data following the format above.
2. Update `Path` in the script with your local font path.
3. Customize the chart settings (see below).
4. Run the script:

```bash
python Player.py
```

The chart will be displayed using `plt.show()`. To save it as an image instead, replace the last line with:

```python
plt.savefig("player_chart.png", dpi=150, bbox_inches="tight")
```

---

## 🎨 Customization

All visual settings are grouped at the top of the script for easy editing:

### 1. Title
```python
First_tittel = "Anis"           # Player name shown as title
First_tittel_color = "#570101"  # Title color
First_tittel_size = 12          # Title font size
First_tittel_bold = "bold"      # Title weight ("bold" or None)
```

### 2. Metric Labels (outside the chart)
```python
Metric_size = 9                  # Font size
Metric_color = "black"           # Label color
Metric_bold = "bold"             # Font weight
Metric_distance = 108            # Distance from the chart edge
Metric_color_option = False      # True = labels take category color
```

### 3. Value Labels (inside each segment)
```python
Metric_Value_size = 8                          # Font size
Metric_Value_color_text = "#000000"            # Text color
Metric_Value_bold = "bold"                     # Font weight
Metric_Value_color_background_light = 0.25     # Box background opacity
Metric_Value_box_pad = 0.2                     # Box padding
Metric_Value_box_edgecolor = "#000000"         # Box border color
```

### 4. Chart Appearance
```python
Circle_size = 10          # Inner circle radius
out_color_light = 0.8     # Opacity of outer (background) segments
background = "#FFFFFF"    # Background color
line_color = "#FFFFFF"    # Divider line color between segments
Length = 8                # Figure height (inches)
Width = 8                 # Figure width (inches)
```

### 5. Legend
```python
legend_text_size = 7          # Legend font size
legend_text_bold = None       # Legend font weight (None or "bold")
legend_color_option = True    # True = legend text matches category color
```

---

## 📦 Dependencies Summary

| Package      | Purpose                     |
|--------------|-----------------------------|
| `pandas`     | Reading Excel data          |
| `matplotlib` | Chart rendering             |
| `numpy`      | Angle calculations          |
| `openpyxl`   | Excel file support          |

---

## 🙏 Credits

Created by **Aymene khellaf**  
