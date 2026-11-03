# BFT Gladesville Roster

A staff view of the roster: Day and Week views, with a "My shifts" filter by coach. It reads the roster straight from a Google Sheet, so edits in the sheet show up on the page without touching this repo.

## Put it on GitHub Pages

1. On GitHub, create a new repository (for example `bft-roster`).
2. Upload `index.html` and `.nojekyll` to the main branch (Add file, then Upload files).
3. Open the repository's Settings, then Pages.
4. Under "Build and deployment", set Source to "Deploy from a branch", choose `main` and `/ (root)`, and save.
5. After a minute or two the site is live at `https://<your-username>.github.io/bft-roster/`.

Share that link with staff. On a phone they can use "Add to Home Screen" to keep it like an app.

## How the live updates work

The page fetches the published CSV link from the Google Sheet (the `CSV_URL` line near the bottom of `index.html`) when it opens and then every minute. The top right of the page says "Live from the roster sheet" when that is working.

If the link can't be reached, the page falls back to the built-in snapshot of the sheet (the `SNAPSHOT` block in `index.html`) and says "Sheet snapshot" instead. It is only a fallback and will go out of date.

Things to know:

- The sheet must stay published. In Google Sheets, File, Share, Publish to web, with the roster tab and the CSV format selected. Un-publishing it stops the page updating.
- Google refreshes published sheets every few minutes, so an edit can take a little while to appear.
- The sheet needs the columns `Date`, `Time`, `Session` and `Coach`, with dates like `16/11/2026` and times like `5:30 PM`. One row per coach per session.
- Only the one tab behind the link is shown. For more session types, add them to that tab or ask for the page to read several tabs.

## Privacy

GitHub Pages sites are public on the free plan, and the CSV link is public too. Anyone with either link can see the coach names and session times. Don't add anything private to the sheet tab behind it.

## Changing the look

Colours are the variables at the top of the `<style>` block in `index.html` (`--bg`, `--ink`, `--accent` and so on). The accent is `#00B5CC`.
