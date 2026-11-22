# StudioAI — Generative AI Image Studio

**StudioAI** is an interactive web-based Generative AI application built with **Streamlit** and **Hugging Face Diffusers** (Stable Diffusion). It provides an intuitive interface for generating new images from text prompts as well as performing advanced image editing tasks such as **Inpainting** and **Outpainting**.

---

## Key Features

### 1. Text-to-Image Generation (`GENERATE` Tab)
- **Prompt & Negative Prompt Control:** Describe what you want to create and specify elements to exclude from the output.
- **Inference Parameter Tuning:** Customize **Quality Steps**, **Guidance Scale (CFG)**, and **Seed Control** for reproducible results.
- **Multiple Schedulers:** Switch dynamically between `Euler A`, `DPM++`, and `DDIM` schedulers.
- **Batch Inference:** Generate single or multiple images in a single run and select any result directly for further editing.

### 2. AI Image Editing (`EDIT` Tab)
- **Inpainting:** Selectively modify or replace specific regions of an image using binary mask processing while preserving the rest of the scene.
- **Outpainting (Zoom Out):** Seamlessly expand the borders of an existing image with AI-generated context and background blending.

### 3. Memory Management
- Built-in GPU cache clearing (`flush_memory`) using PyTorch CUDA memory management and Python garbage collection to prevent Out-of-Memory (OOM) issues during inference.

---

## Project Structure

```text
studioai-generative-app/
├── notebooks/
│   ├── 1_pipeline_logic.ipynb       # Colab notebook for pipeline experimentation
│   └── 2_streamlit_runner.ipynb     # Colab notebook to build & run the Streamlit app via ngrok
├── app.py                           # Main Streamlit user interface
├── logic.py                         # Core Stable Diffusion pipelines & image processing logic
├── requirements.txt                 # Python dependencies
└── README.md                        # Project documentation
```

---

## Tech Stack
- **Frontend / Web UI:** Streamlit
- **Deep Learning & Diffusion Models:** PyTorch, Hugging Face `diffusers`, `transformers`, `accelerate`
- **Models Used:**
  - `runwayml/stable-diffusion-v1-5` (Text-to-Image)
  - `runwayml/stable-diffusion-inpainting` (Inpainting & Outpainting)
- **Image Processing:** Pillow (PIL)
- **Deployment / Tunneling:** Google Colab + `pyngrok`

---

## How to Run (Google Colab)

Because Stable Diffusion requires a GPU for fast inference, this project is designed to run on **Google Colab (T4 GPU)**:

1. Open `notebooks/2_streamlit_runner.ipynb` in **Google Colab**.
2. Set the runtime hardware accelerator to **T4 GPU** (`Runtime > Change runtime type > T4 GPU`).
3. Replace `"YOUR_NGROK_AUTHTOKEN"` with your personal token from the [ngrok Dashboard](https://ngrok.com).
4. Run all cells sequentially to generate `logic.py` and `app.py`, start the Streamlit server, and open the generated public `.ngrok-free.app` URL.
