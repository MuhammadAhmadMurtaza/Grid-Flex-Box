<div align="center">

# 🎨 CSS Fundamentals: Flexbox & CSS Grid

**Three hands-on experiments with the two modern layout systems: one-dimensional Flexbox and two-dimensional Grid**

</div>

---

## 📖 About This Repository

This repository contains mini-projects I built while learning CSS. Each file isolates **one layout idea**, so the effect of every property is easy to see and experiment with.

No frameworks, no build tools. Just HTML and CSS.

---

## 📑 Table of Contents

1. [Project Structure](#-project-structure)
2. [Flexbox or Grid? A Quick Comparison](#-flexbox-or-grid-a-quick-comparison)
3. [Experiment 1: CSS Flexbox](#-experiment-1-css-flexbox)
4. [Experiment 2: CSS Grid Basics](#-experiment-2-css-grid-basics)
5. [Experiment 3: Grid Template Areas](#-experiment-3-grid-template-areas)
6. [How to Run](#-how-to-run)
7. [Key Takeaways](#-key-takeaways)
8. [Roadmap](#-roadmap)

---

## 📂 Project Structure

```
css-fundamentals/
│
├── 15-flexbox/
│   └── index.html
│
├── 16-css-grid/
│   ├── grid-1.html
│   └── grid-2.html
│
└── README.md
```

> 💡 Rename the folders to match your own layout. Each HTML file is fully standalone.

---

## ⚖️ Flexbox or Grid? A Quick Comparison

<table>
  <tr>
    <th></th>
    <th>Flexbox</th>
    <th>CSS Grid</th>
  </tr>
  <tr>
    <td><b>Dimensions</b></td>
    <td>One at a time (a row <b>or</b> a column)</td>
    <td>Two at once (rows <b>and</b> columns)</td>
  </tr>
  <tr>
    <td><b>Driven by</b></td>
    <td>Content: items decide how much space they need</td>
    <td>Layout: the container defines the tracks first</td>
  </tr>
  <tr>
    <td><b>Great for</b></td>
    <td>Navbars, button rows, centering, small components</td>
    <td>Page layouts, galleries, dashboards, card grids</td>
  </tr>
  <tr>
    <td><b>Turn it on with</b></td>
    <td><code>display: flex;</code></td>
    <td><code>display: grid;</code></td>
  </tr>
  <tr>
    <td><b><code>justify-items</code></b></td>
    <td>❌ Not available</td>
    <td>✅ Available</td>
  </tr>
</table>

> 💡 They are not rivals. Real pages usually use **Grid for the overall layout** and **Flexbox inside the components**.

---

## 📦 Experiment 1: CSS Flexbox

📁 `15-flexbox/index.html`

### 🎯 Goal
Understand how a flex container arranges its items along the **main axis** and **cross axis**, and how to control wrapping, spacing, alignment, and order.

### 🧭 The Two Axes

<table>
  <tr>
    <th>Axis</th>
    <th>Default direction</th>
    <th>Controlled by</th>
  </tr>
  <tr>
    <td><b>Main axis</b></td>
    <td>Left to right (for <code>row</code>)</td>
    <td><code>justify-content</code></td>
  </tr>
  <tr>
    <td><b>Cross axis</b></td>
    <td>Top to bottom (for <code>row</code>)</td>
    <td><code>align-items</code>, <code>align-self</code></td>
  </tr>
</table>

> ℹ️ With `flex-direction: column`, the two axes swap: the main axis becomes vertical.

### 🔑 Concepts Covered

<table>
  <tr>
    <th>Property</th>
    <th>Applies to</th>
    <th>What it does</th>
  </tr>
  <tr>
    <td><code>display: flex</code></td>
    <td>Container</td>
    <td>Turns the container into a flex container; its children become flex items.</td>
  </tr>
  <tr>
    <td><code>flex-wrap: wrap</code></td>
    <td>Container</td>
    <td>Lets items move onto new lines instead of squeezing into one.</td>
  </tr>
  <tr>
    <td><code>flex-flow</code></td>
    <td>Container</td>
    <td>Shorthand for <code>flex-direction</code> + <code>flex-wrap</code>. <code>row wrap</code> means a row that wraps.</td>
  </tr>
  <tr>
    <td><code>align-items: center</code></td>
    <td>Container</td>
    <td>Centers items on the cross axis.</td>
  </tr>
  <tr>
    <td><code>justify-content</code></td>
    <td>Container</td>
    <td>Distributes items along the main axis (commented out in this demo).</td>
  </tr>
  <tr>
    <td><code>gap: 40px 10px</code></td>
    <td>Container</td>
    <td>Row gap of <code>40px</code>, column gap of <code>10px</code>. Shorthand for <code>row-gap</code> and <code>column-gap</code>.</td>
  </tr>
  <tr>
    <td><code>order</code></td>
    <td>Item</td>
    <td>Changes visual order without touching the HTML. Default is <code>0</code>; higher numbers go later.</td>
  </tr>
  <tr>
    <td><code>align-self</code></td>
    <td>Item</td>
    <td>Overrides <code>align-items</code> for a single item.</td>
  </tr>
  <tr>
    <td><code>flex-grow</code> / <code>flex-shrink</code></td>
    <td>Item</td>
    <td>How an item grows to fill spare space, or shrinks when space runs out.</td>
  </tr>
</table>

### 🧪 Code Highlight

```css
.container {
  border: 2px solid red;
  display: flex;
  height: 80vh;
  align-items: center;
  flex-flow: row wrap;
  gap: 40px 10px;
}

.item {
  height: 92px;
  width: 92px;
  border: 2px solid black;
  background-color: blueviolet;
}

.order-1 {
  order: 1;
}

.item1 {
  flex-shrink: 2;
  align-self: flex-end;
}
```

### 🧠 What Happens Here

<table>
  <tr>
    <td>1️⃣</td>
    <td>Roughly 40 boxes sit inside one container. Because of <code>flex-wrap: wrap</code>, they flow onto as many rows as needed.</td>
  </tr>
  <tr>
    <td>2️⃣</td>
    <td>The two boxes with <code>.order-1</code> (labelled <b>4</b> and <b>66</b>) jump to the <b>end</b> of the container. Every other box has the default <code>order: 0</code>, so it comes first. Items with the same order keep their HTML order, so 4 comes before 66.</td>
  </tr>
  <tr>
    <td>3️⃣</td>
    <td>The gap is <code>40px</code> between rows and <code>10px</code> between columns.</td>
  </tr>
  <tr>
    <td>4️⃣</td>
    <td><code>flex-shrink</code> only matters when items cannot fit and wrapping is off. With <code>wrap</code>, items move to a new line instead of shrinking.</td>
  </tr>
</table>

### 🐛 Common Pitfalls

<table>
  <tr>
    <td>⚠️</td>
    <td><b>Unused CSS:</b> <code>.item1</code>, <code>.order-2</code>, and <code>.order-3</code> are defined but no element uses them. Add <code>class="item item1"</code> to a box to see <code>align-self: flex-end</code> in action.</td>
  </tr>
  <tr>
    <td>⚠️</td>
    <td><b>Redundant rules:</b> <code>flex-wrap: wrap</code> and <code>flex-flow: row wrap</code> both set wrapping. The later <code>flex-flow</code> line simply repeats it.</td>
  </tr>
  <tr>
    <td>⚠️</td>
    <td><b><code>justify-items</code> does nothing in Flexbox.</b> Use <code>justify-content</code> for the main axis or <code>margin: auto</code> on individual items.</td>
  </tr>
  <tr>
    <td>⚠️</td>
    <td><b>Accessibility:</b> <code>order</code> changes only the visual order. Keyboard and screen-reader order still follows the HTML.</td>
  </tr>
</table>

### 🔬 Try It Yourself

<details>
<summary><b>Click to expand the experiment steps</b></summary>

<br>

1. Uncomment `justify-content: center;` and watch each row center horizontally. Then try `space-between` and `space-around`.
2. Uncomment `flex-direction: column;` and watch the main axis turn vertical. Notice how `align-items` now centers horizontally.
3. Add `class="item1"` to one box to see `align-self: flex-end` pull it to the bottom of its row.
4. Uncomment `flex-grow: 1;` in `.item` so the boxes stretch to fill every row.
5. Give two different boxes `.order-2` and `.order-3` and watch them rearrange.
6. Replace `gap: 40px 10px` with `gap: 30px`, then try separate `row-gap` and `column-gap` values.
7. Remove `flex-wrap` and `flex-flow`, then add `flex-grow: 1` and watch all the boxes squeeze into one line.

</details>

### 📚 Flexbox Cheat Sheet

| Goal | Use |
|---|---|
| Center something both ways | `display: flex; justify-content: center; align-items: center;` |
| Push items to opposite ends | `justify-content: space-between;` |
| Stack items vertically | `flex-direction: column;` |
| Let items wrap onto new lines | `flex-wrap: wrap;` |
| Make one item fill the leftover space | `flex-grow: 1;` on that item |
| Move one item without changing HTML | `order: <number>;` |
| Align one item differently | `align-self: <value>;` |

---

## 🔲 Experiment 2: CSS Grid Basics

📁 `16-css-grid/grid-1.html`

### 🎯 Goal
Define a grid with **explicit columns**, control **spacing and alignment**, and learn how items are placed using **line numbers** and **named lines**.

### 🔑 Concepts Covered

<table>
  <tr>
    <th>Property</th>
    <th>Applies to</th>
    <th>What it does</th>
  </tr>
  <tr>
    <td><code>display: grid</code></td>
    <td>Container</td>
    <td>Creates a grid container; its children become grid items.</td>
  </tr>
  <tr>
    <td><code>grid-template-columns</code></td>
    <td>Container</td>
    <td>Defines the column tracks. <code>repeat(4, 80px)</code> means four columns, each 80px wide.</td>
  </tr>
  <tr>
    <td><code>grid-template-rows</code></td>
    <td>Container</td>
    <td>Defines row tracks (commented out in this demo).</td>
  </tr>
  <tr>
    <td><code>repeat()</code></td>
    <td>Value</td>
    <td>Avoids repeating the same size many times.</td>
  </tr>
  <tr>
    <td><code>minmax(100px, 1fr)</code></td>
    <td>Value</td>
    <td>A track that is never smaller than 100px but can grow to share leftover space.</td>
  </tr>
  <tr>
    <td><code>fr</code> unit</td>
    <td>Value</td>
    <td>A fraction of the available space. <code>1fr 2fr</code> splits space into a 1:2 ratio.</td>
  </tr>
  <tr>
    <td><code>gap</code>, <code>row-gap</code>, <code>column-gap</code></td>
    <td>Container</td>
    <td>Space between tracks. Specific properties override the shorthand when they come later.</td>
  </tr>
  <tr>
    <td><code>justify-items</code> / <code>align-items</code></td>
    <td>Container</td>
    <td>Aligns items horizontally / vertically inside their cells.</td>
  </tr>
  <tr>
    <td><code>grid-row</code> / <code>grid-column</code></td>
    <td>Item</td>
    <td>Places an item between grid lines, such as <code>grid-column: 1 / 2</code>.</td>
  </tr>
  <tr>
    <td>Named lines</td>
    <td>Container + item</td>
    <td><code>[pehla] 120px [doosra] 100px</code> names the lines so items can use <code>grid-column: pehla / 2</code>.</td>
  </tr>
</table>

### 🧪 Code Highlight

```css
.container {
  width: 80vw;
  height: 100vh;
  border: 2px solid black;
  display: grid;
  grid-template-columns: repeat(4, 80px);
  gap: 34px;           /* overridden by the two lines below */
  row-gap: 10px;
  column-gap: 44px;
  justify-items: center;
  align-items: center;
}

.item {
  border: 2px solid red;
  height: 55px;
  width: 55px;
}
```

### 🧠 What Happens Here

<table>
  <tr>
    <td>1️⃣</td>
    <td>Four columns of <code>80px</code> are created. There are five items, so the <b>fifth wraps onto a second row</b> automatically.</td>
  </tr>
  <tr>
    <td>2️⃣</td>
    <td>The final gaps are <code>10px</code> between rows and <code>44px</code> between columns, because <code>row-gap</code> and <code>column-gap</code> come after <code>gap: 34px</code> and override it.</td>
  </tr>
  <tr>
    <td>3️⃣</td>
    <td>Each item is only <code>55px</code> wide inside an <code>80px</code> cell. <code>justify-items: center</code> and <code>align-items: center</code> place it in the middle of its cell.</td>
  </tr>
  <tr>
    <td>4️⃣</td>
    <td>No rows were defined, so the grid creates <b>implicit rows</b> automatically as items need them.</td>
  </tr>
</table>

### 📍 Understanding Grid Lines

A grid with 4 columns has **5 vertical lines**, numbered 1 to 5. An item placed with `grid-column: 1 / 2` starts at line 1 and ends at line 2, so it covers exactly the first column.

<table>
  <tr>
    <th>Line 1</th>
    <th>Column 1</th>
    <th>Line 2</th>
    <th>Column 2</th>
    <th>Line 3</th>
    <th>Column 3</th>
    <th>Line 4</th>
    <th>Column 4</th>
    <th>Line 5</th>
  </tr>
  <tr align="center">
    <td>|</td>
    <td>80px</td>
    <td>|</td>
    <td>80px</td>
    <td>|</td>
    <td>80px</td>
    <td>|</td>
    <td>80px</td>
    <td>|</td>
  </tr>
</table>

**Placement options from the commented code:**

```css
.item1 {
  grid-row: 1 / 2;          /* shorthand */
  /* or the long form: */
  grid-row-start: 1;
  grid-row-end: 2;
  grid-column: 1 / 2;
}

.item4 {
  grid-row: 1 / 2;
  grid-column: pehla / 2;   /* uses a named line */
}
```

### 🐛 Common Pitfalls

<table>
  <tr>
    <td>⚠️</td>
    <td><b>Nested CSS comments:</b> CSS comments do not nest. The first <code>*/</code> closes the whole comment, even if there is another <code>/*</code> inside. Comment out big blocks line by line, or remove the inner comments first.</td>
  </tr>
  <tr>
    <td>⚠️</td>
    <td><b>Shorthand order:</b> <code>gap: 34px</code> followed by <code>row-gap</code> and <code>column-gap</code> means the later, more specific values win.</td>
  </tr>
  <tr>
    <td>⚠️</td>
    <td><b>Line names need brackets:</b> in the definition they are written as <code>[name]</code>, but used without brackets in <code>grid-column</code>.</td>
  </tr>
</table>

### 🔬 Try It Yourself

<details>
<summary><b>Click to expand the experiment steps</b></summary>

<br>

1. Change `repeat(4, 80px)` to `repeat(4, minmax(100px, 1fr))` and resize the window. The columns stretch but never get narrower than 100px.
2. Uncomment `grid-template-rows: 100px 100px 100px;` and see the row sizes become fixed.
3. Remove `justify-items` and `align-items` and watch the items snap to the top-left of their cells.
4. Give `.item1` the rule `grid-column: 2 / 4;` to make it span two columns.
5. Try `grid-column: span 2;` as a shorter way to span columns.
6. Change `justify-items: center` to `start`, `end`, and `stretch` and compare.
7. Add `align-self: end;` to one item to override the container's `align-items` for just that item.

</details>

### 📚 Grid Cheat Sheet

| Goal | Use |
|---|---|
| Three equal columns | `grid-template-columns: repeat(3, 1fr);` |
| Fixed sidebar and flexible main area | `grid-template-columns: 250px 1fr;` |
| Columns that adapt to screen width | `repeat(auto-fit, minmax(250px, 1fr))` |
| Make an item span two columns | `grid-column: span 2;` |
| Space between all cells | `gap: 20px;` |
| Center items in their cells | `justify-items: center; align-items: center;` |

---

## 🗺️ Experiment 3: Grid Template Areas

📁 `16-css-grid/grid-2.html`

### 🎯 Goal
Describe an entire page layout **visually with words**, then assign elements to named areas.

### 🧪 The Layout Map

```css
.container {
  display: grid;
  grid-template-areas:
    "nav nav nav"
    "side article article"
    "footer footer footer";
}
```

The map above creates this layout:

<table width="100%">
  <tr>
    <td colspan="3" align="center" bgcolor="#00ffff"><b>nav</b></td>
  </tr>
  <tr>
    <td align="center" bgcolor="#ffc0cb"><b>side</b></td>
    <td colspan="2" align="center" bgcolor="#add8e6"><b>article</b></td>
  </tr>
  <tr>
    <td colspan="3" align="center" bgcolor="#eeeeee"><b>footer</b></td>
  </tr>
</table>

### 🔑 Concepts Covered

<table>
  <tr>
    <th>Concept</th>
    <th>Example</th>
    <th>What it does</th>
  </tr>
  <tr>
    <td><code>grid-template-areas</code></td>
    <td><code>"nav nav nav"</code></td>
    <td>Each string is one row; each word is one column cell. Repeating a name makes that area span several cells.</td>
  </tr>
  <tr>
    <td><code>grid-area</code></td>
    <td><code>.item1 { grid-area: nav; }</code></td>
    <td>Assigns an element to a named area.</td>
  </tr>
  <tr>
    <td>Spanning</td>
    <td><code>"side article article"</code></td>
    <td><code>article</code> takes two columns; <code>side</code> takes one.</td>
  </tr>
</table>

### 🧪 Code Highlight

```css
.item1 { grid-area: nav;     background-color: aqua; }
.item2 { grid-area: side;    background-color: pink; }
.item3 { grid-area: article; background-color: blue; }
.item4 { grid-area: footer; }
.item5 { grid-area: nav; }
```

### 🧠 What Happens Here

<table>
  <tr>
    <td>1️⃣</td>
    <td>The HTML order is 1, 2, 3, 4, 5, but the <b>position on screen comes from the area names</b>, not from the source order.</td>
  </tr>
  <tr>
    <td>2️⃣</td>
    <td>Items 1 and 5 are both assigned to <code>nav</code>, so they <b>overlap in the same space</b>. Item 5 is drawn on top because it comes later in the HTML.</td>
  </tr>
  <tr>
    <td>3️⃣</td>
    <td>No column or row sizes are set, so tracks are sized <b>automatically</b>. Items have a fixed height of <code>55px</code> and no explicit width.</td>
  </tr>
</table>

### 📐 Rules for `grid-template-areas`

<table>
  <tr>
    <td>✅</td>
    <td>Every row string must have the <b>same number of cells</b>.</td>
  </tr>
  <tr>
    <td>✅</td>
    <td>A named area must form a <b>rectangle</b>. L-shapes are not allowed.</td>
  </tr>
  <tr>
    <td>✅</td>
    <td>Use a dot (<code>.</code>) for an empty cell, for example <code>"nav nav ."</code>.</td>
  </tr>
  <tr>
    <td>✅</td>
    <td>Area names are free-form words that you choose.</td>
  </tr>
</table>

### 🐛 Common Pitfalls

<table>
  <tr>
    <td>⚠️</td>
    <td><b>Overlapping areas:</b> two elements with the same <code>grid-area</code> share the same cells. That is occasionally useful for layering, but usually a mistake.</td>
  </tr>
  <tr>
    <td>⚠️</td>
    <td><b>Visual order vs source order:</b> as with Flexbox <code>order</code>, keep the HTML in a logical reading order for accessibility.</td>
  </tr>
</table>

### 🔬 Try It Yourself

<details>
<summary><b>Click to expand the experiment steps</b></summary>

<br>

1. Give `.item5` its own area, such as `grid-area: extra;`, and add a row `"extra extra extra"` to the map to stop the overlap.
2. Add `grid-template-columns: 200px 1fr 1fr;` to size the sidebar and article columns.
3. Add `grid-template-rows: 80px 1fr 60px;` and `min-height: 100vh` to the container for a full-page layout.
4. Replace one word with a dot (`"side . article"`) to leave a gap in the layout.
5. Swap the map to `"side nav nav"` and `"side article article"` to make a full-height sidebar.
6. Wrap the layout in a media query and redefine `grid-template-areas` as a single column for mobile:

```css
@media (max-width: 600px) {
  .container {
    grid-template-areas:
      "nav"
      "side"
      "article"
      "footer";
  }
}
```

</details>

---

## 🚀 How to Run

No installation needed.

```bash
# 1. Clone the repository
git clone https://github.com/<your-username>/<your-repo-name>.git

# 2. Move into the project
cd <your-repo-name>

# 3. Open any experiment in your browser
open 15-flexbox/index.html      # macOS
start 15-flexbox/index.html     # Windows
xdg-open 15-flexbox/index.html  # Linux
```

💡 **Tip:** Use the VS Code **Live Server** extension to see changes instantly. In browser DevTools, click the small **flex** or **grid** badge next to an element to visualize the layout.

---

## 🎓 Key Takeaways

<table>
  <tr>
    <td>✅</td>
    <td>Flexbox arranges items along <b>one axis</b>; Grid controls <b>rows and columns together</b>.</td>
  </tr>
  <tr>
    <td>✅</td>
    <td><code>justify-content</code> works on the main axis, <code>align-items</code> on the cross axis, and <code>justify-items</code> exists only in Grid.</td>
  </tr>
  <tr>
    <td>✅</td>
    <td><code>flex-wrap: wrap</code> and <code>gap</code> make flexible, evenly spaced collections of items.</td>
  </tr>
  <tr>
    <td>✅</td>
    <td><code>order</code> reorders items visually without changing the HTML, but it does not change keyboard or screen-reader order.</td>
  </tr>
  <tr>
    <td>✅</td>
    <td><code>repeat()</code>, <code>fr</code>, and <code>minmax()</code> make grid columns concise and flexible.</td>
  </tr>
  <tr>
    <td>✅</td>
    <td>Grid items can be placed with line numbers, named lines, or named areas.</td>
  </tr>
  <tr>
    <td>✅</td>
    <td><code>grid-template-areas</code> makes the CSS read like a map of the page.</td>
  </tr>
  <tr>
    <td>✅</td>
    <td>Use Grid for the page structure and Flexbox for the components inside it.</td>
  </tr>
</table>

---

## 🗺️ Roadmap

- [x] `display` property
- [x] Viewport units and box model
- [x] CSS specificity
- [x] `overflow`
- [x] Lists and `list-style`
- [x] `box-shadow` and `text-shadow`
- [x] Positioning (`relative`, `absolute`, `fixed`, `sticky`)
- [x] Card component
- [x] Media queries
- [x] CSS variables
- [x] Landing page project
- [x] Float and clear
- [x] Pseudo-elements and advanced selectors
- [x] Full page layout with sticky navbar
- [x] Flexbox fundamentals
- [x] CSS Grid fundamentals and template areas
- [ ] Responsive project combining Flexbox, Grid, and media queries
- [ ] Grid auto-placement (`grid-auto-flow`, `grid-auto-rows`)
- [ ] Keyframe animations
- [ ] Mobile-first workflow

---

<div align="center">

### ⭐ If you found this helpful, consider giving the repo a star!

Made with ❤️ while learning CSS

</div>
