

---

```markdown
# 📊 Pandas Plotting Cheat Sheet & Flashcards

This document provides a quick reference and understanding of **plotting with Pandas**, including use of Matplotlib under the hood, essential parameters, and best practices.

---

## 🔰 Basic Plot Syntax

Pandas has a built-in `.plot()` method available on DataFrames and Series, which wraps around **Matplotlib**.

```python
df.plot(kind='scatter', x='col_x', y='col_y')
```

---

## 🛠️ Common Parameters in `df.plot()`

| Parameter     | Description |
|---------------|-------------|
| `kind`        | Type of plot: `'line'`, `'bar'`, `'barh'`, `'hist'`, `'box'`, `'kde'`, `'area'`, `'scatter'`, `'pie'` |
| `x`           | Column name for x-axis |
| `y`           | Column name for y-axis |
| `color`       | Color name (e.g. `'red'`) |
| `marker`      | Marker style (`'*'`, `'o'`, `'s'`, etc.) |
| `s`           | Marker size (only for scatter) |
| `figsize`     | Tuple like `(10, 6)` for width and height |
| `title`       | Title of the plot |
| `xlabel` / `ylabel` | Custom labels for axes |
| `legend`      | Show legend (`True`/`False`) |
| `grid`        | Show grid (`True`/`False`) |
| `alpha`       | Transparency (0 = invisible, 1 = solid) |
| `linestyle` / `ls` | `'--'`, `':'`, `'-.'` for line styling |
| `linewidth` / `lw` | Line width |
| `cmap`        | Colormap for color gradients |
| `subplots`    | Plot each column in separate subplot (`True`) |

---

## 📈 Examples

### 1. Line Plot (Default)
```python
df.plot()
```

### 2. Scatter Plot
```python
df.plot(kind='scatter', x='avg', y='strike_rate', s=df['runs'], color='red', marker='*', figsize=(10, 8))
```

### 3. Multiple Line Plots as Subplots
```python
df[['col1', 'col2', 'col3']].plot(subplots=True, figsize=(10, 8))
```

### 4. Bar Plot
```python
df.plot(kind='bar', x='player', y='score')
```

### 5. Pie Chart (for Series only)
```python
df['category'].value_counts().plot(kind='pie', autopct='%1.1f%%')
```

---

## 🔄 Using `.values[i]` in Loops

```python
for i in range(sample.shape[0]):
    plt.text(sample['avg'].values[i], sample['strike_rate'].values[i], sample['batter'].values[i])
```

- `sample.shape[0]` → total number of rows
- `sample['col'].values[i]` → get value from row `i` in `'col'`
- Used for placing text annotations

---

## 🧩 Using Matplotlib for Customization

```python
import matplotlib.pyplot as plt

plt.figure(figsize=(10, 6))
plt.scatter(df['x'], df['y'], color='blue', s=100)
plt.title('Custom Plot')
plt.xlabel('X Axis')
plt.ylabel('Y Axis')
plt.grid(True)
plt.show()
```

---

## 📚 Flashcards (Quick Q&A Format)

### Q: What does `kind='scatter'` do?
A: Creates a scatter plot using x and y columns.

---

### Q: What does `subplot=True` do?
A: Creates separate subplots for each column.

---

### Q: Difference between `df.plot()` and `plt.plot()`?
A: `df.plot()` is a Pandas wrapper using Matplotlib; `plt.plot()` is directly from Matplotlib.

---

### Q: What is `sample.shape[0]` used for?
A: Gets number of rows in a DataFrame — used for iteration.

---

### Q: What does `df['col'].values[i]` do?
A: Accesses the value in row `i` of column `'col'` as a NumPy value.

---

### Q: Can you plot multiple columns with one call?
A: Yes, using `df[['col1', 'col2']].plot()` or `subplots=True`.

---

### Q: How to create a 2x2 subplot layout manually?
```python
fig, axs = plt.subplots(2, 2, figsize=(10, 8))
axs[0, 0].plot(df['A'])
axs[0, 1].plot(df['B'])
axs[1, 0].plot(df['C'])
```

---

## 🎨 Marker Styles for Scatter

| Marker | Meaning     |
|--------|-------------|
| `'o'`  | Circle      |
| `'*'`  | Star        |
| `'s'`  | Square      |
| `'D'`  | Diamond     |
| `'x'`  | Cross       |

---

## 🏁 Tips

- Use `random_state` in `.sample()` for reproducibility.
- Use `.iterrows()` or `.iloc` for row-wise plotting/labeling.
- Use `tight_layout()` in Matplotlib to avoid label overlap.

---

## 📁 Save Plot as Image

```python
plt.savefig('my_plot.png', dpi=300)
```

