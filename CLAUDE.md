# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Commands

- `npm install` — install dependencies (required before first run)
- `npm run dev` — Vite dev server at http://localhost:5173
- `npm run build` — production build
- `npm run lint` — ESLint (flat config in `eslint.config.js`)
- `npm run preview` — serve the production build

There is no test runner configured.

## Architecture

Small Vite + React 19 (JavaScript, no TypeScript) single-page app. This is a course starter project (see README) that intentionally contains a bug, poor UI, and messy code, so expect rough edges.

Essentially all logic lives in `src/App.jsx`: a single component holding all state (`useState`), including the transactions list (seeded with hardcoded data, no persistence or backend), form fields, and filters. Totals and filtered lists are derived inline on each render. Styling is in `src/App.css` (plain CSS, class-based) and `src/index.css`.

## Known gotchas

- Transaction `amount` is stored as a **string** (seed data and form input alike, since `<input type="number">` yields strings), but the income/expense totals use `reduce((sum, t) => sum + t.amount, 0)`, which concatenates strings instead of adding. Convert with `Number()` when fixing or touching amounts.
- Seed transaction "Freelance Work" is typed `expense` with category `salary`, likely wrong data.
