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
