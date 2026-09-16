# Galle Rent Bike & Tours — Website

## Files

| File | What it is |
|---|---|
| `index.html` | The public website. Fully self-contained — all images are embedded, no `images/` folder needed. |
| `admin.html` | Staff panel for editing bikes and tours. Password is set in the code (line ~153). |
| `google-sheet-booking-script.gs` | Apps Script code for logging bookings to Google Sheets. Not uploaded to the site — paste into Google Apps Script. |

## Uploading to GitHub Pages

1. Create a new repository on GitHub
2. Upload `index.html` and `admin.html` (the `images/` folder is NOT required — images are embedded)
3. Go to repo **Settings → Pages**
4. Under "Source", pick branch `main` and folder `/ (root)`, click Save
5. Wait ~1 minute. Your site will be at `https://YOURUSERNAME.github.io/REPONAME/`
6. Admin panel will be at `https://YOURUSERNAME.github.io/REPONAME/admin.html`

## IMPORTANT — read before going live

### 1. The admin password is NOT secure
`admin.html` checks the password in browser code. Anyone can open the page source
and read it. On a **public** GitHub repo, anyone can also read it straight from your
repository files.

This is fine as a "keep casual visitors out" lock. It is NOT protection for anything
sensitive. Never put customer data, payment info, or private notes in this panel.

To change the password: open `admin.html`, find `const PASSWORD = "galle2026";`
and change it. Consider making the GitHub repo **private** (Settings → General →
Danger Zone → Change visibility) — GitHub Pages still works on private repos with
a paid plan, or use Netlify's free password protection instead.

### 2. Admin edits are per-browser, NOT global
Edits in the admin panel save to that browser's local storage only.

- You edit a bike price on your laptop → **you** see the change
- A customer opens the site on their phone → they see the **original** defaults

For edits to show for everyone, you need a real backend/database. Until then, the
admin panel is best used as your own working list — when you want a change to go
live for customers, tell Claude and it gets written into `index.html` directly.

### 3. Booking form → Google Sheets
`index.html` posts booking form submissions to your Apps Script URL. If bookings
aren't appearing in your Sheet, the usual causes are:

- The Apps Script was created standalone at script.google.com instead of via
  **Extensions → Apps Script from inside the Sheet**. It must be bound to the Sheet,
  otherwise `getActiveSpreadsheet()` returns nothing and it silently fails.
- Deployment "Who has access" is not set to **Anyone**
- The script was edited after deploying without pushing a **New version**

Check **Executions** in the Apps Script sidebar to see real errors.

### 4. Things still to confirm before publishing
- Vehicle prices and the 3 tuk tuk rates (Electric $18 / New $20 were placeholder guesses)
- Tour itineraries, durations and pricing
- Deposit, ID and insurance policy wording
- Replace stock tuk tuk/car/tour photos with your own
