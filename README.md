# Vendor Payment Tracker

Single-page web app (no build step) for tracking vendor bills:

**Operations** adds the bill (gross amount only) → **Product / Marketing Manager** approves or denies → **Accounts** adds TDS + UTR and pays → bill moves to **Completed**. A *Payment Advice* PDF can be downloaded for any completed bill.

## Hosting
GitHub Pages: *Settings → Pages → Deploy from branch → `main` / root*. The site is just `index.html`.

## Logins
Defined at the top of the script in `index.html` (`USERS`). Passwords are stored only as SHA-256 hashes of `username:password`.
To change a password: open the live page, press **F12 → Console**, run

```js
makeHash('username', 'new-password').then(console.log)
```

and paste the printed value into that user's `h:` field.

## Important limitations
- Data is saved in each person's **own browser** (localStorage). Different people/devices do **not** see each other's bills yet. A shared backend (e.g. Supabase) is needed for real team use.
- Login runs in the browser, so it only keeps casual visitors out — it is not real security. Do not rely on it for sensitive data; add a backend with proper auth before storing real bills.
