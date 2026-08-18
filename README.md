# Church Voice — Scripture Recording Platform

A platform for recording, managing, and listening to scripture audio narration — upload a manuscript, record verse-by-verse in a dedicated studio, and publish a Spotify-style listening experience with active-verse highlighting and auto-advance.

## Screenshots

**Public site**

| Home | Library | Book detail |
|---|---|---|
| ![Landing page](screenshots/readme/01-home.png) | ![Library — books with completion %](screenshots/readme/02-library.png) | ![Book detail — chapters and verse counts](screenshots/readme/03-book-detail.png) |

**Reader**

| Light | Playing | Dark |
|---|---|---|
| ![Reader, light theme](screenshots/readme/04-reader-light.png) | ![Reader with the bottom player active](screenshots/readme/05-reader-playing.png) | ![Reader, dark theme, active verse highlighting](screenshots/readme/06-reader-dark.png) |

**Admin**

| Login | Dashboard | Management |
|---|---|---|
| ![Admin login](screenshots/readme/07-login.png) | ![Admin dashboard — books/chapters/verses/recordings totals](screenshots/readme/08-admin-dashboard.png) | ![Management — content list](screenshots/readme/09-management.png) |

| Analytics | Upload | Recording Studio |
|---|---|---|
| ![Analytics — listening stats](screenshots/readme/10-analytics.png) | ![Upload a manuscript](screenshots/readme/11-upload.png) | ![Scripture Studio — verse-by-verse recording deck](screenshots/readme/12-recording-studio.png) |

**Mobile**

| Home | Library | Reader |
|---|---|---|
| ![Mobile home](screenshots/readme/13-mobile-home.png) | ![Mobile library](screenshots/readme/14-mobile-library.png) | ![Mobile reader](screenshots/readme/15-mobile-reader.png) |

## How it works

- **Upload** — drag & drop a PDF or EPUB manuscript; the app parses it into books, chapters, and verses
- **Record** — the Scripture Studio steps through a chapter verse by verse, with a live waveform, a verse timeline, and a per-chapter completion blueprint
- **Publish** — the Reader shows recorded verses as playable with active-verse highlighting and auto-advance to the next recorded verse
- **Listen** — a persistent bottom player (play/pause, seek, skip, speed control) follows across pages
- **Admin** — a single-admin dashboard tracks books/chapters/verses/recordings totals, per-book completion, and listening analytics

## Tech Stack

- **Frontend:** Next.js 16 (App Router), React 19, Tailwind CSS 4, Framer Motion, Recharts, epub.js / pdf.js for manuscript parsing
- **Backend:** Supabase (Postgres, Auth) — no separate API server
- **Auth:** Single-admin login (env-configured credentials, session cookie)
- **Storage:** Audio recordings in Supabase; see `frontend/scripts/schema.sql` for the schema

## Quick Start (Development)

### Prerequisites

- Node.js 20+
- A Supabase project (Postgres + connection string)

### Setup

```bash
cd frontend
cp .env.example .env.local   # fill in Supabase URL/keys, admin email+password, session secret
npm install
npm run dev                  # starts on port 3000
```

Open [http://localhost:3000](http://localhost:3000).

## Project Structure

```
frontend/
  src/app/            Pages: home, library, book/[id], reader/[bookId]/[chapterId],
                       login, admin, management, analytics, upload, recording
  src/components/      UI and shared components
  src/lib/supabase/    Supabase client
  src/lib/auth/        Single-admin session auth
  scripts/             DB migration + schema
screenshots/           README screenshots
```

## License

Fork of [SudipThandar/Church-Voice-app](https://github.com/SudipThandar/Church-Voice-app).
