# Screen Macro

Automates repetitive click tasks in a desktop game using template matching. Runs as a Windows desktop app — no Python installation required.

---

## Requirements

- Windows 10 or 11 (64-bit)
- The game running in **true fullscreen mode** at your monitor's native resolution

---

## Initial installation

1. Go to the [Releases](https://github.com/robruijter1/Screen-Macro/releases) page and download the latest `GameBot.zip`.
2. Extract the zip to any folder (e.g. `C:\GameBot`).
3. Run **GameBot.exe**.

**Windows SmartScreen warning**
Because the executable is not code-signed you will likely see a SmartScreen prompt on first launch. Click **More info → Run anyway** to proceed.

**Admin prompt**
The app requests administrator rights on launch — this is required for input automation to work reliably in games. Click **Yes** when Windows asks.

---

## Updating

The app checks for updates automatically when it starts. If a new version is available a dialog will appear with a link to the releases page.

**To apply an update:**

1. Open the [Releases](https://github.com/robruijter1/Screen-Macro/releases) page (or click the link in the update dialog).
2. Download the new `GameBot.zip`.
3. Extract the zip **into your existing GameBot folder**, overwriting the files when prompted.

Your configs, scenarios and templates are stored in a `configs/` subfolder and in `scenarios.json` / `screens.json` next to the exe. These files are **not** included in the release zip, so they will not be touched by the overwrite.

> If a new version changes the internal structure of `scenarios.json` or `screens.json`, the app migrates your data automatically the first time it starts after the update. No manual steps are needed.

---

## First-time setup

After launching the app for the first time:

1. Open the **Screen Editor** tab to define the screens your bot needs to navigate.
   - Add your game's screens, capture marker images, and draw action regions.
   - It is strongly recommended to do this while the game is running in **true fullscreen** at your monitor's native resolution. This gives the sharpest templates and the most reliable matching.
2. Open the **Scenario Editor** tab to create the automation sequences you want to run.
3. Go to the **Configs** tab and click **Save current** to save your setup as a named config (useful for backups or sharing).
4. Switch to the **Bot** tab and click **Start** to run.
