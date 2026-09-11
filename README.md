# JARVIS X

**Production-Grade AI Voice Assistant — Professional Platform**

A sophisticated, enterprise-ready AI voice assistant with a premium futuristic interface, reliable voice interaction, modular architecture, strong error handling, and secure API design.

---

## Vision

JARVIS X is built as a professional, polished AI assistant platform — not a demo, toy project, or simple chatbot. The experience communicates intelligence, reliability, sophistication, speed, calmness, and futuristic technology.

**Core Principle:** Voice and text are one conversation.

---

## Key Features

- **Unified Voice & Text Pipeline**: Speak or type — both enter the same conversation engine
- **Complete Voice Workflow**: Audio capture → STT → AI → TTS → automatic playback
- **Conversation Mode**: Automatic return to listening after each response
- **Interruption / Barge-in**: Stop JARVIS mid-speech and speak new commands
- **Wake Word Architecture**: Foundation for "Jarvis" wake-word detection
- **Professional HUD**: Premium futuristic interface with state-driven animations
- **Modular Providers**: Swappable STT, TTS, and AI backends
- **Voice Settings**: Persistent preferences for voices, speed, pitch, language
- **Secure Design**: Server-side secrets, input validation, safe tool execution
- **Progressive Web App**: Installable application experience
- **Error Resilience**: Graceful degradation when services fail
- **Windows Companion Ready**: Architected for future native desktop integration

---

## Core Architecture

```
┌─────────────────────────────────────────────────────────┐
│                    UI Layer                              │
│  (HUD, Chat, Voice Controls, Settings, Responsive)       │
└─────────────────────────────────────────────────────────┘
                          ↓
┌─────────────────────────────────────────────────────────┐
│              Conversation Engine                         │
│  (Message routing, state management, response sync)      │
└─────────────────────────────────────────────────────────┘
                          ↓
┌─────────────────────────────────────────────────────────┐
│              Provider Managers                           │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐   │
│  │ STTManager   │  │ TTSManager   │  │ AIProvider   │   │
│  └──────────────┘  └──────────────┘  └──────────────┘   │
└─────────────────────────────────────────────────────────┘
                          ↓
┌─────────────────────────────────────────────────────────┐
│          Service Layer (Backend)                         │
│  ┌──────────────────────────────────────────────────┐   │
│  │ Secure environment variables, API keys, secrets  │   │
│  │ Tool validation, execution, rate limiting        │   │
│  └──────────────────────────────────────────────────┘   │
└─────────────────────────────────────────────────────────┘
```

---

## State Machine

JARVIS operates in a well-defined state machine:

```
IDLE
  ↓ (user speaks or types)
LISTENING
  ↓ (speech ends or input sent)
THINKING
  ↓ (if tools needed)
EXECUTING
  ↓
SPEAKING
  ↓
IDLE (or LISTENING if Conversation Mode enabled)
```

**Interruption Flow:**
```
SPEAKING + user speaks → LISTENING → THINKING → ...
```

---

## Project Structure

```
jarvis-x/
├── frontend/
│   ├── public/
│   │   ├── index.html
│   │   ├── manifest.json (PWA)
│   │   └── icons/
│   ├── src/
│   │   ├── index.tsx
│   │   ├── components/
│   │   │   ├── HUD/
│   │   │   │   ├── Orb.tsx
│   │   │   │   ├── StatusIndicator.tsx
│   │   │   │   └── VoiceControls.tsx
│   │   │   ├── Chat/
│   │   │   │   ├── ChatWindow.tsx
│   │   │   │   ├── Message.tsx
│   │   │   │   └── InputArea.tsx
│   │   │   ├── Settings/
│   │   │   │   └── VoiceSettings.tsx
│   │   │   └── Common/
│   │   ├── providers/
│   │   │   ├── STTProvider.ts
│   │   │   ├── STTManager.ts
│   │   │   ├── TTSProvider.ts
│   │   │   ├── TTSManager.ts
│   │   │   ├── AIProvider.ts
│   │   │   └── WakeWordProvider.ts
│   │   ├── services/
│   │   │   ├── ConversationEngine.ts
│   │   │   ├── StateManager.ts
│   │   │   ├── StorageService.ts
│   │   │   └── LoggerService.ts
│   │   ├── hooks/
│   │   ├── types/
│   │   └── styles/
│   └── package.json
├── backend/
│   ├── src/
│   │   ├── server.ts
│   │   ├── routes/
│   │   ├── services/
│   │   ├── tools/
│   │   ├── middleware/
│   │   ├── config/
│   │   └── utils/
│   ├── .env.example
│   └── package.json
├── docs/
│   ├── README.md
│   ├── ARCHITECTURE.md
│   ├── VOICE.md
│   ├── SECURITY.md
│   ├── SETUP.md
│   ├── ENVIRONMENT.md
│   ├── TESTING.md
│   └── WINDOWS_COMPANION.md
└── package.json (monorepo root)
```

---

## Quick Start

### Prerequisites
- Node.js 18+
- npm or yarn

### Setup

1. **Clone the repository:**
   ```bash
   git clone https://github.com/baeawesome213-ai/jarvis-x.git
   cd jarvis-x
   ```

2. **Install dependencies:**
   ```bash
   npm install
   cd frontend && npm install
   cd ../backend && npm install
   ```

3. **Configure environment:**
   ```bash
   cp backend/.env.example backend/.env.local
   # Edit backend/.env.local with your API keys (server-side only)
   ```

4. **Start development:**
   ```bash
   # Backend (from backend/)
   npm run dev
   
   # Frontend (from frontend/, in another terminal)
   npm run dev
   ```

5. **Visit:** `http://localhost:3000`

---

## Documentation

- **[ARCHITECTURE.md](./docs/ARCHITECTURE.md)** — System design, provider abstraction, data flow
- **[VOICE.md](./docs/VOICE.md)** — Voice pipeline, STT, TTS, wake-word, interruption
- **[SECURITY.md](./docs/SECURITY.md)** — API security, secret management, validation, tool execution
- **[SETUP.md](./docs/SETUP.md)** — Development setup, dependencies, configuration
- **[ENVIRONMENT.md](./docs/ENVIRONMENT.md)** — Required and optional environment variables
- **[TESTING.md](./docs/TESTING.md)** — Test scenarios, validation, debugging
- **[WINDOWS_COMPANION.md](./docs/WINDOWS_COMPANION.md)** — Future Windows application integration

---

## Testing Checklist

- [ ] Text conversation works
- [ ] Voice input works
- [ ] Voice notes work
- [ ] Speech automatically transcribed
- [ ] Transcription enters same AI engine
- [ ] AI responses appear as text
- [ ] AI responses automatically speak (Voice Mode enabled)
- [ ] TTS can be stopped and replayed
- [ ] User can interrupt JARVIS
- [ ] Conversation Mode works
- [ ] Voice settings persist
- [ ] STT provider abstraction works
- [ ] TTS provider abstraction works
- [ ] Errors handled gracefully
- [ ] API keys remain server-side
- [ ] Tool execution validated
- [ ] No crashes when voice services fail
- [ ] PWA functionality works
- [ ] Production build succeeds
- [ ] No console errors
- [ ] No fake functionality

---

## Technology Stack

### Frontend
- **React 18** — UI framework
- **TypeScript** — Type safety
- **Web Audio API** — Microphone capture, audio processing
- **Web Speech API** — Browser STT fallback
- **TailwindCSS** — Styling
- **Framer Motion** — Animations
- **IndexedDB** — Persistent storage

### Backend
- **Node.js + Express** — Server framework
- **TypeScript** — Type safety
- **Environment variables** — Secret management
- **Configurable AI/STT/TTS providers** — Modular architecture

### AI Providers (Configurable)
- OpenAI API
- Google Cloud Speech-to-Text / Text-to-Speech
- Azure Cognitive Services
- Anthropic Claude

---

## Security & Privacy

- **Server-side secrets only** — API keys never exposed to frontend
- **Input validation** — All user inputs sanitized
- **Tool execution validation** — AI-generated parameters validated before execution
- **No arbitrary code execution** — Explicit, validated tool definitions only
- **Rate limiting** — Prevent abuse
- **CORS & HTTPS** — Secure communication
- **PWA & Offline** — Graceful degradation

---

## Development Standards

✓ Clean separation of concerns  
✓ Reusable components and services  
✓ Strong TypeScript typing  
✓ Clear naming conventions  
✓ No hard-coded secrets  
✓ Centralized error handling  
✓ Modular provider system  
✓ Production-ready code quality  

**No fake implementations.** If a feature cannot be fully implemented in browser, the limitation is clearly documented and the architecture supports future Windows companion integration.

---

## Roadmap

### Phase 1: Core (Current)
- [x] Repository setup
- [ ] Frontend architecture & HUD
- [ ] Text-based conversation
- [ ] Basic voice input
- [ ] STT/TTS providers
- [ ] State machine
- [ ] Error handling

### Phase 2: Voice Excellence
- [ ] Wake word (browser + Windows ready)
- [ ] Interruption/barge-in
- [ ] Conversation mode
- [ ] Voice notes
- [ ] Replay & speed control
- [ ] Advanced TTS settings

### Phase 3: Tools & Actions
- [ ] Tool system architecture
- [ ] Browser tool execution
- [ ] Search integration
- [ ] Reminders
- [ ] Windows-ready tool definitions

### Phase 4: Polish & Production
- [ ] PWA installation
- [ ] Performance optimization
- [ ] Accessibility audit
- [ ] Security review
- [ ] Production build
- [ ] Documentation complete

### Phase 5: Windows Companion (Future)
- [ ] Companion app scaffolding
- [ ] Secure backend connection
- [ ] Native microphone access
- [ ] Global hotkey
- [ ] Windows app launching
- [ ] System integration

---

## Contributing

This is a professional production project. All code must meet:
- Production quality standards
- Security requirements
- Testing coverage
- Documentation completeness
- Type safety

---

## License

MIT

---

## Contact

**Project Lead:** baeawesome213-ai  
**GitHub:** [@baeawesome213-ai](https://github.com/baeawesome213-ai)

---

**JARVIS X — Intelligence. Reliability. Sophistication.**
