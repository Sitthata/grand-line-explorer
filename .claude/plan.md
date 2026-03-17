# Grand Line Explorer - Project Plan

## Overview

**Project Name:** grand-line-explorer
**Purpose:** An integrated workshop project demonstrating client-server architecture. Students receive a complete Next.js frontend and must implement Express.js API endpoints to make it functional.
**Theme:** One Piece
**Operations:** CRD (Create, Read, Delete) — no Update

---

## Tech Stack

| Layer    | Technology                        | Port |
| -------- | --------------------------------- | ---- |
| Frontend | Next.js + shadcn/ui               | 3000 |
| Backend  | Express.js (no ORM, raw SQL + pg) | 8080 |
| Database | PostgreSQL                        | 5432 |

---

## Color Theme (One Piece Series)

| Name               | Hex       | Usage                          |
| ------------------ | --------- | ------------------------------ |
| Waterfall          | `#60BFF5` | Accents, links, hover states   |
| Azure Blue (Xona)  | `#2E63A4` | Primary buttons, headers       |
| Dark Bronze        | `#AF6528` | Card borders, warm accents     |
| Dark Yellow        | `#FFCE00` | Highlights, badges, bounties   |
| Glossy Red         | `#D70000` | Delete buttons, danger states  |
| African Turquoise  | `#000000` | Text, backgrounds              |

---

## Branching Strategy

| Branch    | Content                                                        |
| --------- | -------------------------------------------------------------- |
| `main`    | Complete working application (all endpoints implemented)       |
| `student` | Full frontend + Express boilerplate (empty routes, pool setup) |

---

## Database Schema

### Table: `islands`

```sql
CREATE TABLE islands (
  id SERIAL PRIMARY KEY,
  name VARCHAR(100) NOT NULL,
  description TEXT,
  image_url TEXT,
  sea VARCHAR(50) NOT NULL
);
```

### Table: `characters`

```sql
CREATE TABLE characters (
  id SERIAL PRIMARY KEY,
  name VARCHAR(100) NOT NULL,
  bounty VARCHAR(50),
  role VARCHAR(100),
  image_url TEXT,
  island_id INTEGER REFERENCES islands(id) ON DELETE CASCADE,
  devil_fruit VARCHAR(100),
  description TEXT
);
```

---

## Seed Data

### Islands (6 total)

| id | name              | sea        | description                                                                                      |
| -- | ----------------- | ---------- | ------------------------------------------------------------------------------------------------ |
| 1  | Marineford        | Grand Line | The Marine Headquarters, site of the legendary Summit War where Whitebeard made his last stand.   |
| 2  | Enies Lobby       | Grand Line | The Judicial Island of the World Government, where the Straw Hats declared war to save Robin.     |
| 3  | Whole Cake Island  | New World  | Big Mom's territory and the centerpiece of Totto Land, a candy-coated island of sweets and terror. |
| 4  | Dressrosa         | New World  | The kingdom of passion and toys, ruled by the tyrant Doflamingo behind a web of lies.              |
| 5  | Wano Country      | New World  | The isolated samurai nation under Kaido's iron rule, steeped in tradition and sorrow.              |
| 6  | Alabasta          | Grand Line | A desert kingdom nearly torn apart by civil war, saved by the Straw Hats and Princess Vivi.       |

### Characters (18 total — 3 per island)

#### Marineford (island_id: 1)

| name      | bounty          | role                    | devil_fruit               | description                                                  |
| --------- | --------------- | ----------------------- | ------------------------- | ------------------------------------------------------------ |
| Ace       | 550,000,000     | 2nd Division Commander  | Mera Mera no Mi (Flame)   | Luffy's sworn brother who gave his life at Marineford.       |
| Whitebeard| 5,046,000,000   | Captain                 | Gura Gura no Mi (Quake)   | The Strongest Man in the World, died standing in Marineford. |
| Sengoku   | None            | Fleet Admiral           | Hito Hito no Mi, Model: Daibutsu | The Buddha of the Marines who orchestrated the Summit War.   |

#### Enies Lobby (island_id: 2)

| name      | bounty          | role                    | devil_fruit               | description                                                  |
| --------- | --------------- | ----------------------- | ------------------------- | ------------------------------------------------------------ |
| Luffy     | 3,000,000,000   | Captain                 | Gomu Gomu no Mi (Rubber)  | The future Pirate King who stormed Enies Lobby for his crew. |
| Rob Lucci | None            | CP9 Assassin            | Neko Neko no Mi, Model: Leopard | The strongest CP9 agent, defeated by Luffy in Enies Lobby.   |
| Spandam   | None            | CP9 Chief               | None                      | The cowardly chief of CP9 who tried to sacrifice Robin.      |

#### Whole Cake Island (island_id: 3)

| name      | bounty          | role                    | devil_fruit               | description                                                  |
| --------- | --------------- | ----------------------- | ------------------------- | ------------------------------------------------------------ |
| Big Mom   | 4,388,000,000   | Captain (Yonko)         | Soru Soru no Mi (Soul)    | One of the Four Emperors, ruler of Totto Land.               |
| Katakuri  | 1,057,000,000   | Sweet Commander         | Mochi Mochi no Mi (Mochi) | Big Mom's strongest son, a man of honor and mochi.           |
| Sanji     | 1,032,000,000   | Cook                    | None                      | The Straw Hat cook whose past was revealed on Whole Cake.    |

#### Dressrosa (island_id: 4)

| name        | bounty          | role                    | devil_fruit               | description                                                  |
| ----------- | --------------- | ----------------------- | ------------------------- | ------------------------------------------------------------ |
| Doflamingo  | 340,000,000     | King / Warlord          | Ito Ito no Mi (String)    | The Heavenly Demon who enslaved Dressrosa with strings.      |
| Law         | 3,000,000,000   | Captain / Surgeon       | Ope Ope no Mi (Op-Op)     | The Surgeon of Death who allied with Luffy to take down Doffy.|
| Rebecca     | None            | Gladiator / Princess    | None                      | The undefeated gladiator princess of Dressrosa.              |

#### Wano Country (island_id: 5)

| name      | bounty          | role                    | devil_fruit               | description                                                  |
| --------- | --------------- | ----------------------- | ------------------------- | ------------------------------------------------------------ |
| Kaido     | 4,611,100,000   | Captain (Yonko)         | Uo Uo no Mi, Model: Seiryu | The King of Beasts, the strongest creature in the world.     |
| Zoro      | 1,111,000,000   | Swordsman               | None                      | The Straw Hat swordsman who inherited Oden's will in Wano.   |
| Kin'emon  | None            | Samurai / Retainer      | Fuku Fuku no Mi (Garment) | The leader of the Nine Red Scabbards, loyal to Oden.         |

#### Alabasta (island_id: 6)

| name      | bounty          | role                    | devil_fruit               | description                                                  |
| --------- | --------------- | ----------------------- | ------------------------- | ------------------------------------------------------------ |
| Crocodile | 1,965,000,000   | Warlord / Captain       | Suna Suna no Mi (Sand)    | The desert king who nearly destroyed Alabasta from within.   |
| Vivi      | None            | Princess                | None                      | The brave princess who infiltrated Baroque Works to save her kingdom. |
| Robin     | 930,000,000     | Archaeologist           | Hana Hana no Mi (Flower)  | The Devil Child who joined the Straw Hats after Alabasta.    |

### Image Strategy

#### Character Images — Jikan API (MyAnimeList CDN)

Character images are sourced from the **Jikan API** (`https://api.jikan.moe/v4`), which serves MyAnimeList CDN images.

**How it works:**
1. During seed script execution, we query the Jikan API for each character
2. The API returns a CDN URL like: `https://cdn.myanimelist.net/images/characters/9/310307.jpg`
3. These URLs are stored directly in the `characters.image_url` column

**Seed script approach:**
- `server/db/seed.js` — A Node.js script (not raw SQL) that:
  1. Fetches each character's image URL from Jikan API: `GET https://api.jikan.moe/v4/characters?q={name}&limit=1`
  2. Extracts `data[0].images.jpg.image_url` from the response
  3. Inserts the character row with the fetched image URL
  4. Includes a 400ms delay between API calls to respect Jikan's rate limit (3 req/sec)
  5. Falls back to placeholder if API fails: `https://placehold.co/400x600?text={name}`

**Jikan API Character Search Reference:**
```
GET https://api.jikan.moe/v4/characters?q=Portgas+Ace&limit=1

Response:
{
  "data": [{
    "mal_id": 603,
    "name": "Ace, Portgas D.",
    "images": {
      "jpg": {
        "image_url": "https://cdn.myanimelist.net/images/characters/2/72220.jpg"
      }
    }
  }]
}
```

**Search queries for each character** (optimized for best match):

| Character   | Jikan Search Query         |
| ----------- | -------------------------- |
| Ace         | `Portgas D. Ace`           |
| Whitebeard  | `Edward Newgate`           |
| Sengoku     | `Sengoku One Piece`        |
| Luffy       | `Monkey D. Luffy`          |
| Rob Lucci   | `Rob Lucci`                |
| Spandam     | `Spandam`                  |
| Big Mom     | `Charlotte Linlin`         |
| Katakuri    | `Charlotte Katakuri`       |
| Sanji       | `Vinsmoke Sanji`           |
| Doflamingo  | `Donquixote Doflamingo`    |
| Law         | `Trafalgar Law`            |
| Rebecca     | `Rebecca One Piece`        |
| Kaido       | `Kaido One Piece`          |
| Zoro        | `Roronoa Zoro`             |
| Kin'emon    | `Kin'emon`                 |
| Crocodile   | `Crocodile One Piece`      |
| Vivi        | `Nefertari Vivi`           |
| Robin       | `Nico Robin`               |

#### Island Images — Local Assets

Island images are stored locally in the frontend since there is no reliable API for One Piece locations.

**Location:** `client/public/images/islands/`

**Files:**
```
client/public/images/islands/
├── marineford.jpg
├── enies-lobby.jpg
├── whole-cake-island.jpg
├── dressrosa.jpg
├── wano-country.jpg
└── alabasta.jpg
```

**Referenced in seed data as:** `/images/islands/{filename}`
(Next.js serves files from `public/` at the root path)

**Source:** Images will be sourced during implementation from publicly available One Piece fan art or screenshots. If suitable images cannot be found, AI-generated or stylized placeholder images will be used.

#### Student-Created Characters — Placeholder

When students add new characters via POST, the form defaults the image URL to:
```
https://placehold.co/400x600?text={Character+Name}
```

---

## API Endpoints (Student Must Implement)

All endpoints are prefixed with `/api`.

### 1. GET `/api/islands`

**Description:** Retrieve all islands.

**Response:**
```json
{
  "data": [
    {
      "id": 1,
      "name": "Marineford",
      "description": "The Marine Headquarters...",
      "image_url": "https://...",
      "sea": "Grand Line"
    }
  ]
}
```

**SQL Hint:**
```sql
SELECT * FROM islands ORDER BY id;
```

---

### 2. GET `/api/islands/:id/characters`

**Description:** Retrieve all characters associated with a specific island.

**Response:**
```json
{
  "data": {
    "island": {
      "id": 1,
      "name": "Marineford",
      "description": "...",
      "image_url": "...",
      "sea": "Grand Line"
    },
    "characters": [
      {
        "id": 1,
        "name": "Ace",
        "bounty": "550,000,000",
        "role": "2nd Division Commander",
        "image_url": "...",
        "island_id": 1,
        "devil_fruit": "Mera Mera no Mi (Flame)",
        "description": "Luffy's sworn brother..."
      }
    ]
  }
}
```

**SQL Hint:**
```sql
SELECT * FROM islands WHERE id = $1;
SELECT * FROM characters WHERE island_id = $1 ORDER BY id;
```

---

### 3. GET `/api/characters`

**Description:** Retrieve all characters.

**Response:**
```json
{
  "data": [
    {
      "id": 1,
      "name": "Ace",
      "bounty": "550,000,000",
      "role": "2nd Division Commander",
      "image_url": "...",
      "island_id": 1,
      "devil_fruit": "Mera Mera no Mi (Flame)",
      "description": "Luffy's sworn brother...",
      "island_name": "Marineford"
    }
  ]
}
```

**SQL Hint:**
```sql
SELECT characters.*, islands.name AS island_name
FROM characters
LEFT JOIN islands ON characters.island_id = islands.id
ORDER BY characters.id;
```

---

### 4. POST `/api/characters`

**Description:** Add a new character.

**Request Body:**
```json
{
  "name": "Nami",
  "bounty": "366,000,000",
  "role": "Navigator",
  "image_url": "https://placehold.co/400x600?text=Nami",
  "island_id": 2,
  "devil_fruit": "None",
  "description": "The Straw Hat navigator."
}
```

**Response (201 Created):**
```json
{
  "data": {
    "id": 19,
    "name": "Nami",
    "bounty": "366,000,000",
    "role": "Navigator",
    "image_url": "https://placehold.co/400x600?text=Nami",
    "island_id": 2,
    "devil_fruit": "None",
    "description": "The Straw Hat navigator."
  }
}
```

**SQL Hint:**
```sql
INSERT INTO characters (name, bounty, role, image_url, island_id, devil_fruit, description)
VALUES ($1, $2, $3, $4, $5, $6, $7)
RETURNING *;
```

---

### 5. DELETE `/api/characters/:id`

**Description:** Delete a character by ID.

**Response (200 OK):**
```json
{
  "data": {
    "message": "Character deleted successfully"
  }
}
```

**Error Response (404):**
```json
{
  "error": "Character not found"
}
```

**SQL Hint:**
```sql
DELETE FROM characters WHERE id = $1 RETURNING *;
```

---

## Frontend Pages

### Page 1: All Islands (`/`)

**Route:** `/`
**Description:** Landing page displaying all islands as cards in a grid layout.

**Components:**
- `IslandCard` — Displays island image, name, sea badge, and short description
- Click on a card navigates to `/islands/[id]`

**Behavior:**
- Fetches `GET /api/islands` on mount
- Displays a grid of island cards (responsive: 1 col mobile, 2 col tablet, 3 col desktop)
- Each card shows the island image as a background/cover, the island name, sea as a colored badge, and a truncated description
- Loading skeleton while data is being fetched

**Design Notes:**
- Header with "Grand Line Explorer" title and One Piece themed navigation
- Sea badges use color coding: Grand Line = Azure Blue (`#2E63A4`), New World = Glossy Red (`#D70000`)
- Cards have Dark Bronze (`#AF6528`) border on hover
- Background: subtle wave pattern or dark theme with `#000000`

---

### Page 2: Island Characters (`/islands/[id]`)

**Route:** `/islands/[id]`
**Description:** Shows island details and its associated characters.

**Components:**
- `IslandHeader` — Large hero section with island image, name, sea, and full description
- `CharacterCard` — Card for each character showing name, bounty, role, devil fruit
- Back button to return to `/`

**Behavior:**
- Fetches `GET /api/islands/:id/characters` on mount
- Displays island info at top as a hero/banner
- Below: grid of character cards
- Each character card shows: image, name, role badge, bounty (formatted with Dark Yellow `#FFCE00`), devil fruit info
- Delete button on each character card (Glossy Red `#D70000`)
- Delete triggers `window.confirm()` dialog, then calls `DELETE /api/characters/:id`
- After delete, revalidate the character list (no redirect)

**Design Notes:**
- Bounty displayed in gold/yellow with berry symbol
- Devil fruit shown as a pill/badge
- "No devil fruit" characters show "None" in muted text

---

### Page 3: All Characters (`/characters`)

**Route:** `/characters`
**Description:** Lists all characters across all islands with an "Add Character" form.

**Components:**
- `CharacterTable` or `CharacterGrid` — All characters displayed with their island name
- `AddCharacterForm` — Form dialog/modal to add a new character
- Delete button on each character

**Behavior:**
- Fetches `GET /api/characters` on mount
- Displays all characters in a grid or table
- "Add Character" button opens a shadcn Dialog/Sheet with form:
  - `name` (text input, required)
  - `bounty` (text input)
  - `role` (text input)
  - `island_id` (dropdown select — fetches from `GET /api/islands`)
  - `devil_fruit` (text input)
  - `description` (textarea)
  - `image_url` (text input, defaults to placeholder)
- Submit calls `POST /api/characters`, then revalidates the list
- Delete button on each character with `window.confirm()`, calls `DELETE /api/characters/:id`
- After delete, revalidate the list

**Design Notes:**
- Each character card/row shows island name as a link to that island's page
- Add button uses Azure Blue (`#2E63A4`)
- Form dialog has One Piece styling

---

## Navigation

| Label       | Route          | Description         |
| ----------- | -------------- | ------------------- |
| Islands     | `/`            | All islands grid    |
| Characters  | `/characters`  | All characters list |

- Fixed top navbar with "Grand Line Explorer" branding
- Navigation links styled with Waterfall (`#60BFF5`) on hover

---

## Project Structure

```
grand-line-explorer/
├── docker-compose.yml
├── package.json                  # Root scripts (dev, setup)
├── client/                       # Next.js frontend
│   ├── package.json
│   ├── next.config.js
│   ├── tailwind.config.ts
│   ├── components.json           # shadcn config
│   ├── public/
│   │   └── images/
│   │       └── islands/          # Local island images (6 files)
│   ├── src/
│   │   ├── app/
│   │   │   ├── layout.tsx        # Root layout with navbar
│   │   │   ├── page.tsx          # All Islands page
│   │   │   ├── globals.css       # One Piece theme colors
│   │   │   ├── islands/
│   │   │   │   └── [id]/
│   │   │   │       └── page.tsx  # Island Characters page
│   │   │   └── characters/
│   │   │       └── page.tsx      # All Characters page
│   │   ├── components/
│   │   │   ├── ui/               # shadcn components
│   │   │   ├── navbar.tsx
│   │   │   ├── island-card.tsx
│   │   │   ├── character-card.tsx
│   │   │   └── add-character-form.tsx
│   │   └── lib/
│   │       ├── api.ts            # API fetch helpers
│   │       └── utils.ts          # shadcn utils
├── server/                       # Express.js backend
│   ├── package.json
│   ├── index.js                  # Entry point (app.listen, middleware)
│   ├── db/
│   │   ├── pool.js               # pg Pool config
│   │   ├── init.sql              # CREATE TABLE statements
│   │   └── seed.js               # Seed script (fetches images from Jikan API)
│   └── routes/
│       ├── islands.js            # Island routes (student implements)
│       └── characters.js         # Character routes (student implements)
```

---

## Docker Compose Services

| Service  | Image         | Port Mapping | Notes                     |
| -------- | ------------- | ------------ | ------------------------- |
| db       | postgres:16   | 5432:5432    | Volume for persistence    |
| server   | node:20       | 8080:8080    | Express dev with nodemon  |
| client   | node:20       | 3000:3000    | Next.js dev server        |

---

## Root package.json Scripts

| Script       | Description                                |
| ------------ | ------------------------------------------ |
| `dev`        | Runs docker-compose up (all 3 services)    |
| `dev:client` | Runs only the client locally               |
| `dev:server` | Runs only the server locally               |
| `db:init`    | Runs init.sql against the database         |
| `db:seed`    | Runs seed.js (fetches Jikan images + inserts data) |
| `db:reset`   | Drops and recreates tables, then seeds             |

---

## Student Branch (`student`) Differences

The `student` branch contains:

1. **Full frontend** — Complete, working Next.js app (no modifications needed)
2. **Express boilerplate** — Server with:
   - `index.js` — Express app with CORS, JSON middleware, `app.listen(8080)`
   - `db/pool.js` — pg Pool configured and exported
   - `db/init.sql` — Full table creation SQL
   - `db/seed.js` — Full seed script (fetches character images from Jikan API)
   - `routes/islands.js` — Empty router exported (no route handlers)
   - `routes/characters.js` — Empty router exported (no route handlers)
3. **Working docker-compose** — Database starts and seeds automatically
4. **README with instructions** — API endpoint specs the student must implement

Students must implement the 5 endpoints in the route files to make the frontend work.

---

## Error Handling Convention

All endpoints should follow this pattern:

**Success:**
```json
{ "data": ... }
```

**Error:**
```json
{ "error": "Error message here" }
```

Status codes: `200` (success), `201` (created), `404` (not found), `500` (server error)

---

## CORS Configuration

```js
app.use(cors({
  origin: 'http://localhost:3000',
  methods: ['GET', 'POST', 'DELETE'],
}));
```
