# Catalog Voice AI

Catalog-grounded voice retail agent with a 3D boutique. Turns a static product catalog into an interactive shopping experience: users ask questions by voice or text, see recommendations on screen, and hear replies spoken aloud.

Full engineering workspace:

- `wine-boutique-world` — flagship 3D boutique demo with an in-world NPC consultation overlay
- `wine-voice-explorer` — standalone sandbox for the same advisor core
- `packages/wine-ai-core` — shared retrieval, prompt, streaming, voice, and proxy logic

## Demo

[Watch the Demo on Loom](https://www.loom.com/share/eae8e365e71a489e872152db640f4e63)

## What the System Does

- Loads a product catalog as the source of truth (JSON, client-side)
- Accepts voice or text questions via WebRTC
- Parses structured shopping signals: price, region, type, occasion, gift intent
- Retrieves a candidate set locally using a deterministic filter — no vector store
- Sends only grounded catalog context to Vertex AI (Gemini 2.5 Flash)
- Streams the answer into the UI and speaks it with Google Cloud TTS
- 3-layer TTS fallback: Cloud TTS → browser speech synthesis → text
- 5-state consultation flow with carry-forward filters; progressively relaxes constraints on a miss

The 3D boutique app wraps that core in a full product shell: 3D scene, NPC interaction, ambient audio, and an integrated consultation overlay.

## Stack

React 19, THREE.js, Gemini 2.5 Flash, Vertex AI Streaming, Google Cloud TTS, WebRTC, FastAPI

## Workspace Layout

```
Catalog-Voice-AI/
├── wine-boutique-world/      # 3D boutique app
├── wine-voice-explorer/      # standalone sandbox
└── packages/
    └── wine-ai-core/         # shared core logic
```
