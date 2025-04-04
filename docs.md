Documentation Website Structure (docs/)
code

docs/
├── index.md                # Landing Page / Introduction
├── getting-started/
│   ├── installation.md     # Desktop app installation
│   └── first-recording.md  # Quick start tutorial
├── core-features/
│   ├── recording-modes.md  # Screen, Window, Area
│   ├── camera.md           # Camera overlay options
│   ├── audio.md            # Mic & System audio
│   ├── editing.md          # Built-in editor features
│   └── sharing.md          # Sharing via the web platform
├── desktop-app/
│   ├── index.md            # Overview, UI
│   ├── settings.md         # Configuration options
│   └── hotkeys.md          # Keyboard shortcuts
├── web-platform/
│   ├── index.md            # Overview, Dashboard
│   ├── accounts.md         # User accounts, profiles
│   ├── workspaces.md       # Collaboration features
│   ├── billing.md          # Subscription info
│   └── sharing-pages.md    # Viewing shared Caps
├── integrations/
│   ├── index.md            # Overview
│   ├── s3.md               # Self-hosted S3 config
│   └── discord.md          # Discord bot features (if any user-facing)
├── advanced/
│   ├── cli.md              # Using the command-line interface
│   └── self-hosting.md     # Guide for self-hosting the web platform
├── technical/
│   └── architecture.md     # High-level overview of the tech stack
└── contributing/
    ├── index.md            # Contribution guidelines (links to CONTRIBUTING.md)
    └── development-setup.md # Detailed local dev setup guide
Content Drafts (Markdown)
docs/index.md
markdown

# Welcome to Cap Documentation

**Cap is an open-source, privacy-focused alternative to Loom.**

It's a video messaging tool that allows you to record your screen and camera, perform basic edits, and share your recordings instantly via a web link.

## Key Features

*   **Screen & Camera Recording:** Capture your entire screen, specific windows, or select areas, optionally including your webcam.
*   **Audio Recording:** Record from your microphone and capture system audio.
*   **Simple Editing:** Trim and adjust your recordings within the desktop app.
*   **Instant Sharing:** Upload recordings automatically and get a shareable link.
*   **Web Platform:** Manage recordings, view shared content, manage workspaces, and handle billing.
*   **Cross-Platform Desktop App:** Available for macOS and Windows (Linux support TBD based on dependencies).
*   **Self-Hostable:** Option to host the web platform yourself.
*   **Integrations:** Support for custom S3-compatible storage.

## Get Started

*   **[Installation](./getting-started/installation.md):** Download and install the desktop application.
*   **[Your First Recording](./getting-started/first-recording.md):** Learn how to make and share your first Cap in minutes.
docs/getting-started/installation.md
markdown

# Installation

Download the latest version of the Cap desktop application for your operating system.

## Download Links

*   **macOS:** [Download Link for macOS `aarch64` (Apple Silicon)](/download/macos-aarch64) <!-- Typically `/download/[platform]/[arch]` -->
*   **macOS:** [Download Link for macOS `x86_64` (Intel)](/download/macos-x86_64)
*   **Windows:** [Download Link for Windows `x86_64`](/download/windows-x86_64)

*(Note: Replace `/download/...` with actual download paths or a link to a download page)*

## Installation Steps

### macOS

1.  Download the `.dmg` file.
2.  Open the `.dmg` file.
3.  Drag the `Cap.app` icon into your Applications folder.
4.  Eject the disk image.
5.  Launch Cap from your Applications folder.
6.  Grant necessary permissions (Screen Recording, Microphone, Camera) when prompted.

### Windows

1.  Download the `.msi` installer.
2.  Run the installer and follow the on-screen prompts.
3.  Launch Cap from the Start Menu or Desktop shortcut.
4.  Grant necessary permissions (Microphone, Camera) if prompted by Windows or security software.

## First Launch & Permissions

Upon first launch, Cap (or the operating system) will likely ask for permissions:

*   **Screen Recording (macOS):** Essential for capturing your screen.
*   **Microphone:** Required to record your voice.
*   **Camera:** Required to record your webcam overlay.
*   **Accessibility (macOS, optional):** May be required for specific features like detecting window titles accurately or advanced controls.

Please grant these permissions for Cap to function correctly. You can usually manage these later in your system's Privacy & Security settings.

Next Steps: [Your First Recording](./first-recording.md)
docs/getting-started/first-recording.md
markdown

# Your First Recording

Let's create and share your first Cap recording!

1.  **Launch Cap:** Open the Cap application.
2.  **Select Recording Mode:**
    *   Click the mode selection button (usually shows an icon for Screen, Window, or Area).
    *   Choose:
        *   **Screen:** Select the display you want to record.
        *   **Window:** Click on the specific application window you want to record.
        *   **Area:** Click and drag to select a custom portion of your screen.
3.  **Configure Inputs (Optional):**
    *   Use the toolbar or settings icons to toggle your **Camera** and **Microphone**.
    *   Select your desired microphone from the input device list if needed.
4.  **Start Recording:**
    *   Click the main record button (often a red circle).
    *   A countdown might appear before recording starts.
5.  **Perform Your Recording:** Demonstrate your task, explain your concept, or provide feedback.
6.  **Stop Recording:**
    *   Click the Stop button (often a square) in the recording controls overlay or use the system tray/menu bar icon.
    *   Alternatively, use the configured hotkey (check [Hotkeys](./desktop-app/hotkeys.md)).
7.  **Editing (Optional):**
    *   The recording will open in the Cap editor.
    *   Use the timeline to trim the start or end of your video. (See [Editing](./core-features/editing.md)).
8.  **Upload & Share:**
    *   Click the "Upload" or "Share" button.
    *   Cap will process and upload the video (this might happen automatically based on settings).
    *   Once uploaded, the shareable link will be copied to your clipboard automatically.
9.  **Paste the Link:** Share the link with colleagues, friends, or customers!

Congratulations! You've created and shared your first Cap. Explore the other documentation sections to learn about more advanced features.
docs/core-features/recording-modes.md
markdown

# Recording Modes

Cap offers several modes to capture exactly what you need:

## 1. Full Screen Recording

*   **What it does:** Captures everything visible on one of your connected displays.
*   **How to use:** Select the "Screen" mode, then click on the preview of the desired monitor.
*   **Best for:** Demonstrating workflows across multiple applications, showing the entire desktop context.

## 2. Window Recording

*   **What it does:** Captures the content of a single application window. Only the selected window will be recorded, even if other windows overlap it.
*   **How to use:** Select the "Window" mode, then move your mouse over different windows. Click on the window you want to capture.
*   **Best for:** Focusing on a specific application, tutorials for a single software.

## 3. Area Recording

*   **What it does:** Captures a specific, rectangular portion of your screen that you define.
*   **How to use:** Select the "Area" mode. Click and drag your mouse cursor to draw a rectangle around the region you wish to record. You can adjust the selection before starting.
*   **Best for:** Highlighting a particular part of a webpage or application, hiding irrelevant screen areas.

## Selection UI

The selection process typically involves:

*   A mode selection interface (e.g., buttons or dropdown shown in `ModeSelect.tsx`).
*   An overlay or highlighting mechanism to indicate the selected screen or window.
*   A cropping tool (`Cropper.tsx`) for defining the recording area in Area mode.
docs/core-features/camera.md
markdown

# Camera Recording

Cap allows you to include a webcam overlay in your screen recordings, making them more personal and engaging.

## Enabling the Camera

*   Before or during recording setup, toggle the camera icon in the controls.
*   If you have multiple cameras, you might be able to select the desired one (check settings).

## Camera Overlay Options

You can customize the appearance and position of your camera overlay (usually accessible via settings before recording or potentially adjustable in the editor):

*   **Position:** Choose where the camera bubble appears (e.g., bottom-right, top-left). See `CameraPosition` in `project/configuration.rs`.
*   **Shape:** Typically a circle, but square might be an option. See `rounding` in `project/configuration.rs` Camera struct.
*   **Size:** Adjust the relative size of the camera overlay. See `size` in `project/configuration.rs` Camera struct.
*   **Mirroring:** Flip the camera horizontal (useful if text behind you appears backwards). See `mirror` in `project/configuration.rs` Camera struct.
*   **Hide:** You can choose to hide the camera overlay entirely. See `hide` in `project/configuration.rs` Camera struct.

*(Implementation Note: These options are likely configured via the UI and stored in the `ProjectConfiguration` defined in `/crates/project/`)*
docs/core-features/audio.md
markdown

# Audio Recording

Capture your voice and system sounds alongside your screen recording.

## Microphone Recording

*   **Enable/Disable:** Use the microphone toggle in the recording controls.
*   **Device Selection:** If you have multiple microphones connected (e.g., built-in, external USB mic, headset), you can select your preferred input device from a dropdown list in the settings or near the microphone toggle.
*   **Audio Levels:** A visual meter might show your microphone input level, helping you ensure you're not too quiet or too loud.
*   **Audio Processing:** Settings might include options to "Improve" audio, potentially involving noise suppression or level adjustments (See `AudioConfiguration` in `project/configuration.rs`).

*(Implementation Note: Relies on the `cpal` crate and potentially custom processing in `/crates/audio/` and `/crates/media/`)*

## System Audio Recording (macOS & Windows)

*   **What it does:** Captures the sound output from your computer (e.g., application sounds, video playback audio).
*   **Enable/Disable:** This is usually a separate toggle in the recording setup or settings, often labeled "System Audio" or "Computer Sound".
*   **Use Cases:** Recording presentations with audio, capturing sound from videos or games you are demonstrating.
*   **Exclusion:** By default, Cap attempts to exclude its own audio to prevent feedback loops.

*(Implementation Note: System audio capture is platform-specific, likely handled within `/crates/media/src/platform/` and `/crates/media/src/sources/system_audio.rs` using platform APIs or libraries like `cpal`'s loopback features where available.)*
docs/core-features/editing.md
markdown

# Editing Recordings

Cap includes a basic editor to refine your recordings before sharing.

*(Based on the `apps/desktop/src/routes/editor/` directory structure)*

## Timeline Interface

After stopping a recording, it usually opens in the editor view. The core of the editor is the timeline:

*   **Visual Representation:** Shows video and potentially audio waveforms.
*   **Playhead:** A marker indicating the current playback position. Click or drag to navigate.
*   **Playback Controls:** Play, pause, and potentially skip controls.

## Trimming

*   **Handles:** Drag the handles at the beginning and end of the timeline clips to trim unwanted sections from the start or end of your recording.
*   **Precision:** Zoom controls might be available for more precise trimming.

## Aspect Ratio & Background

*   **Presets:** Apply different aspect ratios (Wide, Vertical, Square, etc.) (See `AspectRatioSelect.tsx`).
*   **Background Customization:** Modify the background behind your recording, especially if the aspect ratio has changed (See `ConfigSidebar.tsx`, `ShadowSettings.tsx`). Options likely include:
    *   Colors
    *   Gradients
    *   Images (including desktop wallpapers)
    *   Padding and Rounding
    *   Shadow effects

## Camera Adjustments (Post-Recording)

*   You might be able to reposition or resize the camera overlay after recording within the editor.

## Exporting

*   Once you're satisfied with your edits, you can proceed to export or share the final video. The editor likely includes an "Export" or "Share" button leading to the upload process or saving locally (`ExportDialog.tsx`).

*(Implementation Note: Core editing logic resides in `/crates/editor/` and `/crates/rendering/`, with the UI in `apps/desktop/src/routes/editor/`)*
docs/core-features/sharing.md
markdown

# Sharing Caps

Once your recording is ready (and potentially edited), sharing it is simple.

## Upload Process

*   Clicking "Share" or "Upload" in the editor or from the recording list typically triggers the upload process.
*   Recordings are uploaded to the configured storage backend (Cap's default cloud storage or your self-hosted S3-compatible bucket).
*   The upload progress might be shown in the app.

*(Implementation Note: Upload logic is handled in `apps/desktop/src-tauri/src/upload.rs` and interacts with API routes in `apps/web/app/api/upload/`)*

## Shareable Links

*   **Automatic Copying:** Once the upload is complete, a unique shareable link is automatically generated and copied to your clipboard.
*   **Link Format:** Links typically point to the Cap web platform (e.g., `https://cap.so/s/[videoId]`) or your custom domain if configured.
*   **Accessing Links Later:** You can find the links to your uploaded recordings in the desktop app's recording list or on your dashboard on the web platform.

## Viewing Shared Caps

*   Anyone with the link can view the recording on the Cap web platform.
*   The viewing page (`apps/web/app/s/[videoId]/page.tsx`) includes:
    *   Video playback.
    *   Metadata (title, creator).
    *   Comment section.
    *   Activity/Transcript tabs (if features are enabled).
*   Access control (e.g., public vs. workspace-only) might be configurable via workspace settings.

## Sharing within Workspaces

*   Caps created within a workspace might be automatically accessible to other members of that workspace via the dashboard.
*   You can explicitly share Caps to specific workspaces.
docs/desktop-app/index.md
markdown

# Desktop Application

The Cap desktop application is the primary tool for recording and editing.

## Overview

*   **Technology:** Built with [Tauri](https://tauri.app/), using a Rust backend for core logic and performance, and a web-based frontend for the user interface.
*   **Frontend:** Uses the [SolidJS](https://www.solidjs.com/) framework for a reactive and performant UI. UI components are likely built using `@kobalte/core` (referenced in `packages/ui-solid/`).
*   **Platforms:** Officially supports macOS (Intel & Apple Silicon) and Windows (`x86_64`).
*   **Key Areas:**
    *   **Recording Setup:** Select mode, inputs, start/stop controls.
    *   **In-Progress Overlay:** Minimal controls shown while recording is active.
    *   **Editor:** Post-recording trimming and customization.
    *   **Recording List/Library:** View past recordings, manage uploads, get share links.
    *   **Settings:** Configure application behavior, hotkeys, integrations, account, etc.

## Main Interface Windows

Cap utilizes several windows:

*   **Main Window/Dashboard:** Likely where you manage recordings and settings when not actively recording.
*   **Mode Selection:** A dedicated, possibly borderless window for choosing the recording mode (`mode-select.tsx`).
*   **Capture Area Selection:** An overlay for drawing the recording region (`capture-area.tsx`, `Cropper.tsx`).
*   **In-Progress Controls:** A small overlay with stop/pause buttons visible during recording (`in-progress-recording.tsx`).
*   **Editor Window:** Opens after a recording is stopped for editing.
*   **Camera Preview (Optional):** A separate window to preview the camera feed (`camera.tsx`).

*(Implementation Note: Window management is handled in Tauri (`src-tauri/src/windows.rs`, `tauri.conf.json`). The UI for these windows is in `apps/desktop/src/routes/`)*
docs/desktop-app/settings.md
markdown

# Desktop App Settings

Configure Cap to suit your workflow. Access settings via the main application window (often through a gear icon or menu).

*(Based on `apps/desktop/src/routes/(window-chrome)/settings/`)*

## General

*   **Launch on Startup:** Automatically start Cap when your computer boots.
*   **Appearance:** Theme selection (Light/Dark), potentially accent colors.
*   **Notifications:** Configure which events trigger desktop notifications.
*   **Updates:** Check for updates automatically.

## Account & Licensing

*   Sign in/out of your Cap account.
*   View current plan (Free/Pro).
*   Manage subscription (usually links to the web platform).
*   Activate commercial licenses (if applicable).

## Recordings

*   **Save Location:** Choose where local recording files are stored before upload.
*   **Default Quality/FPS:** Set default recording parameters.
*   **Auto-Upload:** Automatically upload recordings after stopping.
*   **Auto-Copy Link:** Automatically copy the share link after upload.

## Screenshots

*   Configure screenshot behavior (if Cap supports standalone screenshots).
*   Set default save location or auto-upload options.

## Hotkeys

*   Customize keyboard shortcuts for starting, stopping, and pausing recordings. (See [Hotkeys](./hotkeys.md)).

## Integrations

*   Configure integrations like custom S3 storage. (See [Integrations](../integrations/index.md)).

## Feedback & Changelog

*   Links to provide feedback or view the application's version history.
docs/desktop-app/hotkeys.md
markdown

# Hotkeys

Configure keyboard shortcuts to quickly control Cap recordings. Access hotkey settings within the application's Settings menu.

## Default Hotkeys

*(Note: List default hotkeys here if known, otherwise provide examples)*

*   **Start/Stop Recording:** e.g., `Cmd+Shift+C` (macOS) / `Ctrl+Shift+C` (Windows)
*   **Pause/Resume Recording:** e.g., `Cmd+Shift+P` / `Ctrl+Shift+P`
*   **Cancel Recording:** e.g., `Esc` (during countdown or setup)

## Customization

*   You can typically reassign these shortcuts to key combinations that work best for you.
*   Be mindful of conflicts with other application or system-wide shortcuts.

*(Implementation Note: Hotkey registration and handling are managed in the Tauri backend (`src-tauri/src/hotkeys.rs`).)*
docs/web-platform/index.md
markdown

# Web Platform (cap.so)

The Cap web platform is where you manage your account, view recordings, collaborate, and handle billing.

## Overview

*   **Technology:** Built with [Next.js](https://nextjs.org/) and [React](https://reactjs.org/).
*   **Access:** Visit [https://cap.so](https://cap.so) (or your self-hosted domain).
*   **Authentication:** Log in via Google, Email Magic Link, or potentially SSO (WorkOS integration detected).

## Dashboard

The main hub after logging in (`/dashboard`):

*   **Your Recordings:** A list or grid view of recordings you've created.
    *   View thumbnails (`VideoThumbnail.tsx`).
    *   Access sharing links.
    *   Delete recordings (`CapCardActions.tsx`).
    *   View basic analytics (view counts) (`CapCardAnalytics.tsx`).
*   **Shared With You:** Recordings shared with you or your workspace (`/shared-caps`).
*   **Navigation:** Links to Settings, Workspaces, Billing, etc. (`AdminNavbar/`).

## Key Sections

*   **Sharing Pages (`/s/[videoId]`):** Public or private pages to view individual recordings. Includes playback, comments, transcripts, and activity logs.
*   **Settings (`/dashboard/settings`):** Manage your user profile, workspace settings, billing, and integrations.
*   **Workspaces (`/dashboard/settings/workspace`):** Invite members, manage roles, configure workspace settings like allowed domains or custom domains.
*   **Billing (`/dashboard/settings` -> Billing):** Manage your subscription plan (Free/Pro), view usage quotas.
docs/integrations/index.md
markdown

# Integrations

Connect Cap with other services.

*   **[S3-Compatible Storage](./s3.md):** Configure Cap to upload recordings to your own S3 bucket (e.g., AWS S3, Cloudflare R2, MinIO) instead of Cap's default storage.
*   **[Discord](./discord.md):** (Details needed - likely notifications for new recordings, comments, or potentially slash commands).
*   **SSO (WorkOS):** Configure Single Sign-On for workspaces via WorkOS (Managed via Web Platform Workspace Settings).
docs/integrations/s3.md
markdown

# Custom S3 Storage

Configure the Cap desktop app to upload recordings directly to your own S3-compatible storage bucket. This is useful for compliance, data residency, or cost management.

## Configuration

Access the S3 configuration in the **Desktop App Settings > Integrations** section.

You will need to provide:

1.  **Provider:** Select your S3 provider (e.g., AWS S3, Cloudflare R2, Other).
2.  **Bucket Name:** The name of your S3 bucket.
3.  **Region:** The AWS region your bucket is located in (e.g., `us-east-1`).
4.  **Endpoint (Optional):** Required for S3-compatible services other than AWS S3 (e.g., `https://<accountid>.r2.cloudflarestorage.com` for R2, or your MinIO endpoint). Leave blank for standard AWS S3.
5.  **Access Key ID:** Your S3 access key ID.
6.  **Secret Access Key:** Your S3 secret access key.

## Permissions Required

Ensure the provided Access Key has the necessary permissions on your bucket:

*   `s3:PutObject`: To upload video files, thumbnails, metadata.
*   `s3:GetObject`: Potentially needed for verification or listing (though primarily PutObject is essential for upload).
*   `s3:ListBucket` (Optional but recommended for testing): Allows the "Test Connection" feature to verify bucket access.
*   `s3:DeleteObject` (Optional): If Cap supports deleting self-hosted recordings from the app.

**It is highly recommended to create a dedicated IAM user or API token with *only* the necessary permissions scoped to the specific bucket.**

## Testing

Use the "Test Connection" button in the settings to verify Cap can access your bucket with the provided credentials.

## Guides

*   [Configuring with AWS S3](./s3/aws-s3.mdx) *(Placeholder - Link to specific guide)*
*   [Configuring with Cloudflare R2](./s3/cloudflare-r2.mdx) *(Placeholder - Link to specific guide)*

*(Implementation Note: Configuration UI is in `s3-config.tsx`. Tauri backend handles saving and using these credentials in `upload.rs` and potentially `s3.ts`/`s3.rs` helpers.)*
docs/advanced/cli.md
markdown

# Command-Line Interface (CLI)

Cap includes a basic command-line interface (`apps/cli`) for scriptable recording.

**(Note: The CLI's capabilities are limited based on the current code (`main.rs`, `record.rs`). This section assumes basic recording functionality.)**

## Installation / Usage

The CLI is typically bundled with the main application or might require separate compilation.

*(Instructions unclear from repo structure - needs clarification. Assume it's either included or needs `cargo run -p cap-cli` from the repo.)*

## Basic Recording

```bash
# Example command (syntax is hypothetical)
cap-cli record --output my_recording.mp4 --mode screen --screen-id 0
cap-cli record --output my_app.mp4 --mode window --window-id 12345
Available Commands/Options
(This needs to be derived from the actual CLI implementation in src/main.rs and src/record.rs. Look for argument parsing logic, e.g., using clap.)


record: Start a recording.
--output <path>: Specify the output file path.
--mode <screen|window|area>: Set the recording mode.
--screen-id <id>: ID of the screen to record.
--window-id <id>: ID of the window to record.
--area <x,y,w,h>: Coordinates and dimensions for area recording.
--no-audio / --no-camera: Disable inputs.
--fps <rate>: Set the frame rate.

Listing Targets (Hypothetical)
bash

cap-cli list screens
cap-cli list windows
Check the CLI's help output (cap-cli --help) for actual commands and options.

code


### `docs/advanced/self-hosting.md`

```markdown
# Self-Hosting Guide

Cap's web platform (`apps/web`) can be self-hosted, giving you full control over your data and infrastructure.

**(Note: This is a high-level guide based on the repository structure. Detailed steps require examining deployment configurations or specific documentation if available.)**

## Prerequisites

*   **Server Environment:** A server or platform capable of running Node.js applications (e.g., Docker, VPS, PaaS like Vercel/Netlify - though Vercel seems implied by infra).
*   **Database:** A MySQL-compatible database (PlanetScale is used in development, but any MySQL 8+ should work).
*   **S3-Compatible Storage:** An S3 bucket (AWS S3, Cloudflare R2, MinIO) for storing video recordings, transcriptions, etc.
*   **Email Service:** An email provider configured for sending magic links, notifications, etc. (Resend is used in the codebase).
*   **Environment Variables:** Proper configuration of all required server and public environment variables (see `.env.example` and `packages/env/`).

## Key Components to Host

1.  **Next.js Web Application (`apps/web`):** This is the main user interface and API backend.
2.  **Database:** Your chosen MySQL database.
3.  **S3 Storage:** Your chosen S3-compatible storage.
4.  **(Optional) `apps/tasks` Service:** This backend service seems responsible for background processing (e.g., merging audio). It needs to be hosted and accessible by the main web application if its functionality is required. It appears to be an Express app, potentially run in Docker.

## General Steps

1.  **Clone the Repository:** Get the Cap codebase.
2.  **Configure Environment Variables:** Create a `.env` file (or use your hosting provider's environment variable system) based on `.env.example`. Key variables include:
    *   `DATABASE_URL` / `DATABASE_MIGRATION_URL`
    *   `NEXTAUTH_SECRET`, `NEXTAUTH_URL`
    *   `CAP_AWS_ACCESS_KEY`, `CAP_AWS_SECRET_KEY`, `NEXT_PUBLIC_CAP_AWS_BUCKET`, `NEXT_PUBLIC_CAP_AWS_REGION`, `NEXT_PUBLIC_CAP_AWS_ENDPOINT` (if needed)
    *   `RESEND_API_KEY` (or other email provider config)
    *   Potentially keys for Google Auth, WorkOS, Stripe, Deepgram, etc., if using those features.
    *   `NEXT_PUBLIC_WEB_URL` (set to your self-hosted domain).
3.  **Set up Database:**
    *   Create your MySQL database.
    *   Run database migrations using `pnpm db:push` (ensure `DATABASE_MIGRATION_URL` points to your write-access DB URL if different from the read URL).
4.  **Build the Application:**
    *   Run `pnpm install`.
    *   Run `pnpm build --filter=@cap/web`. If `apps/tasks` is needed, build it too (`pnpm build --filter=@cap/tasks`).
5.  **Deploy:**
    *   **Web App:** Deploy the `apps/web/.next` directory using a Node.js hosting provider or containerize it.
    *   **Tasks App (if needed):** Deploy the `apps/tasks` service, potentially as a Docker container using the provided `Dockerfile`. Ensure it's configured to be reachable by the web app.
6.  **Configure DNS:** Point your chosen domain to your hosted web application.
7.  **Configure Desktop App (Users):** Users wishing to use your self-hosted instance will need to configure the "Server URL" in their desktop app's settings to point to your domain instead of `cap.so`.

**(Disclaimer: This is a simplified overview. Self-hosting may require significant technical expertise depending on your chosen infrastructure.)**
docs/technical/architecture.md
markdown

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
docs/contributing/index.md
markdown

# Contributing to Cap

Thank you for your interest in contributing to Cap! As an open-source project, we welcome contributions from the community.

## Ways to Contribute

*   **Report Bugs:** If you find a crash, error, or unexpected behavior, please [file a bug report](https://github.com/CapSoftware/cap/issues/new?template=bug_report.md) on GitHub. Include steps to reproduce and details about your system.
*   **Suggest Features:** Have an idea for a new feature or improvement? Join our [Discord Server](https://discord.com/invite/y8gdQ3WRN3) (link from `CONTRIBUTING.md`) to discuss it with the community and developers.
*   **Submit Pull Requests:** If you'd like to contribute code, please follow the setup guide and development workflow.

## Development Workflow

1.  **Fork & Clone:** Fork the repository on GitHub and clone your fork locally.
2.  **Setup:** Follow the [Development Setup Guide](./development-setup.md).
3.  **Branch:** Create a new branch for your feature or bug fix (`git checkout -b my-feature`).
4.  **Code:** Make your changes. Ensure code is formatted (`cargo fmt`, `pnpm format`) and passes checks (`cargo clippy`, `pnpm lint`, `pnpm typecheck`).
5.  **Test:** Add tests for new functionality and ensure existing tests pass.
6.  **Commit:** Commit your changes with clear messages.
7.  **Push:** Push your branch to your fork (`git push origin my-feature`).
8.  **Pull Request:** Open a Pull Request against the `main` branch of the `CapSoftware/cap` repository. Describe your changes clearly.

## Code of Conduct

Please note that this project is released with a Contributor Code of Conduct. By participating in this project you agree to abide by its terms. *(Link to Code of Conduct if it exists)*

---

For detailed instructions on setting up your local development environment, see the [Development Setup Guide](./development-setup.md).
docs/contributing/development-setup.md
markdown

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


---

This structure provides a solid foundation. You'll need to fill in more specific detail