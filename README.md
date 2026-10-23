# Setbook

Free workout tracker. Log sets, track history and weekly progress. Data stays on your device.

**Live app:** https://prathameshbodhankar.github.io/setbook/

## What it does

- **Workout**: start a workout, add exercises from a list of 30, and log weight and reps (or seconds) for each set. Your numbers from last time show next to each set.
- **History**: every finished workout with its date, duration, total volume and sets. Delete any you don't want.
- **Progress**: this week's workouts, volume and sets, plus a chart of the last 8 weeks.
- **Profile**: name, bodyweight, height and goal. Export or import a backup of your data.

It also works as an installable app. On Android or desktop Chrome, choose **Install app**. On iPhone, open it in Safari and choose **Share → Add to Home Screen**. Once installed, it works offline.

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
