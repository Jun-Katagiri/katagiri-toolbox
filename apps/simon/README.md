# 📝 **PC Numpad Memory Game — README（10キー版）**

## Overview

This is a **numeric memory game inspired by “Simon Says,”**
designed around the **PC numeric keypad layout (0–9)**.

A sequence of digits (0–9) is highlighted using the visual layout of a standard PC numpad:

```
7 8 9
4 5 6
1 2 3
  0
```

The player must reproduce the sequence using either:

* the on-screen keypad, or
* a physical **PC numpad / USB numeric keypad / calculator-style keypad**

Each successful round adds one more digit to the sequence and increases the score.

This mini-app lives under:

```
apps/simon/
```

and serves as a compact demonstration of **interactive UI**,
**real-time input handling**, and **full-stack workflow** with modern web tools.

---

## Features

### 🎮 Game Mechanics

* Visual keypad replicating the PC numpad layout
* Sequence plays one digit at a time
* Player repeats the digits in order
* Score increments each round
* Incorrect input → game over
* Optional keyboard input (0–9 numpad keys)

### 🏆 High Score System

* After game over, the user enters a nickname
* Score is sent to a backend API
* High scores are stored using Drizzle ORM
* Top 10 scores are displayed on the page
* Database:

  * **SQLite** in development
  * **Turso** in production

---

## Tech Stack

* **Next.js (App Router)**
* **React + Hooks**
* **shadcn/ui**
* **Tailwind CSS**
* **Zod** for API input validation
* **Drizzle ORM**
* **SQLite** (local)
* **Turso** (hosted, production)
* **Vercel** (deployment)
* **Turborepo** monorepo structure

---

## App Structure (inside this application)

```
apps/simon/
  ├─ app/
  │   ├─ page.tsx                 ← UI, keypad layout, game logic (client)
  │   └─ api/
  │        └─ scores/
  │             └─ route.ts       ← High Score API (GET/POST)
  ├─ db/
  │   ├─ schema.ts                ← Drizzle schema (scores table)
  │   └─ client.ts                ← Database client (Turso / SQLite)
  ├─ public/                      ← Optional assets
  ├─ README.md                    ← This file
  └─ package.json
```

---

## API Specification

### **GET `/api/scores`**

Returns the top stored high scores.

### **POST `/api/scores`**

Registers a new high score.

Payload:

* `name` — string (1–32 chars)
* `score` — integer (>= 0)

Validation handled by **Zod**.

---

## Local Development

### 1. Install dependencies (monorepo root)

```
pnpm install
```

### 2. Environment variables

Create `apps/simon/.env.local` and set:

```
TURSO_DATABASE_URL=""
TURSO_AUTH_TOKEN=""
```

For local development, the database can be changed to a SQLite file URL.

### 3. Run this app only

```
pnpm dev --filter simon
```

---

## Deployment (Vercel + Turso)

1. Create a Turso database
2. Set `TURSO_DATABASE_URL` and `TURSO_AUTH_TOKEN` in Vercel project settings
3. Deploy (Vercel automatically detects the app inside `apps/simon/`)

---

## Future Enhancements

* Sound feedback and error sounds
* Keypress highlight animations
* Quick-mode (shorter glow time)
* Reverse mode (repeat the sequence backwards)
* Time-attack challenges
* Score sharing via unique URLs
* Full keyboard support (including fallback keys)

---

## License

This project is part of a public portfolio and intended for demonstration and educational purposes.

---
