# 🚀 megastreamer v0.4 Release Notes: Cloud Streaming Suite

## A new Tier of Kodi Cloud Streaming!
We are proud to present **megastreamer v0.4**, the most ambitious and transformative release of our premier cloud streaming client and decryption suite built natively for Kodi.

Version 0.4 elevates the addon from a simple Mega.nz stream handler into a complete, bulletproof, and highly secure multi-cloud streaming engine. By incorporating the advanced quota and proxy management systems of **v0.3** with the native Google Drive integration, persistent background services, and hardened platform-agnostic layer of **v0.4**, this build represents the pinnacle of performance, anonymity, and stability.

---

## ⚡ What's New in Version 0.4 (The Multi-Cloud & Hardening Milestone)

Version 0.4 re-architects the core execution layer, adds native Google Drive support, and hardens the settings system against system-specific environment errors.

### 📂 1. Native Google Drive Integration
MegaStreamer now natively supports browsing and streaming media files directly from your personal Google Drive account! Your entire GDrive library is rendered seamlessly alongside your Mega cloud storage.

### 🔑 2. Automated Loopback OAuth 2.0 Flow
Setting up Google Drive relies on a built-in background loopback server (`127.0.0.1:53682`). When you authorize Google Drive, our local server automatically captures the secure token exchange in your system web browser, with a manual text input fallback if needed.

### 🛡️ 3. Hardened Custom Credentials Setup
To prevent rate limits and API bans, GDrive access utilizes your own Google Cloud credentials (Client ID and Secret). Detailed step-by-step setup guides in English & German are included ([GoogleAuth_english.md](GoogleAuth_english.md) / [GoogleAuth_deutsch.md](GoogleAuth_deutsch.md)) to guide you through registering a Google Cloud project and obtaining keys in minutes.

### 🔄 4. Persistent Background Service Architecture
We migrated the core streaming WSGI server from a blocking script to a native, persistent `xbmc.service` background model (`service.py`).
**Why it matters**: Resolves slow folder loading times and completely eliminates Python standalone execution errors ("Streaming Service nicht aktiv") during Kodi startup.

### ⚙️ 5. Recovered General Settings & Custom Buffer Caching
* **General Controls**: Restored Localhost, Minimum Port, and Maximum Port configuration fields under "General" settings by re-implementing mandatory `<control>` tags in the XML schema.
* **Custom Buffer Cache Slider**: Added a slider to dynamically allocate Kodi's network video buffer up to 500MB. The addon automatically writes your changes directly to `advancedsettings.xml`. Check our new [recommended_cache_values.md](recommended_cache_values.md) guide for optimal configurations based on your hardware RAM footprint (Android TV, Linux, Windows).

### 🔒 6. Force Cloudflare Worker Toggle (100% Anonymity & Obfuscation)
Added a toggle to route **all** Mega.nz streaming traffic directly through a Cloudflare Worker, bypassing IP limit checks.
* **Failsafe Privacy**: If the Cloudflare Worker fails, the stream stops immediately with a warning dialog and **does not** fall back to your direct IP. This guarantees that your real IP address is never leaked to Mega.nz, ensuring 100% privacy and obfuscation from your ISP.

---

## 📊 What's New in Version 0.3 (Smart Quota & Proxy Optimization)

Version 0.3 introduced advanced bandwidth management and smart proxy routing:
* **Smart Quota Management**: Tracks cumulative data usage locally. It automatically minimizes Cloudflare Worker bandwidth by only triggering the proxy once a 4.9 GB direct download threshold is reached.
* **HTTP 509 (Bandwidth Limit Exceeded) Fallback**: Seamlessly catches Mega bandwidth blocks and automatically switches to the Cloudflare Worker proxy mid-stream to ensure uninterrupted playback.
* **Smart Cooldown**: Implements a rolling 6-hour cooldown period to reset usage tracking effectively.
* **Cloudflare Error 1027 Handling**: Added dedicated exception logic to handle Cloudflare proxy error codes, boosting overall stream reliability.

---

## 🛠️ Installation & Getting Started
1. **Download the ZIP**: Grab `plugin.video.megastreamer_0.4.zip` from the release assets.
2. **Install in Kodi**: 
   * Navigate to **Settings** -> **Add-ons** -> **Install from zip file**.
   * Select the downloaded ZIP file.
3. **Configure Account**:
   * Long-press or right-click **megastreamer** -> select **Settings (Einstellungen)**.
   * Enter your Mega.nz credentials under the accounts tab, or configure Google Drive under the GDrive tab.
4. **Stream away!** Browse your cloud drives, import batch links, or stream public folders immediately.

---

## ☕ Support the Project (Buy Me A Coffee)
If you love `megastreamer` and want to support its continued development, feel free to buy me a coffee!

👉 **[Support this project on Buy Me A Coffee](https://buymeacoffee.com/Anti.gravity)**

---

> [!WARNING]
> **Disclaimer:** Use of this add-on is entirely at your own risk. This project has no affiliation with Mega.nz or Google (no endorsement) and is neither supported nor approved by them. Licensed under the **GNU General Public License v3.0 (GPLv3)**.
