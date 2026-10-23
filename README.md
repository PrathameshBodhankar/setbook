# Setbook

Free workout tracker. Log sets, track history and weekly progress. Data stays on your device.

**Live app:** https://prathameshbodhankar.github.io/setbook/

## What it does

- **Workout**: start an empty workout, repeat your last one, or start a saved routine. Add exercises from a list of over 70 (including a Pilates section) and log weight and reps, or seconds for holds. Last time's numbers show next to each set. Mark warm-up sets, reorder exercises, add notes, and change the date if you're logging after the fact.
- **Your own exercises**: type a name that isn't listed and press Enter (or tap **+ Add**). It's saved on your device and included in backups. Tap **Suggest** next to it to propose it for everyone; that opens a pre-filled issue on this repo.
- **Records**: tap any exercise to see every session, your heaviest set, estimated 1-rep max and best reps or hold. Workouts that beat a record get a **New PR** badge.
- **History**: every finished workout with its date, volume, sets and notes. Edit, delete or save any workout as a routine.
- **Progress**: workouts, volume and working sets for the last 1, 4, 8 or 12 weeks, compared with the period before, plus a chart and the exercises you trained.
- **Profile**: name, units (kg or lb), bodyweight, height and goal. Export or import a backup of your data.

Warm-up sets don't count toward volume or records.

It also works as an installable app. On Android or desktop Chrome, choose **Install app**. On iPhone, open it in Safari and choose **Share → Add to Home Screen**. Once installed, it works offline.

## Adding suggested exercises

Suggestions arrive as issues titled "Exercise suggestion: …". To add one for everyone, add a `["Name","Section"]` line to the `EX` list near the top of the script in `index.html` (and the name to `TIMED` if it's logged in seconds), then commit.

## How your data is stored

Everything is saved in your browser's `localStorage` on your device. Nothing is uploaded, and there's no account or server.

That means:

- Your data lives only in the browser you used. A different browser or device starts empty.
- Clearing your browser's site data erases your workouts.
- Use **Profile → Export backup** to save a dated `.json` file, and **Import backup** to restore it here or on another device. Importing replaces your current data after you confirm.

## Run it locally

Download or clone this repo and open `index.html` in a browser. There's no build step and nothing to install.

Offline mode and the install prompt need the page served over `http://localhost` or HTTPS, not opened as a file. To test those, run a local server from the repo folder:

```sh
python3 -m http.server 8000
```

Then open http://localhost:8000/.

## Files

| File | Purpose |
| --- | --- |
| `index.html` | The whole app: HTML, CSS and JavaScript |
| `manifest.webmanifest` | App name, colors and icons for installing |
| `sw.js` | Service worker that caches the app for offline use |
| `icon-192.png`, `icon-512.png` | App icons |

`index.html` updates reach users the next time they open the app online. If you change the manifest or icons, bump `VERSION` in `sw.js` so installed copies refresh their cache.
