# Streamlit Deployment Troubleshooting Guide

## Common Error: "Thinking fail. Sorry, I encountered an error while generating the response."

This error has been **FIXED** with enhanced error handling. The app will now show you the actual error details.

## Most Common Causes & Solutions

### 1. ❌ API Key Not Configured (Most Common)

**Symptoms:**
- Error mentioning "GROQ_API_KEY"
- "API key not found" messages

**Solution for Streamlit Cloud:**
1. Go to your Streamlit Cloud dashboard
2. Click on your app
3. Go to **Settings** → **Secrets**
4. Add the following (replace with your actual key):
   ```toml
   GROQ_API_KEY = "gsk_your_actual_groq_api_key_here"
   ```
5. Save and redeploy

**Solution for Local Development:**
1. Navigate to `phase_6_streamlit_app/.streamlit/`
2. Copy `secrets.toml.example` to `secrets.toml`
3. Edit `secrets.toml` and replace the placeholder with your actual API key
4. Run the app: `streamlit run phase_6_streamlit_app/app.py`

### 2. ❌ Missing Vector Database Files

**Symptoms:**
- Error: "Vector store not found"
- Error: "Embeddings not found"

**Solution:**
The vector database files (`phase2_vector_db/`) must be included in your repository:
- `embeddings.npy`
- `embeddings.db`
- `vector_store.json`

These files are currently tracked in git. If missing, regenerate them by running:
```bash
python phase2_vector_db/vector_store.py
```

### 3. ❌ Missing Dependencies

**Symptoms:**
- Import errors
- Module not found errors

**Solution:**
Ensure all dependencies are in `phase_6_streamlit_app/requirements.txt`:
```
streamlit
sentence-transformers
groq
python-dotenv
numpy
```

For Streamlit Cloud, these are auto-installed. For local:
```bash
pip install -r phase_6_streamlit_app/requirements.txt
```

### 4. ❌ Path Issues

**Symptoms:**
- "No such file or directory" errors
- Import errors for phase modules

**Solution:**
The app automatically adjusts paths. Ensure you're running from the project root:
```bash
# Correct
streamlit run phase_6_streamlit_app/app.py

# Also correct (from phase_6_streamlit_app folder)
cd phase_6_streamlit_app
streamlit run app.py
```

## Debugging Steps

### Step 1: Check Error Details
The app now shows detailed error messages with expandable debug traces. Click "🔍 Debug Details" to see the full error.

### Step 2: Verify API Key
Test your API key locally first:
```python
from groq import Groq
client = Groq(api_key="your_key_here")
# If this works, your key is valid
```

### Step 3: Check Streamlit Logs
In Streamlit Cloud:
1. Go to your app dashboard
2. Click "Manage app"
3. View logs for detailed error messages

### Step 4: Test Locally
Always test locally before deploying:
```bash
cd phase_6_streamlit_app
streamlit run app.py
```

## Verification Checklist

Before deploying to Streamlit Cloud:

- [ ] API key is valid and working
- [ ] All vector database files exist in `phase2_vector_db/`
- [ ] App runs successfully locally
- [ ] All dependencies are in `requirements.txt`
- [ ] Secrets are configured in Streamlit Cloud dashboard

## Getting a Groq API Key

If you don't have a Groq API key:
1. Visit https://console.groq.com/
2. Sign up for a free account
3. Navigate to API Keys
4. Create a new API key
5. Copy and save it securely

## Still Having Issues?

The enhanced error handling will now show you:
- Exact error type and message
- Full stack trace (in expandable section)
- Helpful troubleshooting steps

Check the error message carefully - it will tell you exactly what's wrong!
