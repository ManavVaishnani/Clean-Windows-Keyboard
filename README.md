# Clean Keyboard for Windows (Raycast Extension)

This extension allows you to lock your keyboard for cleaning purposes, similar to the macOS version.

## Features
- **Lock Keyboard**: Blocks all keyboard input globally.
- **Unlock**: Press `Ctrl + U` to unlock the keyboard.

## Requirements
- **Raycast for Windows** (Beta)
- **Node.js** (for development)
- **.NET Framework 4.x** (Pre-installed on most Windows systems)

## Setup

1.  **Install Dependencies**:
    ```bash
    npm install
    ```

2.  **Compile the Helper**:
    The extension uses a small C# utility to handle the low-level keyboard hooking. You need to compile it once.
    ```bash
    node src/native/compile.js
    ```
    *Note: This script uses the C# compiler (`csc.exe`) found in your Windows installation.*

3.  **Run the Extension**:
    ```bash
    npm run dev
    ```
    This will open Raycast and load the extension.

## How it works
- The React UI spawns a background process (`assets/KeyboardBlocker.exe`).
- This process installs a low-level keyboard hook (`WH_KEYBOARD_LL`).
- It swallows all key events, effectively locking the keyboard.
- It listens for `Ctrl + U`. When detected, it exits the process, restoring keyboard input.
