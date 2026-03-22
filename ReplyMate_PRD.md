# ReplyMate — Product Requirements Document (PRD / BRD)
**Version:** 1.1
**Date:** March 2026
**Status:** Draft

---

## 1. Executive Summary

**ReplyMate** is a cross-platform mobile communication assistant that covers the full lifecycle of a conversation — helping users **start** a conversation, **reply** to one, and **follow up** when they don't hear back. Whether drafting a first message to a recruiter, responding to a WhatsApp thread, or nudging a contact who went silent, ReplyMate generates ready-to-send options in seconds.

Powered by an LLM backend and designed with a radically simple interface, ReplyMate understands multiple languages, mixed-language (code-switched) speech, and visual context (screenshots). It also listens in real time during live conversations and surfaces reply suggestions on screen. Users get 2–3 options per request, choose their tone, and copy or share directly — no typing required.

---

## 2. Problem Statement

Modern users manage communication across 5–10 channels daily. Every conversation has three moments where they get stuck — starting it, responding to it, and chasing it when it goes quiet. Pain points include:

**Responding**
- **Reply paralysis** — not knowing what to say or how to phrase it.
- **Context switching** — jumping between apps to think through a reply.
- **Tone mismatch** — replies that land too formal, too casual, or simply unclear.

**Initiating**
- **Blank page problem** — knowing what you want to say but not how to open.
- **Fear of sounding wrong** — especially in professional, sensitive, or cross-cultural contexts.
- **Language barrier** — non-native speakers struggling to write confidently in a second language.

**Following Up**
- **Ghost anxiety** — someone hasn't replied; user doesn't know whether to follow up or how.
- **Tone calibration** — following up too aggressively burns bridges; too softly gets ignored.
- **No memory** — user has to re-read the original message and reconstruct context before writing.

**Across all three**
- **Language complexity** — multilingual users think in blended languages but most tools force a single language.
- **Live conversations** — no tool assists in real-time spoken dialogue.

---

## 3. Vision & Goals

### Vision
Be the invisible, intelligent co-communicator in every user's pocket — helping them start conversations, respond to anyone, and follow through — in any language, in any context, faster and better.

### Goals
| Goal | Metric |
|------|--------|
| Reduce average message drafting time | From ~3 min to <30 seconds |
| Cover full conversation lifecycle | Reply, Initiate, and Follow-Up all in v1.0 |
| Support multilingual & code-switched input | 50+ languages, unlimited mixing |
| Achieve daily active usage | DAU/MAU ratio > 40% |
| High message acceptance rate | User sends LLM-drafted message (with/without edits) >60% of time |
| Follow-up feature adoption | ≥25% of active users use Follow-Up mode within first month |
| Cross-platform parity | Feature-equivalent on iOS and Android on launch |

---

## 4. Target Users

### Primary Persona — "The Juggler"
- Age: 22–45
- Uses 4+ messaging apps daily
- Bilingual or multilingual (e.g., speaks Marathi + Hindi + English)
- Busy professional, student, or entrepreneur
- Needs help at all three stages: starting conversations, replying, and following up
- Wants fast, smart, natural-sounding messages without overthinking

### Primary Persona — "The Initiator"
- Age: 22–40
- Regularly reaches out cold or semi-cold: job applications, client pitches, partnership proposals, reconnecting with contacts
- Knows what they want to say but struggles with how to open or frame it
- High stakes mean they want multiple options and tonal control before hitting send

### Secondary Persona — "The Non-Native Speaker"
- Age: 18–60
- Not fully confident writing in a second language (e.g., English at work)
- Needs help phrasing thoughts clearly and professionally
- Especially benefits from initiate and follow-up modes where blank-page anxiety is highest

### Tertiary Persona — "The Live Talker"
- Attends meetings, calls, interviews, or negotiations
- Wants real-time coaching or reply suggestions during spoken conversations

---

## 5. Core Use Cases

ReplyMate covers **three primary modes** that together span the full lifecycle of any conversation:

---

### MODE A — RESPOND (Inbound)
*Someone has sent you a message and you need to reply.*

### UC-1: Reply to a Text Message / Chat Screenshot
User attaches a screenshot of a conversation (WhatsApp, Instagram, iMessage, email, etc.). The app reads the thread context and suggests 2–3 reply options in the user's preferred style and language.

### UC-2: Voice Input to Draft Reply
User verbally describes the situation or what they want to say. The app transcribes (handling multilingual/code-switched speech) and generates polished reply options.

### UC-3: Paste or Type the Incoming Message
User manually pastes or types the message they received. The app generates reply options.

### UC-4: Live Conversation Mode
User presses a "Live" button during an in-person meeting, phone call, or video call. The app continuously listens, transcribes what others are saying, and surfaces reply suggestions in real time — quietly and discreetly on screen.

---

### MODE B — INITIATE (Outbound — First Message)
*You are the one starting the conversation. No prior thread exists.*

### UC-5: Draft an Opening Message
User describes who they are writing to, what they want to say, and why — via voice or text. The app drafts 2–3 opening message options suited to the context and relationship. Examples:
- Reaching out to a recruiter or hiring manager
- Reconnecting with an old colleague or friend
- Pitching a collaboration or business proposal
- Introducing yourself to a new client or teammate
- Asking a favour from someone you don't know well

The app accounts for platform context (LinkedIn message ≠ WhatsApp ≠ formal email) and lets the user control tone from warm and personal to crisp and professional.

---

### MODE C — FOLLOW UP (Outbound — No Reply)
*You sent a message. They haven't responded. You need to follow up without seeming desperate or aggressive.*

### UC-6: Follow-Up When No Reply Received
User provides their original message (paste, describe, or pull from history) and tells the app how long it has been since sending. The app drafts a context-aware follow-up with three urgency options:

| Urgency | Description |
|---------|-------------|
| **Gentle nudge** | Friendly, low-pressure — "Just checking in…" |
| **Clear reminder** | Polite but direct — signals the ask is still open |
| **Final follow-up** | Firm, closes the loop — signals this is the last attempt |

The app understands that chasing a business lead requires a different tone than nudging a friend to confirm dinner plans. Users can also request a **follow-up sequence** (nudge → reminder → final), with suggested timing between each message.

---

### CROSS-CUTTING USE CASES (apply to all three modes)

### UC-7: Style & Tone Selection
After generating options, user can request a different tone — more formal, more casual, shorter, friendlier, assertive, apologetic, humorous, etc. — without re-entering their input.

### UC-8: Language Output Choice
User specifies the language of the output (e.g., "Reply in Marathi", "Write in formal Hindi with English tech terms", "Make it Hinglish"). Output language is independent of input language.

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
| **Initiate mode** — draft opening message | P0 | User describes context; app drafts cold/warm outreach, intro, pitch, etc. |
| **Follow-up mode** — no reply nudge | P0 | User inputs original message + time elapsed; app drafts follow-up with selectable urgency (gentle / firm / final) |
| Follow-up series (multi-step) | P1 | App suggests a sequence: nudge → reminder → final follow-up, spaced appropriately |
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
│   ReplyMate             │  ← Home Screen (Mode Selector)
│                         │
│  ┌───────┐ ┌─────────┐  │
│  │ 💬    │ │  ✉️     │  │
│  │ Reply │ │ Initiate│  │
│  └───────┘ └─────────┘  │
│       ┌───────────┐      │
│       │  🔁       │      │
│       │ Follow Up │      │
│       └───────────┘      │
│                         │
│  [🔴 Live Mode]         │
│                         │
│  Lang: [English ▾]      │
└─────────────────────────┘

┌─────────────────────────┐
│   ReplyMate  [Reply]    │  ← Reply Input Screen
│                         │
│  ┌───────────────────┐  │
│  │  What did they    │  │
│  │  send you?        │  │
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
│  ← Start a Message      │  ← Initiate Screen
│                         │
│  Who are you writing to?│
│  [                    ] │
│                         │
│  What's it about?       │
│  [🎙 Speak] [⌨ Type]   │
│                         │
│  Tone: [Warm ▾]         │
│  Platform: [Email ▾]    │
└─────────────────────────┘

┌─────────────────────────┐
│  ← Follow Up            │  ← Follow-Up Screen
│                         │
│  Original message:      │
│  [paste or describe]    │
│                         │
│  How long since sent?   │
│  [1 day] [3 days] [1wk] │
│                         │
│  Urgency:               │
│  ○ Gentle nudge         │
│  ○ Clear reminder       │
│  ○ Final follow-up      │
│                    [→]  │
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

### Mode A — Reply Prompt
```
System:
You are ReplyMate, an expert communication assistant.
The user received a message and needs to reply.
Generate exactly 3 reply options:
- Option 1: Friendly and warm
- Option 2: Professional and clear
- Option 3: Concise (under 10 words)

Rules:
- Write in [USER_LANGUAGE_PREFERENCE]
- If input mixes languages (e.g., Hindi + English), reply in the same blend unless instructed otherwise
- Match the platform context: [PLATFORM: WhatsApp / Email / Instagram / Other]
- Return only the 3 reply texts with tone labels — no explanations

User input / message received: [USER_INPUT or SCREENSHOT_OCR_TEXT]
```

### Mode B — Initiate Prompt
```
System:
You are ReplyMate, an expert communication assistant.
The user wants to start a conversation from scratch (no prior thread).
Generate exactly 3 opening message options:
- Option 1: Warm and personal
- Option 2: Professional and direct
- Option 3: Brief and low-pressure

Rules:
- Write in [USER_LANGUAGE_PREFERENCE]
- Tailor length and tone to the platform: [PLATFORM: LinkedIn / WhatsApp / Email / Other]
- The message should feel natural and human — not like a template
- Return only the 3 message texts with tone labels

Context provided by user:
- Recipient: [WHO]
- Purpose: [WHAT / WHY]
- Relationship: [e.g., cold outreach / old contact / new colleague]
```

### Mode C — Follow-Up Prompt
```
System:
You are ReplyMate, an expert communication assistant.
The user sent a message and received no reply. They need a follow-up.
Generate exactly 3 follow-up options matching the urgency level selected:
- Urgency: [GENTLE / CLEAR / FINAL]

Rules:
- Write in [USER_LANGUAGE_PREFERENCE]
- Gentle: warm, non-pressuring, gives the benefit of the doubt
- Clear: polite but unambiguous — signals the ask is still open
- Final: firm and closing — signals this is the last follow-up
- Platform context: [PLATFORM]
- Time since original message: [X days / weeks]
- Return only the 3 follow-up texts with urgency labels

Original message sent by user: [ORIGINAL_MESSAGE]
```

---

*Document prepared by: Product Management*
*Next step: Review with engineering lead, design lead, and legal. Schedule discovery sprint.*
