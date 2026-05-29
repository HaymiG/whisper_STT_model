#  Speech-to-Text with OpenAI Whisper

> **Fluentian Internship Programme — Task Round 1**
> AI Engineer Task: Fine-Tuning STT/TTS Models

---

##  Overview

This project demonstrates a **Speech-to-Text (STT)** system using [OpenAI's Whisper](https://github.com/openai/whisper) model. The system converts audio input into text and evaluates performance across different model sizes (`tiny`, `base`, `small`).

---

##  Objective

- Explore speech recognition using open-source pre-trained models
- Compare performance of different Whisper model sizes
- Evaluate trade-offs between speed and accuracy
- Lay the groundwork for fine-tuning on under-resourced languages (e.g., Amharic)

---

##  Model Used

| Feature | Detail |
|---|---|
| **Model** | OpenAI Whisper |
| **Architecture** | Transformer Encoder-Decoder |
| **Languages** | 99+ (multilingual) |
| **License** | MIT (open-source) |
| **Sizes Tested** | `tiny`, `base`, `small` |

### Why Whisper?

-  **Multilingual** — Trained on 680,000 hours of multilingual data
-  **Pre-trained** — Strong zero-shot performance, no fine-tuning needed
-  **Easy to use** — Simple 3-line Python API
-  **Multiple sizes** — From tiny (39M) to large (1.5B) parameters

---

##  Project Structure

```
fluentian_internship/
├── STT_Project.ipynb      # Main notebook with experiments
├── audio.wav              # Sample audio for testing
├── STT_TTS_Report.pdf     # Detailed report (PDF)
├── README.md              # This file
└── myenv/                 # Python virtual environment
```

---

##  Installation

### 1. Create virtual environment (optional)

```bash
python3 -m venv myenv
source myenv/bin/activate
```

### 2. Install dependencies

```bash
pip install openai-whisper
pip install ffmpeg-python
```

### 3. Install FFmpeg

```bash
# Ubuntu/Debian
sudo apt install ffmpeg

# macOS
brew install ffmpeg
```

---

## How to Run

1. **Clone the repository:**

```bash
git clone https://github.com/HaymiG/whisper_STT_model
cd fluentian_internship
```

2. **Open the notebook:**

```bash
jupyter notebook STT_Project.ipynb
```

3. **Run all cells** — Make sure `audio.wav` is in the same directory.

---

##  Experiments

### Models Tested

| Model | Parameters | Speed | Accuracy |
|---|---|---|---|
| `tiny` | 39M |  Very Fast | Lower |
| `base` | 74M |  Fast | Good |
| `small` | 244M |  Moderate |  High |

### Audio Inputs Tested

-  Clear speech
-  Noisy audio
-  Fast speech

---

## Results

| Model | Result |
|---|---|
| **Tiny** | Fast but less accurate — misses some words |
| **Base** | Balanced performance — best speed/accuracy trade-off |
| **Small** | Most accurate but slower processing |

> **Key Finding:** Larger models produce better transcriptions but need more compute. Background noise significantly degrades all models.

---

##  Challenges

- Background noise reduces transcription accuracy
- Accent variations cause misrecognition (especially with tiny model)
- Medium/large models couldn't run on free-tier GPU
- Some audio formats need FFmpeg conversion to WAV

---

## Low-Compute Fine-Tuning Strategies

| Strategy | Description |
|---|---|
| **Smaller models** | Use `tiny` or `base` variants (39M–74M params) |
| **Freeze encoder** | Only fine-tune the decoder (~50% fewer params) |
| **LoRA/PEFT** | Low-rank adapters reduce trainable params by 90%+ |
| **Mixed precision** | FP16 training halves memory usage |
| **Gradient accumulation** | Simulates larger batches without extra memory |

---

##  Deployment Options

| Option | Stack | Cost |
|---|---|---|
| **REST API** | FastAPI + Whisper | $20–50/month (CPU) |
| **Web App** | React + FastAPI backend | $100–300/month (GPU) |
| **Mobile** | whisper.cpp + React Native | Free (on-device) |
| **Serverless** | AWS Lambda | Pay-per-use |

---

## Future Work

-  Fine-tune Whisper on Amharic using Mozilla Common Voice
-  Deploy as a real-time web API using FastAPI
-  Implement WER (Word Error Rate) evaluation with `jiwer`
- Compare Whisper vs Wav2Vec2 on the same dataset
- Explore TTS models (Coqui TTS, VITS) for text-to-speech

---

##  References

1. Radford, A., et al. (2022). *Robust Speech Recognition via Large-Scale Weak Supervision.* OpenAI.
2. [OpenAI Whisper GitHub](https://github.com/openai/whisper)
3. [Mozilla Common Voice](https://commonvoice.mozilla.org)
4. [Hugging Face Transformers](https://huggingface.co/docs/transformers)
5. Hu, E., et al. (2021). *LoRA: Low-Rank Adaptation of Large Language Models.*

---

## Author

**Haymanot Getachew**
Fluentian Internship Programme — April 2026
