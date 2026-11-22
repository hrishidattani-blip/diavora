# Diavora Phase 2 setup

Diavora keeps using the existing `dayflow_final_v1` browser storage. Accounts add private cloud sync; the app still works locally while signed out or offline.

## Adult help and account ownership

The developer is 13. A parent or guardian should review Supabase's current Terms of Service and create/own the Supabase project if required in your country. Do not enter a parent's payment card or accept a legal agreement without their permission.

## 1. Create the backend

1. With a parent or guardian, create a Supabase project at https://supabase.com/dashboard.
2. Open **SQL Editor**, paste all of `supabase-setup.sql`, and run it.
3. In **Authentication → URL Configuration**, set the Site URL to `https://hrishidattani-blip.github.io/diavora/` and add the same URL as a redirect URL.
4. Keep email confirmation enabled for public use.

## 2. Connect this site

1. In Supabase, open the project's **Connect** dialog.
2. Copy the Project URL and the **publishable** key (`sb_publishable_...`).
3. Put those two values in `config.js`.

The publishable key is designed for browser code and is restricted by Row Level Security. Never paste a secret key (`sb_secret_...`) or legacy `service_role` key into this repository, `config.js`, GitHub, screenshots, or chat.

## 3. Test before publishing

Serve the folder from a local web server (ES modules do not work reliably from a `file://` URL). Verify:

- The existing routine is still present before signing in.
- A new account receives a confirmation email.
- After confirming and signing in, the header says **Saved to cloud**.
- A change made in one browser appears after signing in on another.
- Signing out leaves local saving working.
- In Supabase Table Editor, two test users cannot access each other's rows (the included RLS policies enforce this).

## 4. Publish with GitHub Pages

Commit and push `index.html`, `config.js`, `supabase-setup.sql`, and this guide to the `main` branch. In GitHub, check **Actions** until the Pages deployment succeeds, then open the live site in a private window and repeat the login/sync test. A commit alone is not proof that deployment succeeded.
