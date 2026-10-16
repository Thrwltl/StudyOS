# StudyOS — Vercel + Groq

StudyOS preserves the original browser-local dashboard, subjects, tasks, calendar, planner, timer, goals and JSON backups, and adds a secure AI proxy, adaptive personality selector and downloadable audio lessons.

## Deploy

1. Create a Groq API key in the Groq console.
2. Create an Upstash Redis database and copy its REST URL and REST token. **Production requests fail closed if these are missing** (shared rate limiting is required for a public site).
3. Import this folder as a Vercel project (Framework Preset: Other; output directory: `public`). Set environment variables from `.env.example` in Vercel project settings. **Never prefix secrets with `NEXT_PUBLIC_` or put them in frontend code.**
4. Deploy. The frontend calls same-origin `/api/chat`, `/api/lesson` and `/api/speech`; users never enter API keys.
5. Test chat, a 3-minute Photosynthesis audio lesson, playback, progress, WAV download, and your original dashboard.

## Important notes

- Groq Orpheus speech output is WAV, so offline downloads are **WAV rather than MP3**. Actual spoken length depends on the model and pacing; the target is approximate.
- The configured Groq TTS model, voice, provider input size and model availability can change. Confirm current model access and quotas in your Groq account. The server chunks narration into short TTS requests and joins WAV data. Long lessons may still exceed Vercel function execution time or provider quotas; use shorter durations or move synthesis to an asynchronous job queue for production reliability. The generated transcript remains visible if speech fails.
- A single public IP is limited to 25 chat/lesson requests and 8 audio requests per hour, via shared Upstash Redis. These are basic limits; for larger traffic add bot protection, global cost ceilings, observability and provider usage alerts. No user login is required.
- Prompts and notes are transmitted to Groq only when the student generates an answer or lesson. The user's study dashboard data stays in browser localStorage. Personality preference is also stored locally.
- Generated audio exists in the browser session as a blob URL; download it to keep it offline. Refreshing the page clears the audio.
- The `/api/speech` endpoint accepts a script from the browser. Public abuse controls are rate limits, origin checking and input limits; for stronger protection add signed short-lived lesson tokens or authenticated sessions.
- For local development, install the Vercel CLI and run `vercel dev` with environment variables configured. Local mode has a best-effort in-memory rate limit; do not use that mode for public production traffic.
