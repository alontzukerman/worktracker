# WorkTracker

A small macOS app that measures **how much you're actually working** — not how long your laptop was on.

![WorkTracker dashboard](screenshots/dashboard-native.png)

> Apple Silicon (M1–M4) · macOS 11+ · everything stays on your Mac

---

## Install

```bash
brew tap alontzukerman/worktracker
brew trust --cask alontzukerman/worktracker/worktracker
brew install --cask --no-quarantine worktracker
```

`--no-quarantine` is required: the app isn't notarized by Apple (it's a personal
project, not a paid developer account), so without that flag macOS blocks it.

### Updating

```bash
brew upgrade --cask worktracker
```

<details>
<summary>Prefer a manual download?</summary>

Grab the `.dmg` from [Releases](../../releases/latest), drag the app to
Applications, then clear the quarantine flag once:

```bash
xattr -cr /Applications/WorkTracker.app
```

</details>

---

## What it does

**Tracks real work, automatically.** Every 15s it asks macOS how long since your
last input. Actively using the machine counts; idle past 2 minutes doesn't. No
keylogging — it never sees *what* you type.

**Counts meetings as work.** Log a meeting and it counts even though you weren't
typing. Time spent working *during* a meeting is never double-counted.

**Pause when you're not working.** Watching something on the commute? Pause for
30 min / 1 hour / 2 hours — it auto-resumes when the timer ends, so a forgotten
pause can't swallow your day.

**Log life, too.** Gym and food are tracked and charted, but never counted as work.

---

## The dashboard

- **Today · Last week · Last month · All time**
- Working-hours headline with a status read on how the day is going
- Activity by hour (or by day), where your time went, and your top apps
- 📸 **Day snapshot** — export a shareable summary card, including how the day
  compares to your all-time average

### Themes

Five palettes that retint the entire app — including exported snapshots.

| Espresso ☕ | Pride 🏳️‍🌈 |
|---|---|
| ![Espresso](screenshots/dashboard-espresso.png) | ![Pride](screenshots/dashboard-pride.png) |

---

## Privacy

Everything is local. No account, no telemetry, nothing uploaded — ever.

Your data lives in `~/Library/Application Support/WorkTracker/`:

| File | Contents |
|---|---|
| `activity.json` | per-minute activity samples |
| `events.json` | meetings / gym / food you logged |
| `settings.json` | your preferences |

Delete that folder and it's all gone. Uninstall completely with
`brew uninstall --zap --cask worktracker`.

### Permissions

On first launch macOS asks for two, both optional:

- **Automation (System Events)** — to read the frontmost app name, for the
  "top apps" breakdown
- **Notifications** — to tell you when a pause has ended

Decline them and time tracking still works; you just lose those two features.

---

## Notes

- Apple Silicon only right now. Open an issue if you need an Intel build.
- Screenshots use sample data.
