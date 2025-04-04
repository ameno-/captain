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
