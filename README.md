# Brewing Time

A filter coffee recipe book with a guided brew timer, recipe scaling, bean and gear notes, and sync between devices through a private GitHub Gist.

It is a single `index.html` with no build step and no server.

## 1. Host it on GitHub Pages

1. Create a new repository on GitHub, for example `brewing-time`. It can be public or private. Pages on a private repo needs a paid plan.
2. Upload `index.html` (and this README) to the repository's root. Use **Add file → Upload files**, then commit.
3. Go to **Settings → Pages**. Under **Build and deployment**, choose **Deploy from a branch**, pick `main` and `/ (root)`, then save.
4. After a minute your app is live at `https://<your-username>.github.io/brewing-time/`.

Tip: on your phone, open the address and use **Add to Home Screen** so it opens like an app.

## 2. Turn on sync between devices

Recipes are always saved in the browser you're using. Sync also copies them to a **secret gist** in your GitHub account, so all your devices share the same recipes.

1. Create a token at <https://github.com/settings/tokens/new?scopes=gist&description=Brewing%20Time>:
   - Type: **Personal access token (classic)**
   - Scope: **gist** only (nothing else)
   - Expiration: your choice. When it expires, create a new one and paste it in again.
2. In the app, press **Sync**, paste the token, then press **Connect**.
   - The first device creates a secret gist named `pour-notes.json`.
   - Every other device finds that gist on its own. Just paste the same token on each device.

### How syncing works

- The app pulls from the gist when it opens, when you return to the tab, and every few minutes while it's open.
- It pushes about 3 seconds after you save, favourite or delete a recipe.
- Changes are merged recipe by recipe, and the newest edit of each recipe wins. Deletes carry over to your other devices too.
- Editing the same recipe on two devices at almost the same moment keeps the later edit.
- If you're offline, the app keeps working and syncs once you're back online.

### About the token

- The token is stored only in that browser's local storage. It is never written into the HTML or the repository, so don't commit it anywhere.
- With only the `gist` scope, the token can read and write your gists and nothing else in your account.
- On a shared computer, press **Sync → Disconnect this device** when you're done. You can revoke the token at any time at <https://github.com/settings/tokens>.
- A secret gist is unlisted, not encrypted. Anyone who has its URL can read it, so don't put anything private in your recipe notes.

## Backup

**Backup** lets you copy or download all your recipes as JSON, and paste a backup back in to restore it. This works with or without sync.

## Moving recipes from the Claude version

Open the old app, press **Backup → Copy backup**, then paste the text under **Backup → Import recipes** in the GitHub version.
