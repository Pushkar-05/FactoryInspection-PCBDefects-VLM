# Edge VLM Industrial Inspector

**Zero-shot defect detection with bounding boxes.**

No labeling. No training. Type what to find → Get visual detection.

![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)
![License](https://img.shields.io/badge/License-MIT-green.svg)

## 🎬 Demo Video

[![Edge VLM Inspector Demo](https://img.youtube.com/vi/FL0ycnFfG1s/0.jpg)](https://youtu.be/FL0ycnFfG1s)

**[▶️ Watch Demo on YouTube](https://youtu.be/FL0ycnFfG1s)**

## Features

- 🎯 **Bounding box detection** — Visual localization of defects
- 🎥 **Live webcam** — Real-time inspection
- ✏️ **Open vocabulary** — Detect ANY defect by typing
- 🖥️ **Web GUI** — Easy-to-use interface
- 📁 **Batch processing** — Inspect multiple images

## Quick Start

```bash
# Install
pip install torch transformers pillow opencv-python gradio

# Run GUI
python inspector_gui.py

# Opens at http://localhost:7860
```

## Screenshot

```
┌─────────────────────────────────────────────────────────┐
│  🔍 Edge VLM Industrial Inspector                       │
├─────────────────────────────────────────────────────────┤
│  [📷 Image] [🎥 Live Video] [📁 Batch] [⚙️ Settings]    │
├─────────────────────────────────────────────────────────┤
│                                                         │
│   ┌──────────────┐    Defects to Detect:               │
│   │   [IMAGE]    │    [solder bridge, scratch, crack]  │
│   │  ┌────────┐  │                                     │
│   │  │ defect │  │    Confidence: [====|====] 0.15     │
│   │  └────────┘  │                                     │
│   └──────────────┘    [🔍 Inspect]                     │
│                                                         │
│   Results:                                              │
│   ⚠ 2 DEFECTS DETECTED                                 │
│   1. solder bridge (87%)                               │
│   2. scratch (72%)                                     │
│                                                         │
└─────────────────────────────────────────────────────────┘
```

## Usage

### GUI Mode (Recommended)
```bash
python inspector_gui.py

# With public link (share with others)
python inspector_gui.py --share
```

### Command Line
```bash
# Single image
python src/inspector.py image.jpg

# Custom query
python src/inspector.py image.jpg -p "Is there a crack?"

# Batch
python src/inspector.py ./images/ -o results.json
```

## How It Works

Uses **OWL-ViT** (Open-World Localization Vision Transformer):
- Type any defect description
- Model finds and localizes matching regions
- Draws bounding boxes with confidence scores

**No training required** — Works out of the box for any defect type.

## Preset Queries

| Category | Defects |
|----------|---------|
| PCB | solder bridge, missing component, burn mark, cold joint |
| Metal | scratch, dent, rust, crack, corrosion |
| Plastic | crack, discoloration, warping, flash |
| Assembly | misalignment, missing screw, wrong orientation |

## Requirements

- Python 3.8+
- 8GB+ RAM
- GPU recommended (works on CPU too)

## Author

**Pushkar Prashantrao Shinde**  
NYU Tandon School of Engineering  
[LinkedIn](https://www.linkedin.com/in/pushkar-shinde/)

## License

MIT
