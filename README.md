# Edge VLM Industrial Inspector

**Zero-shot defect detection using Vision-Language Models.**

No labeling. No training. Point a camera and ask.

![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)
![License](https://img.shields.io/badge/License-MIT-green.svg)

## The Problem

Traditional inspection requires training separate ML models for each defect type. When products change, you retrain.

## The Solution

VLMs understand images + language. Instead of training, just ask:

```bash
python src/inspector.py circuit.jpg --prompt "Is there a solder bridge?"
```

**Change the prompt, not the model.**

## Quick Start

```bash
# Clone
git clone https://github.com/YOUR_USERNAME/edge-vlm-inspection.git
cd edge-vlm-inspection

# Install
pip install -r requirements.txt

# Run
python demo.py your_circuit.jpg
```

## Usage

```bash
# Single image
python src/inspector.py image.jpg

# Custom prompt
python src/inspector.py image.jpg -p "Are there scratches or burns?"

# Batch inspection
python src/inspector.py ./images/ -o results.json

# Different inspection types
python src/inspector.py image.jpg -t binary    # YES/NO answer
python src/inspector.py image.jpg -t solder    # Solder joints
python src/inspector.py image.jpg -t component # Component placement
```

## Models

| Model | Size | RAM Needed | Quality |
|-------|------|------------|---------|
| `git-base` | 350MB | 4GB | Basic |
| `blip-base` | 500MB | 6GB | Good ⭐ |
| `blip-large` | 1GB | 8GB | Better |
| `moondream` | 2GB | 12GB | Best |

```bash
# Use specific model
python src/inspector.py image.jpg --model blip-large
```

## Python API

```python
from src.inspector import EdgeVLMInspector

inspector = EdgeVLMInspector(model_name="blip-base")

result = inspector.inspect(
    image="pcb.jpg",
    prompt="Check for solder bridges or missing components"
)

print(f"Defect: {result['has_defect']}")
print(f"Analysis: {result['response']}")
```

## Output Format

```json
{
    "image_source": "pcb.jpg",
    "has_defect": true,
    "response": "There appears to be a solder bridge between pins...",
    "inference_time_ms": 1250,
    "model": "blip-base"
}
```

## Project Structure

```
edge-vlm-inspection/
├── src/
│   ├── inspector.py      # Core VLM engine
│   └── __init__.py
├── samples/              # Test images
├── demo.py               # Quick test
├── requirements.txt
└── README.md
```

## Why This Matters

$15B+ industrial vision market still runs on 2018 workflows:
1. Collect images → 2. Label manually → 3. Train model → 4. Deploy → 5. Repeat

VLMs collapse steps 1-4 into a single prompt.

## Author

**Pushkar Prashantrao Shinde**  
NYU Tandon School of Engineering  
[LinkedIn](https://www.linkedin.com/in/pushkar-shinde/)

## License

MIT
