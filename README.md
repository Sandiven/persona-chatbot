# Persona-Based AI Chatbot

> A prompt engineering project built for **Scaler Academy — Assignment 01**.  
> Chat with AI-powered personas of **Anshuman Singh**, **Abhimanyu Saxena**, and **Kshitij Mishra** — crafted with researched system prompts, few-shot examples, and chain-of-thought instructions.

🔗 **Live Demo:** https://persona-c.netlify.app/ 
🖥️ **Backend API:** https://persona-chatbot-986m.onrender.com

---

## 📸 Screenshots

> *(Add screenshots here before submission)*

### 🏠 Home / Persona Switcher
![Home](https://github.com/user-attachments/assets/99f26f37-18dc-4122-8bc6-3bcf447e6db3)

---

### 💬 Chat with Anshuman
![Anshuman](https://github.com/user-attachments/assets/b0d5b682-d962-48c9-84c1-808790978521)

---

### 💬 Chat with Abhimanyu
![Abhimanyu](https://github.com/user-attachments/assets/2c8eb4cb-43fe-4ba5-8331-e46cda457d9d)

---

### 💬 Chat with Kshitij
![Kshitij](https://github.com/user-attachments/assets/ce18fda1-333c-4dc9-b2fa-895ec9d4cbf3)

---

## Features

- 🎭 **3 distinct personas** — each with a fully researched system prompt
- 🔄 **Persona switcher** — switching resets the conversation automatically
- 💡 **Suggestion chips** — quick-start questions per persona
- ⌨️ **Typing indicator** — shown while waiting for API response
- ⚠️ **Graceful error handling** — rate limits and failures shown as friendly messages
- 📱 **Responsive UI** — works on mobile and desktop

---

## Project Structure

```
persona-chatbot/
├── backend/
│   ├── .env.example        # Environment variable template
│   ├── package.json
│   ├── personas.js         # All 3 system prompts
│   └── server.js           # Express API server
├── frontend/
│   ├── index.html
│   ├── script.js           # Chat logic + API calls
│   └── style.css
├── prompts.md              # Annotated system prompts
├── reflection.md           # 300–500 word reflection
└── README.md
```

---

## Tech Stack

| Layer | Technology |
|---|---|
| Frontend | HTML, CSS, Vanilla JavaScript |
| Backend | Node.js, Express |
| AI API | Groq (llama-3.1-8b-instant) |
| Deployment — Frontend | Netlify |
| Deployment — Backend | Render |

---

## Local Setup

### Prerequisites

- Node.js v18+
- A free [Groq API key](https://console.groq.com)

---

### 1. Clone the repo

```bash
git clone https://github.com/your-username/persona-chatbot.git
cd persona-chatbot
```

---

### 2. Backend setup

```bash
cd backend
npm install
```

Create a `.env` file from the example:

```bash
cp .env.example .env
```

Open `.env` and fill in your key:

```env
GROQ_API_KEY=your_groq_api_key_here
GROQ_MODEL=llama-3.1-8b-instant
PORT=5000
FRONTEND_ORIGIN=http://localhost:5500
```

Start the backend:

```bash
npm start
# or for development with auto-reload:
npm run dev
```

Backend runs at: `http://localhost:5000`

---

### 3. Frontend setup

Open `frontend/index.html` using **VS Code Live Server** (recommended, runs on port 5500).

Or serve it with any static server:

```bash
npx serve frontend
```

Make sure `API_BASE_URL` in `frontend/script.js` points to your local backend:

```js
const API_BASE_URL = "http://localhost:5000";
```

---

## API Reference

### `GET /health`

Health check — returns `{ ok: true }` if the server is running.

---

### `POST /chat`

Send a message to a persona.

**Request body:**
```json
{
  "message": "How do I stay consistent with DSA practice?",
  "persona": "kshitij"
}
```

**Persona values:** `anshuman` | `abhimanyu` | `kshitij`

**Response:**
```json
{
  "reply": "Consistency comes from systems, not motivation. Here's what I'd do..."
}
```

**Error response:**
```json
{
  "reply": "Rate limit reached. Please wait a minute and try again."
}
```

---

## Deployment

### Backend → Render

1. Go to [render.com](https://render.com) → **New Web Service**
2. Connect your GitHub repo
3. Set **Root Directory** to `backend`
4. Set **Build Command** to `npm install`
5. Set **Start Command** to `npm start`
6. Add environment variables in the Render dashboard:

| Key | Value |
|---|---|
| `GROQ_API_KEY` | Your Groq API key |
| `GROQ_MODEL` | `llama-3.1-8b-instant` |
| `FRONTEND_ORIGIN` | Your Netlify URL |
| `PORT` | `5000` |

7. Deploy — Render gives you a URL like `https://your-app.onrender.com`

---

### Frontend → Netlify

1. Go to [netlify.com](https://netlify.com) → **Add new site → Import from Git**
2. Connect your GitHub repo
3. Set **Publish directory** to `frontend`
4. Deploy — Netlify gives you a URL like `https://your-app.netlify.app`

---

### After deployment

Update `API_BASE_URL` in `frontend/script.js`:

```js
const API_BASE_URL = "https://your-app.onrender.com";
```

Push the change — Netlify auto-redeploys.

---

## Environment Variables

| Variable | Required | Description |
|---|---|---|
| `GROQ_API_KEY` | ✅ Yes | API key from console.groq.com |
| `GROQ_MODEL` | ✅ Yes | Model name, e.g. `llama-3.1-8b-instant` |
| `PORT` | No | Server port (default: 5000) |
| `FRONTEND_ORIGIN` | No | Allowed CORS origin |
| `OPENAI_API_KEY` | No | Optional OpenAI key |
| `OPENAI_MODEL` | No | Optional OpenAI model |
| `GEMINI_API_KEY` | No | Optional Gemini key |
| `GEMINI_MODEL` | No | Optional Gemini model |

> ⚠️ Never commit your `.env` file. Only `.env.example` should be in the repo.

---

## Submission Checklist

- [ ] GitHub repo is public and link is shared
- [ ] README contains setup instructions and deployed link
- [ ] `prompts.md` contains all 3 system prompts with inline annotations
- [ ] `reflection.md` is 300–500 words
- [ ] `.env.example` is present; no real API key committed anywhere
- [ ] App is deployed and live
- [ ] All 3 personas work in the live app
- [ ] Persona switching resets the conversation
- [ ] API errors are handled gracefully
- [ ] UI is mobile-responsive

---

## License

MIT
