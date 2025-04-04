# Technical Architecture

This page provides a high-level overview of Cap's technical stack and structure.

## Monorepo Structure

Cap is developed as a monorepo using `pnpm` workspaces and `turborepo` for build orchestration.

*   **`apps/`:** Contains the runnable applications (Desktop, Web, CLI, Services).
*   **`crates/`:** Contains core Rust libraries shared across Rust-based applications (Desktop backend, CLI).
*   **`packages/`:** Contains shared TypeScript/JavaScript libraries used across web frontends and potentially backend services.

## Core Technologies

*   **Backend (Desktop & CLI):** [Rust](https://www.rust-lang.org/)
    *   **Desktop Framework:** [Tauri](https://tauri.app/) (Rust backend + Webview frontend)
    *   **Async Runtime:** [Tokio](https://tokio.rs/)
    *   **Media Processing:** [FFmpeg](https://ffmpeg.org/) (via `ffmpeg-next-rs`), [cpal](https://github.com/RustAudio/cpal) (audio I/O), [Scap](https://github.com/CapSoftware/scap) / [SCKit](https://github.com/CapSoftware/screencapturekit-rs) (screen capture), [Nokhwa](https://github.com/l1npengcz/nokhwa) (camera).
    *   **Rendering/GPU:** [WGPU](https://wgpu.rs/) (for video compositing/editing effects, pixel conversions).
*   **Frontend (Desktop):** [SolidJS](https://www.solidjs.com/) with [SolidStart](https://start.solidjs.com/), [TypeScript](https://www.typescriptlang.org/), [Tailwind CSS](https://tailwindcss.com/). UI components via `@kobalte/core`.
*   **Frontend (Web Platform):** [Next.js](https://nextjs.org/), [React](https://reactjs.org/), [TypeScript](https://www.typescriptlang.org/), [Tailwind CSS](https://tailwindcss.com/). UI components via `@radix-ui`.
*   **Database:** MySQL-compatible (PlanetScale used in dev env), accessed via [Drizzle ORM](https://orm.drizzle.team/).
*   **API:** Defined using [`@ts-rest/core`](https://ts-rest.com/) for end-to-end type safety (`packages/web-api-contract/`). Hono might be used for some API routes in the Next.js app.
*   **Authentication:** [NextAuth.js](https://next-auth.js.org/) (handling Google, Email, WorkOS).
*   **Infrastructure (Potentially):** [SST](https://sst.dev/) defined in `infra/` (might be for deploying auxiliary services like the Discord bot or managing AWS resources). Uses Pulumi providers for Vercel/GitHub.

## Key Rust Crates (`crates/`)

*   **`media`:** Central hub for media pipelines, encoding (H264, Opus), muxing (MP4, Ogg), platform-specific capture interfaces.
*   **`recording`:** Orchestrates different recording modes (Studio vs. Instant), managing pipelines and file output.
*   **`rendering`:** Handles compositing video layers (screen, camera, cursor, background) using WGPU shaders.
*   **`editor`:** Contains the logic for video editing operations (likely interacts heavily with `rendering` and `media`).
*   **`video-decode`:** Provides an abstraction layer over video decoding backends (FFmpeg, AVAssetReader on macOS).
*   **`project`:** Defines the structure and configuration (`ProjectConfiguration`) for a Cap recording project.
*   **`gpu-converters`:** Likely leverages WGPU for efficient pixel format conversions (e.g., YUV to RGBA).

## Key TS/JS Packages (`packages/`)

*   **`database`:** Drizzle schema, migrations, auth adapter, email templates.
*   **`ui` / `ui-solid`:** React and SolidJS component libraries, respectively.
*   **`web-api-contract`:** Type-safe API definition shared between frontend and backend.
*   **`env`:** Centralized environment variable management and validation.
*   **`utils`:** Shared utility functions and constants (Stripe client, S3 helpers, etc.).
