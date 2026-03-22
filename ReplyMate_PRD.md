# ReplyMate — Product Requirements Document (PRD / BRD)
**Version:** 1.0
**Date:** March 2026
**Status:** Draft

---

## 1. Executive Summary

**ReplyMate** is a cross-platform mobile assistant app that helps users craft fast, thoughtful, and contextually appropriate replies — whether they are responding to a WhatsApp message, an Instagram DM, an email, a tweet, or a live in-person/phone conversation. Powered by an LLM backend and designed with a radically simple interface, ReplyMate understands multiple languages, mixed-language (code-switched) speech, and visual context (screenshots), and returns reply options the user can review, customize, and send.

---

## 2. Problem Statement

Modern users receive messages across 5–10 communication channels daily. Crafting an appropriate, well-worded reply requires time, mental energy, and often clarity that isn't always available in the moment. Pain points include:

- **Reply paralysis** — not knowing what to say or how to start.
- **Context switching** — jumping between apps to think through replies.
- **Language complexity** — multilingual users think and speak in blended languages but most tools force a single language.
- **Live conversations** — no tool assists in real-time spoken dialogue.
- **Tone mismatch** — users often send replies that are too formal, too casual, or simply unclear.

---

## 3. Vision & Goals

### Vision
Be the invisible, intelligent co-communicator in every user's pocket — helping them respond to anyone, in any language, in any context, faster and better.

### Goals
| Goal | Metric |
|------|--------|
| Reduce average reply drafting time | From ~3 min to <30 seconds |
| Support multilingual & code-switched input | 50+ languages, unlimited mixing |
| Achieve daily active usage | DAU/MAU ratio > 40% |
| High reply acceptance rate | User sends LLM-drafted reply (with/without edits) >60% of time |
| Cross-platform parity | Feature-equivalent on iOS and Android on launch |

---

## 4. Target Users

### Primary Persona — "The Juggler"
- Age: 22–45
- Uses 4+ messaging apps daily
- Bilingual or multilingual (e.g., speaks Marathi + Hindi + English)
- Busy professional, student, or entrepreneur
- Wants fast, smart, natural-sounding replies

### Secondary Persona — "The Non-Native Speaker"
- Age: 18–60
- Not fully confident writing in a second language (e.g., English at work)
- Needs help phrasing thoughts clearly and professionally

### Tertiary Persona — "The Live Talker"
- Attends meetings, calls, interviews, or negotiations
- Wants real-time coaching or reply suggestions during spoken conversations

---

## 5. Core Use Cases

### UC-1: Reply to a Text Message / Chat Screenshot
User takes or attaches a screenshot of a conversation (WhatsApp, Instagram, iMessage, etc.). The app reads the context, and suggests 2–3 reply options in the user's preferred style and language.

### UC-2: Voice Input to Draft Reply
User verbally describes what they want to say or what situation they're in. The app transcribes (handling multilingual/code-switched speech) and generates polished reply options.

### UC-3: Paste or Type the Incoming Message
User manually pastes or types the message they received. The app generates reply options.

### UC-4: Live Conversation Mode
User presses a "Live" button. The app continuously listens to what others are saying in a conversation (in-person or on a call), transcribes it, and surfaces reply suggestions in real time — quietly and discreetly on screen.

### UC-5: Style Selection
After generating replies, user can request a different tone — more formal, more casual, shorter, friendlier, assertive, apologetic, humorous, etc.

### UC-6: Language Output Choice
User can specify the language of the reply (e.g., "Reply in Marathi" or "Reply in formal Hindi with English tech terms").

---

## 6. Feature Requirements

### 6.1 Input Methods
| Feature | Priority | Notes |
|---------|----------|-------|
| Screenshot/image attachment | P0 | OCR + vision model to read chat UI |
| Voice input (multilingual) | P0 | Whisper-class STT supporting 50+ languages and code-switching |
| Text paste / manual type | P0 | Simple text field |
| Live microphone mode | P1 | Continuous listening; privacy-first (on-device buffer only) |
| Share-sheet integration | P1 | iOS/Android share extension — share a message directly from WhatsApp/Gmail into ReplyMate |

### 6.2 Language Intelligence
| Feature | Priority | Notes |
|---------|----------|-------|
| Multilingual voice recognition | P0 | Must handle Marathi+Hindi+English in same sentence |
| Auto language detection | P0 | Detect dominant language; flag mixed |
| Reply language choice | P0 | User sets default; can change per session |
| Code-switched output | P1 | e.g., "Reply in Hinglish (Hindi + English)" |
| Script support | P1 | Devanagari, Latin, Arabic, Cyrillic, etc. |

### 6.3 Reply Generation
| Feature | Priority | Notes |
|---------|----------|-------|
| 2–3 reply options per request | P0 | Varied tone/length per option |
| Tone labels on each option | P0 | e.g., "Friendly", "Professional", "Concise" |
| Regenerate / more options | P0 | Tap to get fresh suggestions |
| Tone slider / style picker | P1 | Formal ↔ Casual; Short ↔ Detailed |
| Match sender's style | P1 | Analyze incoming message style and mirror it |
| Custom tone presets | P2 | User-saved styles (e.g., "My work tone") |

### 6.4 Context Awareness
| Feature | Priority | Notes |
|---------|----------|-------|
| Screenshot reading (OCR + vision) | P0 | Extract message thread context |
| Conversation thread memory (session) | P1 | Within a session, remember prior context |
| Platform-aware suggestions | P1 | WhatsApp reply ≠ email reply in length/formality |
| Emoji / GIF suggestion | P2 | Optional add-ons to reply |

### 6.5 Interface & UX
| Feature | Priority | Notes |
|---------|----------|-------|
| Minimalist home screen | P0 | Single action prompt, no clutter |
| Dark mode / Light mode | P0 | System default + manual override |
| One-tap copy reply | P0 | Copy to clipboard for pasting anywhere |
| One-tap share reply | P1 | Direct share sheet to WhatsApp, Gmail, etc. |
| Reply history (local) | P1 | Last 20 replies cached on device |
| Haptic feedback | P1 | Subtle confirmation on copy/send |
| Onboarding in <60 seconds | P0 | 3-screen onboarding, no account required to try |

### 6.6 Privacy & Trust
| Feature | Priority | Notes |
|---------|----------|-------|
| No message storage on server by default | P0 | Stateless API calls; opt-in history sync |
| Live mode privacy indicator | P0 | Clear visual "mic is active" state |
| Screenshot data not retained | P0 | Processed and discarded server-side |
| Transparent AI disclosure | P0 | "Powered by AI" visible in UI |
| Opt-in analytics only | P1 | GDPR / DPDP compliant |

---

## 7. Interface Design Principles

Inspired by Google and Apple's minimalist app aesthetics:

1. **One thing per screen.** Each screen has one primary action. No sidebars, no tabs overload.
2. **Content-first.** The reply text is the hero. Everything else recedes.
3. **Invisible intelligence.** AI feels like magic, not machinery. No "processing..." spinners — use skeleton loaders and smooth transitions.
4. **Touch-native.** Large tap targets. Swipe to dismiss. Long-press for options.
5. **Calm color palette.** White/off-white base. One accent color. No aggressive gradients.

### Key Screens (Wireframe Concepts)

```
┌─────────────────────────┐
│   ReplyMate             │  ← Home / Input Screen
│                         │
│  ┌───────────────────┐  │
│  │  What's the       │  │
│  │  message about?   │  │
│  │  [                │  │
│  └───────────────────┘  │
│                         │
│  [📷 Screenshot]        │
│  [🎙 Speak]  [⌨ Type]  │
│                         │
│  Reply in: [English ▾]  │
└─────────────────────────┘

┌─────────────────────────┐
│  ← Reply Options        │  ← Results Screen
│                         │
│  ─── Friendly ───       │
│  "Hey! Sure, sounds     │
│   good to me 😊"        │
│                    [📋] │
│                         │
│  ─── Professional ───   │
│  "Thank you for         │
│   reaching out. I'd     │
│   be happy to..."       │
│                    [📋] │
│                         │
│  ─── Concise ───        │
│  "Works for me."        │
│                    [📋] │
│                         │
│  [↻ More options]       │
│  [🎨 Change tone]       │
└─────────────────────────┘

┌─────────────────────────┐
│   🔴 LIVE MODE          │  ← Live Conversation Screen
│                         │
│  "...so I was thinking  │
│   we should move the    │
│   deadline to Friday."  │
│                         │
│  ── Suggested replies ──│
│  • "That works for me." │
│  • "Can we do Thursday  │
│     instead?"           │
│  • "Let me check and    │
│     confirm."           │
└─────────────────────────┘
```

---

## 8. Technical Architecture (High-Level)

### Stack Recommendation
| Layer | Technology |
|-------|-----------|
| Mobile Framework | React Native (iOS + Android, single codebase) |
| Voice/STT | OpenAI Whisper API or on-device Whisper (multilingual) |
| Vision / OCR | GPT-4o Vision or Google Vision API |
| LLM (reply gen) | Claude (claude-sonnet-4-6) via Anthropic API |
| Backend | Lightweight Node.js / Python API gateway (stateless) |
| Auth (optional) | Sign in with Apple / Google (for sync features only) |
| Local Storage | SQLite (via Expo SQLite) for reply history |
| Analytics | PostHog (privacy-first, self-hostable) |

### Data Flow
```
User Input (voice / image / text)
        ↓
STT / OCR preprocessing (edge or API)
        ↓
Context builder (language detection + platform tag)
        ↓
LLM API call (Claude) with structured prompt
        ↓
3 reply options returned + tone labels
        ↓
Rendered in UI → user copies or shares
```

---

## 9. Multilingual Design — Deep Dive

### The Code-Switching Challenge
Most STT and LLM tools fail at intra-sentence language mixing. ReplyMate must handle:
- "Mala vatata ki we should **postpone** the **meeting**." *(Marathi + English)*
- "Yaar, **seriously** ek baar **check** kar le." *(Hindi + English)*
- "Can you **kal tak** send kar do?" *(English + Hindi)*

### Approach
1. **STT with language hints:** Allow user to set "primary language" and "secondary languages" — pass as hints to Whisper/STT engine.
2. **LLM prompt design:** System prompt instructs model to recognize and respect code-switching, and to reply in the same blend unless instructed otherwise.
3. **Language of reply ≠ language of input:** User may speak in Marathi but request a formal English email reply.
4. **Script rendering:** Ensure app font renders Devanagari, Arabic, and other non-Latin scripts correctly.

---

## 10. Monetization Strategy

| Tier | Price | Features |
|------|-------|----------|
| **Free** | $0 | 10 replies/day, text + screenshot input, 3 languages |
| **Pro** | $4.99/month | Unlimited replies, voice input, live mode (30 min/day), all languages, custom tones |
| **Ultra** | $9.99/month | Unlimited live mode, reply history sync, priority response speed, team sharing (future) |

**Additional:** B2B licensing for customer support teams, sales reps, or language schools.

---

## 11. Go-to-Market Strategy

### Phase 1 — Soft Launch (Months 1–2)
- Launch on iOS (App Store) in India, USA, UK
- Target multilingual communities (Indian diaspora, ESL professionals)
- Product Hunt launch
- Influencer seeding in productivity / language learning niches

### Phase 2 — Growth (Months 3–6)
- Android launch
- WhatsApp share-sheet integration (Android deep link)
- Localized App Store listings in Hindi, Marathi, Spanish, Arabic
- Referral program ("Give a friend 7 Pro days")

### Phase 3 — Expansion (Months 7–12)
- Live mode GA
- Business tier
- API for third-party integration (keyboard apps, CRM tools)

---

## 12. Success Metrics (KPIs)

| Metric | Target (6 months) |
|--------|------------------|
| Total downloads | 100,000+ |
| DAU | 25,000+ |
| Free → Pro conversion | 8–12% |
| Reply acceptance rate | >60% |
| Avg session length | 90–120 seconds |
| App Store rating | ≥ 4.5 stars |
| Crash-free sessions | >99.5% |

---

## 13. Risks & Mitigations

| Risk | Likelihood | Impact | Mitigation |
|------|-----------|--------|-----------|
| LLM API latency hurts UX | Medium | High | Stream responses; show partial replies as they generate |
| Privacy concerns around Live mode | High | High | On-device processing where possible; clear visual indicators; zero server retention |
| App Store rejection (audio recording) | Medium | High | Comply fully with Apple/Google mic permission guidelines; add clear consent flows |
| Low multilingual STT accuracy | Medium | High | Allow user to correct transcription before generating reply |
| Competitive response from Big Tech | Medium | Medium | Focus on multilingual code-switching — underserved by incumbents |
| LLM cost at scale | Medium | Medium | Cache similar prompts; optimize token usage; tiered limits |

---

## 14. Out of Scope (v1.0)

- Direct in-app sending (sending reply directly from within ReplyMate to WhatsApp, etc.)
- AI memory across sessions (long-term user relationship tracking)
- Voice output (text-to-speech of replies)
- Web browser extension
- Wearable / smartwatch version
- Group conversation dynamics

---

## 15. Open Questions

1. Should v1 require an account, or allow fully anonymous use?
2. For Live Mode — should transcription be on-device (private, slower) or server-side (faster, privacy tradeoff)?
3. Should we support right-to-left languages (Arabic, Urdu) at launch or Phase 2?
4. What is the primary monetization priority — consumer subscription or B2B licensing?
5. App name: **ReplyMate**, **ReplyAI**, **Saathi** (Hindi for "companion"), or open to branding exercise?

---

## Appendix — Sample Prompt Architecture (LLM)

```
System:
You are ReplyMate, an expert communication assistant.
The user will give you a message they received (via text or described verbally).
Generate exactly 3 reply options:
- Option 1: Friendly and warm
- Option 2: Professional and clear
- Option 3: Concise (under 10 words)

Rules:
- Reply in [USER_LANGUAGE_PREFERENCE]
- If the user's input mixes languages (e.g., Hindi + English), recognize it and reply in the same blend unless instructed otherwise
- Match the platform context: [PLATFORM: WhatsApp / Email / Instagram / Other]
- Do not add explanations — only return the 3 reply texts with tone labels

User: [USER_INPUT or SCREENSHOT_OCR_TEXT]
```

---

*Document prepared by: Product Management*
*Next step: Review with engineering lead, design lead, and legal. Schedule discovery sprint.*
