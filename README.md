
# Audio AI Processor – Language Agnostic Speech to English Pipeline

A sophisticated **Streamlit** web application designed for processing **Language agnostic audio** and converting it into accurate English text with optional summarization.

Ideal for transcribing and understanding non english podcasts, lectures, YouTube videos, interviews, voice notes, or live recordings.

<grok-card data-id="3f8fe4" data-type="image_card"  data-arg-size="LARGE" ></grok-card>



<grok-card data-id="363b9f" data-type="image_card"  data-arg-size="LARGE" ></grok-card>


## Key Features

- **Multiple Audio Sources**:
  - Download and process audio from **YouTube** videos
  - **Upload** local audio files (WAV, MP3, OGG, FLAC, M4A)
  - **Live microphone recording** directly in the browser

- **Advanced Speech Processing**:
  - Voice Activity Detection (VAD) with Silero to extract clean speech segments from long audio
  - High-accuracy **Language ASR** (Automatic Speech Recognition)

- **Translation & Enhancement**:
  - Translate Persian transcripts to **English** using Facebook's M2M100 (418M parameters) multilingual model
  - Refine translated English for grammar, clarity, and natural phrasing using Qwen2.5-1.5B-Instruct LLM

- **Summarization**:
  - Generate concise abstractive summaries (5–7 bullet points) of full YouTube/video transcripts

- **User-Friendly Interface**:
  - Clean, modern light-themed UI with cards, expanders, audio players, and sidebar controls
  - Real-time progress indicators and error handling

- **Security**:
  - Password-protected access with optional **time-limited keys** (configurable start date & validity period)

<grok-card data-id="27ebb6" data-type="image_card"  data-arg-size="LARGE" ></grok-card>


## High-Level Workflow

1. **Input Audio** → YouTube URL / Upload / Record
2. **Preprocess** → Convert to 16kHz mono WAV
3. **VAD Segmentation** (for long audio) → Split into speech-only chunks
4. **Transcribe** → Persian text (NVIDIA NeMo FastConformer ~115M params)
5. **Translate** → Raw English (M2M100 418M)
6. **Correct & Improve** → Natural English (Qwen2.5-1.5B-Instruct)
7. **Summarize** (optional for full audio) → Key points in English

Results are displayed with original audio playback, Non Eng transcription, and polished English output.

## Core Models

| Component                  | Model                                                                 | Parameters | Details |
|----------------------------|-----------------------------------------------------------------------|------------|---------|
| **Language Agnostic ASR**            | `nvidia/stt_fa_fastconformer_hybrid_large` (NeMo)                     | ~115M     | Hybrid Transducer-CTC FastConformer, fine-tuned on Persian data |
| **Translation (fa → en)**  | `facebook/m2m100_418M`                                               | 418M      | Multilingual many-to-many translation supporting 100 languages |
| **English Correction & Summarization** | `Qwen/Qwen2.5-1.5B-Instruct` (Alibaba Cloud)                  | 1.5B      | Instruction-tuned LLM with strong reasoning and text improvement |

All models are cached locally after first download (~8–10 GB total).

## Project Structure
