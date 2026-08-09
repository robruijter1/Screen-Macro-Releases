# Screen Macro

Automates repetitive click tasks in a desktop game using template matching. Runs as a Windows desktop app — no Python installation required.

---

## Requirements

- Windows 10 or 11 (64-bit)
- **Desktop mode:** the game running in **true fullscreen mode** at your monitor's native resolution
- **Android mode:** the [LDPlayer](https://www.ldplayer.net/) Android emulator installed, with your target game installed inside it

---

## Initial installation

1. Go to the [Releases](https://github.com/robruijter1/Screen-Macro-Releases/releases) page and download the latest `ScreenMacro-vX.X.X.zip`.
2. Extract the zip to any folder (e.g. `C:\ScreenMacro`).
3. Run **ScreenMacro.exe**.

**Windows SmartScreen warning**
Because the executable is not code-signed you will likely see a SmartScreen prompt on first launch. Click **More info → Run anyway** to proceed.

**Admin prompt**
The app requests administrator rights on launch — this is required for input automation to work reliably in games. Click **Yes** when Windows asks.

---

## Updating

The app checks for updates automatically when it starts. If a new version is available a dialog will appear with a link to the releases page.

**To apply an update:**

1. Open the [Releases](https://github.com/robruijter1/Screen-Macro-Releases/releases) page (or click the link in the update dialog).
2. Download the new `ScreenMacro-vX.X.X.zip`.
3. Extract the zip **into your existing ScreenMacro folder**, overwriting the files when prompted.

Your configs, scenarios and templates are stored in a `configs/` subfolder and in `scenarios.json` / `screens.json` next to the exe. These files are **not** included in the release zip, so they will not be touched by the overwrite.

> If a new version changes the internal structure of `scenarios.json` or `screens.json`, the app migrates your data automatically the first time it starts after the update. No manual steps are needed.

---

## First-time setup

After launching the app for the first time:

1. Open the **Screen Editor** tab and add your first screen. You'll be asked to choose a target for this config:
   - **Desktop** — the game runs in a window on your physical screen. It is strongly recommended to capture screens while the game is running in **true fullscreen** at your monitor's native resolution. This gives the sharpest templates and the most reliable matching.
   - **Android** — the game runs inside an [LDPlayer](https://www.ldplayer.net/) emulator instance. A setup wizard walks you through locating your LDPlayer install, picking the instance, and selecting the installed game package. From then on, screens/templates are captured from that emulator instance instead of your physical screen, and the bot controls the game through it. This choice is per-config and can't be changed later — start a new config to switch.
   - Either way, continue adding your game's screens, capture marker images, and draw action regions.
2. Open the **Scenario Editor** tab to create the automation sequences you want to run.
3. Go to the **Configs** tab and click **Save current** to save your setup as a named config (useful for backups or sharing).
4. Switch to the **Start** tab and click **Start** to run.
