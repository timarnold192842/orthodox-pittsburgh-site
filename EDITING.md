# Editing the site content

All editable text and photos live in **`content.json`**. The website reads that
file and fills in the page, so you never edit HTML directly. You can change it
two ways:

## Option A — Visual editor (recommended)

This runs the admin panel on your own computer. No login or password needed.

1. Open the Terminal app and go to the project folder:
   ```sh
   cd "/Users/tarnold/Library/Mobile Documents/com~apple~CloudDocs/Notebooks/orthodoxpittsburgh"
   ```
2. Start the two helpers (leave both running):
   ```sh
   # Terminal window 1 — serves the website
   python3 -m http.server 8765

   # Terminal window 2 — lets the editor save changes
   npx decap-server
   ```
3. In a browser, open **http://localhost:8765/admin/**
4. Edit the fields, then click **Save**. Your changes are written straight to
   `content.json`.
5. Preview the result at **http://localhost:8765/index.html**

## Option B — Edit the file by hand

Open `content.json` in any text editor and change the wording. Keep the quotes
and commas intact (it's a JSON file). Save when done.

## Publishing your changes to the live site

Editing locally only changes your copy. To put the changes online:

```sh
cd "/Users/tarnold/Library/Mobile Documents/com~apple~CloudDocs/Notebooks/orthodoxpittsburgh"
git add -A
git commit -m "Update content"
git push
```

GitHub Pages rebuilds automatically a minute or two after the push.

---

### Why isn't there a "Login" on the live site?

The admin panel's **Login** button on the published site shows *"Not Found"* on
purpose for now — public login needs an extra OAuth service that GitHub Pages
can't host. Editing happens locally (Option A) until that's set up. The page
itself is unaffected; only the admin login is disabled online.
