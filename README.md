# J.A.R.V.I.S - Just A Rather Very Intelligent System

JARVIS is an intelligent AI assistant built with FastAPI, LangChain, Groq AI, and a modern glassmorphism web UI. It supports multiple chat modes, streaming responses, voice input, text-to-speech, image generation, and personal memory using local learning data.

It is designed as a smart personal AI workspace that can answer questions, search the web in real time, remember user preferences, generate images, analyze uploaded photos, and speak responses naturally.

## Features

- General AI chat mode powered by Groq
- Realtime mode with Tavily-powered web search
- Jarvis mode that automatically decides whether to use general or realtime mode
- Streaming responses in real time
- Text-to-speech using Microsoft Edge TTS
- Voice input using browser speech recognition
- Personal learning memory from `.txt` files in `database/learning_data/`
- Conversation/session persistence across restarts
- Image generation using Pollinations.ai
- Camera / vision analysis for uploaded or live images
- Multi-key Groq API rotation and fallback support
- Dark glassmorphism frontend with responsive UI

## Tech Stack

### Backend
- Python
- FastAPI
- LangChain
- Groq AI
- Tavily
- FAISS
- Hugging Face Transformers
- Pydantic
- Uvicorn

### Frontend
- HTML
- CSS
- JavaScript
- Web Speech API
- WebGL / GLSL orb animation

## Demo / Run

Quick start:

```bash
pip install -r requirements.txt
python run.py
```

Open in your browser:

```text
http://localhost:8000
```

## Prerequisites

- Python 3.10+
- pip
- Groq API key
- Optional: Tavily API key for realtime mode

## Environment Variables

Create a `.env` file in the project root with the following variables:

```env
GROQ_API_KEY=your_groq_api_key_here
TAVILY_API_KEY=your_tavily_api_key_here

GROQ_MODEL=llama-3.3-70b-versatile
ASSISTANT_NAME=Jarvis
JARVIS_USER_TITLE=Sir
TTS_VOICE=en-GB-RyanNeural
TTS_RATE=+22%
```

Optional multiple Groq keys for fallback:

```env
GROQ_API_KEY=first_key
GROQ_API_KEY_2=second_key
GROQ_API_KEY_3=third_key
```

## Project Structure

```text
Jarvis-Intelligent-AI-Assistant/
├── app/
│   ├── main.py
│   ├── models.py
│   ├── services/
│   │   ├── chat_service.py
│   │   ├── groq_service.py
│   │   ├── realtime_service.py
│   │   ├── brain_service.py
│   │   ├── vector_store.py
│   │   ├── task_executor.py
│   │   ├── task_manager.py
│   │   └── vision_service.py
│   └── utils/
│       ├── time_info.py
│       ├── retry.py
│       └── key_rotation.py
├── frontend/
│   ├── index.html
│   ├── style.css
│   ├── script.js
│   └── orb.js
├── database/
│   ├── learning_data/
│   ├── chats_data/
│   └── vector_store/
├── config.py
├── run.py
├── requirements.txt
├── .env
├── README.md
└── LICENSE
```

## How It Works

### Chat Modes

- General Mode: Uses your conversation history and local memory to answer without the web
- Realtime Mode: Searches the web before responding with up-to-date data
- Jarvis Mode: Automatically chooses between General and Realtime based on the query

### Learning / Memory

Add text files in `database/learning_data/` to teach the assistant about your preferences, information, or personal context. It loads and indexes them using a local vector store for semantic retrieval.

### Session Persistence

The assistant saves chat sessions to disk so conversation history survives server restarts.

### Text-to-Speech

Responses can be spoken aloud using Edge TTS and streamed in real time while the model is generating output.

## API Endpoints

- `POST /chat` — standard chat response
- `POST /chat/stream` — streamed chat response
- `POST /chat/realtime` — realtime web-search mode
- `POST /chat/realtime/stream` — streaming realtime mode
- `POST /chat/jarvis/stream` — auto-routing Jarvis mode
- `GET /chat/history/{session_id}` — get session history
- `GET /health` — check backend health
- `POST /tts` — generate TTS audio

## Usage

1. Install dependencies
2. Add your `.env` values
3. Run the app:

```bash
python run.py
```

4. Open:

```text
http://localhost:8000
```

5. Select a mode and start chatting

## Troubleshooting

### App will not start
- Make sure Python dependencies are installed
- Check your `.env` file for valid keys
- Ensure port 8000 is free

### Realtime mode is not working
- Verify `TAVILY_API_KEY` is set correctly
- Check server logs for Tavily and Groq errors

### TTS not playing
- Make sure the speaker toggle is enabled
- On iPhone/iPad, use a user interaction before speaking

### Vector memory issues
- Check `database/learning_data/` for valid `.txt` files
- Restart the app if the index needs rebuilding

## Security Notes

- Keep API keys in `.env` and never commit them publicly
- The app is designed for local/personal use and may require extra hardening for public deployment

## Developer

Developed by Gyana Ranjan Mishra.

- Instagram: https://www.instagram.com/__gyana__04__/
- Telegram: https://t.me/gyanranjanmishra
- YouTube: https://www.youtube.com/@GyanRanjanMishra-sb7io

## License

This project is licensed under the MIT License unless otherwise stated.

## End

JARVIS is built to feel like a personal AI assistant that is fast, smart, real-time aware, and responsive across chat, voice, and multimodal experiences.
