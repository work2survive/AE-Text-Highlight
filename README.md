# AE Text Highlight (v3.0.0)

[![Live Browser Simulator](https://img.shields.io/badge/Live%20Demo-AE%20ScriptUI%20Simulator-2c8cff?style=for-the-badge&logo=javascript)](https://work2survive.github.io/AE_JS_builder/?jsx=AE_Text_Highlight.jsx&autobuild=true)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=for-the-badge)](LICENSE)
[![Adobe After Effects](https://img.shields.io/badge/Adobe%20After%20Effects-CS6%20--%20CC%202026%2B-9999FF?style=for-the-badge&logo=adobeaftereffects)](https://www.adobe.com/products/aftereffects.html)
[![Built with Antigravity](https://img.shields.io/badge/Built%20With-Antigravity-4285F4?style=for-the-badge&logo=google)](https://deepmind.google/)

**Live Demo**: [https://work2survive.github.io/AE_JS_builder/?jsx=AE_Text_Highlight.jsx&autobuild=true](https://work2survive.github.io/AE_JS_builder/?jsx=AE_Text_Highlight.jsx&autobuild=true)

**AE Text Highlight v3.0.0** is a streamlined, lightweight procedural typography highlighter for Adobe After Effects ScriptUI and the [AE JS & ScriptUI Simulator](https://work2survive.github.io/AE_JS_builder/).

Completely rewritten from the ground up for maximum simplicity, predictability, and 100% deterministic consistency.

---

## 🎯 Key Design Innovations (v3.0.0 Ground-Up Rewrite)

1. **100% Idempotent & Deterministic**:
   - Re-running the script on a text layer cleans up and replaces previous highlights in-place.
   - Zero duplicated, stacked, or orphaned layers.
   - Deterministic target matching: never picks random words or unpredictable samples.

2. **Zero Premature Layer Creation**:
   - Zero layers or helper items are created on panel launch, window focus, or selection polling.
   - Layers are created **strictly and only** when the user clicks **"✨ Build Highlights"**.

3. **Untouched Original Text Layer**:
   - The original text layer's anchor point, position, scale, and rotation are **never modified**.
   - The procedural highlight Shape Layer is parented directly to the text layer and compensates internally for the parent's anchor point `[curAx, curAy]`.

4. **Multi-Word & Comma Support**:
   - Targets can be full multi-word phrases or sentences containing internal commas (e.g. `"peace of mind, body, and soul"`).
   - Enter targets one per line in the clean ScriptUI text area.

5. **Sub-Pixel Delimiter-Anchored Advance**:
   - Uses delimiter-anchored advance (`"|"` suffix) to measure true word bounds including trailing whitespace, preventing After Effects' native whitespace trimming from throwing off coordinates.

6. **Ultra-Clean Codebase**:
   - Reduced from ~3,400 lines of convoluted legacy code down to **~560 lines** of clear, modular JavaScript.

---

## 🏛️ How It Works

```mermaid
flowchart TD
    SELECT["User Selects Text Layer"] --> CLICK["Clicks 'Build Highlights'"]
    CLICK --> CLEAN["1. Clean Up Previous Highlights (Idempotency)"]
    CLEAN --> MEASURE["2. Measure Accurate Prefix Advance & Word Widths"]
    MEASURE --> SHAPE["3. Create Procedural Shape Layer Behind Text"]
    SHAPE --> PARENT["4. Parent Shape Layer to Text Layer (Pos [0,0], Anchor [0,0])"]
    PARENT --> CONTROLS["5. Attach Expression Master Sliders (Color, Padding, Roundness, Opacity)"]
    CONTROLS --> DONE["Highlight Rigs Live with Sub-Pixel Precision!"]
```

---

## 🛠️ Usage

1. Open After Effects and open your composition containing a Text Layer.
2. Run `AE_Text_Highlight.jsx` via **File > Scripts > Run Script File...** or install in `Scripts/ScriptUI Panels`.
3. Select the text layer you want to highlight.
4. Enter target words or phrases (one per line).
5. Adjust Padding, Roundness, and Highlight Color.
6. Click **✨ Build Highlights**.
7. To revert or remove highlights, click **🗑️ Remove Highlights**.

---

## 📜 License

MIT License. Co-authored & architected with Google DeepMind Antigravity for `work2survive`.
