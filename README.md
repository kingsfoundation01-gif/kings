# UNIPOD design lab attendance

A static website (no server to run) hosted free on GitHub Pages, with Firebase as the database.

## What you need
1. A free GitHub account
2. A free Google account (for Firebase)
3. The 4 files in this folder: `index.html`, `firebase-config.js`, `firestore.rules`, `README.md`

## Step 1: Create the Firebase project
1. Go to https://console.firebase.google.com and click **Add project**. Name it `unipod-attendance`.
2. **Build > Firestore Database > Create database**. Choose a location and **Production mode**.
3. **Build > Authentication > Get started**. Under **Sign-in method**, enable **Anonymous** and **Email/Password**.
4. **Project settings (gear icon) > Your apps > Web (`</>`)**. Register an app and copy the `firebaseConfig` values.
5. Paste those values into `firebase-config.js`.

## Step 2: Set the security rules
Open **Firestore Database > Rules**, replace everything with the contents of `firestore.rules`, and click **Publish**.
These rules are what keep the data private. Do not skip them.

## Step 3: Create your admin account(s)
1. **Authentication > Users > Add user**. Enter the admin's email and a strong password. Copy the **User UID** shown.
2. **Firestore Database > Start collection**. Collection ID: `admins`. Document ID: paste the **User UID**. Add any one field (for example `role` = `admin`). Save.
3. Repeat for each admin.

## Step 4: Put it on GitHub Pages
1. On GitHub, create a new repository (for example `unipod-attendance`).
2. Upload `index.html`, `firebase-config.js`, `firestore.rules`, `README.md`.
3. **Settings > Pages**. Under **Build and deployment**, set Source to **Deploy from a branch**, branch `main`, folder `/ (root)`. Save.
4. After a minute your site is live at `https://YOUR-USERNAME.github.io/unipod-attendance/`.

## Step 5: Allow your site address in Firebase
**Authentication > Settings > Authorized domains > Add domain**: `YOUR-USERNAME.github.io`.

## Step 6: Start using it
1. Open the site, click **Admin login**, and sign in with an admin email.
2. Go to **Staff list** and add every worker's name.
3. Share the site link with workers. They search their name and press Sign in or Sign out. No login needed.

## Notes
- The Firebase config values are not secrets. The security rules protect the data.
- Workers use anonymous sign-in behind the scenes, so only people using the site can read names or write records.
- Anyone who has the link can sign in as any listed name. If you need stricter control, ask for a per-worker PIN version.
- To clear data later: Firestore Database > delete the `attendance` and `status` collections.
