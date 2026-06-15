# Endpoints — Cyber Cheatsheets API

| Method | Path                          | Purpose                                                  | Auth Required   |
|--------|-------------------------------|-----------------------------------------------------------|-----------------|
| GET    | /categories                   | List all categories                                        | No              |
| GET    | /fiches                        | List/search fiches (filter by category, level, keyword)   | No              |
| GET    | /fiches/{ficheId}              | Get one fiche's full content                               | No              |
| POST   | /fiches                        | Create a new fiche                                         | Admin (API key) |
| PATCH  | /fiches/{ficheId}              | Update an existing fiche                                   | Admin (API key) |
| DELETE | /fiches/{ficheId}              | Delete a fiche                                             | Admin (API key) |
| POST   | /fiches/{ficheId}/validate     | Mark a fiche as read/understood, award XP to the user      | No              |
| POST   | /users                         | Create an anonymous user profile                           | No              |
| GET    | /users/{userId}                | Get a user's profile (XP, rank, badges, fiches read)        | No              |
| GET    | /ranks                          | List all ranks and their XP thresholds                     | No              |
| GET    | /badges                         | List all available badges and their conditions             | No              |
| POST   | /requests                       | Submit a request for a new fiche topic                      | No              |
| GET    | /requests                       | List all pending fiche requests                             | Admin (API key) |
| PATCH  | /requests/{requestId}           | Update the status of a fiche request (pending → done)       | Admin (API key) |
