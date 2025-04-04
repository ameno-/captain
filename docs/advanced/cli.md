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
