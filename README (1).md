# Wylie Pure Gold Band — Website

**Wylie High School Band | Abilene, TX | 2026-27**
Live at: [puregoldband.org](https://www.puregoldband.org) (point your domain to Vercel after setup)

---

## Stack

| Layer      | Technology                                     |
|------------|------------------------------------------------|
| Framework  | Plain HTML5 — zero build step required         |
| Styling    | Tailwind CSS v3 via CDN                        |
| Fonts      | Google Fonts (Oswald + DM Sans)                |
| Calendar   | Google Calendar public embed iframe            |
| Forms      | JotForm App iframe embed                       |
| Hosting    | Vercel (auto-deploys from GitHub `main` branch)|

---

## One-Time Setup

### 1. GitHub Repository

1. Go to [github.com](https://github.com) and create a new repository named `puregold-band`
2. Set visibility to **Private** (recommended)
3. Upload these files to the repository root:
   - `index.html`
   - `vercel.json`
   - `README.md`

### 2. Vercel Deployment

1. Go to [vercel.com](https://vercel.com) and sign in (use "Continue with GitHub")
2. Click **Add New Project**
3. Import the `puregold-band` repository from GitHub
4. Leave all build settings at their defaults — Vercel auto-detects static HTML
5. Click **Deploy**

Vercel will give you a URL like `puregold-band.vercel.app`. Every future push to the `main` branch automatically redeploys — **no manual steps needed.**

### 3. Custom Domain (puregoldband.org)

1. In Vercel: go to your project → **Settings** → **Domains**
2. Add `puregoldband.org` and `www.puregoldband.org`
3. Vercel provides DNS records (CNAME or A record) — log into your domain registrar and add them
4. SSL certificate is provisioned automatically by Vercel — no action needed

---

## Director Maintenance Guide

### How to Update the Site

All editable content lives in the `CONFIG` object and data arrays near the top of `index.html`. You never need to touch the HTML structure.

**Method A — GitHub Web Editor (recommended, no software needed):**
1. Go to your GitHub repository
2. Click `index.html`
3. Click the pencil icon (Edit)
4. Make changes
5. Click **Commit changes** → **Commit directly to main**
6. Vercel auto-deploys in ~30 seconds

**Method B — Local editor:**
1. Edit `index.html` in VS Code or any text editor
2. Push to GitHub via GitHub Desktop or `git push origin main`

---

### Announcement Banner

Find this in `CONFIG`:

```javascript
announcement: "",
```

- **Empty string** = banner is hidden
- **Any text** = yellow banner appears at the top of every page

**Example:**
```javascript
announcement: "🏆 Area Contest this Saturday! Call time 1:30 PM. Travel uniform required.",
```

To clear it after the event, set it back to `""`.

---

### Google Calendar

The calendar is a live embed — it updates automatically whenever you add or edit events in the
**whspuregold@gmail.com** Google Calendar account. No changes to the website are needed.

To sync the calendar to a personal device or share it:
- **Subscribe (iPhone/Android/Outlook):** Click "Sync to Device Calendar" button on the site
- **Download .ics:** Click "Download .ics File" button on the site

**Calendar iCal URL:**
```
webcal://calendar.google.com/calendar/ical/whspuregold%40gmail.com/public/basic.ics
```

---

### JotForm

All forms are managed through the JotForm App:
```
https://www.jotform.com/app/213223550674148
```

To add, remove, or edit forms, log into your JotForm account. Changes reflect immediately in the embedded iframe — no website update needed.

---

### Adding Photo Albums

Find `photoSources` in `CONFIG` and add objects:

```javascript
photoSources: [
  {
    label:       "Google Photos",
    description: "Official 2026-27 season album",
    url:         "https://photos.app.goo.gl/YOUR_ALBUM_ID_HERE",
    icon:        "📸",
    cta:         "View Album"
  },
  {
    label:       "Contest Photos — Area 2026",
    description: "Area Marching Contest photos",
    url:         "https://photos.app.goo.gl/ANOTHER_ALBUM_ID",
    icon:        "🏆",
    cta:         "View Photos"
  }
]
```

Leave `url: ""` to display a "Coming Soon" placeholder until the album is ready.

---

### Updating Shop Links

Find `shopItems` in `CONFIG` and replace the `url` values:

```javascript
shopItems: [
  {
    label: "Pure Gold Fanwear",
    url:   "https://your-fanwear-store-link-here.com",
    ...
  }
]
```

---

### Updating Staff or Booster Roster

Find the `DIRECTORS` array or `BOOSTERS` array and edit names, titles, bios, or emails directly.
The page renders from these arrays automatically — no HTML editing required.

---

## Known Flags / Items to Resolve

| Flag | Status | Action |
|------|--------|--------|
| Booster roster section header mismatch (PDF said "2023-2024") | Resolved — 2026-27 names used | Verify roster is current before launch |
| Performance schedule page was blank in handbook | By design — defer to Google Calendar | Confirm calendar is public before launch |
| Google Photos album URL | Empty placeholder | Director to paste URL into `CONFIG.photoSources` |
| Fanwear store direct URL | Placeholder (points to puregoldband.org) | Replace with direct store URL when available |
| BCMF specific date | Not yet confirmed | Will appear on calendar automatically when added |

---

## File Structure

```
puregold-band/
├── index.html     ← Entire website (edit CONFIG at the top)
├── vercel.json    ← Vercel routing & security headers (do not edit)
└── README.md      ← This file
```

---

## Support

For issues with the website structure, contact the developer.
For issues with JotForm, log into jotform.com.
For issues with Google Calendar, log into the whspuregold@gmail.com Google account.
For Vercel/GitHub issues, visit vercel.com/support or github.com/support.
