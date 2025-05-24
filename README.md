# 🧱 sted – A Scratch Tilemap Editor

**sted** is a simple Excel-based tilemap editor that helps you design grid-based layouts for Scratch games. Visually build your levels and export clean coordinate data for dynamic tile-based rendering in Scratch.

---

## 🚀 Features

- Visual tilemap editor built in Excel
- Exports precise tile coordinates to `tilemap.txt`
- Grid-based layout with 24×24-step tiles, ideal for platformers
- Seamless integration with Scratch's coordinate system

---

## 🛠 How to Use

### 1️⃣ Design Your Tilemap in Excel

Open `sted.xlsm` and follow these steps:

- The **top row** contains X-coordinate values.
- The **first column** contains Y-coordinate values.
- Mark cells with `#` to place tiles at those positions.

#### Example Layout:

|          | -228 | -204 | -180 |
| :------: | :--: | :--: | :--: |
| **-96**  |      |  #   |      |
| **-120** |  #   |      |  #   |

✅ This layout generates tiles at:

- `(-204, -96)`
- `(-228, -120)`
- `(-180, -120)`

> ⚠️ **Note:** If macros are disabled in Excel, the export feature won’t work. Be sure to **enable macros** if prompted when opening `sted.xlsm`.

---

### 2️⃣ Export Tile Coordinates

Run the `Export` macro:

1. Press `ALT + F8` to open the **Macro dialog**.
2. Select `Export` and click **Run**.
3. A file named `tilemap.txt` will be created in the same folder as `sted.xlsm`.

📄 The file contains one coordinate per line, alternating X and Y:

```
-204
-96
-228
-120
-180
-120
```

---

### 3️⃣ Import into Scratch

1. Open your Scratch project.
2. Load the contents of `tilemap.txt` into a list variable in Scratch (e.g., `TilePositions`).
3. Each pair of values (`x`, then `y`) represents one tile’s position.

You can use one of two methods to draw the tiles:

#### 🧱 Option 1: Using Clones _(Recommended for interactive tiles)_

- In your startup script (e.g., when the green flag is clicked), loop through the list and `create clone of [tile]` at each coordinate.
- Use the `when I start as a clone` block to position and show the clone.
- This approach allows each tile to act independently (e.g., collisions, animation).

#### 🖊️ Option 2: Using Pen Stamp _(For static backgrounds)_

- Loop through the list and move the tile sprite to each `(x, y)` coordinate.
- Use the `stamp` block to draw it on the stage.
- Ideal for large, unchanging maps where performance is a concern.

> 🧩 **Note:** Each coordinate represents the **center** of a tile placed on a 24-step grid. Ensure your tile sprite is centered and sized to fit a 24×24-step area for proper alignment.

---

## 📏 Understanding the Grid and "Steps"

In Scratch, the stage is **480 steps wide** and **360 steps tall**, centered at `(0, 0)`. Positions are measured in **steps**—the same units used in blocks like `move (10) steps`. These are logical units, _not_ pixels.

- The grid consists of **20 columns** and **15 rows**.
- Each tile takes up a fixed 24×24-step area on the grid.
- X coordinates run from **-228** to **228** (20 columns).
- Y coordinates run from **168** (top) down to **-168** (bottom) (15 rows).

---

## 🧑‍💻 Editing the Macro (Optional)

To view or modify the macro:

1. Press `ALT + F11` to open the **VBA Editor**.
2. Navigate to `VBAProject` → `Modules` → `Module1`.
3. You’ll find `Export`, the macro that handles coordinate extraction.

---

**Build levels visually. Load them dynamically.**
