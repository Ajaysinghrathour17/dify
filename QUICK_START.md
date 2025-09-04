# Quick Start Guide - "Open It"

This guide helps you quickly **open** the Dify development environment.

## Prerequisites

- Docker and Docker Compose installed
- Node.js v20+ (v22.11.0+ recommended)
- pnpm package manager
- uv package manager (for Python/API setup)

## Quick Setup

1. **Run the setup script:**
   ```bash
   ./open-dev
   ```

2. **If uv is not available, install it manually:**
   - Visit: https://github.com/astral-sh/uv
   - Follow installation instructions for your system
   - Then run: `uv sync --dev` in the `api` directory
   - Run: `uv run flask db upgrade` in the `api` directory

## Start Development Servers

After setup, start the services in separate terminals:

### 1. API Server
```bash
./dev/start-api
```
- Runs on: http://localhost:5001

### 2. Celery Worker (Background Tasks)
```bash
./dev/start-worker
```

### 3. Web Development Server
```bash
cd web && pnpm dev
```
- Runs on: http://localhost:3000

## Quick Start with Web Only

To quickly start just the web development server:
```bash
./open-dev --start-web
```

## Environment Files

The setup script automatically creates these files from examples:
- `api/.env` (API configuration)
- `web/.env` (Web configuration)
- `docker/middleware.env` (Docker services)

## Docker Services

The following middleware services are started automatically:
- PostgreSQL database
- Redis cache
- Weaviate vector database
- SSRF proxy
- Plugin daemon
- Sandbox environment

## Troubleshooting

### Node.js Version Warning
If you see a warning about Node.js version, consider upgrading to v22.11.0+ for best compatibility.

### Missing Dependencies
- Run `npm install -g pnpm` if pnpm is missing
- Install uv from https://github.com/astral-sh/uv for Python/API setup

### Port Conflicts
- Web: Change port with `PORT=3001 pnpm dev`
- API: Modify port in `dev/start-api` script

## Development Workflow

1. Use `./open-dev` to set up the environment
2. Start the services you need (web, API, worker)
3. Access the application at http://localhost:3000
4. Make changes and see them reflected automatically

For more detailed information, see `README.md` and `CLAUDE.md`.