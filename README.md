# Joie: home screen web app

Joie lives on your friends' home screens like an app. There's no App Store and nothing to download from a store: people open a link once and tap **Add to Home Screen**.

- It opens full-screen with the sunset icon.
- Friends join a trip with a **6-letter code**. No login is needed.
- Everything syncs live between phones and still works offline.
- Receipt photos can be read on the phone to fill in the amount and date.

It's free to run, using Firebase (Google) for the shared data and GitHub Pages for the link.

---

## 1. Firebase: shared data (about 10 minutes, free)

1. Go to **console.firebase.google.com**, click **Create a project**, and name it `joie`. Turn Google Analytics off.
2. **Turn on anonymous sign-in.** Go to **Build → Authentication → Get started → Sign-in method → Anonymous → Enable → Save**.
3. **Create the database.** Go to **Build → Firestore Database → Create database**.
   - Location: **asia-southeast1 (Singapore)**.
   - Start in **production mode**.
4. **Paste the security rules.** In Firestore, open the **Rules** tab, replace everything with the contents of `firestore.rules`, and click **Publish**.
5. **Get your settings.** Go to **Project settings** (the gear icon) → **Your apps** → click the **`</>` (Web)** icon.
   - Name it `joie` and register it. Skip "Firebase Hosting".
   - Firebase shows a `firebaseConfig = { ... }` block. Copy the values into **`config.js`** in place of the `PASTE_...` lines.

## 2. GitHub Pages: the link (about 5 minutes, free)

1. Sign in at **github.com** (create a free account if needed). Click **+ → New repository**.
   - Name it `joie`, choose **Public**, and click **Create**.
2. Click **uploading an existing file** and drag in **everything in this folder**: `index.html`, `config.js`, `manifest.webmanifest`, `sw.js`, and the `icons` folder. Click **Commit changes**.
3. Go to **Settings → Pages → Source: Deploy from a branch → Branch: main / (root) → Save**.
4. After about a minute your link appears, for example `https://YOURNAME.github.io/joie/`.

## 3. Put Joie on your iPhone

1. Open the link in **Safari**.
2. Tap **Share**, then **Add to Home Screen**, then **Add**.
3. Open Joie from the home screen, tap **Start a new trip**, and enter everyone's names.
4. Go to **People → Share** to send the link and trip code to your LINE group. Friends do the same three taps, then **Join a trip** with the code.

On Android, open the link in Chrome, tap **⋮**, then **Add to Home screen**.

---

**Updating later:** upload the changed file to GitHub again. Phones pick up the new version the next time they open Joie.

**Privacy:** only phones that entered a trip's code can see that trip. Anyone you give the code to can view and edit it, so share it only with your group.

**Receipt reading:** the first scan downloads a reading engine of about 10 MB, then it's cached. It works best on English and number receipts. Always check the filled-in fields before saving.
