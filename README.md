<div align="center">

<img src="docs/icon.png" width="96" alt="Erebus icon">

# Erebus

**A louder, clearer voice on WhatsApp Web calls.**
Glassy sky-blue UI. One-click simple mode. Pro controls when you want them.

by **@Noxmirage ~𝑯𝒂𝒛𝒆**

![Manifest V3](https://img.shields.io/badge/Manifest-V3-38bdf8?style=for-the-badge)
![Chromium](https://img.shields.io/badge/Chrome%20%7C%20Edge%20%7C%20Brave-supported-7dd3fc?style=for-the-badge)
![Privacy](https://img.shields.io/badge/Network%20requests-0-ffffff?style=for-the-badge&labelColor=0284c7)

<br>

<img src="docs/simple.png" width="300" alt="Erebus main screen">
&nbsp;&nbsp;
<img src="docs/customize.png" width="300" alt="Erebus customize tab">

</div>

---

## What is Erebus?

Erebus is a browser extension that boosts and cleans up your microphone **before WhatsApp Web sends it**. The person on the other end hears a stronger, clearer you, with no extra apps or hardware.

It runs entirely inside your browser. There are **no network requests, no recording, and no accounts**.

## Features

| | |
|---|---|
| **Simple mode** | A power button, a live voice-level bar, and a Boost slider with four presets: *Normal, Louder, Loud, Max*. |
| **Live level meter** | See your voice in real time. The bar glows white when you are too loud. |
| **Safety ceiling** | A hard limit so your voice never goes past the level you set, which prevents harsh distortion. |
| **Customize tab** | Boost, ceiling, bass, clarity, treble, rumble cut, noise gate, compressor, and echo/noise options. Tap **?** on any control for a plain-words explanation. |
| **How it works tab** | A built-in step-by-step explanation of what happens to your voice. |
| **Password lock** | A glass lock screen in front of the popup. |
| **Glass UI** | Sky blue and white, translucent cards, blur, bright edges. |

## Install

> Works on **Chrome, Edge, Brave** and other Chromium browsers (version 111 or newer).

1. **Download** this repository: click **Code → Download ZIP**, then unzip it. (Or run `git clone <this-repo-url>`.)
2. Open your extensions page:
   - Chrome: `chrome://extensions`
   - Edge: `edge://extensions`
   - Brave: `brave://extensions`
3. Turn on **Developer mode** (top-right switch).
4. Click **Load unpacked** and select the **Erebus folder** (the one that contains `manifest.json`).
5. *(Optional)* Click the puzzle icon in your toolbar and **pin Erebus**.
6. Open **https://web.whatsapp.com** and **reload the tab** once.

## Use it

1. Click the Erebus icon and enter the password: **`Erebus`**.
2. Start a voice or video call on WhatsApp Web.
3. Pick a preset (*Louder* is a good start) and watch **Your voice level**.
4. Keep the bar below the bright-white zone. If it says *Too hot*, lower the Boost a little.

Changes apply instantly, even in the middle of a call.

<div align="center">
<img src="docs/lock.png" width="260" alt="Lock screen">
&nbsp;&nbsp;
<img src="docs/how-it-works.png" width="260" alt="How it works tab">
</div>

## How it works

WhatsApp Web asks your browser for the microphone. Erebus steps in between and passes your voice through a small audio chain, then hands the result to WhatsApp:

```
Mic → Rumble cut → Noise gate → Boost → Tone → Compressor → Safety ceiling → WhatsApp
```

| Step | What it does |
|---|---|
| **Rumble cut** | Removes low hum, desk bumps and wind. |
| **Noise gate** | Silences the mic while you are not talking (off by default). |
| **Boost** | Makes your voice louder, from 0 to +24 dB. |
| **Tone** | Bass, clarity and treble shaping. |
| **Compressor** | Evens out quiet and loud parts. |
| **Safety ceiling** | A soft limit that the output can never exceed. |

Technically, the extension wraps `navigator.mediaDevices.getUserMedia` on `web.whatsapp.com` and routes the mic track through the Web Audio API. When Erebus is switched off, your normal mic passes through untouched.

## Settings cheat sheet

| Setting | Good starting value | Notes |
|---|---|---|
| Boost | 8 dB (*Louder*) | Higher also boosts background noise. |
| Safety ceiling | -3 dB | Lower = safer and cleaner, slightly quieter. |
| Rumble cut | 80 Hz | Raise it if you hear low hum. |
| Noise gate | Off | Move right in noisy rooms. |
| Echo cancel | On | Keep on unless you wear headphones. |
| Browser auto-volume | Off | Usually fights the boost. |

*Browser options apply the next time a call starts.*

## Troubleshooting

| Problem | Fix |
|---|---|
| Popup says **Open WhatsApp Web to start** | Open `web.whatsapp.com` and **reload** the tab after installing. |
| **Waiting for a call** never changes | Start a call, then speak. The meter only moves during a call. |
| Voice is distorted | Lower **Boost**, or lower the **Safety ceiling**. |
| Other person hears echo | Use headphones, and keep **Echo cancel** on. |
| Hiss or background noise | Lower the Boost and raise the **Noise gate** in Customize. |
| Nothing changed after an update | Go to the extensions page, click **reload** on Erebus, then reload WhatsApp Web. |

## Project structure

```
erebus/
├── manifest.json        Extension manifest (MV3)
├── config.js            Shared defaults and control definitions
├── content/
│   ├── engine.js        Audio engine, runs inside the WhatsApp page
│   └── bridge.js        Passes settings in and the level meter out
├── popup/               The glass UI (HTML, CSS, JS)
├── fonts/               Inter and Space Grotesk, bundled locally
├── icons/               Extension icons
└── docs/                README screenshots
```

## Privacy

- Runs only on `https://web.whatsapp.com`.
- The only permission used is `storage`, to remember your settings on your device.
- No audio is recorded, stored, or sent anywhere.

## Good to know

- Results depend on your microphone, device, browser and connection. Boost is a processing setting, not a guarantee of louder audio on every setup.
- The password is a casual lock for the popup, not strong security. Anyone with access to the extension files can read it.
- Modifying a web client may go against WhatsApp's terms of service. Use it responsibly and at your own risk.
- This project is unofficial and is not affiliated with WhatsApp or Meta.

---

<div align="center">

Made by **@Noxmirage ~𝑯𝒂𝒛𝒆**

</div>
