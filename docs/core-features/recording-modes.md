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
