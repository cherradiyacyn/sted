# 🧱 sted – The Scratch Tilemap Editor

**sted** is a simple Excel-based tilemap editor that helps you design grid-based layouts for Scratch games. Visually build your levels and export clean coordinate data for dynamic tile-based rendering in Scratch.

---

## 🚀 Features

- Visual tilemap editor built in Excel
- Exports precise tile coordinates to `tilemap.txt`
- Grid-based layout, ideal for platformers or top-down games
- Seamless integration with Scratch's clone system

---

## 🛠 How to Use

### 1️⃣ Design Your Tilemap in Excel

Open `sted.xlsm` and follow these steps:

- The **top row** contains X-coordinate values.
- The **first column** contains Y-coordinate values.
- Mark cells with `#` to place tiles at those positions.

#### Example Layout:

|      | -228 | -204 | -180 |
| :--: | :--: | :--: | :--: |
| -96  |      |  #   |      |
| -120 |  #   |      |  #   |

✅ This layout generates tiles at:

- `(-204, -96)`
- `(-228, -120)`
- `(-180, -120)`

---

### 2️⃣ Export Tile Coordinates

Run the macro `Export`:

1. Press `ALT + F8` to open the **Macro dialog**.
2. Select `Export` and click **Run**.
3. A file named `tilemap.txt` will be created in the same folder as your Excel file.

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
2. Load the contents of `tilemap.txt` into a List (e.g., `TilePositions`).
3. Each pair of values (`x`, then `y`) represents one tile’s position.
4. In your startup script (e.g., on green flag), loop through the list and `create clone of [tile]` at each coordinate.

---

## 🧑‍💻 Editing the Macro (Optional)

To view or modify the macro:

1. Press `ALT + F11` to open the **VBA Editor**.
2. Navigate to `VBAProject` → `Modules` → `Module1`.
3. You’ll find `Export`, the macro that handles coordinate extraction.

---

**Build levels visually. Load them dynamically.**
