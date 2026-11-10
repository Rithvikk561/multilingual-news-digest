# 📰 MND — Multilingual News Digest

> **MND (Multilingual News Digest)** is an Indian news aggregation platform delivering real-time, curated stories from trusted national sources. Every article is enriched with concise AI summaries, bullet-point highlights, text-to-speech audio narration, and translation across 12 Indian regional languages. Users can track daily reading streaks, bookmark stories for offline reading, share news effortlessly, and submit direct feedback.

[![Next.js](https://img.shields.io/badge/Next.js-16.3.3-black?logo=next.js)](https://nextjs.org/)
[![React](https://img.shields.io/badge/React-19-blue?logo=react)](https://react.dev/)
[![Neon Database](https://img.shields.io/badge/Neon-PostgreSQL-00e599?logo=postgresql)](https://neon.tech/)
[![Drizzle ORM](https://img.shields.io/badge/Drizzle-ORM-C5F74F)](https://orm.drizzle.team/)
[![NextAuth.js](https://img.shields.io/badge/NextAuth.js-v5_beta-purple)](https://authjs.dev/)
[![Vercel Deployment](https://img.shields.io/badge/Vercel-Deployed-success?logo=vercel)](https://multilingual-news-digest1-aqjw.vercel.app)

---

## 🚀 How to Access & Explore the Project

### Live Web Application
* **Production URL:** [https://multilingual-news-digest1-aqjw.vercel.app](https://multilingual-news-digest1-aqjw.vercel.app)

---

### What to Look For Inside the App (Quick Tour)

1. **Header & Dateline Bar (Top):**
   * **Date & Edition:** Displays today's localized Indian dateline.
   * **State & Region Filter:** Select specific Indian states (e.g. *Maharashtra, Karnataka, Tamil Nadu, Delhi*) or view *All India*.
   * **12-Language Selector:** Switch instantly between English and 11 regional Indian languages (*Hindi, Bengali, Telugu, Marathi, Tamil, Urdu, Gujarati, Kannada, Odia, Malayalam, Punjabi*).
   * **Top Share Button:** Share the entire newspaper digest via your device's native share sheet or one-click clipboard copy.

2. **Category Navigation:**
   * Explore news organized across: **Politics**, **Business**, **Technology**, **Sports**, **Education**, and **Entertainment**.
   * Features deep-linking (e.g. `#category-technology`) with smooth auto-scroll.

3. **Interactive News Cards:**
   * **Lead Story Feature:** The top story of each section is prominently highlighted with an editorial badge.
   * **Quick AI Summary & Bullet Highlights:** Read key takeaways directly on the card without clicking away.
   * **Audio Reader (Listen):** Click the speaker button to hear the headline and summary read aloud in your selected language.
   * **Bookmark (Save):** Save stories to your account with instant optimistic state changes.
   * **Share Button:** Share specific articles via native OS share sheet or instant link copying.
   * **In-Website Full Reader:** Click any story or *"Read Story →"* to view the complete article context inside a distraction-free modal without external redirects.

4. **Account & Daily Reading Streaks:**
   * Click **Sign In / Create Account** to register with email and password.
   * **Daily Reading Streaks:** Reading news each day increases your login streak (`🔥 Day X Streak`). Consecutive days build streaks, calculated cleanly in Indian Standard Time (IST).
   * **My Account Slide-in Drawer:** View your profile details, member date, current streak, all-time best streak, and your full library of saved bookmarks.

5. **Feedback Drawer:**
   * Click **Feedback** in the header or footer to submit thoughts, bug reports, or category suggestions. Submissions are durably stored in Neon PostgreSQL and routed via Resend email.

---

## ✨ Features Overview

### 1. News Aggregation & AI Processing
* **Multi-Source RSS Pipeline:** Continuously ingests and normalizes news feeds from trusted Indian publications (*The Hindu, Indian Express, NDTV, Times of India, etc.*).
* **Automated Categorization:** Classifies articles accurately into standard news desks.
* **Instant Summaries & Highlights:** Extracts main bullet points for quick skimming.
* **Smart Image Fallback:** Filters broken, placeholder, or low-resolution thumbnail images, replacing them with clean editorial placeholders.
* **Date Switcher & Archive:** View today's feed or step back in time (*Yesterday, 2 Days Ago, 3 Days Ago, Past Week, or Custom Date*).
* **Headline Search Filter:** Real-time client-side search filtering across all loaded headlines.

### 2. Regional Languages & Accessibility
* **12 Indian Regional Languages Supported:**
  * English (`en`), Hindi (`hi`), Bengali (`bn`), Telugu (`te`), Marathi (`mr`), Tamil (`ta`), Urdu (`ur`), Gujarati (`gu`), Kannada (`kn`), Odia (`or`), Malayalam (`ml`), Punjabi (`pa`).
* **Complete UI Localization:** Every button, tab, date, badge, and modal message is translated natively.
* **Client Translation Cache:** Caches on-demand article translations to prevent duplicate API calls.
* **Text-to-Speech (TTS) Engine:** Built-in audio speech synthesis honoring the active regional language dialect.

### 3. User Authentication & Security
* **NextAuth v5 (Auth.js) JWT Sessions:** Fast, stateless, rolling JWT session cookies with 30-day expiration.
* **Encrypted Passwords:** Passwords salted and hashed with `bcryptjs` (12 rounds).
* **Brute-Force & Rate Limiting:** Server-side rate limiting on registration endpoints to prevent credential stuffing.
* **Clear User Feedback:** Prominent in-modal and floating on-screen success popups confirming account creation and sign-in.

### 4. Reading Streaks & Saved Articles
* **IST-Synchronized Daily Streaks:** Automatically tracks daily reading habits in Indian Standard Time (`UTC+5:30`), supporting same-day idempotency, consecutive increments, and grace periods.
* **Canonical URL Normalization:** Uses deterministic 32-character SHA-256 hashes that strip tracking parameters (`utm_*`, `gclid`, `fbclid`, etc.) to guarantee bookmark integrity across sources.
* **Saved Articles Drawer:** Slide-in management panel to review and remove bookmarked articles with optimistic UI response.

### 5. Sharing & Deep Linking
* **Multi-Level Share Buttons:** Embedded on every single news card, the in-modal reader, category headers, and saved bookmarks.
* **Web Share API with Clipboard Fallback:** Launches the mobile OS share drawer on mobile devices, or copies direct article links to clipboard with animated `"Link copied!"` toasts.

### 6. User Feedback System
* **Persist-First Architecture:** Submissions are saved securely to the database before email dispatch.
* **Resend Email Integration:** Automated background delivery to administration inboxes with exponential backoff retries.
* **Spam & Flooding Protection:** Rate-limited to 3 submissions per IP per hour, with 10-minute content deduplication.

---

## 🛠️ Tech Stack

| Layer | Technology |
| :--- | :--- |
| **Framework** | [Next.js 16.3.3](https://nextjs.org/) (App Router & Turbopack) |
| **UI Library** | [React 19](https://react.dev/) |
| **Database** | [Neon](https://neon.tech/) Serverless PostgreSQL |
| **ORM** | [Drizzle ORM](https://orm.drizzle.team/) & Drizzle Kit |
| **Authentication** | [NextAuth.js v5](https://authjs.dev/) (Auth.js beta) |
| **Password Security** | `bcryptjs` (12 salt rounds) |
| **Email Delivery** | [Resend](https://resend.com/) API SDK |
| **RSS Ingestion** | `rss-parser` & `sanitize-html` |
| **Styling** | Custom Editorial CSS with CSS Variables (Responsive, Mobile-First) |
| **Hosting & CI/CD** | [Vercel](https://vercel.com/) |

---

## 💻 Local Development Setup

### 1. Clone the repository
```bash
git clone https://github.com/Rithvikk561/multilingual-news-digest.git
cd multilingual-news-digest
```

### 2. Install dependencies
```bash
npm install
```

### 3. Configure Environment Variables
Create a `.env.local` file in the root directory:
```env
AUTH_SECRET=your-random-auth-secret
NEXTAUTH_SECRET=your-random-auth-secret
AUTH_TRUST_HOST=true
DATABASE_URL=postgresql://user:password@your-neon-host.neon.tech/neondb?sslmode=require
RESEND_API_KEY=re_your_api_key
RESEND_FROM_EMAIL="onboarding@resend.dev"
FEEDBACK_TO_EMAIL=your-email@example.com
```

### 4. Push Database Schema (Neon)
```bash
npm run db:generate
npm run db:migrate
```

### 5. Run Development Server
```bash
npm run dev
```
Open **[http://localhost:3000](http://localhost:3000)** in your browser.

---

## 🧪 Testing & Quality Assurance

MND includes a comprehensive automated test suite covering unit logic, route handlers, and integration workflows:

```bash
# Run all unit tests and feedback suite
npm test

# Run isolated unit tests
npm run test:unit

# Run route handler API tests
npm run test:routes

# Run production build check
npm run build
```

* **97 Unit & Integration Tests Passing** (covers URL canonicalization, streak algorithms, authentication validators, and mock route responses).
* **Feedback Suite:** Verifies deduplication windows, rate limiting, and atomic worker backoff.

---

## 📂 Project Directory Structure

```text
multilingual-news-digest/
├── app/
│   ├── api/
│   │   ├── auth/[...nextauth]/route.js   # NextAuth session handlers
│   │   ├── feedback/route.js              # User feedback submission API
│   │   ├── news/route.js                  # Multi-category RSS aggregation
│   │   ├── summarize/route.js             # AI headline & bullet summarization
│   │   ├── translate/route.js             # Regional language translation endpoint
│   │   ├── tts/route.js                    # Text-to-speech audio reader API
│   │   └── user/
│   │       ├── profile/route.js           # User account profile stats
│   │       ├── register/route.js          # User account registration with rate limit
│   │       ├── saved/route.js             # Saved bookmarks list & creation
│   │       └── streak/route.js            # IST-based streak calculation
│   ├── globals.css                        # Newspaper editorial design system
│   ├── layout.js                          # Root HTML layout with providers
│   ├── page.js                            # Main newspaper feed view
│   └── providers.js                       # NextAuth session provider wrapper
├── components/
│   ├── ArticleReaderModal.js              # In-site full reader with audio & share
│   ├── AuthModal.js                       # Sign In & Registration dialog
│   ├── CategoryNav.js                     # News desk category navigation bar
│   ├── CategorySection.js                 # Category grid container with lead story
│   ├── DateSwitcher.js                    # Archive dateline switcher & search bar
│   ├── FeedbackModal.js                   # Feedback form with instant status
│   ├── Footer.js                          # Editorial footer & quick links
│   ├── Header.js                          # Masthead, state selector, & language menu
│   ├── NewsCard.js                        # Individual story card with audio & bookmark
│   ├── ProfilePanel.js                    # User profile, streak badges, & bookmarks
│   ├── ShareButton.js                     # Universal Web Share & clipboard button
│   └── StreakPopup.js                     # Animated streak milestone notifications
├── lib/
│   ├── articleId.js                       # 32-hex canonical URL identification
│   ├── auth.js                            # NextAuth v5 configuration & credentials
│   ├── db.js                              # Neon Serverless PostgreSQL connection
│   ├── fetchNews.js                       # RSS fetching & client cache manager
│   ├── languages.js                       # 12 Indian regional language configs
│   ├── schema.js                          # Drizzle ORM PostgreSQL schema
│   ├── streakLogic.js                     # Pure IST-based streak calculations
│   └── translations.js                    # UI localization dictionary
└── scripts/
    └── retry-feedback-email.js            # Resend email retry worker
```

---

## 📄 License
This project is open-source and available under the [MIT License](LICENSE).
