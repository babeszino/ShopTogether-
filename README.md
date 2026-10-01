# ShopTogether!

A shared shopping list that opens in the iPhone browser. Same link on both phones, updates live.

- Add items by name; the other phone sees them instantly.
- Tap the circle to check an item off when it's in the cart.
- "Done with shopping" at the bottom clears everything that's checked.
- Shows who added each item. Works offline in the store and syncs when signal returns.

It's a single static page (`index.html`) plus Firebase (free tier) for the live sync.
No Mac, no App Store, no install.

## Setup (about 10 minutes, all from Windows)

### 1. Firebase
1. <https://console.firebase.google.com> → **Add project** (skip Analytics).
2. **Build → Authentication → Get started → Sign-in method → Anonymous → Enable.**
3. **Build → Firestore Database → Create database** (production mode, region e.g. `eur3`).
4. Firestore → **Rules** → paste the contents of `firestore.rules` → **Publish**.
5. **Project settings (gear) → Your apps → Web (`</>`)** → register an app (no hosting needed).
   Copy the `firebaseConfig` values into `firebase-config.js`.

### 2. Put it online (GitHub Pages)
1. Commit and push this folder to a GitHub repo (`git add . && git commit -m "web app" && git push`).
2. On GitHub: repo → **Settings → Pages → Build from branch → `main` / root → Save**.
3. After a minute your site is at `https://<your-username>.github.io/<repo-name>/`.

### 3. Use it
1. Open that address on your iPhone. Enter your name. The address now ends in `#something`.
   **That full link is your shared list.**
2. Tap the share button (top right) and send the link to your girlfriend. She opens it, enters her name, done.
3. Optional: in Safari tap Share → **Add to Home Screen** for an app-like icon.
   (Do this from the full link with the `#…` part.)

Anyone with the full link can edit the list, so keep it between you two.

## Troubleshooting
- "One-time setup needed" screen → `firebase-config.js` still has the placeholder values.
- "Missing or insufficient permissions" → rules not published, or Anonymous sign-in not enabled.
- Sign-in error mentioning the domain → Authentication → Settings → Authorized domains → add `<your-username>.github.io`.
- Test locally first: `npx serve .` in this folder (opening the file directly won't work because of ES modules).
