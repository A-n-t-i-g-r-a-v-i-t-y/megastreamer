# 🚀 meg·a·stream·er
/ˈmɛɡəˌstriːmər/

noun

1. Software & Tech. An advanced, highly optimized video add-on built natively for Kodi designed to stream, traverse, and automatically decrypt public shared folders and private files hosted on the Mega.nz cloud service in real-time, eliminating the need for local storage or pre-downloads.
2. Usage. A tool that bypasses traditional cloud storage barriers, allowing instant playback and connection keep-alive optimizations.


With `megastreamer`, you can access, stream, and automatically decrypt both **public Mega links** and your **private Mega Cloud Drive** files directly inside Kodi, without downloading them first.

---

## 📦 Repository Structure & Versions

This repository offers both the base and the latest versions of the addon side-by-side:

*   **📁 [`plugin.video.megastreamer-0.2`](plugin.video.megastreamer-0.2)**: The active, latest **Version 0.2** of the addon. It features a complete multi-account manager, deep public shared folder traversal, batch file imports with custom CSV metadata, custom premium icons, and generic root/nested key decryption.
*   **📁 [`plugin.video.megastreamer-0.1`](plugin.video.megastreamer-0.1)**: The first **Version 0.1** of the addon, offering the baseline core client for private accounts.

---

## 📖 Background & History

The story behind megastreamer (v0.1):

1. **Inspiration:** The addon is inspired by the work of **MrDini123** (`movieshark` / `megastream`). As Mega.nz is a very popular resource it has always bothered me, that there was no easy solution to import and/or stream files/folders on Mega.nz from within Kodi. It seems to have remained a sore spot for users worldwide.
2. **Expanded Focus:** It has been enhanced so that it allows the user to browse and stream any media elements directly from their **private Mega account**.
3. **Human & AI Hand-in-Hand (Antigravity):** The addon was created during a longer recovery/convalescence period as a fun "sandbox project" to explore the capabilities of **Antigravity** The effective "programming time" of v0.1 was about **1.5-2 hours**, v,0.2 took another 2 hours due to some technical hiccups, but for most parts was realized by Antigravity and **without any advanced programming experience** on my part, as the AI autonomously managed the complex implementation steps.
4. **Hardened from Real-World Testing:** During development, early test versions repeatedly triggered automatic account lockdowns due to Mega.nz's aggressive bot-detection systems detecting "suspicious activity". These lessons have been incorporated directly into the hardening architecture of this final version (including intelligent AES-encrypted session caching and authentic browser spoofing), meaning this **no longer happens** in the release version.

> [!WARNING]
> **Disclaimer:** Use of this addon is entirely at your own risk. This project has no affiliation with Mega.nz (no endorsement) and is neither supported nor approved by Mega.nz.

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
    *   **`plugin.video.megastreamer_0.2.zip`** (Version 0.2)
    *   **`plugin.video.megastreamer_0.1.zip`** (Version 0.1)
2.  Rename the file to `plugin.video.megastreamer.zip` 
3. In Kodi, go to **Settings -> Add-ons -> Install from zip file** and select the desiredZIP file.
4.  Right-click (or long-press) the **megastreamer** addon, choose **Settings (Einstellungen)**, and enter your Mega.nz E-Mail and Password.
5.  Open the addon to access your private Cloud Drive, import batch links, or stream public files!

---

## 📄 License

This project is licensed under the **GNU General Public License v3.0 (GPLv3)**. 

### Why GPLv3?
1.  **Modern Library Compatibility:** Full compatibility with modern Python libraries (such as Apache 2.0 licensed dependencies).
2.  **Anti-Tivoization Protection:** Guarantees that users retain the right to modify and run the code on any device it's installed on.
3.  **Patent Security:** Includes explicit patent grants from contributors to protect users and developers against patent litigation.

See [LICENSE.md](LICENSE.md) for the full license text.

THE SOFTWARE IS PROVIDED 'AS IS', WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

## ☕ Support the Project (Buy Me A Coffee)
If you find `megastreamer` useful and want to support its development, feel free to buy my human a coffee!

👉 **[Support this project on Buy Me A Coffee](https://buymeacoffee.com/Anti.gravity)**
