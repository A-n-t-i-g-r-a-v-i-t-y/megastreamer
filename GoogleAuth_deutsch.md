# Google Drive Einrichtung & Authentifizierung für MegaStreamer v0.4

Diese Anleitung führt Sie Schritt für Schritt durch die Einrichtung Ihrer eigenen Google OAuth-Zugangsdaten für MegaStreamer. 

## 🛠️ Teil 1: Google Cloud Console einrichten

### 1. Projekt erstellen
1. Öffnen Sie die [Google Cloud Console](https://console.cloud.google.com/).
2. Melden Sie sich mit Ihrem Google-Konto (Gmail) an.
3. Klicken Sie oben links auf das Projekt-Dropdown und wählen Sie **Neues Projekt** (New Project).
4. Geben Sie dem Projekt einen beliebigen Namen (z. B. `MegaStreamer-Cloud`) und klicken Sie auf **Erstellen**.

### 2. Google Drive API aktivieren
1. Stellen Sie sicher, dass oben links Ihr neu erstelltes Projekt ausgewählt ist.
2. Suchen Sie in der oberen Suchleiste nach **Google Drive API** und klicken Sie darauf.
3. Klicken Sie auf den blauen Button **Aktivieren** (Enable).

### 3. OAuth-Zustimmungsbildschirm konfigurieren (Sehr wichtig!)
1. Wählen Sie im linken Menü **OAuth-Zustimmungsbildschirm** (OAuth consent screen).
2. Wählen Sie als Nutzertyp **Extern** (External) und klicken Sie auf **Erstellen** (Create).
3. **App-Informationen ausfüllen**:
   * *App-Name*: `MegaStreamer Desktop`
   * *Nutzer-Support-E-Mail*: Ihre eigene E-Mail-Adresse auswählen.
   * *E-Mail-Adressen für Entwickler*: Ihre eigene E-Mail-Adresse eintragen.
4. Klicken Sie unten auf **Speichern und fortfahren** (Save and continue).
5. Überspringen Sie den Schritt *Berechtigungen* (Scopes) durch Klicken auf **Speichern und fortfahren**.

### 4. Testnutzer hinzufügen (Zwingend erforderlich!)
Da Ihre App im Google-Sicherheitsstatus "Testing" (Testphase) bleibt, erlaubt Google den Zugriff **ausschließlich** für explizit eingetragene Testkonten.
1. Scrollen Sie im OAuth-Zustimmungsbildschirm zum Bereich **Testnutzer** (Test users).
2. Klicken Sie auf **+ Add Users** (Nutzer hinzufügen).
3. Geben Sie die **E-Mail-Adresse Ihres eigenen Google-Kontos** ein (mit dem Sie später auf Ihr Google Drive in Kodi zugreifen möchten).
4. Klicken Sie auf **Speichern** (Save) und dann auf **Speichern und fortfahren**.

### 5. Desktop-Anmeldedaten erstellen
1. Wählen Sie im linken Menü **Anmeldedaten** (Credentials).
2. Klicken Sie oben auf **+ Anmeldedaten erstellen** (Create Credentials) und wählen Sie **OAuth-Client-ID**.
3. Wählen Sie als *Anwendungstyp* zwingend: **Desktop-Anwendung** (Desktop App).
4. Geben Sie der ID einen beliebigen Namen (z. B. `MegaStreamer-Zugang`) und klicken Sie auf **Erstellen**.
5. Ein Pop-up zeigt Ihnen nun Ihre **Client-ID** (eine sehr lange Zeichenkette) und Ihr **Client-Secret** an. Kopieren Sie beide Werte!

---

## 📺 Teil 2: Verbindung in MegaStreamer herstellen

### 1. Zugangsdaten in Kodi eintragen
1. Starten Sie Kodi und öffnen Sie die **Einstellungen** des MegaStreamer Addons.
2. Navigieren Sie zur Kategorie **Google Drive**.
3. Aktivieren Sie den Button **Google Drive aktivieren**.
4. Tragen Sie Ihre kopierte **Client-ID** und Ihr **Client-Secret** in die entsprechenden Felder ein.
5. Klicken Sie auf **OK / Speichern**.

### 2. Autorisierung starten
1. Navigieren Sie im MegaStreamer Addon-Hauptmenü auf den Ordner **"Mein Google Drive"**.
2. Kodi fragt Sie, ob Sie die Verbindung jetzt herstellen möchten. Wählen Sie **Ja**.
3. **Automatischer Login**: MegaStreamer öffnet nun automatisch Ihren Webbrowser (auf PC/Linux) mit dem Anmeldebildschirm.
4. **Sicherheitswarnung umgehen (Wichtig!)**:
   * Google zeigt eine Warnmeldung: *"Google hat diese App nicht überprüft"* (App not verified) oder *"Die Anfrage von MegaStreamer Desktop ist unsicher"*.
   * Keine Sorge, das ist völlig normal bei eigenen privaten Apps!
   * Klicken Sie links unten auf **Erweitert** (Advanced).
   * Klicken Sie auf den Link **Weiter zu MegaStreamer Desktop (unsicher)** (Go to MegaStreamer Desktop (unsafe)).
5. Wählen Sie Ihr Google-Konto aus und klicken Sie auf **Zulassen / Erlauben**.
6. Sobald Ihr Webbrowser die Meldung *"✔ Erfolgreich autorisiert! Sie können dieses Fenster schließen"* anzeigt, schließt sich das Fortschrittsfenster in Kodi automatisch.

**Herzlichen Glückwunsch! Ihr Google Drive ist nun vollständig und sicher in Kodi integriert!**
