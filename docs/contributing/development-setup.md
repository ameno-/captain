# Development Setup

This guide details how to set up your local environment to contribute to Cap, based on the `CONTRIBUTING.md` file and repository structure.

## Prerequisites

Ensure you have the following installed:

*   **Node.js:** Version 20 or later.
*   **Rust:** Version 1.80.0 or later (check `rustc --version`). Install via [rustup](https://rustup.rs/).
*   **pnpm:** Version 10.5.2 or later (check `pnpm --version`). Install via `corepack enable` or `npm install -g pnpm`.
*   **Docker:** Required for running the web platform locally with its database and S3 dependencies. [Docker Desktop](https://www.docker.com/products/docker-desktop/) or [OrbStack](https://orbstack.dev/) (macOS recommended) work.
*   **Platform-Specific Build Tools:**
    *   **macOS:** Xcode Command Line Tools (`xcode-select --install`).
    *   **Windows:**
        *   Visual Studio with C++ Build Tools.
        *   LLVM/Clang.
        *   VCPKG.
        *   *(Note: `pnpm cap-setup` may not fully handle these Windows dependencies yet.)*
    *   **Linux (Ubuntu Example):** `libwebkit2gtk-4.1-dev`, `build-essential`, `curl`, `wget`, `file`, `libssl-dev`, `libayatana-appindicator3-dev`, `librsvg2-dev`, `ffmpeg`, `clang`, `pkg-config`, `libasound2-dev`, `libpipewire-0.3-dev`. (See `.github/actions/install-desktop-deps/action.yml`).

## Initial Setup

1.  **Clone the Repository:**
    ```bash
    git clone https://github.com/CapSoftware/cap.git # Or your fork
    cd cap
    ```

2.  **Configure Environment:**
    *   Copy the example environment file:
      ```bash
      cp .env.example .env
      ```
    *   **Important:** Edit the `.env` file. Follow the instructions within the file to:
        *   Set `VITE_SERVER_URL`:
            *   Use `http://localhost:3000` if running the web app locally.
            *   Use `https://cap.so` (or the production URL) if *only* running the desktop app against the live backend.
        *   Configure database and S3 URLs (if *not* using the default Docker setup for web development).
        *   Generate secrets (`NEXTAUTH_SECRET`, `DATABASE_ENCRYPTION_KEY`) if they are missing or run `pnpm env-setup`.

3.  **Install Native Dependencies:**
    *   This script downloads and sets up dependencies like FFmpeg.
    *   It also configures Cargo environment variables (`.cargo/config.toml`).
    ```bash
    pnpm cap-setup
    ```

4.  **Install Node Modules:**
    ```bash
    pnpm install
    ```

## Running Applications

### Running Everything (Desktop + Web + Docker Services)

This is the recommended way if you need to test interactions between the desktop app and the local web backend.

```bash
# On macOS/Linux:
pnpm dev

# On Windows:
pnpm dev:windows
This command will:


Start Docker containers for MySQL and MinIO (local S3).

Run turbo run dev, which starts both the desktop app and the web app in development mode.

Running Only the Desktop App
If you only need to work on the desktop app and intend to use the live cap.so backend:


Ensure VITE_SERVER_URL=https://cap.so (or the correct production URL) is set in .env.

Run:
bash

pnpm dev:desktop


macOS Permissions: When running from a terminal (like Terminal.app or iTerm2), macOS will ask for permissions (Screen Recording, Mic, etc.) for the terminal application itself, not Cap - Development.app. Grant permissions to your terminal.

Running Only the Web App (with Docker Services)
If you only need to work on the cap.so website/backend:

bash

pnpm dev:web
This will start Docker (MySQL, MinIO) and the Next.js development server.

Running Only the Web App (Standalone Next.js)
If you have your own MySQL database and S3 storage configured in .env and don't need the Docker services:

bash

cd apps/web
pnpm dev
Development Tips

Database Studio: To inspect the local Docker database: pnpm db:studio

Database Migrations: Manage database schema changes with pnpm db:generate (create migration) and pnpm db:push (apply changes).

Recordings Location (Desktop Dev):
macOS: ~/Library/Application Support/so.cap.desktop.dev/recordings
Windows: %APPDATA%\so.cap.desktop.dev\recordings (or similar - check CONTRIBUTING.md for exact path)

Formatting: pnpm format

Linting: pnpm lint

Type Checking: pnpm typecheck

code
