# 42 Cluster Lens 🛰️🗺️

Welcome to **42 Cluster Lens** — an alternative interactive cluster map for 42 campuses. It makes the map feel alive, useful, and reliable: it loads fast, shows relevant info, and helps you navigate in real time.

> If the official “Intra” map doesn’t load or doesn’t show what you need — **Cluster Lens** has your back and gives you more.

---

## 🚀 What it is and why it matters

**42 Cluster Lens** is a visual cluster map that:

- helps you **quickly see where seats are free**;
- provides **live statistics about people and promos**;
- stays reliable even when the official map is slow or unavailable;
- makes on-campus navigation easier and more pleasant;
- surfaces key data **without bouncing through dozens of pages**.

The project was created to solve everyday student pain points:
- “Where are free seats right now?”
- “Why is the official map not loading?”
- “Why is the official map not zooming?”
- “How can I instantly see the cluster load?”
- “Who can check me, and who might need my check?”

---

## 🧠 Why statistics are a key feature

Statistics in **Cluster Lens** are not just “occupied vs free.” They help you understand **who is around and how you can help each other**:

- you can see **how many people are from each promo** — which matters because new promo students often have check limitations;
- you immediately know **who can check you** and **who might need your check**;
- you can spot **more experienced students (older promos / higher levels)** and quickly identify who to ask for advice or help;
- all of this is visible **right on the map**, without extra navigation or waiting.

That’s why statistics are one of the most valuable and “alive” features of the project.

---

## 🧩 Core features

- **Interactive map** of 42 clusters
- **Promo and level statistics** + visual highlighting
- **Overlay module**: quick view of a student’s level and status (Common Core completed / not yet)
- **Full mobile support**: zooming and navigation that work smoothly on phones
- **Fast load times and stable performance**
- Clean UI without clutter

---

## ⚔️ How we differ from the official 42 (Intra) map

| Feature | Official map | 42 Cluster Lens |
|--------|-------------------|-----------------|
| Load speed & stability | Sometimes unavailable | Stable and fast ✅ |
| Promo/level statistics | No | Yes ✅ |
| Quick “who can check” overview | No | Yes ✅ |
| Level/status on the map | No | Yes (overlay) ✅ |
| Mobile usability (zoom) | Often awkward | Fully supported ✅ |
| Number of page hops | Many | Minimal ✅ |
| Pleasant UI | Basic | More lively and friendly ✅ |

**In short:** the official map is the “minimum.” **Cluster Lens** is the map you actually want to use every day.

---

## 🎯 Who it’s for

- 42 students looking for free seats;
- anyone who wants to quickly find people to check with or talk to;
- mentors and staff who need fast orientation;
- anyone who wants a stable and friendly tool.

---
## 🏗️ Architecture & flow

This repo is **full‑stack**: a static front‑end + a Cloudflare Worker back‑end.

```
User (browser)
   │
   ├──> Frontend (Vercel) ──┐
   │                        │
   └──> Worker (Cloudflare) ├──> 42 API (OAuth + data)
                            └──> KV Cache (seatmap + sessions)
```

### Frontend (apps/web)
- Static HTML/CSS/JS pages (`index.html`, `cluster.html`, `profile.html`).
- Calls the Worker for OAuth, session validation, cluster data, and user overlays.
- Deployed on **Vercel** with clean URLs support. 

### Backend (apps/worker)
- Cloudflare Worker handling OAuth, session storage, and data aggregation.
- Uses **KV** to cache seatmaps, sessions, and user data to reduce 42 API load.
- Includes background seatmap refresh with cooldowns for rate limits.
- Exposes endpoints: `/login`, `/callback`, `/session`, `/cluster`, `/user` and debug helpers. 

---

## 📦 Repository structure

```
apps/
  web/      # Frontend (static pages + JS/CSS)
  worker/   # Cloudflare Worker backend
```

---

## 🚀 Deployment model (Vercel + Cloudflare)

- **Frontend**: Vercel serves static pages and is already configured for clean URLs. 
- **Backend**: Cloudflare Worker + KV (Wrangler config in `apps/worker`).

Both platforms support **automatic deployments** when connected to a Git repo (Vercel Git integration + Cloudflare Wrangler CI). This repo is laid out to make that split‑deploy workflow straightforward. 

---

## 🔐 OAuth & privacy

- Login happens on 42’s side via OAuth.
- No passwords are stored.
- The Worker only stores short‑lived session tokens in KV.

---

## 🤝 Contributions are welcome

We’re always happy to see new ideas and new contributors!

**Want to help?** Awesome — you can:
- improve UI/UX;
- add new features (filters, statuses, color schemes);
- optimize performance;
- fix bugs and polish details.

Just fork the project, make your changes, and open a PR — **every contribution matters**. 🚀

---

## 🌟 Future ideas

- highlighting “almost free” clusters;
- saved favorite seats;

If you like the idea — a star ⭐ and participation help the project grow.

---

**42 Cluster Lens** — a map that works when you need it and shows what matters. Welcome! 🫡
