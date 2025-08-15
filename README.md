# SigilShield

> **Adversarial watermarking for humans—keep AI edits at bay.**

<p align="center">
  <img src="assets/social-preview.png" alt="SigilShield banner" width="800"/>
</p>

<p align="center">
  <a href="#-features"><img src="https://img.shields.io/badge/✨-Polished%20UI-blue" /></a>
  <a href="LICENSE"><img src="https://img.shields.io/badge/License-GPL--3.0-green" /></a>
  <img src="https://img.shields.io/badge/Stack-HTML%20%7C%20CSS%20%7C%20JavaScript-informational" />
  <img src="https://img.shields.io/badge/Status-Active-success" />
  <a href="#-contributing"><img src="https://img.shields.io/badge/PRs-Welcome-brightgreen" /></a>
</p>

---

## 🚀 What is SigilShield?

**SigilShield** is a lightweight, client‑side web app that lets you add a customizable (and optionally adversarial) watermark to your images. Protect your visuals before sharing them on social media or the web—no uploads, no servers, fully local in your browser.

* 📍 Position presets (9 hotspots)
* 🔍 Size & opacity sliders
* 🔗 Default or custom watermark URL (CORS‑friendly)
* 🖱️ Drag‑and‑drop or click‑to‑upload
* 💾 One‑click “Download Protected Image”

> Your images never leave your device. Everything runs in the canvas.

---

## ✨ Demo

<p align="center">
  <img src="assets/demo.gif" alt="Animated demo of SigilShield" width="700"/>
  <br/>
  <sub>Add a watermark, tweak size/opacity, and export in seconds.</sub>
</p>

<p align="center">
  <img src="assets/ui.png" alt="SigilShield UI screenshot" width="700"/>
</p>

> Place these files under `assets/` or update the paths above.

---

## 🧩 Features

* **Modern glassmorphism UI** with smooth hover/press states
* **Default embedded watermark** (Base64) that works out of the box
* **Custom watermark** via URL with CORS guidance & helpful fallbacks
* **Nine position presets** from top‑left to bottom‑right
* **Pixel‑perfect canvas export**
* **No build step, no dependencies**—just open `index.html`

---

## 🛠️ Getting Started

### Option A — Quick open

1. Clone the repo

   ```bash
   git clone https://github.com/<your-username>/sigilshield.git
   cd sigilshield
   ```
2. Open `index.html` in your browser (double‑click or drag into a tab).

### Option B — Local dev server (recommended for CORS testing)

```bash
# Using Python
python -m http.server 8000
# or
python3 -m http.server 8000

# Using Node (serve)
npm i -g serve
serve .
```

Then visit `http://localhost:8000` (or the URL shown).

---

## 🧪 How it works (brief)

* Loads your main image into an HTML5 `<canvas>`.
* Loads the watermark (default Base64 PNG or custom URL) into an offscreen `Image` object.
* Draws background → overlays watermark with `globalAlpha` → exports via `canvas.toDataURL()`.

Core tweakables in `index.html`:

```js
const DEFAULT_OVERLAY_URL = 'data:image/png;base64,...';
let currentPosition = 'bottom-right';
let overlayScale = 0.25; // 10–50% via slider
let overlayOpacity = 1.0; // 0–1 via slider
```

---

## 🔐 CORS & Custom Watermarks

To use a custom watermark image, it **must** be hosted with permissive CORS headers. Good options:

* **GitHub/raw**: `https://raw.githubusercontent.com/<user>/<repo>/main/logo.png`
* **Imgur direct**: `https://i.imgur.com/<id>.png`
* **Cloudinary**: `https://res.cloudinary.com/<cloud>/image/upload/<file>.png`

> Many social sites (Google Images/Instagram/Twitter) block cross‑origin access. If load fails, SigilShield will prompt to fall back to the default watermark.

---

## 📦 File Structure

```
.
├─ assets/
│  ├─ demo.gif              # Animated demo (optional)
│  ├─ ui.png                # Screenshot (optional)
│  └─ social-preview.png    # Open Graph / social card (optional)
├─ index.html               # The app (no build step!)
├─ README.md
└─ LICENSE                  # GPL-3.0
```

---

## 🧭 Usage

1. **Open** the app and **drop** an image (or click to choose).
2. Choose **Watermark Source** → **Default** or **Custom URL**.
3. Set **Position**, adjust **Size** & **Opacity**.
4. Click **Download Protected Image**. Done.

> Tip: For consistent branding, keep Size at \~20–30% and Opacity at 40–70%.

---

## 🌐 Deploy (GitHub Pages)

1. Push this repo to GitHub.
2. Settings → **Pages** → **Source: `main`** → **Root** → Save.
3. Your app will be live at `https://<user>.github.io/<repo>/`.

Add this to the README once live:

```md
**Live demo:** https://<user>.github.io/<repo>/
```

---

## 🧭 Roadmap

* [ ] Tiled watermark mode (grid repeat)
* [ ] Text watermark (custom font, color, shadow)
* [ ] Batch processing (multiple images → zip export)
* [ ] Smart margins (percent of short edge)
* [ ] PWA support (offline install)
* [ ] EXIF scrub option on export

---

## 🧰 Troubleshooting

* **“Failed to load watermark (CORS or invalid URL)”**

  * Try a raw GitHub/Imgur/Cloudinary link
  * Ensure the URL points **directly to the image** (ends with `.png/.jpg/.webp`)
* **Blurry output**

  * Check the original image resolution; canvas exports at source size
* **Nothing happens on drop**

  * Make sure the file is an image type (`image/*`)

---

## 🤝 Contributing

PRs welcome! If you’re adding a feature, please include:

* A short description in the PR
* A demo GIF or screenshots in `assets/`
* Minimal, well‑commented code

---

## 📜 License

GPL‑3.0. See [LICENSE](LICENSE) for details.

---

## 🙌 Credits

Built with ❤️ by **Arjun Dixit**. UI theme inspired by modern glassmorphism and gradient aesthetics.

If this helped, ⭐ the repo and share your watermarked shots!
