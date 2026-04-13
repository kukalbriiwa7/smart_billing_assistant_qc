# Smart Billing Assistant QC — email login setup

## Recommended stack
- Frontend: GitHub Pages
- Auth + database: Supabase
- Login method: email OTP (6-digit code)

## Files you need
- `index.html`
- `manifest.json`
- `supabase_setup.sql`

## 1) Create a Supabase project
Create a free Supabase project and wait for it to finish provisioning.

## 2) Create the database table
Open the SQL Editor in Supabase and run the contents of `supabase_setup.sql`.

## 3) Enable email OTP instead of magic link
In Supabase:
- Go to **Authentication → URL Configuration**
- Set **Site URL** to your GitHub Pages URL
- Add the same GitHub Pages URL to allowed redirect URLs if needed

Then:
- Go to **Authentication → Email Templates**
- Open the **Magic Link** template
- Replace the template body with something that includes `{{ .Token }}`

Example template:

```html
<h2>Code de connexion</h2>
<p>Votre code Smart Billing Assistant QC est :</p>
<p style="font-size: 28px; font-weight: 700; letter-spacing: 4px;">{{ .Token }}</p>
<p>Ce code expire bientôt. Si vous n'avez pas demandé cette connexion, ignorez ce message.</p>
```

## 4) Get your public project keys
In Supabase:
- Go to **Project Settings → API**
- Copy:
  - Project URL
  - `anon` public key

## 5) Paste them into `index.html`
Find this block:

```js
const SUPABASE_CONFIG = {
  url: 'REPLACE_WITH_YOUR_SUPABASE_URL',
  anonKey: 'REPLACE_WITH_YOUR_SUPABASE_ANON_KEY'
};
```

Replace the placeholders with your real values.

## 6) Push to GitHub Pages
Commit and push the updated files to your GitHub repo. GitHub Pages can continue serving the frontend; Supabase will handle auth and storage.

## 7) First login behavior
- User enters email
- Supabase emails a 6-digit code
- User enters the code in the app
- The app loads that user's private case history from Supabase
- Future edits auto-sync to the cloud

## 8) Important note on privacy
This app stores sensitive clinical billing-related information. Before real-world deployment, you should review institutional privacy, PHI handling, device security, audit logging, and retention requirements.
