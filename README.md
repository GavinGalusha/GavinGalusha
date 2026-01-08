## Hi 👋

I’m a software engineer.  
Most of my work lives in private repos, but I want to spotlight **MySplit** — a project I actively design, build, and run end-to-end.

---


## MySplit — Fixing What Workout Apps Get Wrong
<p align="center">
  <!-- Icons -->
  <img src="https://cdn.simpleicons.org/react/61DAFB" width="40" alt="React" />
  <img src="https://cdn.simpleicons.org/nextdotjs/000000" width="40" alt="Next.js" />
  <img src="https://cdn.simpleicons.org/supabase/3ECF8E" width="40" alt="Supabase" />
  <img src="https://cdn.simpleicons.org/postgresql/316192" width="40" alt="PostgreSQL" />
  <img src="https://cdn.simpleicons.org/redis/DC382D" width="40" alt="Redis" />

  <img src="https://cdn.simpleicons.org/langchain/316192" width="40" alt="LangChain" />

</p>

<p>  
🔗 **Live web app:** https://mysplit-dun.vercel.app/
</p>
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
- **Notes** — derive workouts from natural language that persists across sessions
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
- Maintains **tunable context boundaries**, allowing behavior changes without rewriting prompts
- Keeps execution and reasoning **traceable**, making failures debuggable instead of opaque

This architecture allows the coach to:
- Plan workouts
- Post completed sessions
- Create and update user data from high-level statements  
  (e.g. “I ran 5 miles every day this week” → 5 run activities)
- Reuse historical patterns  
…without becoming brittle as the product grows.

It avoids the common “chatbot glued to a CRUD app” trap and treats AI as a **first-class system component**.

---

## Platform support

MySplit exists as:
- A **web app** built with **Next.js**
- A **deployed mobile app** built with **React Native**

Both share the same backend, data models, and AI logic.

---

## Tech behind the scenes

This is a full-stack system I run end-to-end, optimized for **latency, correctness, and scale**:

- **Web:** Next.js, React
- **Mobile:** React Native (deployed)
- **Backend:** API routes + server actions
- **AI:** LangGraph, LangChain, OpenAI APIs
- **Data:** Postgres / Supabase

### Performance, caching, and correctness

- **Client & server caching**
  - **React Query** for request deduplication, background refetching, and fine-grained cache invalidation
  - **Redis** for shared caching of hot paths (profiles, feeds, recent workouts)

- **Lazy loading & rendering control**
  - Aggressive route-level and component-level lazy loading
  - Heavy **`.glb` 3D muscle models** are virtualized with hard limits (only a few mounted at once) to avoid GPU and memory thrashing

- **Database optimization**
  - Indexed user profiles, social graphs, and workout queries for fast feed and profile loads
  - **Database triggers** maintain derived user data and aggregates so reads stay cheap and consistent

- **Optimistic UI with guarantees**
  - Likes, follows, and social actions use **optimistic updates** for instant feedback
  - All mutations are **idempotent**, making retries and race conditions safe
  - Clean reconciliation on refetch without UI jank

- **Middleware & request hygiene**
  - Centralized **Axios middleware** for rate limiting, auth, and path/payload validation
  - Keeps API routes small, predictable, and safe by default

A lot of effort went into **latency control**, **tool boundaries**, and **minimizing unnecessary model calls** so the app feels fast during workouts, where responsiveness matters most.

---

## Why I built this

MySplit is less about fitness specifically, and more about exploring:

- How to reduce friction in real user workflows
- How to make AI systems **structured instead of fuzzy**
- How to ship agentic systems that hold up under real use

If you’re curious, the live app is here:
👉 https://mysplit-dun.vercel.app/
