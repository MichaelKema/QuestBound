# Questbound

A Tauri 2 desktop app that turns your to-do list into a first-person dungeon adventure. React, TypeScript, Vite, and a local canvas raycaster; no accounts, servers, or external art assets.

This was made for a short AI hackathon
## Run

Install Node.js 22+ and Rust, plus the [Tauri prerequisites](https://v2.tauri.app/start/prerequisites/) for your platform.

```sh
npm install
npm run desktop:dev
```

For a browser preview, use `npm run dev` and open `http://localhost:1420`.

## Build

```sh
npm run desktop:build
```

On macOS, this produces a native app and DMG in `src-tauri/target/release/bundle/`. On Windows or Linux, build on that platform to produce its native packages. Unsigned builds are intended for local development.

## Play

- Add quests, enter the dungeon, select an enemy, and begin an encounter. The five initial quests are examples you can remove and replace.
- Complete the real-world task, then click **Task complete** before its deadline. Time starts only when you begin an encounter. Expiration or retreat loses the fight; retry to try again with a fresh timer.
- Difficulty follows the time limit: **yellow** basic enemies (1–15 min), **orange** mini bosses (16–30 min), **red** main bosses (31–60 min), **purple** super bosses (61–240 min).
- **Green** breaks/supports complete automatically when their timer ends. You may end a break early. Breaks are optional for clearing a dungeon.
- Defeat every enemy to claim a one-time **100 XP + 50 gold** clear bonus. Start a new dungeon to plan another run, keeping your lifetime XP, gold, level, and adventure log.
- Click the dungeon scene, use **W A S D** to move, and **← / →** to turn. On-screen movement buttons also work. You can begin tasks from any location in the dungeon.
- Timers use absolute deadlines and continue while the app is closed. Quests and rewards save in the webview’s local storage on this device; the browser preview has its own separate save. No cloud sync is included.

The enemies are deliberately simple, faceted placeholders. Gold is currently a progress reward; there is no shop or equipment system yet. Sound is optional, off by default, and generated locally.

## Validate

```sh
npm test
npm run build
cargo check --manifest-path src-tauri/Cargo.toml
```

The tests cover task tiers, deadline boundaries, retrying, persistence reconciliation, support completion, reward duplication, dungeon reset, and corrupted saves.

