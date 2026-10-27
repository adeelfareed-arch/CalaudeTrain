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

`src/App.jsx` is the only stateful parent: it holds the `transactions` array (seeded with hardcoded data, no persistence or backend) and an `addTransaction` handler, and composes three child components:

- `Summary.jsx` — takes `transactions` and computes total income, expenses and balance itself.
- `TransactionForm.jsx` — owns the form field state; on submit it builds a transaction and calls `onAdd`.
- `TransactionList.jsx` — takes `transactions` and owns the type/category filter state and the table.

`src/categories.js` holds the shared category list used by the form and the list. Styling is plain class-based CSS in `src/App.css` and `src/index.css`.

## Conventions and gotchas

- Transaction `amount` is a **number** (seed data and `TransactionForm` convert with `Number()`); keep it numeric so the totals in `Summary` add rather than concatenate.
- Seed transaction "Freelance Work" is typed `expense` with category `salary`, likely wrong data.
