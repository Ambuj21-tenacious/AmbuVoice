# AmbuVoice — Real‑time Voice Chatbot (Server‑to‑Server with Gemini Live)

AmbuVoice is a beginner‑friendly template that lets you talk to a chatbot in real time.
It uses a **server‑to‑server** architecture: the browser streams microphone audio to your Node/Express server, which connects
to **Gemini Live** over **WebSockets** and streams back audio replies.

> ⚠️ You'll need a Google **Gemini API key**. Create one in Google AI Studio, then put it in `server/.env`.

## Features
- Low‑latency, bidirectional audio via WebSockets
- Works with **native‑audio** model `gemini-2.5-flash-preview-native-audio-dialog`
- Barge‑in/interrupt support (start talking to interrupt the model)
- Simple, dependency‑light frontend (plain HTML/JS)
- Beginner‑friendly, fully commented code

## Project structure
```
AmbuVoice/
├── frontend/
│   ├── index.html
│   ├── app.js
│   └── assets/styles.css
└── server/
    ├── src/server.js
    ├── src/geminiClient.js
    ├── package.json
    ├── .env.example
    └── Dockerfile
```

## Quick start
1) Install server deps and set your API key
```bash
cd server
cp .env.example .env  # then edit .env and paste your key
npm install
npm run dev           # starts server at http://localhost:5173
```
2) Open the frontend
- Double‑click `frontend/index.html` (or use a static file server).  
- Click **Connect** → allow microphone. Speak and you'll hear AmbuVoice reply.

## Environment
- Node 18+ recommended
- Tested on Chrome

## Notes
- The sample streams **16 kHz, 16‑bit PCM, mono** up to the server.
- The server forwards audio frames to Gemini Live and plays back 24 kHz audio from the model to the browser.

## Security
- For production, prefer **ephemeral tokens** rather than long‑lived API keys.
- Always keep `.env` out of version control.
