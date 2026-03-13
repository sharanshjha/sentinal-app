# 🛡️ SENTINEL — AI Room Guardian

<div align="center">

![Sentinel Banner](https://img.shields.io/badge/SENTINEL-AI%20Room%20Guardian-00ff88?style=for-the-badge&logo=tensorflow&logoColor=white)
![Platform](https://img.shields.io/badge/Platform-Android%20PWA%20%7C%20APK-4CAF50?style=for-the-badge&logo=android&logoColor=white)
![TensorFlow](https://img.shields.io/badge/TensorFlow.js-COCO--SSD-FF6F00?style=for-the-badge&logo=tensorflow&logoColor=white)
![Telegram](https://img.shields.io/badge/Telegram-Bot%20Alerts-2CA5E0?style=for-the-badge&logo=telegram&logoColor=white)

**A covert AI-powered room monitoring system that detects intruders in real-time and silently alerts you on Telegram — disguised as a battery charging screen.**

[🚀 Live Demo](https://sharanshjha.github.io/sentinal-app/) • [📱 Install as App](#installation) • [⚙️ Features](#features)

</div>

---

## 🎯 What is SENTINEL?

SENTINEL is a browser-based AI security monitor that uses your smartphone's camera and **TensorFlow.js (COCO-SSD)** to detect people in real time. When someone enters your room, it instantly sends you a **Telegram alert with a photo snapshot** — all while your phone looks like it's just sitting on a charging screen.

> Built entirely with vanilla HTML, CSS, and JavaScript. No backend. No server. No app store. Just open the link and it works.

---

## ✨ Features

### 🤖 AI Detection
- Real-time person detection using **TensorFlow.js + COCO-SSD** neural network
- Runs 100% on-device — no cloud, no API calls for detection
- Adjustable confidence threshold (30–90%)
- ~4 FPS detection loop optimized for battery efficiency

### 📲 Smart Alerts
- **Telegram Bot integration** — instant silent alerts to your phone
- **Photo snapshots** — captures the intruder's image and sends it directly
- Configurable cooldown (5 sec – 1 min) to prevent spam
- Silent vibration on the guardian phone
- Optional audio beep

### 🕵️ Covert Operation
- **Disguise modes** — screen shows a fake Battery Charging UI, Clock, or pure Black screen
- The app title shows as "Battery Monitor" — completely innocent looking
- **Secret access** — triple-tap the top-right corner to open the real control panel
- **WakeLock API** — keeps the screen on without looking active

### 📱 True Mobile App
- **PWA (Progressive Web App)** — installs directly from Chrome, works like a native app
- **Signed APK** built with Google's Bubblewrap/TWA — real Android app
- Works on any Android device with Chrome
- Rear camera by default for door/entrance monitoring

---

## 🛠️ Tech Stack

| Layer | Technology |
|-------|-----------|
| AI Model | TensorFlow.js + COCO-SSD v2.2.2 |
| Runtime | Vanilla JavaScript (ES2020) |
| Camera | WebRTC `getUserMedia` API |
| Alerts | Telegram Bot API |
| Screen Lock | WakeLock API |
| Sound | Web Audio API |
| Deployment | GitHub Pages (HTTPS) |
| App Packaging | Google Bubblewrap (TWA) → signed APK |

---

## 📸 How It Works

```
Phone Camera → TensorFlow.js → Person Detected?
                                      │
                              YES ────┤
                                      ↓
                          Capture JPEG Snapshot
                                      │
                                      ↓
                     Telegram Bot API → Your Phone 🔔
                                      │
                                      ↓
                    Silent Vibrate + Flash on Guardian Phone
```

---

## 🚀 Installation

### Option 1 — Use Instantly (No Install)
Open in Chrome on any Android phone:
```
https://sharanshjha.github.io/sentinal-app/
```

### Option 2 — Install as PWA (Recommended)
1. Open the link above in **Chrome**
2. Tap **⋮ menu → "Add to Home Screen"** or **"Install App"**
3. Tap **Add** — appears on home screen like a native app ✅

### Option 3 — Sideload APK
1. Clone this repo
2. Run `bubblewrap build` (see [Build from Source](#build-from-source))
3. Transfer `app-release-signed.apk` to phone and install

---

## ⚙️ Setup & Configuration

### 1. Create a Telegram Bot
- Open Telegram → search **@BotFather**
- Send `/newbot` → follow prompts → copy your **Bot Token**
- Search **@userinfobot** → copy your **Chat ID**
- Search your new bot → send `/start`

### 2. Update Credentials
In `index.html`, find and replace:
```javascript
const TG_TOKEN   = 'YOUR_BOT_TOKEN_HERE';
const TG_CHAT_ID = 'YOUR_CHAT_ID_HERE';
```

### 3. Deploy to GitHub Pages
- Fork this repo
- Go to **Settings → Pages → Deploy from main branch**
- Your app is live at `https://yourusername.github.io/sentinal-app/`

---

## 🔧 Build from Source

### Prerequisites
- Node.js 16+
- JDK 17 (auto-installed by Bubblewrap)
- Android SDK (auto-installed by Bubblewrap)

### Steps
```bash
# Install Bubblewrap
npm install -g @bubblewrap/cli

# Initialize APK project
mkdir sentinel-apk && cd sentinel-apk
bubblewrap init --manifest https://yourusername.github.io/sentinal-app/manifest.json

# Build signed APK
bubblewrap build
```
Output: `app-release-signed.apk`

---

## 🎮 Usage

1. **Open the app** on your guardian phone
2. Tap **TEST** to verify Telegram alerts are working
3. Configure sensitivity and cooldown to your preference
4. Choose your disguise mode (Battery Charging recommended)
5. Tap **🛡️ ACTIVATE GUARDIAN**
6. Place phone facing your room entrance
7. The screen switches to the disguise UI — looks like it's just charging
8. Walk away — you'll get Telegram alerts with photos on your other device

**To check logs secretly:** Triple-tap the top-right corner of the screen

---

## 🔒 Privacy & Security

- All AI processing happens **on-device** — no video is ever uploaded
- Only triggered snapshots are sent via Telegram (not a live stream)
- Bot Token and Chat ID are stored client-side only
- No analytics, no tracking, no third-party SDKs except TensorFlow.js

> ⚠️ **Security Note:** Rotate your Telegram Bot Token periodically via @BotFather. Never share your token publicly.

---

## 📁 Project Structure

```
sentinal-app/
├── index.html        # Main app (entire frontend in one file)
├── manifest.json     # PWA manifest — enables "Install App"
├── sw.js             # Service Worker — offline support & caching
├── icon-192.png      # App icon (home screen)
└── icon-512.png      # App icon (splash screen)
```

---

## 🗺️ Roadmap

- [ ] Multiple camera support (switch between cameras)
- [ ] Motion-based pre-detection trigger (save battery)
- [ ] Night mode / low-light enhancement
- [ ] Multi-device alerts (notify multiple Telegram users)
- [ ] Detection history with timestamps and gallery
- [ ] Face recognition to whitelist known people

---

## 👨‍💻 Author

**Sharansh Jha**
Final Year B.Tech CSE | AKTU
[GitHub](https://github.com/sharanshjha) • [Telegram](https://t.me/Sharanshjha)

---

## 📄 License

MIT License — free to use, modify, and distribute.

---

<div align="center">

**Built with ❤️ using TensorFlow.js, Telegram Bot API, and vanilla JavaScript**

⭐ Star this repo if you found it useful!

</div>
