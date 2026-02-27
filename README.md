# 🤖 AI Logging Agent with Gemini

An AI-powered log analysis agent built with **Python** and **Google Gemini**.

This project walks you through setting up your environment, installing dependencies, securing your API key, and running your first AI-driven log analysis.

---

## 📋 Requirements

Make sure you have the following installed:

- Python 3.9+
- pip (comes with Python)
- A code editor (VS Code recommended)
- Git (optional but recommended)
- A Google AI Studio account (for your Gemini API key)

---

# 🐍 Installing Python

## Check Your Version

```bash
python3 --version
```

If the version is **3.9 or higher**, you're ready.

If not, install Python:

### macOS (Homebrew)

```bash
brew install python3
```

### Ubuntu / Debian

```bash
sudo apt update
sudo apt install python3 python3-pip
```

### Fedora / CentOS

```bash
sudo dnf install python3 python3-pip
```

---

# 📁 Project Setup

Create the project structure:

```bash
mkdir ai-logging-agent
cd ai-logging-agent

mkdir src
mkdir logs
```

Project structure:

```
ai-logging-agent/
├── src/
└── logs/
```

---

# 🧪 Virtual Environment Setup

Create and activate a virtual environment:

```bash
python3 -m venv venv
source venv/bin/activate
```

You should now see `(venv)` in your terminal.

---

# 📦 Install Dependencies

Create a `requirements.txt` file:

```bash
touch requirements.txt
```

Add the following:

```
google-generativeai>=0.8.5
python-dotenv>=1.1.1
requests>=2.32.5
```

Install them:

```bash
pip install -r requirements.txt
```

---

# 🔑 Get Your Gemini API Key

1. Go to: https://aistudio.google.com/app/api-keys
2. Click **Create API Key**
3. Copy the generated key

⚠️ Keep this key secret.

---

# 🔐 Store Your API Key Securely

Create a `.env` file:

```bash
touch .env
```

Add your API key:

```
GEMINI_API_KEY=your-actual-api-key-here
```

---

# 🚫 Protect Your Secrets

Create a `.gitignore` file:

```bash
cat > .gitignore << EOF
.env
venv/
__pycache__/
*.pyc
EOF
```

---

# 🧠 Create Your First AI Script

Create `src/test_setup.py`:

```python
import os
from dotenv import load_dotenv
import google.generativeai as genai

# Load environment variables
load_dotenv()

# Get API key
api_key = os.getenv("GEMINI_API_KEY")
if not api_key:
    print("Error: GEMINI_API_KEY not found in .env file")
    exit(1)

# Configure Gemini
genai.configure(api_key=api_key)

# Create model
model = genai.GenerativeModel("gemini-2.5-flash-lite")

# Sample logs
sample_log = """
2024-10-21 14:23:45 ERROR Database connection
2024-10-21 14:23:46 WARN Retry attempt 1 of 3
2024-10-21 14:23:48 ERROR Database connection
2024-10-21 14:23:49 WARN Retry attempt 2 of 3
2024-10-21 14:23:51 ERROR Database connection
2024-10-21 14:23:52 ERROR Maximum retries reached
"""

prompt = f"""You are a DevOps engineer analyzing application logs.
Analyze this log and explain what's happening:

{sample_log}

Provide a brief analysis and suggest what might be wrong.
"""

print("Analyzing logs with AI...")
print("-" * 50)

response = model.generate_content(prompt)
print(response.text)

print("-" * 50)
print("✓ Setup successful! Your environment is ready.")
```

---

# ▶️ Run the Script

Make sure your virtual environment is active, then run:

```bash
python src/test_setup.py
```

If everything is configured correctly, you should see an AI-generated analysis of the logs.

---

# 🎉 You're Ready!

You now have:

- A clean Python project structure
- Secure API key management
- Gemini API integration
- A working AI-powered log analysis script

---

## 🚀 Next Steps

- Analyze real log files
- Monitor the `logs/` directory automatically
- Add Slack or email alerts
- Deploy as a background service
- Expand into a full DevOps AI assistant

---

Happy Building 🚀

## **Author** ✍️

Created by [Ali Bahrami](https://github.com/alibahrami2). If you find this repository helpful, feel free to fork it or contribute!