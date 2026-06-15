# Cyber Cheatsheets API

A small OpenAPI 3.0 design for a gamified cybersecurity cheatsheet platform — think *Matrix-style* revision cards for Cyber Attack, Cyber Defense, OSINT, and Networking, with XP, ranks, and badges to keep things fun.

> This repo contains the **API design only** (no backend code). It's a prototyping exercise: define the contract first, build later.

---

## Contents

| File | Description |
|---|---|
| [`openapi.yaml`](./openapi.yaml) | Full OpenAPI 3.0 specification — paths, schemas, auth |
| [`endpoints.md`](./endpoints.md) | Quick-reference table of all endpoints |

---

## Concept

**Purpose** — Let visitors browse short, AI-written cybersecurity cheatsheets, track their progress, and request new topics. The site owner manages content through admin-only endpoints.

**Main resources**

- `Fiche` — a cheatsheet (title, category, content, keywords, difficulty level, XP reward)
- `Category` — `cyber-attack` / `cyber-defense` / `osint` / `reseaux`
- `User` — anonymous profile tracking XP, rank, badges, and read fiches
- `Rank` — XP-based progression tier
- `Badge` — gamified achievement
- `FicheRequest` — a visitor's request for a new topic

**Roles & Auth**

| Role | Access | Auth |
|---|---|---|
| Visitor (anonymous) | Browse, search, validate fiches, submit requests | None |
| Admin (site owner) | Create/edit/delete fiches, manage requests | API key (`X-API-Key` header) |

---

## Gamification

**Ranks** (based on cumulative XP)

| Rank | XP required |
|---|---|
| Noob | 0 |
| Script Kiddie | 50 |
| Débutant Cyber | 150 |
| Analyste Junior | 300 |
| Pentester | 600 |
| Cyber Expert | 1000 |
| Red Team Elite | 1500 |
| Légende Matrix | 2500 |

**Badges**

| Badge | Condition |
|---|---|
| Première Connexion | Validate your first fiche |
| Network Ninja | Validate all "Réseaux" fiches |
| Red Team | Validate all "Cyber Attack" fiches |
| Blue Team | Validate all "Cyber Defense" fiches |
| OSINT Hunter | Validate all "OSINT" fiches |
| Marathonien | Validate 20 fiches total |
| Curieux | Submit your first fiche request |
| Élu·e | Reach the "Légende Matrix" rank |

---

## Endpoints at a glance

14 endpoints, full CRUD on `Fiche`, plus profile, progression, and request-handling routes. See [`endpoints.md`](./endpoints.md) for the complete table.

```
GET    /categories
GET    /fiches              (filters: category, level, search)
GET    /fiches/{ficheId}
POST   /fiches                         🔒 admin
PATCH  /fiches/{ficheId}               🔒 admin
DELETE /fiches/{ficheId}               🔒 admin
POST   /fiches/{ficheId}/validate
POST   /users
GET    /users/{userId}
GET    /ranks
GET    /badges
POST   /requests
GET    /requests                       🔒 admin
PATCH  /requests/{requestId}           🔒 admin
```

---

## Try it out

1. Open [Swagger Editor](https://editor.swagger.io)
2. Paste the contents of `openapi.yaml`
3. Use **"Try it out"** on any endpoint to see example requests/responses

---

## Status

Design complete and validated in Swagger Editor. Next step: build the real Matrix-style frontend + backend.
