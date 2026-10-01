# ShopTogether!

A shared shopping list that opens in the iPhone browser. Accounts, invitations, live sync.

- Sign in with email + password. Everyone opens the same site address.
- Create a named shopping list and invite your partner by email.
- They sign up with that email, accept the invitation, and the list is on both front pages from then on.
- Tap a list to open it: add items, tap the circle to check them off, "Done with shopping" clears what's checked.
- Everything updates live on both phones. Works offline in the store and syncs when signal returns.

Single static page (`index.html`) + Firebase (free tier): Authentication + Firestore.

## Firebase setup

1. **Authentication → Sign-in method → Email/Password → Enable** (leave "Email link" off). You can disable Anonymous now.
2. **Firestore Database → Rules** → replace everything with the contents of `firestore.rules` → **Publish**.
3. `firebase-config.js` must contain your web app config (already done if the site loaded before).

## Deploy (GitHub Pages)

```powershell
git add .
git commit -m "Accounts and invitations"
git push
```
The site updates a minute later. If your phone still shows the old version, reload or close the tab and reopen it.

## Using it

1. Both of you open the site address, tap **Create an account**, enter name + email + password.
2. One of you taps **New shopping list**, names it, and types the other person's email (the one they signed up with).
3. The other person signs in and sees the invitation on the front page → **Accept**.
4. Optional: in Safari tap Share → **Add to Home Screen**.

Invitations match the exact email address. Lists can be renamed (✎), extended with more people, or deleted by their creator.

## Troubleshooting
- "Email/password sign-in isn't enabled" → step 1 above.
- "You don't have permission…" → the rules from step 2 aren't published.
- Forgot password → "Forgot password?" on the sign-in screen sends a reset email.
- Test locally: `npx serve .` in this folder (opening the file directly won't work because of ES modules).

Note: invitations trust the email on the account; there is no email-verification step. Fine for two people, but don't invite an address you don't control.
