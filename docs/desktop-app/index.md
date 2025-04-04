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
