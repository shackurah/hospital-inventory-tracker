# Phase 2 Setup Guide — Getting Your App Live

You now have 5 files: `index.html`, `manifest.json`, `sw.js`, `icon-192.png`, `icon-512.png`.

Offline features and "install to phone" only work when the app is served over **https**, not opened directly as a file. The easiest free way to do that with zero coding is **GitHub Pages**.

## Step 1: Put your Apps Script URL into the app

1. Open `index.html` in any text editor (Notepad, TextEdit, or even Google Docs → "Plain text" mode).
2. Near the top of the `<script>` section (search for `CONFIG`), find this line:
   ```
   APPS_SCRIPT_URL: "PASTE_YOUR_APPS_SCRIPT_URL_HERE"
   ```
3. Replace the text between the quotes with the Web App URL you copied in Phase 1, so it looks like:
   ```
   APPS_SCRIPT_URL: "https://script.google.com/macros/s/AKfycb.../exec"
   ```
4. Save the file.

(Tip: you can skip this step and instead click "Set it now" on the login screen after the app is live — it'll ask you to paste the URL and remember it on that device. Editing the file is better if multiple people will use the app, so everyone gets it automatically.)

## Step 2: Create a GitHub account (skip if you have one)

1. Go to **github.com** → **Sign up**. Free.

## Step 3: Create a repository for the app

1. Click the **+** icon (top-right) → **New repository**.
2. Name it: `hospital-inventory-tracker`
3. Set it to **Public**.
4. Click **Create repository**.

## Step 4: Upload your files

1. On your new repository page, click **Add file** → **Upload files**.
2. Drag in all 5 files: `index.html`, `manifest.json`, `sw.js`, `icon-192.png`, `icon-512.png`.
3. Click **Commit changes**.

## Step 5: Turn on GitHub Pages

1. In your repository, click **Settings** (top menu).
2. In the left sidebar, click **Pages**.
3. Under "Branch," select `main` and folder `/ (root)`. Click **Save**.
4. Wait about a minute, then refresh the page. You'll see a message like:
   `Your site is live at https://yourusername.github.io/hospital-inventory-tracker/`
5. That link is your live app. Open it.

## Step 6: Install it like a real app

- **On a phone**: open the link in Chrome or Safari → tap the browser menu → **Add to Home Screen**. It now behaves like a normal app icon, works offline, no browser bar.
- **On a computer**: open the link in Chrome → click the install icon (⊕) in the address bar.

## Step 7: Log in

Use one of the username/password rows you added to the `Users` tab in your Google Sheet back in Phase 1.

## Making updates later

Whenever you want to change the app (colors, text, features), edit the file, go back to your GitHub repository → click on the file → click the pencil (edit) icon → paste the updated content → **Commit changes**. The live link updates automatically within a minute.

---

### What each part does, so future changes are easy
- **`index.html`** — the entire app: login, dashboard, inventory, forms, offline logic. Everything visual lives here.
- **`manifest.json`** — tells phones/browsers this is an installable app, and what icon/name to use.
- **`sw.js`** — the "service worker": lets the app open even with no signal, by keeping a saved copy of the app shell on the device.
- **`Code.gs`** (in Google Apps Script, not this folder) — the backend that reads/writes your Google Sheet.
