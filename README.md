

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

Loose, human input still needs to become **clean, consistent data**.

Under the hood, MySplit uses an **agentic AI system** built with **LangGraph** to:

- Break raw input into **explicit planning steps**
- Convert intent into **schema-validated actions**
- Ground decisions using **retrieval (RAG)** from:
  - Past workouts
  - Training plans
  - User-specific history
- Keep reasoning **traceable**, so failures are understandable instead of mysterious

This avoids the usual “chatbot glued to a CRUD app” problem and keeps the system predictable as it grows.

---

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
