# 🍵 Bakery Potluck

A password-protected event RSVP web app built for a private matcha-themed bakery potluck, hosted by Helen & Vicki. Guests can RSVP, sign up for potluck dishes, and vote on milk preferences — all from a single beautifully designed HTML page.

Live site: [yevicki.github.io/bakerypotluck](https://yevicki.github.io/bakerypotluck)

---

## Features

- **Password-protected entry** — only invited guests can access the page
- **RSVP form** — guests enter their name and phone number, then confirm attendance or decline
- **Change RSVP** — guests can return and update their response at any time
- **Potluck sign-up sheet** — shared live spreadsheet where guests claim what they're bringing
- **Milk preferences poll** — helps hosts stock the right milk options (including Lactaid!)
- **RSVP deadline** — prominently displayed on the invite page
- **Phone number auto-formatting** — input formats to `(xxx) - xxx - xxxx` as you type
- **Host admin dashboard** — password-protected view with RSVP counts, potluck list, poll results, and CSV export
- **Supabase backend** — all data is stored in a real PostgreSQL database so every guest sees live, shared data

---

## Tech Stack

| Layer | Tool |
|---|---|
| Frontend | Vanilla HTML, CSS, JavaScript |
| Database | [Supabase](https://supabase.com) (PostgreSQL) |
| Hosting | GitHub Pages |
| Fonts | Cormorant Garamond, DM Sans (Google Fonts) |

No build tools, no frameworks, no npm — just one `index.html` file.

---

## Database Schema

Three tables in Supabase, each keyed by phone number (one entry per guest):

```sql
rsvps       — name, phone, rsvp ('yes'|'no'), submitted_at
potluck     — name, phone, item, submitted_at
milk_poll   — name, phone, preference, submitted_at
```

Upserts on `phone` mean guests can update their responses without creating duplicates.

---

## Local Development

No build step needed. Just open the file:

```bash
open index.html
```

To connect to Supabase, set your credentials at the top of the `<script>` block in `index.html`:

```js
const SUPABASE_URL = 'https://your-project.supabase.co';
const SUPABASE_KEY = 'your-anon-public-key';
```

---

## Deployment

This site is deployed via **GitHub Pages** from the `main` branch. Any push to `main` automatically updates the live site within ~60 seconds.

```bash
git add index.html
git commit -m "your message"
git push
```

---

## Project Structure

```
bakerypotluck/
└── index.html    # Entire app — all pages, styles, and logic in one file
└── README.md
```

---

## Pages

| Page | Description |
|---|---|
| Lock screen | Password entry for guests |
| Invite + RSVP | Event details and RSVP form |
| Yes — You're going! | Event logistics, potluck sheet, milk poll |
| No — Declined | Decline confirmation with option to change RSVP |
| Admin lock | Password entry for hosts |
| Admin dashboard | Live data tables, stats, and CSV export |

---

*Built with love (and a lot of matcha) for a one-time private event. 🌿*
