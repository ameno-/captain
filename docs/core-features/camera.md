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
