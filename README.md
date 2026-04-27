<div align="center">

# 🥩 No-Vegan Game

### Eat the meat. Avoid the veggies. With your face.

**An AI-powered browser game where you catch falling food using your mouth — tracked in real-time by your webcam.**

[![Play Now](https://img.shields.io/badge/▶_Play_Now-no--vegan.vercel.app-ff6b35?style=for-the-badge&logoColor=white)](https://no-vegan.vercel.app)
[![MediaPipe](https://img.shields.io/badge/AI-MediaPipe_FaceLandmarker-00c8ff?style=for-the-badge)](https://developers.google.com/mediapipe/solutions/vision/face_landmarker)
[![Vercel](https://img.shields.io/badge/Deployed-Vercel-000000?style=for-the-badge&logo=vercel)](https://no-vegan.vercel.app)

![No-Vegan Game Demo](media/promo.gif)

> 📺 **[Watch the trailer in HD (MP4)](media/promo.mp4)** &nbsp;·&nbsp; 🎮 **[Play live](https://no-vegan.vercel.app)**

</div>

---

## 🎯 How to Play

1. **Open** [no-vegan.vercel.app](https://no-vegan.vercel.app) in Chrome/Edge/Safari
2. **Allow camera access** — the AI needs to see your face to track your mouth
3. **Open your mouth** to "eat" food as it falls past your face
4. **Score 60 seconds of pure carnivorous chaos**

| Catch this | Don't catch this |
|:---:|:---:|
| 🥩 🍖 🥓 🍗 🌭 🫀 | 🥦 🥕 🧅 🌽 🥒 🥬 🫑 |
| **+10 points** | **−5 points** |

---

## ✨ Features

- 🤖 **Real-time AI face tracking** using MediaPipe FaceLandmarker (478 facial landmarks)
- 👄 **Mouth-open detection** by measuring the distance between upper/lower lip landmarks
- 🎬 **Cinematic effects** —
  - Eat a veggie? Big red **"No Vegan!"** flash with a screen shake
  - Eat meat? Warm golden recovery glow + ❤️ heart particles floating up (RPG-style)
- ⏱️ **60-second time attack** with progressive difficulty (faster spawns over time)
- 🏆 **5-tier ranking system**: 👑 Carnivore King → 🥦 Suspected Vegan
- 🎨 **Single HTML file** — zero build step, runs anywhere

---

## 🏆 Ranking

| Score | Rank | Title |
|:---:|:---:|:---|
| 200+ | 👑 | 진정한 육식주의자! |
| 120+ | 🥇 | 고기 마스터! |
| 60+ | 🥈 | 괜찮은 노비건이에요! |
| 20+ | 🥉 | 야채를 너무 많이 먹었어요... |
| <20 | 🥦 | 혹시 비건이세요? |

---

## 🛠️ Tech Stack

| Layer | Tool |
|---|---|
| **AI / Computer Vision** | [MediaPipe FaceLandmarker](https://developers.google.com/mediapipe/solutions/vision/face_landmarker) (WASM, GPU-accelerated) |
| **Rendering** | HTML5 Canvas 2D |
| **Camera** | `getUserMedia()` (WebRTC) |
| **Hosting** | [Vercel](https://vercel.com) |
| **Promo video** | [HyperFrames](https://github.com/heygen-com/hyperframes) (HTML → MP4) |

**No frameworks. No build step. No backend.** The entire game is one [`index.html`](index.html) file (~830 lines).

---

## 🚀 Run Locally

```bash
git clone https://github.com/LeoOH5/VeganGame.git
cd VeganGame

# Camera APIs require HTTPS or localhost — serve it:
python3 -m http.server 8080
# or: npx serve
```

Then open <http://localhost:8080>.

> ⚠️ Opening `index.html` directly via `file://` will fail — browsers block camera access on the `file:` protocol.

---

## 🧠 How the AI Detection Works

The game uses **MediaPipe's FaceLandmarker** model to extract 478 facial landmarks per frame at ~30 FPS:

```
┌────────────────────────────────────────────────┐
│  Webcam → MediaPipe (WASM) → 478 landmarks     │
│                                ↓               │
│       Lip landmarks: #13 (top) ↔ #14 (bottom)  │
│                                ↓               │
│    Mouth open if  (lip_height / lip_width) >   │
│                    0.18                        │
└────────────────────────────────────────────────┘
```

Collision = falling item's center within `mouth_radius + item_size * 0.4` **and** mouth open.

---

## 🎬 Promo Video

The [trailer above](media/promo.mp4) was generated with **[HyperFrames](https://github.com/heygen-com/hyperframes)** — an HTML+GSAP video composition framework. Source: [`promo/index.html`](promo/index.html).

---

## 📁 Project Structure

```
no-vegan/
├── index.html          ← The game (single-file)
├── media/
│   ├── promo.mp4       ← 15s trailer (1920×1080, 30fps)
│   └── promo.gif       ← Preview animation for this README
├── promo/              ← HyperFrames source for the trailer
│   └── index.html
└── README.md
```

---

## 📜 License

MIT — go forth and consume.

---

<div align="center">

**Made with 🥩 by [@LeoOH5](https://github.com/LeoOH5)**

[![Play Now](https://img.shields.io/badge/▶_Play_Now-no--vegan.vercel.app-ff6b35?style=for-the-badge)](https://no-vegan.vercel.app)

</div>
