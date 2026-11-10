# JRL Launcher

**Install:** on the phone, download [`jrl-launcher.apk`](https://github.com/jere-mee-as/jrl-launcher/releases/latest/download/jrl-launcher.apk) from the [latest release](https://github.com/jere-mee-as/jrl-launcher/releases/latest), open it, and allow the install. Then Settings → Apps → JRL → ⋮ → **Allow restricted settings**, and choose JRL under Settings → Apps → Choose default apps → Home app. Try it without a phone: [jere.ing/#lab](https://jere.ing/#lab).

JRL Launcher is an Android home screen for a Galaxy Z Fold7, in the same style as jere.ing. It's a thin native Kotlin shell, registered as the HOME app, that hosts a full-screen WebView running the launcher UI. A JavaScript bridge gives the page the phone's apps, calendar, media and notifications. In a desktop browser the page falls back to a mock bridge with example data, so every screen can be tried without a phone.

| Path | What |
|---|---|
| `android/` | Kotlin shell (HOME app, WebView, `window.JRLAndroid` bridge); see its README |
| `web/src/` | v3.0 modular web UI sources: `shell.html`, `launcher.css`, `core.js`, `bridge.js`, `pal.js`, `app.js`, `term.js`, plus `assemble.py` |
| `web/archive/src-v2.2/` | The v2.2 sources, same layout, kept for reference |
| `previews/v0-first-mockup.html` | First mockup |
| `previews/v2.0.html` to `v2.2.html` | v2 previews |
| `previews/v3.0.html` | v3.0 preview (what `web/src/` builds) |
| `previews/v4.0.html` | v4.0 preview, current |
| `screens/` | Test screenshots of v2.0 to v3.0, taken with fallback fonts |
| `docs/` | Briefs, plans, handoffs and build notes |

## How to open and build

- **Preview:** open any file in `previews/` in a browser. The mock bridge drives it. Phone-sized windows (about 412×915 folded, 984×1092 unfolded) match the device.
- **Assemble the web UI:** `python3 web/src/assemble.py OUT.html` inlines the sources into one HTML file. With no argument it writes `previews/out.html`. Today the output is identical to `previews/v3.0.html`.
- **Release:** Actions → **Release APK** → **Run workflow** builds the APK and publishes it as release `v<versionName>` (the button is the only trigger). Signing keys and APKs are never committed.
- **Over-the-air UI:** installed launchers load their page from https://raw.githubusercontent.com/jere-mee-as/jrl-launcher/main/android/app/src/main/assets/www/index.html and fall back to the bundled copy when offline.

## Status

v4.0 is the current design. The APK (shell 0.3.1) bundles it with the adapter fixed for the real bridge; releases come from the Actions tab. The modular sources in `web/src/` are still at v3.0.

## Docs

[`docs/`](docs/). Start with `jrl-launcher-v4-plan.md` and `jrl-launcher-v4-status.md`; `jrl-launcher-brief-OLD.md` is superseded.
