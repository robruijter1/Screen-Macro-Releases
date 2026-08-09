# Tutorial: Your First Scenario

This walks through a small, complete example: three screens, a couple of clickable
actions, and one scenario that ties them together. It assumes you've already
installed ScreenMacro (see [README.md](README.md)) and have your game running.

The example uses generic screen/button names — substitute your own game's actual
screens as you go. Everything below is written for **Desktop mode**; **Android
mode** works exactly the same way, except every capture pulls a screenshot from
your configured LDPlayer instance instead of your physical screen.

## What you'll build

```
        +----------+
        |   Home   |  (home screen)
        +----------+
          /      \
   go_farm        go_shop
        /            \
+----------+      +----------+
|   Farm   |      |   Shop   |
+----------+      +----------+
  "collect"          "buy"
  + back to Home     + back to Home
```

A scenario will send the bot to **Farm**, click **collect**, then to **Shop**,
click **buy** — repeating on a cooldown.

---

## Part 1 — Create three screens (Screen Editor tab)

### 1. The Home screen

1. Open the **Screen Editor** tab.
2. Click **+ Add**, type `Home`, press OK.
   - If this is the very first screen in a brand-new config, you'll first be asked
     whether this config targets **Desktop** or **Android** — pick whichever
     matches where your game runs. Android additionally walks you through a short
     LDPlayer setup wizard (instance + game package) before continuing.
3. With **Home** selected in the list, the **Flow Actions** table shows a
   `screen_marker` row. Select that row and click **Recapture**:
   - *Step 1/2* — drag a box around a small, unique part of the Home screen that's
     always visible (a logo or title works well).
   - *Step 2/2* — drag a slightly larger box around where that marker should be
     searched for, or press **Escape** to auto-pad around it.
4. Click **Set as Home** so the bot knows this is its home base — the screen it
   falls back to for recovery.

### 2. The Farm screen

1. Click **+ Add**, type `Farm`.
2. Capture its marker the same way as Home (select the `screen_marker` row →
   **Recapture**), using something only visible on the Farm screen.
3. Click **+ Back** and pick how the game actually leaves this screen for
   wherever it came from — an image button, a fixed click point, or a key press
   (e.g. Esc). Every screen except Home needs one of these.
4. Click **+ Click Image**, drag a box around the button that collects resources,
   and name it `collect`. This action clicks the button without leaving the Farm
   screen — nothing else to configure for a simple click.

### 3. The Shop screen

Repeat the same pattern:

1. **+ Add** → `Shop`.
2. Capture its marker.
3. **+ Back** to get back out of the Shop screen.
4. **+ Click Image** around the "buy" button, name it `buy`.

### 4. Wire up navigation between them

1. Select **Home** in the list.
2. Click **+ Navigate**, drag a box around whatever button on Home opens the Farm
   screen, name it `go_farm`, and choose **Farm** as the destination when prompted.
3. Still on **Home**, click **+ Navigate** again for the button that opens the
   Shop screen, name it `go_shop`, destination **Shop**.

At this point: Home can reach Farm and Shop; Farm and Shop can each get back to
Home via their Back action; Farm has a `collect` action and Shop has a `buy`
action. That's enough for the navigator to path between any of the three screens
automatically.

---

## Part 2 — Build the scenario (Scenario Editor tab)

1. Open the **Scenario Editor** tab.
2. Click **+ Add** — a new scenario is created and selected.
3. Fill in the form:
   - **Name:** `farm_and_shop`
   - **Enabled:** checked
   - **Cooldown seconds:** how long to wait after this scenario finishes before it
     can run again (default 5 is fine to start with).
4. Click **+ Add Step**:
   - **Navigate to:** `Farm`
   - **Actions:** check `collect`
5. Click **+ Add Step** again:
   - **Navigate to:** `Shop`
   - **Actions:** check `buy`
6. Click **Save**.

There's no "start from" field to set — each step's own navigation already
computes the shortest path from wherever the bot currently is, so this scenario
is eligible to run from Home, Farm, Shop, or anywhere reachable from them.

---

## Part 3 — Run it

1. Switch to the **Start** tab.
2. Click **Start**.

The bot detects the current screen, paths to Farm, clicks `collect`, paths to
Shop, clicks `buy`, then waits out the cooldown before doing it again.

---

## Where to go from here

- **Check** actions (`+ Check`) detect an image without clicking it — useful for
  prerequisites (e.g. "only run this scenario if a resource icon is full").
- **Alternates**, on a flow step, watch for an unexpected popup (like an ad) mid-step
  and react to it without aborting the whole scenario.
- **Depends on**, on an individual action's checkbox, makes it wait for another
  action in the same step to have already fired first.
- The **Configs** tab lets you save this whole setup (screens + scenarios +
  templates) as a named config you can reload, back up, or share.
