# 🚀 megastreamer (v0.1 to v0.5)

An advanced, secure, and lightning-fast **Mega.nz** and **Google Drive** streaming client natively built as a Kodi Video Addon.

With `megastreamer`, you can access, stream, and automatically decrypt both **public Mega links** and your **private Mega and Google Drive cloud storage** directly inside Kodi, without downloading them first.

---

⚡ What’s New in Version 0.5

Version 0.5 adds GoFile.io streaming support as well as the ability to browse and stream directly from your favorite Debrid services (Real-Debrid, Premiumize.me, AllDebrid, EasyDebrid, and Offcloud, tested only with Offcloud, but in principle it should work). 

📂 1. Native GoFile.io Integration 
Browse and stream media directly from your GoFile.io cloud folders! MegaStreamer now parses folder contents, manages
sessions, and plays back video files seamlessly in your Kodi interface.

⚙️ 2. Manual Salt Override 
The current salt value is hardcoded, but Gofile.io may change it at their own discretion some time in the future. If that
happens and the current salt is no longer valid, streaming may fail. There are fallback routines in place to check if a new salt
key is already published. In addition to these fallback routines, you can desalinate a local copy of GoFile.io yourself using our
GoFile Desalinator Companion and enter the new salt value in settings, which will override the hardcoded salt value until a
new update is published. 

🧪 3. GoFile Desalinator Companion 
Alongside the addon, we designed a local browser-based decryption app: Gofile Desalinator.html. * Native Browser
Execution: Simply double-click the HTML page to run it locally in any web browser (Chrome, Opera, Firefox). * Drag-and
Drop Parsing: Drop your local wt.js or wt.obf.js script onto the interface. These files are part of the files and folders
saved when you open GoFile.io in your browser and choose to save the webpage (“Save As…”). 

---

🚀 megastreamer v0.4a Release

Fixed a small human-originated mistake, which may have prevented the Cloudflare Worker from being invoked correctly.
That was entirely my mistake and due to improper handling of multiple "beta" versions of the same release, and I apologize... 

I stumbled upon this mistake by checking my CloudWorker backend logs.

Nothing else has changed, but the Cloudworker now works as intended.

---

## 📦 Repository Structure & Versions

This repository offers both the base and the latest versions of the addon side-by-side:

*   **📁 plugin.video.megastreamer_0.4a**: fixed a human error. 
*   **📁 plugin.video.megastreamer_0.4**: The active, latest **Version 0.4** of the addon. It features native **Google Drive Integration**, automated local Loopback OAuth 2.0 flow, secure client secret encryption, and a custom copyright-compliant brushed metal menu artwork.
*   **📁 plugin.video.megastreamer_0.3**: The previous **Version 0.3** of the addon featuring smart quota management, automatic Cloudflare proxy fallback, and enhanced stream stability.
*   **📁 plugin.video.megastreamer_0.2**: The previous **Version 0.2** of the addon featuring a complete multi-account manager, deep public shared folder traversal, batch file imports with custom CSV metadata, custom premium icons, and generic root/nested key decryption.
*   **📁 plugin.video.megastreamer_0.1**: The first **Version 0.1** of the addon, offering the baseline core client for private accounts.

---

## 📖 Background & History

The story behind megastreamer (v0.1):

1. **Inspiration:** The addon is inspired by the work of **MrDini123** (`movieshark` / `megastream`).
2. **Expanded Focus:** It has been enhanced so that it allows the user to browse and stream any media elements directly from their **private Mega account**.
3. **Human & AI Hand-in-Hand (Antigravity):** The addon was created during a longer recovery/convalescence period as a fun "sandbox project" to explore the capabilities of **Antigravity** The effective "programming time" of v0.1 was about **1.5-2 hours**, v,0.2 took another 2 hours due to some technical hiccups, but for most parts was realized by Antigravity and **without any advanced programming experience** on my part, as the AI autonomously managed the complex implementation steps.
4. **Hardened from Real-World Testing:** During development, early test versions repeatedly triggered automatic account lockdowns due to Mega.nz's aggressive bot-detection systems detecting "suspicious activity". These lessons have been incorporated directly into the hardening architecture of this final version (including intelligent AES-encrypted session caching and authentic browser spoofing), meaning this **no longer happens** in the release version.

> [!WARNING]
> **Disclaimer:** Use of this addon is entirely at your own risk. This project has no affiliation with Mega.nz (no endorsement) and is neither supported nor approved by Mega.nz.

---

## 🚀 What's New in Version 0.4 (Changelog & Enhancements)

Version 0.4 introduces native Google Drive integration with automated Loopback authentication, a persistent background service architecture, hardened cross-platform configuration safety, custom menu artwork, and a dedicated setup workflow.

### 1. 📂 Native Google Drive Integration
*   **What it is:** MegaStreamer now natively supports browsing and streaming media directly from your personal Google Drive account.
*   **Why it matters:** Access your entire Google Drive library directly within Kodi alongside your Mega cloud storage files.

### 🔑 2. Automated Loopback OAuth 2.0 Flow & Manual Fallback
*   **What it is:** Relies on a built-in background loopback server (`127.0.0.1:53682`) to automatically capture the Google authorization code, with a manual text input fallback if needed.
*   **Why it matters:** Bypasses Google's strict blocks on TV/Limited-input devices by performing the login seamlessly inside your standard system web browser.

### 🛡️ 3. Mandatory Custom Credentials & External Setup
*   **What it is:** Setting up Google Drive requires generating your own Google Cloud credentials (Client ID and Secret). Public shared keys are no longer supported.
*   **Setup Notice:** This process requires a few initial steps outside Kodi (registering a project, configuring the OAuth screen under "Testing" status, adding your Gmail as a "Test User", and bypassing Google's app verification warning). Detailed step-by-step instructions are available in the [GoogleAuth_deutsch.md](GoogleAuth_deutsch.md) and [GoogleAuth_english.md](GoogleAuth_english.md) guides.

### 🔄 4. Persistent Background Service Architecture & Absolute Imports
*   **What it is:** Migrated the core streaming server from a blocking plugin script to a persistent `xbmc.service` running in the background. Structured with absolute path bootstrapping and absolute imports.
*   **Why it matters:** Ensures lightning-fast folder navigation, lower playback start times, and eliminates Python standalone execution errors ("Streaming Service nicht aktiv") during Kodi startup.

### 🔒 5. Force Cloudflare Worker Toggle (100% Anonymity/Privacy)
*   **What it is:** Added a toggle to route **all** Mega.nz traffic directly through a Cloudflare Worker, bypassing IP quota checks entirely. Includes automatic failsafe protection that refuses to fallback to your direct IP if the worker fails.
*   **Why it matters:** Guarantees 100% traffic obfuscation and privacy from your ISP, ensuring your real IP address is never leaked.

---

## 🚀 What's New in Version 0.3 (Changelog & Enhancements)

Version 0.3 introduces advanced quota management, Cloudflare worker proxy optimizations, and improved playback stability.

### 1. 📊 Smart Quota Management & Cloudflare Proxy
*   **What it is:** The addon now tracks your cumulative data usage locally.
*   **Why it matters:** It automatically reduces unnecessary Cloudflare Worker usage by only triggering the proxy once a 4.9 GB threshold is reached.

### 2. 🔄 Automatic Fallback for Bandwidth Limits (HTTP 509)
*   **What it is:** A robust fallback mechanism that seamlessly catches HTTP 509 (Bandwidth Limit Exceeded) errors.
*   **Why it matters:** Ensures uninterrupted streaming by automatically switching to the proxy when your primary IP quota is exhausted.

### 3. ⏱️ Smart Cooldown Management
*   **What it is:** Implements a cooldown period to reset usage tracking effectively.
*   **Why it matters:** Keeps your quota tracking accurate over time and optimizes when the proxy is utilized.

### 4. 🛠️ Cloudflare Error 1027 Handling
*   **What it is:** Added specific logic to properly handle Cloudflare Error 1027.
*   **Why it matters:** Increases overall stream stability when interacting with the proxy.

---

## 🔄 What's New in Version 0.2 (Changelog & Enhancements)

Version 0.2 represents a leap forward in stability, navigation, cross-platform compatibility, and customizability over the initial release. The key differences and improvements are detailed below:

### 1. 👥 Multi-Account Support (Slot System)
*   **What it is:** While Version 0.1 only supported a single login credential, Version 0.2 introduces a robust multi-slot account management system.
*   **Why it matters:** You can now configure multiple Mega accounts in the addon settings and seamlessly switch the active account. Assign distinct accounts for private cloud browsing versus public link streaming to manage bandwidth quotas dynamically.

### 2. 📂 Public Shared Folder Traversal & Key Decryption Overhaul
*   **Resolved API Constraint:** 
*   **Overhauled Decryption:**

### 3. 📥 OS-Independent Batch Link Import (Custom CSV-style Metadata)
*   **What it is:** The import interface was restructured to be fully platform-agnostic to ensure 100% compatibility across Android, Linux, Windows, macOS, and more.
*   **Rich Semicolon Format:** Supports loading list files (`.txt` or `.links`) with optional semicolon metadata:
    ```text
    <MEGA_URL>;[Custom Name];[Category/Genre];[Year]
    ```
*   **Instant API Bypass:** When a custom name is supplied, the importer skips resolving the name via the MEGA API. This prevents rate limits, handles dead/expired links gracefully, and registers imports instantaneously.
*   **Persistency:** Saved persistently in the addon data directory in `imported.json`.

### 🗂️ 4. Rich Native Kodi Metadata Display & Alphabetical Sorting
*   **What it is:** In Version 0.1, listings had no sorted order and lacked rich metadata. Version 0.2 implements a strict, elegant **Folders-First** alphabetical ascending sorting across private cloud browsing, public folder trees, and imported libraries.
*   **Natively Mapped Info:** Parsed categories (genres) and release years are bound directly to Kodi's native metadata engine (`listitem.setInfo('video')`), allowing seamless integration with premium Kodi skins.

### 5. 🔀 "Play All" Playlist Generation
*   **What it is:** Added a prominent "[ Alle abspielen (Playlist) ]" command at the top of every shared public directory.
*   **Why it matters:** Easily queue all playable media items in any public shared folder as a standard Kodi playlist, enabling consecutive playback with standard player controls.


### 🌐 6. Bilingual Localization
*   **What it is:** Added full localized translation support for German (`de_de`) and English (`en_gb`) for all settings, dialogs, context menus, and menu descriptions.

---

## ✨ Features (Core Architecture)

Both versions of the addon share a core streaming architecture:
*   **⚡ Connection Keep-Alive Engine:** Reuses open TCP/TLS sockets for incredibly snappy seeking (skipping forward/backward) and stutter-free streaming.
*   **🔒 Transparent Credential Encryption:** Passwords stored in settings are automatically encrypted on-disk using military-grade **AES-CBC** (`crypto_utils.py`), ensuring your credentials are never exposed in plaintext.
*   **💾 Persistent Session Caching:** Bypasses aggressive Mega anti-bot triggers and account lockdowns by securely caching active login sessions in a local `session.json` profile.
*   **🌐 Native Kodi Video Plugin:** Registered as a native `plugin.video.megastreamer`, enabling full integration with Kodi's Video Addon category and supporting standard Kodi GUI uninstallation.
*   **🛡️ Bot Detection Avoidance:** Blends into standard web traffic using authentic Chrome browser agent signatures, Origin, and Referer headers.

---

## 🔧 Installation & Setup

1.  Download or package the compiled ZIP file for your preferred version:
    *   **`plugin.video.megastreamer_0.4.zip`** (Version 0.4 - Latest Release)
    *   **`plugin.video.megastreamer_0.3.zip`** (Version 0.3)
    *   **`plugin.video.megastreamer_0.2.zip`** (Version 0.2)
    *   **`plugin.video.megastreamer_0.1.zip`** (Version 0.1)
2.  Rename the file to `plugin.video.megastreamer.zip` 
3. In Kodi, go to **Settings -> Add-ons -> Install from zip file** and select the desiredZIP file.
4.  Right-click (or long-press) the **megastreamer** addon, choose **Settings (Einstellungen)**, and enter your Mega.nz E-Mail and Password.
5.  Open the addon to access your private Cloud Drive, import batch links, or stream public files!

---

## ☕ Support the Project (Buy Me A Coffee)

If you find `megastreamer` useful and want to support its continued development, feel free to buy me a coffee!

[![Support on Buy Me A Coffee](coffee.png)](https://buymeacoffee.com/Anti.gravity)

👉 **[Support this project on Buy Me A Coffee](https://buymeacoffee.com/Anti.gravity)**

---

## 📄 License

This project is licensed under the **GNU General Public License v3.0 (GPLv3)**. 

### Why GPLv3?
1.  **Modern Library Compatibility:** Full compatibility with modern Python libraries (such as Apache 2.0 licensed dependencies).
2.  **Anti-Tivoization Protection:** Guarantees that users retain the right to modify and run the code on any device it's installed on.
3.  **Patent Security:** Includes explicit patent grants from contributors to protect users and developers against patent litigation.

See [LICENSE.md](LICENSE.md) for the full license text.

THE SOFTWARE IS PROVIDED 'AS IS', WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
