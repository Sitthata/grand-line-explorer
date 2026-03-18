# Grand Line Explorer

A One Piece themed full-stack workshop project. You will implement Express.js API endpoints to power a pre-built Next.js frontend.

## Prerequisites

- [Docker](https://www.docker.com/products/docker-desktop/) installed and running
- [Git](https://git-scm.com/)

## Getting Started

### 1. Clone the repository with submodules

```bash
git clone --recurse-submodules https://github.com/Sitthata/grand-line-explorer.git
cd grand-line-explorer
```

If you already cloned without `--recurse-submodules`:

```bash
git submodule update --init --recursive
```

### 2. Start all services

```bash
npm run dev
```

This starts three Docker containers:

| Service  | URL                    |
| -------- | ---------------------- |
| Frontend | http://localhost:3000  |
| Backend  | http://localhost:3001  |
| Database | localhost:5432         |

### 3. Initialize the database

In a separate terminal, run:

```bash
npm run db:init
```

### 4. Seed the database

```bash
npm run db:seed
```

### 5. Start coding!

Open `server/routes/islands.js` and `server/routes/characters.js` — implement the API endpoints described in the [server README](https://github.com/Sitthata/grand-line-explorer-server/blob/da6114d7cc2d458f8c2f0b1c09f0f8ee227468bf/README.md).

## Available Scripts

| Script              | Description                                      |
| ------------------- | ------------------------------------------------ |
| `npm run dev`       | Start all services (frontend, backend, database) |
| `npm run dev:build` | Start all services and rebuild containers        |
| `npm run db:init`   | Create database tables                           |
| `npm run db:seed`   | Seed the database with One Piece data            |
| `npm run db:reset`  | Drop tables, recreate, and re-seed               |
| `npm run stop`      | Stop all services                                |
| `npm run clean`     | Stop all services and remove database volume     |

## Project Structure

```
grand-line-explorer/
├── client/          # Next.js frontend (DO NOT EDIT)
├── server/          # Express.js backend (YOUR WORK HERE)
│   ├── index.js     # Express app entry point
│   ├── db/
│   │   ├── pool.js  # PostgreSQL connection pool
│   │   ├── init.sql # Table definitions
│   │   └── seed.js  # Seed script
│   └── routes/
│       ├── islands.js     # Island endpoints (implement these)
│       └── characters.js  # Character endpoints (implement these)
└── docker-compose.yml
```
