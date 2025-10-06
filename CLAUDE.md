# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a Vue 3 frontend application built with TypeScript and Vite for a dating website with ML-powered photo recommendations. It's a single-page application (SPA) that connects to a FastAPI backend.

### Backend API

**Base URL**: `https://ml_api.gaga5lala.dev`

**Key Endpoints**:
- `POST /register` - User registration (username: 3+ chars, password: 6+ chars)
- `POST /login` - User authentication
- `GET /users/{username}/recommendations` - Get 10 personalized photo recommendations
- `GET /photos/{photo_id}` - Fetch photo binary content
- `POST /swipe` - Record user swipe actions (like/dislike)
- `POST /users/{username}/embeddings` - Add user embedding
- `GET /users/{username}/embeddings` - Retrieve user embeddings
- `GET /users/{username}/avg_embedding` - Get user's average embedding
- `POST /users/{username}/search` - Search embeddings
- `POST /admin/rebuild_index` - Rebuild FAISS index (admin)
- `GET /admin/index_status` - Get FAISS index status (admin)

**Technology**: The backend uses FastAPI with FAISS (Facebook AI Similarity Search) for ML-powered photo recommendations based on user preferences and embeddings.

## Development Commands

### Install dependencies
```sh
npm install
```

### Development server
```sh
npm run dev
```
Starts Vite dev server with hot module replacement (HMR).

### Production build
```sh
npm run build
```
Runs type checking (`vue-tsc --build`) and production build (`vite build`) in parallel using `npm-run-all2`.

### Type checking only
```sh
npm run type-check
```
Runs `vue-tsc --build` to check TypeScript types across the project.

### Preview production build
```sh
npm run preview
```
Serves the production build locally for testing.

### Linting
```sh
npm run lint
```
Runs ESLint with `--fix` flag to automatically fix issues.

### Code formatting
```sh
npm run format
```
Formats code in `src/` using Prettier.

## Architecture

### Build System
- **Vite**: Modern build tool providing fast HMR and optimized production builds
- **Vue 3**: Composition API-based SPA framework
- **TypeScript**: Strict type checking with `vue-tsc` for `.vue` files

### Project Structure
- `src/main.ts`: Application entry point that creates and mounts the Vue app
- `src/App.vue`: Root component
- `src/components/`: Vue components directory
- `src/assets/`: Static assets (CSS, images, etc.)

### Path Aliases
- `@` resolves to `./src` (configured in `vite.config.ts:14-16`)

### TypeScript Configuration
Uses composite TypeScript projects:
- `tsconfig.json`: Root config referencing `tsconfig.node.json` and `tsconfig.app.json`
- Separate configs for application code and build tooling

### Code Quality
- **ESLint**: Vue 3 + TypeScript recommended rules with Prettier integration
- **Prettier**: Configured with:
  - No semicolons (`semi: false`)
  - Single quotes (`singleQuote: true`)
  - 100 character line width (`printWidth: 100`)

### Node Version Requirements
Node.js `^20.19.0` or `>=22.12.0` (specified in `package.json:6-8`)

## Development Notes

- IDE: VS Code with Vue (Official) extension (Volar) recommended
- Browser DevTools: Vue.js devtools extension recommended for debugging
- Type support for `.vue` imports requires Volar extension
- Vue DevTools plugin is enabled in development via `vite-plugin-vue-devtools`
