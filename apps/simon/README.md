# 📝 **Simon 9-Panel Memory Game — README（ベース版）

## Overview

This is a **9-panel memory game inspired by “Simon Says.”**
A random sequence of highlighted panels is played, and the player must reproduce the same sequence.
Each successful round extends the sequence and increases the score.

This application is part of a **Turborepo monorepo** and lives under:

```
apps/simon/
```

The goal of this mini-app is to demonstrate:

* Front-end interaction with the **Next.js App Router**
* Real-time UI feedback using React state
* Minimal but clean **game state management**
* A simple **serverless API** using the Next.js route handler
* Persistent **high-score storage** backed by **Drizzle ORM**

  * SQLite (development)
  * Turso (production)
* Component styling using **shadcn/ui + Tailwind CSS**

This project doubles as a **public portfolio entry**, showing the developer’s ability to build interactive UI, manage game logic, and integrate a backend in a modern full-stack web environment.

---

## Features

### 🎮 Game System

* 3×3 grid (9 panels)
* Random sequence playback
* Player taps panels in order
* Score increases each round
* Game ends upon a mistake

### 🏆 High Score Recording

* After game over, player enters a nickname
* Score is sent to the backend via a POST API
* Top scores are stored in the Turso database
* The top 10 scores are displayed on the page

### 🌐 Tech Stack

* **Next.js (App Router)**
* **React + Hooks**
* **shadcn/ui**
* **Tailwind CSS**
* **Zod (for API validation)**
* **Drizzle ORM**
* **SQLite** (local development)
* **Turso** (production)
* **Vercel** (deployment)

---

## Project Structure (inside this app)

```
apps/simon/
  ├─ app/
  │   ├─ page.tsx                 ← Main game UI
  │   └─ api/
  │        └─ scores/
  │             └─ route.ts       ← High score API (GET/POST)
  ├─ db/
  │   ├─ schema.ts                ← Drizzle table schema
  │   └─ client.ts                ← DB client (Turso / SQLite)
  ├─ public/                      ← Static assets (if needed)
  ├─ README.md                    ← You are here
  └─ package.json
```

---

## API Specification

### **GET `/api/scores`**

Returns the top high scores.

**Response example**

* `[{ id, name, score, createdAt }, ...]`

### **POST `/api/scores`**

Registers a new high score.

**Payload**

* `name`: string (1–32 chars)
* `score`: integer (>= 0)

**Validation**

* Performed using Zod

---

## Local Development

### 1. Install dependencies (monorepo root)

```
pnpm install
```

### 2. Set up environment variables

Inside `apps/simon/.env.local`:

```
TURSO_DATABASE_URL=""
TURSO_AUTH_TOKEN=""
```

For local SQLite development, the URL can be replaced with a file-based libsql URL.

### 3. Run the simon app only

```
pnpm dev --filter simon
```

---

## Deployment (Vercel + Turso)

1. Create a Turso database and obtain:

   * `TURSO_DATABASE_URL`
   * `TURSO_AUTH_TOKEN`
2. Set these in the Vercel project settings
3. Deploy using Vercel (monorepo-aware)

---

## Future Enhancements (optional ideas)

* Sound effects
* Difficulty modes (speed-up / double playback)
* Shareable score page (`/score/[id]`)
* Leaderboard sorting improvements
* UI animations (panel press, failure flash)
* Responsive layout tuning

---

## License

This project is part of a public portfolio and is intended for demonstration and educational purposes.

---

# 👍 必要なら…

* **もっと技術寄りの README**
* **もっとマーケ寄り（ポートフォリオ向け）の README**
* **日本語版 README**
* **GIF アニメーション付きの README**

などにもすぐ変換できます。

どうする?
