# 🌱 EchoMind: A Lightweight, Offline Conversational AI with Contextual Memory

![Python](https://img.shields.io/badge/Python-3.8%2B-blue?logo=python&logoColor=white)
![Hugging Face](https://img.shields.io/badge/Hugging%20Face-FFD700?logo=huggingface&logoColor=black)
![Streamlit](https://img.shields.io/badge/Streamlit-FF4B4B?logo=streamlit&logoColor=white)
![License](https://img.shields.io/badge/License-MIT-green)

**EchoMind** is a sleek, fully offline conversational AI built with Hugging Face transformers that remembers your last 4–6 interactions — all running locally on your machine. No cloud, no API keys, no tracking. Just you and an intelligent, memory-aware chatbot that respects your privacy.

Built for developers, privacy advocates, and AI enthusiasts who want to experience LLMs without leaving their device.

---

## 💡 Why EchoMind?

- 🔒 **100% Offline**: No internet needed after first download.
- 🧠 **Smart Memory**: Sliding window context keeps conversations coherent without memory bloat.
- 🖥️ **Dual Interfaces**: Use it via terminal (CLI) or sleek web UI (Streamlit).
- ⚡ **Lightweight**: Runs on CPU with just 2GB RAM using Qwen1.5-0.5B-Chat.
- 🛠️ **Modular Design**: Easy to extend, swap models, or integrate into other apps.
- 🌐 **Deployable**: Ready for Hugging Face Spaces or Vercel (web UI).

---

## 🚀 Quick Start

### Prerequisites
- Python 3.8+
- 2GB+ RAM
- 2GB+ free disk space (for model cache)

### Installation
```bash
# Clone the repo
git clone https://github.com/itripathiharsh/EcoRAG-Agent.git
cd EcoRAG-Agent

# Create & activate virtual environment (recommended)
python -m venv venv
source venv/bin/activate     # On Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt
```

### Run the CLI Interface
```bash
python interface.py
```

### Run the Web Interface (Streamlit)
```bash
streamlit run app.py
```

> 💡 Tip: Use `streamlit run app.py --server.port=8501` to change the default port.

---

## 🧩 Features

| Feature | Description |
|--------|-------------|
| **Local Inference** | Runs entirely on your machine — no external API calls. |
| **Contextual Memory** | Remembers last 4–6 exchanges using a sliding window. |
| **Dual UIs** | CLI for quick access, Streamlit for a polished web experience. |
| **Model Flexibility** | Easily swap models (e.g., TinyLlama, Phi-2, Mistral). |
| **Command Controls** | `/exit`, `/clear`, `/history` for seamless interaction. |
| **GPU Support** | Auto-detects CUDA for faster inference (if available). |

---

## 🛠️ How It Works

### Model Loading
Uses Hugging Face `pipeline` with optimized settings:
- Model: `Qwen/Qwen1.5-0.5B-Chat` (default, lightweight & capable)
- Precision: FP16/FP32 auto-selected
- Tokenizer: Efficient, fast, and memory-aware

### Memory Management
- Stores only the last `N` user-bot exchanges (configurable).
- Prevents prompt bloat and context overflow.
- Uses simple JSON-like structure for readability and debugging.

### Text Generation
Optimized generation parameters:
```python
temperature=0.7,
top_p=0.9,
repetition_penalty=1.1,
max_new_tokens=128
```

---

## ⚙️ Configuration

### Change the Model
Edit `interface.py`:
```python
chatbot = ChatbotInterface(
    model_name="TinyLlama/TinyLlama-1.1B-Chat-v1.0",  # ← Change here
    memory_window=6  # Keep last 6 turns
)
```

> 💡 Try `microsoft/Phi-2` for faster responses or `TheBloke/Mistral-7B-Instruct-v0.1-GGUF` (via `llama.cpp`) for advanced users.

### Adjust Memory Window
Change `memory_window` in `interface.py`:
```python
memory_window=4  # Default
memory_window=8  # For longer conversations
```

> ⚠️ Larger windows increase memory usage — balance based on your device.

---

## 📊 Performance (Qwen1.5-0.5B-Chat on CPU)

| Metric | Value |
|-------|-------|
| Model Size | ~1.24 GB |
| RAM Usage | ~2.1 GB |
| Avg Response Time | 2–5 seconds |
| Context Window | 4–8 exchanges |
| GPU Support | Yes (CUDA auto-detected) |

---

## 🖥️ Web Interface (Streamlit)

Launch with:
```bash
streamlit run app.py
```

![Streamlit UI Preview](https://via.placeholder.com/800x500?text=EchoMind+Web+UI+Preview)  
*(Replace with actual screenshot when deployed)*

Features:
- Clean, responsive UI
- Chat history persistence (in-session)
- One-click clear
- Mobile-friendly

> ✅ **Deploy to Hugging Face Spaces**: Just upload `app.py`, `requirements.txt`, and your model. No secrets needed!

---

## 🧭 Future Enhancements

- [ ] GPU acceleration optimization (vLLM or TensorRT)
- [ ] Model switching at runtime
- [ ] Export chat logs (JSON/Markdown)
- [ ] Custom prompt templates
- [ ] Plugin system for tools (e.g., calculator, search)
- [ ] Dockerize for one-click deployment

---

## 📂 Project Structure

```
EchoMind/
├── model_loader.py       # Loads & configures Hugging Face model
├── chat_memory.py        # Sliding window context manager
├── interface.py          # CLI chat loop with commands
├── app.py                # Streamlit web interface
├── requirements.txt      # All dependencies
├── README.md             # You're here!
└── .gitignore            # Avoids caching models or venv
```

---

## 🤝 Contributing

EchoMind is open for improvements!  
Feel free to:
- Suggest better models
- Add new features (e.g., voice input)
- Improve UI/UX
- Document usage on Raspberry Pi or Windows

Open an issue or submit a PR!

---

## 📜 License

MIT License — Use it anywhere. Modify it. Share it.

> **Note**: The underlying Hugging Face model (Qwen1.5-0.5B-Chat) is licensed under Apache 2.0. Please respect its terms.

---

## 💬 Connect With Me

Hi, I’m **Harsh Vardhan Tripathi** — AI Developer & Open Source Enthusiast.  
I build tools that put power back in the user’s hands.

- 📧 [imharshofficial322@gmail.com](mailto:imharshofficial322@gmail.com)
- 💼 Open to full-time AI/ML roles
- 🌐 [GitHub Profile](https://github.com/itripathiharsh)

> *Privacy. Performance. Simplicity.*

