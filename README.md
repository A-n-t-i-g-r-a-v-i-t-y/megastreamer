# 🚀 megastreamer v0.1

An advanced, secure, and lightning-fast **Mega.nz** streaming client and decrypter natively built as a Kodi Video Addon.

With `megastreamer`, you can access, stream, and automatically decrypt **Mega Cloud Drive** files directly inside Kodi, without downloading them first.

---

## 📖 Background & History

The story behind megastreamer:

1. **Inspiration:** The addon is inspired by the work of **MrDini123** (`movieshark` / `megastream`).
2. **Expanded Focus:** It has been enhanced so that it allows the user to browse and stream any media elements directly from their **private Mega account**.
3. **Human & AI Hand-in-Hand (Antigravity):** The addon was created during a longer recovery/convalescence period as a fun "sandbox project" to explore the capabilities of Google's **Antigravity** (Advanced Agentic Coding AI / Gemini 3.5 Flash Medium). The effective "programming time" was only about **2-3 hours**, achieved **without any prior programming experience** on the user's part, as the AI autonomously managed the complex implementation steps.
4. **Hardened from Real-World Testing:** During development, early test versions repeatedly triggered automatic account lockdowns due to Mega.nz's aggressive bot-detection systems detecting "suspicious activity". These lessons have been incorporated directly into the hardening architecture of this final version (including intelligent AES-encrypted session caching and authentic browser spoofing), meaning this **no longer happens** in the release version.

> [!WARNING]
> **Disclaimer:** Use of this addon is entirely at your own risk. This project has no affiliation with Mega.nz (no endorsement) and is neither supported nor approved by Mega.nz.

---

## ✨ Features

*   **⚡ Connection Keep-Alive Engine:** Reuses open TCP/TLS sockets for incredibly snappy seeking (skipping forward/backward) and stutter-free streaming.
*   **🔒 Transparent Credential Encryption:** Passwords stored in settings are automatically encrypted on-disk using military-grade **AES-CBC** (`crypto_utils.py`), ensuring your credentials are never exposed in plaintext.
*   **💾 Persistent Session Caching:** Bypasses aggressive Mega anti-bot triggers and account lockdowns by securely caching active login sessions in a local `session.json` profile.
*   **🌐 Native Kodi Video Plugin:** Registered as a native `plugin.video.megastreamer`, enabling full integration with Kodi's Video Addon category and supporting standard Kodi GUI uninstallation.
*   **🛡️ Bot Detection Avoidance:** Blends into standard web traffic using authentic Chrome browser agent signatures, Origin, and Referer headers.

---

## 🔧 Installation & Setup

1.  Download the compiled **`plugin.video.megastreamer.zip`** package.
2.  In Kodi, go to **Settings -> Add-ons -> Install from zip file** and select the ZIP file.
3.  Right-click (or long-press) the **megastreamer** addon, choose **Settings (Einstellungen)**, and enter your Mega.nz E-Mail and Password.
4.  Open the addon to access your private Cloud Drive or stream public files!

---

## 📄 License

This project is licensed under the **GNU General Public License v3.0 (GPLv3)**. 

### Why GPLv3?
1.  **Modern Library Compatibility:** Full compatibility with modern Python libraries (such as Apache 2.0 licensed dependencies).
2.  **Anti-Tivoization Protection:** Guarantees that users retain the right to modify and run the code on any device it's installed on.
3.  **Patent Security:** Includes explicit patent grants from contributors to protect users and developers against patent litigation.

See [LICENSE.md](LICENSE.md) for the full license text.
