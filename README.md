# ollama-colab
run an ollama server on google colab for dev purposes

## Overview

This project provides a Jupyter Notebook (`serve_ollama_model.ipynb`) that allows you to:

1.  Select an Ollama model (or pull a new one).
2.  Serve the selected model using a local FastAPI server.
3.  Expose the local API server to the internet using localtunnel, making it publicly accessible.

## Open in Google Colab

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/phantomic12/ollama-colab/blob/main/serve_ollama_model.ipynb)

*Click the badge above to open and run the notebook directly in Google Colab.*
*(Note: For the notebook to function fully in Colab, Ollama itself would need to be running and accessible to the Colab environment. This might involve running Ollama on a separate, publicly accessible server and configuring the notebook to connect to it, or exploring methods to run Ollama within Colab's allocated resources, which can be complex.)*

## How to Use Locally

1.  **Prerequisites:**
    *   Ensure you have [Ollama](https://ollama.com/download) installed and the `ollama serve` command is running.
    *   Python 3.7+ and pip installed.
    *   Node.js and npm installed (for `localtunnel`).

2.  **Setup & Run:**
    *   Clone the repository (if you haven't already):
        ```bash
        git clone https://github.com/phantomic12/ollama-colab.git
        cd ollama-colab
        ```
    *   Open the `serve_ollama_model.ipynb` notebook in a Jupyter environment (like Jupyter Lab, Jupyter Notebook, or VS Code).
    *   Run the cells in the notebook sequentially.
        *   It will install necessary Python and npm packages.
        *   It will guide you to select or pull an Ollama model.
        *   It will start a FastAPI server locally.
        *   It will then attempt to create a public URL using `localtunnel`.

3.  **Accessing the API:**
    *   Once `localtunnel` is running, it will print a public URL (e.g., `https://<random-subdomain>.loca.lt`).
    *   You can send POST requests to the `/api/generate` endpoint of this public URL to interact with your Ollama model.
    *   Example using `curl`:
        ```bash
        curl -X POST YOUR_PUBLIC_URL/api/generate \
             -H "Content-Type: application/json" \
             -d '{"prompt": "Why is the sky blue?"}'
        ```
        (Replace `YOUR_PUBLIC_URL` with the actual URL provided by `localtunnel`).

## Important Notes

*   **Localtunnel Stability:** Public `localtunnel` instances can sometimes be unstable or have rate limits.
*   **Ollama Server:** Ensure the `ollama serve` command is running before starting the notebook.
*   **Resource Usage:** Running LLMs can be resource-intensive.
*   **Security:** Be mindful when exposing local servers to the internet.
