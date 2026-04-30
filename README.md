# Persona Console Chatbot

A prompt-engineering project that compares how three mentor personas answer the same kind of user questions. The app keeps one interaction pattern (switch persona -> reset session -> chat) while giving each persona a distinct voice.

## Personas

- Anshuman Singh (systems and leverage framing)
- Abhimanyu Saxena (execution and shipping focus)
- Kshitij Mishra (fundamentals and consistency coaching)

## What Improved

- Completely redesigned frontend UI (dashboard + sidebar + clean chat workspace)
- Persona switching still works the same and resets conversation context
- Persona-specific quick prompts update instantly on switch
- Active persona state is always visible in the chat header
- Improved send-state feedback (`Sending...`) and typing indicator clarity
- Updated prompt artifacts and reflection for better alignment with behavior

## Project Structure

```txt
personas_chatbot/
├── backend/
│   ├── .env.example
│   ├── package.json
│   ├── personas.js
│   └── server.js
├── frontend/
│   ├── index.html
│   ├── script.js
│   └── style.css
├── .env.example
├── prompts.md
├── reflection.md
└── README.md
```

## Local Setup

### 1. Backend

```bash
cd backend
npm install
npm start
```

Create `backend/.env` from `backend/.env.example`:

```env
GROQ_API_KEY=your_groq_api_key_here
GROQ_MODEL=llama-3.1-8b-instant
# OPENAI_API_KEY=your_openai_api_key_here
# OPENAI_MODEL=gpt-4o-mini
# GEMINI_API_KEY=your_gemini_api_key_here
# GEMINI_MODEL=gemini-2.0-flash
PORT=5000
FRONTEND_ORIGIN=http://localhost:5500
```

### 2. Frontend

Open `frontend/index.html` with Live Server (port `5500` recommended) or any static server.

## API Endpoints

- `GET /health` - basic health check
- `POST /chat` - sends user message with selected persona

Example request:

```json
{
  "message": "How should I plan my next 2 weeks?",
  "persona": "abhimanyu"
}
```

## Notes

- If you deploy backend, update `API_BASE_URL` in `frontend/script.js`
- Do not commit real API keys
- Use `prompts.md` and `reflection.md` as submission artifacts
