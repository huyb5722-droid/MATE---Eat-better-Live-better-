# MATE — website upload package

This folder contains the MATE web app ready to upload to GitHub. It includes the app code, logo, and selected real dish photos from `.image-audit/real-review`. The old `assets/recipes` image set and audit sheets are excluded. Recipes without a suitable real photo show the built-in food illustration.

## Upload to GitHub

Upload the **contents of this folder** so `package.json`, `server.js`, and `index.html` appear at the repository's top level. Keep `.env.example`; do not upload a real `.env` file or the generated `data/` folder. `.gitignore` excludes both.

## Deploy on Render

1. Create a Render **Web Service** connected to the GitHub repository.
2. Set **Build Command** to `npm install` and **Start Command** to `npm start`.
3. Add `HOST` = `0.0.0.0` and a new long secret as `MATE_ADMIN_TOKEN` in the service's Environment settings. Render supplies `PORT` automatically.
4. To keep account data after redeploys, attach a persistent disk at `/var/data` and set `MATE_DATA_DIR` = `/var/data`.
5. For the embedded map, set `MATE_GOOGLE_MAPS_EMBED_KEY` to a browser key restricted to Maps Embed API and the Render website referrer, for example `https://mate-eat-better-live-better.onrender.com/*`. For server-side nearby place results, set a separate `MATE_GOOGLE_MAPS_API_KEY` restricted to Places API (New).

If the deployed map reports an unauthorized site, add the exact Render hostname in Google Cloud's website restrictions and confirm Maps Embed API is enabled for that key. Never put the admin token or server-side Places key in browser code or GitHub.

## Run on Windows

Install Node.js 18 or newer and double-click `Run-MATE.bat`, or open a terminal in this folder and run `npm start`. Then visit `http://localhost:4173`.

## Included features

- Bilingual Vietnamese and English interface.
- Weekly meal planning, pantry matching, recipe search, and cooking instructions.
- Budget tracking, spending reminders, and preferences for health, taste, allergies, and cooking equipment.
- Nearby food shops and restaurants through Google Maps and optional Places API.
- Guest mode and account sign-in; account data is stored by the MATE server under `data/` or `MATE_DATA_DIR`.
- 203 recipes; recipes with matching photos use selected real images, and remaining recipes use the built-in illustration fallback.

Before making the repository public, confirm you have permission to publish each photo included in `assets/meal-photos`.
