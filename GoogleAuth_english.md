# Google Drive Setup & Authentication Guide for MegaStreamer v0.4

This guide will walk you through setting up your private Google OAuth credentials to successfully link Google Drive with MegaStreamer in Kodi.


## 🛠️ Part 1: Google Cloud Console Configuration

### 1. Create a New Project
1. Open the [Google Cloud Console](https://console.cloud.google.com/).
2. Log in with your standard Google Account (Gmail).
3. Click the project dropdown menu in the upper-left corner and click **New Project**.
4. Give your project a recognizable name (e.g., `MegaStreamer-Cloud`) and click **Create**.

### 2. Enable the Google Drive API
1. Ensure your newly created project is selected in the upper-left project dropdown.
2. In the top search bar, search for **Google Drive API** and click on it.
3. Click the blue **Enable** button.

### 3. Configure the OAuth Consent Screen (Crucial!)
1. Click **OAuth consent screen** in the left sidebar menu.
2. Under User Type, select **External** and click **Create**.
3. **Fill in App Information**:
   * *App name*: `MegaStreamer Desktop`
   * *User support email*: Select your Gmail address from the dropdown list.
   * *Developer contact information*: Enter your own Gmail address.
4. Click **Save and Continue** at the bottom.
5. Skip the *Scopes* screen by clicking **Save and Continue** again.

### 4. Add a Test User (Mandatory!)
Since your private app remains in the "Testing" publishing status, Google strictly restricts access to accounts that are explicitly registered as test users.
1. Scroll down to the **Test users** section on the OAuth consent screen.
2. Click the **+ Add Users** button.
3. Enter your **own Google email address** (the exact account you want to connect to Google Drive inside Kodi).
4. Click **Save** and then click **Save and Continue** at the bottom.

### 5. Create Desktop Credentials
1. Click **Credentials** in the left sidebar menu.
2. Click **+ Create Credentials** at the top and select **OAuth client ID**.
3. Under *Application type*, you MUST select: **Desktop app** (Desktop-Anwendung).
4. Give the client a name (e.g., `MegaStreamer-Access`) and click **Create**.
5. A pop-up dialog will appear displaying your **Client ID** and **Client Secret**. Copy both values securely!

---

## 📺 Part 2: Connect MegaStreamer in Kodi

### 1. Insert Credentials in Kodi
1. Start Kodi and open the **Settings** panel for the MegaStreamer addon.
2. Navigate to the **Google Drive** category tab on the left.
3. Turn on the **Enable Google Drive** toggle button.
4. Paste your copied **Client ID** and **Client Secret** into the designated input fields.
5. Click **OK / Save** to store the credentials (they are securely encrypted instantly).

### 2. Start the Connection Flow
1. Open the MegaStreamer addon main directory and click on **"Mein Google Drive" / "My Google Drive"**.
2. Kodi will prompt you if you want to establish the connection now. Select **Yes**.
3. **Automatic Web Login**: MegaStreamer will launch your system's default web browser (on PC/Linux) showing Google's sign-in page.
4. **Bypassing the Security Warning (Important!)**:
   * Google will show a warning screen saying: *"Google hasn't verified this app"* or *"This request is unsecure"*.
   * This is normal and expected for private, self-hosted developer credentials!
   * Click **Advanced** in the bottom-left corner of the warning.
   * Click the link **Go to MegaStreamer Desktop (unsafe)** at the bottom.
5. Select your Google account and click **Allow**.
6. Once the browser page displays *"✔ Successfully authorized! You can close this window now"*, return to Kodi. The progress dialog in Kodi will have closed automatically.

**Congratulations! Your personal Google Drive is now safely integrated and ready to stream in Kodi!**
