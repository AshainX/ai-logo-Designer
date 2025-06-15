# AI Logo Generator

This project is a web-based AI logo generator built with **FastAPI** for the backend and **Streamlit** for the frontend. It uses the Stable Diffusion model to generate logos from textual prompts.

---

## Project Structure

- **api.py** — Backend API serving the Stable Diffusion image generation.
- **app.py** — Frontend Streamlit app for user interaction.

---

## How It Works

### 1. `api.py` — Backend API

- Uses **FastAPI** to create an HTTP API.
- Loads the Stable Diffusion model (`stabilityai/stable-diffusion-2-1`) using the `diffusers` library.
- Accepts POST requests at `/generate_logo` with the following JSON payload:
  - `prompt`: Text description of the desired logo.
  - `negative_prompt`: Text specifying what to avoid.
  - `width` & `height`: Dimensions of the generated image.
  - `seed`: Optional random seed for deterministic output.
- Generates the image using Stable Diffusion.
- Converts the image to a base64 string and returns it in the response.
- Handles errors gracefully and returns appropriate HTTP status codes.

### 2. `app.py` — Frontend UI

- Uses **Streamlit** to create an interactive web interface.
- Lets users input the prompt, negative prompt, image size, and seed.
- Sends a POST request with user inputs to the backend API.
- Receives the base64-encoded image, decodes it, and displays a preview.
- Provides a button to download the full-size generated logo as a PNG.

---

## Workflow Summary

1. User enters inputs in the Streamlit app.
2. App sends inputs to FastAPI backend.
3. Backend generates the logo image.
4. Backend returns the image as base64.
5. Frontend shows a preview and allows downloading the full image.

---

## Requirements

Make sure to install dependencies with:

```bash
pip install fastapi uvicorn torch diffusers transformers pillow accelerate streamlit requests
```