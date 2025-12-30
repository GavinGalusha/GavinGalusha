

## Hi 👋

I’m a software engineer.  
Most of my work lives in private repos, but I want to spotlight **MySplit** — a project I actively design, build, and run end-to-end.

---

## 🏋️ MySplit — Fixing What Workout Apps Get Wrong
🔗 **Live web app:** https://mysplit-dun.vercel.app/

<!-- HERO IMAGE -->
<p align="center">
  <img src="./mysplit.png" alt="MySplit app screenshot" width="800" />
</p>

Most workout apps fail for a simple reason:

> **Logging workouts is labor-intensive.**

Typing sets, reps, weights, exercises, and notes every session is tedious, especially mid-workout. Over time, friction wins — and people stop logging consistently.

MySplit is built around the idea that **the system should adapt to how humans actually record workouts**, not the other way around.

---

## The core idea

Instead of forcing one rigid input method, MySplit lets users record workouts through **six different mediums**, all feeding into the same structured backend.

### Ways to record workouts
- **Text** — quick natural language input  
  > “Push day, bench 3x8 at 185, incline DB press 3x10”
- **Audio** — talk between sets instead of typing
- **Video** — capture context when typing isn’t practical
- **Previous workouts** — reuse and modify past sessions
- **Notes** — loose thoughts that still get incorporated
- **Manual selection** — traditional UI when precision matters

Users can mix and match these freely. The system handles normalization.

---

## What makes this hard (and interesting)

MySplit is **AI-native** — the coach isn’t a feature layered on top of the app, it *is* the interface between users and the system.

Loose, human input still needs to become **clean, consistent, structured data** that can support planning, history, and iteration over time.

Under the hood, the MySplit coach is an **agentic system** built with **LangGraph** that:

- Explicitly plans before acting (no single-shot prompts)
- Routes intent through **schema-validated tools** for logging, planning, and posting workouts
- Uses retrieval (RAG) to ground decisions in:
  - Past workouts
  - Training plans
  - User-specific preferences and context
- Maintains **tunable context boundaries**, so the coach can be adjusted without rewriting prompts or logic
- Keeps execution and reasoning **traceable**, making failures debuggable instead of opaque

This architecture allows the coach to:
- Plan workouts
- Post completed sessions
- Modify existing plans
- Reuse historical patterns  
…without becoming brittle as the product grows.

It avoids the common “chatbot glued to a CRUD app” trap and treats AI as a **first-class system component**.


## Platform support

MySplit exists as:
- A **web app** built with **Next.js**
- A **deployed mobile app** built with **React Native**

Both share the same backend, data models, and AI logic.

---

## Tech behind the scenes

This is a full-stack system I run end-to-end:

- **Web:** Next.js, React
- **Mobile:** React Native (deployed)
- **Backend:** API routes + server actions
- **AI:** LangGraph, LangChain, OpenAI APIs
- **Data:** Postgres / Supabase
- **Infra:** Deployed, monitored, and iterated based on real usage

A lot of effort went into **latency control**, **tool boundaries**, and **minimizing unnecessary model calls** so the app feels fast during workouts.

---

## Why I built this

MySplit is less about fitness specifically, and more about exploring:

- How to reduce friction in real user workflows
- How to make AI systems **structured instead of fuzzy**
- How to ship agentic systems that hold up under real use

If you’re curious, the live app is here:
👉 https://mysplit-dun.vercel.app/
