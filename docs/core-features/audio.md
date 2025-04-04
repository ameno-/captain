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
