# Deploying to Streamlit Community Cloud

This guide explains how to deploy your **Phase 6: Streamlit App** to the cloud so it's accessible via a public URL.

## Prerequisites
1.  **GitHub Account**: You need to embrace Git. Since you have a local repo, push it to GitHub.
2.  **Streamlit Account**: Sign up at [share.streamlit.io](https://share.streamlit.io/).
3.  **Groq API Key**: Have your key ready.

## Steps

### 1. Push Code to GitHub
Ensure you have committed all your changes, including the `phase_6_streamlit_app/` folder and the updated `requirements.txt` in the root.

```bash
git add .
git commit -m "Add Streamlit app for deployment"
git push origin main
```

### 2. Deploy on Streamlit Cloud
1.  Go to [share.streamlit.io](https://share.streamlit.io/).
2.  Click **"New app"**.
3.  Select your repository (`Streamlit-RAG-based-Mutual-Fund-FAQ-Chatbot`).
4.  **Main file path**: Enter `phase_6_streamlit_app/app.py`.
5.  Click **"Deploy!"**.

### 3. Configure Secrets
Your app will fail initially because the API key is missing.
1.  In your deployed app dashboard, go to **Settings** (three dots top right) -> **Secrets**.
2.  Paste your API key in TOML format:
    ```toml
    GROQ_API_KEY = "your_actual_api_key"
    ```
3.  Save. The app will reboot and should work!

## Troubleshooting
-   **"Module not found"**: Ensure `requirements.txt` in the root contains all packages (`streamlit`, `groq`, `sentence-transformers`, etc.).
-   **"Path not found"**: The app assumes it's run from the root or the `phase_6` folder. Streamlit Cloud runs from the root by default if `requirements.txt` is there.
