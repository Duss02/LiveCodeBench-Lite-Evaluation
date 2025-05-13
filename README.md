# 🧠 LLM CodeGen Evaluation Pass@1 (LiveCodeBench Lite)

Evaluate Pass@1 of your Hugging Face model on [LiveCodeBench Lite](https://huggingface.co/datasets/livecodebench/code_generation_lite) using quantization.

## 🔧 Setup

```bash
pip install transformers datasets accelerate bitsandbytes
```
Access HF
```python
from huggingface_hub import login
login("your_hf_token")
```
Change to your model
```python
model_name = "Qwen/Qwen2.5-Coder-3B-Instruct"
```
Set samples numbers
```python
# --- Configuration ---
MAX_SAMPLES_TO_EVALUATE = 100
```
## ▶️ Run

The script:

* Loads preset Qwen model with 4-bit quantization
* Streams 100 test samples
* Generates Python code
* Executes code and tests against public cases
* Logs pass/fail and output to `result_eval_100.json`

## 📄 Prompt Format

````
<|im_start|>system
You are a helpful coding assistant. Generate only Python code wrapped in ```python ... ``` unless otherwise specified.<|im_end|>
<|im_start|>user
[Problem Statement]<|im_end|>
<|im_start|>assistant
````

## 📊 Output

* ✅ Pass\@1 score
* 📈 Per-difficulty stats
* 📂 `result_eval_100.json`

Run in Colab or locally ( 15GB VRAM GPU recommended).
