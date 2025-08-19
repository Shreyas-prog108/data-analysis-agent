
# 🚄 **TDS Project 2 Data Analyst – Railway Deployment Guide**

Easily deploy your **AI-powered Data Analyst Agent** to **Railway** in minutes.
Follow these steps and your app will be live with a public URL.

---

## ✅ **What’s Already Set Up**

The repo includes all necessary Railway config files:

| File            | Purpose                                       |
| --------------- | --------------------------------------------- |
| `.env`          | Stores environment variables (e.g., API keys) |
| `Dockerfile`    | Defines container build                       |
| `railway.json`  | Railway deployment configuration              |
| `Procfile`      | Tells Railway how to start the app            |
| `runtime.txt`   | Python version specification                  |
| `.dockerignore` | Files to ignore during Docker build           |

---

## 🔑 **1. Configure Environment Variables**

Create a `.env` file in your project root and add your details:

```env
# Google Gemini API Keys (Add 1–10 keys for load balancing if you don't have multiple key just paste your one key in all variable)
gemini_api_1=your_api_key_here
gemini_api_2=your_api_key_here
gemini_api_3=your_api_key_here
gemini_api_4=your_api_key_here
gemini_api_5=your_api_key_here
gemini_api_6=your_api_key_here
gemini_api_7=your_api_key_here
gemini_api_8=your_api_key_here
gemini_api_9=your_api_key_here
gemini_api_10=your_api_key_here
LLM_TIMEOUT_SECONDS=240

```
> ⚠ **if you don't have multiple gemini key just copy one key in all. but my recommendation is used atleast two different key for fallback mechanism to work properly
---
> ⚠ **Never commit your `.env` file** to GitHub. Add it to `.gitignore`.

---

## 📤 **2. Push Code to GitHub**

```bash
cd /path/to/project
git init
git add .
git commit -m "Initial commit with Railway deployment config"
git remote add origin https://github.com/your-username/your-repo.git
git push -u origin main
```

---

## 🚀 **3. Deploy to Railway**

### **Option A – Dashboard**

1. Visit [railway.app](https://railway.app)
2. Sign in with GitHub
3. **New Project → Deploy from GitHub**
4. Select your repo
5. Railway will auto-deploy

### **Option B – CLI**

```bash
npm install -g @railway/cli
railway login
railway init
railway link
railway up
```

---

## 🌍 **4. Add Environment Variables in Railway**

1. Go to your Railway project
2. Click **Variables**
3. Add your Gemini keys & settings exactly as in `.env`

---

## 🧪 **5. Test Locally**

```bash
source venv/bin/activate   # Windows: venv\Scripts\activate
uvicorn app:app --host 0.0.0.0 --port 8000
```

Visit: **[http://localhost:8000](http://localhost:8000)**

---

## 🐳 **6. (Optional) Test with Docker**

```bash
docker build -t tds-data-analyst .
docker run -p 8000:8000 --env-file .env tds-data-analyst
```

---

## ⚙ **Environment Variable Reference**

| Variable                       | Description            | Default          | Required       |
| ------------------------------ | ---------------------- | ---------------- | -------------- |
| `gemini_api_1`......`gemini_api_10` | Google Gemini API keys | —                | ✅ (at least 1 but make copy of it in all variable) |
| `LLM_TIMEOUT_SECONDS`          | LLM Max Time for task  | 240              | ❌              |
| `PORT`                         | App port               | 8000             | ❌              |

---

## 🛠 **Troubleshooting**

**Common Issues**

* `Module not found` → Check `requirements.txt`
* Port conflict → Use Railway’s `PORT` variable in architecture => project=> setting => networking => edit =>select default port (uvicorn)
* API key errors → Ensure keys are correct in Railway Variables
* Build fails → See Railway build logs

**View Logs**

```bash
railway logs
```

---

## 📚 **Helpful Links**

* 📖 [Railway Docs](https://docs.railway.app)
* 🤖 [Google AI Docs](https://ai.google.dev)

---

