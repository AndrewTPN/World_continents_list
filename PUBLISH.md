# How to publish this project

Your app is a **static site** (HTML + JS + CSS, no server needed). Here are simple ways to put it online.

---

## Make it live (no Git, no push)

### A. Netlify Drop — drag & drop

1. Open **[netlify.com/drop](https://app.netlify.com/drop)** in your browser.
2. Drag your **project folder** (`World_continents_list` — the one that contains `index.html` and `py_world.html`) onto the page.
3. Netlify uploads it and gives you a **live URL** (e.g. `random-name-123.netlify.app`). That’s your live site. No Git, no push.

### B. Vercel from your PC — one command

1. Open a terminal in your project folder:
   ```bash
   cd e:\git\World_continents_list
   ```
2. Run:
   ```bash
   npx vercel
   ```
3. Log in or sign up when asked. Accept the defaults (just press Enter).
4. Vercel deploys your folder and prints a **live URL** (e.g. `world-continents-list-xxx.vercel.app`). No Git push needed.

---

## Option 1: GitHub Pages (if you use Git)

You already have a Git repo. If it’s on **GitHub**, you can host it with GitHub Pages.

### 1. Push your code to GitHub

If you haven’t already:

```bash
git add .
git commit -m "Add index redirect and publish guide"
git push origin main
```

If the repo doesn’t exist on GitHub yet:

1. Go to [github.com](https://github.com) → **New repository**.
2. Name it (e.g. `World_continents_list`), create it **without** initializing with a README.
3. In your project folder, add the remote and push:

```bash
git remote add origin https://github.com/YOUR_USERNAME/World_continents_list.git
git branch -M main
git push -u origin main
```

### 2. Turn on GitHub Pages

1. Open your repo on GitHub.
2. Go to **Settings** → **Pages** (left sidebar).
3. Under **Source**, choose **Deploy from a branch**.
4. Branch: **main**, folder: **/ (root)**.
5. Click **Save**.

### 3. Get your live URL

After a minute or two, the site will be at:

- **https://YOUR_USERNAME.github.io/World_continents_list/**

Opening that URL will load `index.html`, which redirects to `py_world.html` (your “My World – Book” app).

---

## Option 2: Netlify (drag & drop, free)

1. Go to [netlify.com](https://www.netlify.com) and sign up / log in.
2. Drag your **project folder** (the one containing `py_world.html` and `index.html`) onto the Netlify “Deploy” area.
3. Netlify will give you a URL like `random-name-123.netlify.app`. You can change it in **Site settings** → **Domain management**.

---

## Option 3: Vercel (free)

1. Go to [vercel.com](https://vercel.com) and sign up (e.g. with GitHub).
2. Click **Add New** → **Project** and import your **GitHub repo** (or upload the folder).
3. **Important:** Set **Root Directory** to `.` or leave it **blank** (so the repo root with `index.html` and `py_world.html` is used). Do not set it to a subfolder.
4. **Build and Output:** Leave **Build Command** empty. **Output Directory** should be empty or `.`.
5. Deploy. You’ll get a URL like `world-continents-list.vercel.app`.

---

## Fixing 404 NOT_FOUND (Vercel)

If you see **404: NOT_FOUND** (Code: NOT_FOUND, ID: pdx1::…):

1. **Check the URL**  
   Use the exact deployment URL Vercel shows (e.g. `https://your-project.vercel.app`). Don’t add a path unless you mean to open a specific file (e.g. `/py_world.html`).

2. **Root Directory**  
   In Vercel: **Project → Settings → General → Root Directory**.  
   It must be **empty** or **`.`** so that `index.html` and `py_world.html` at the repo root are deployed. If it points to a subfolder (e.g. `New folder`), change it to `.` and redeploy.

3. **Redeploy after fixing**  
   After changing settings or adding `vercel.json`, go to **Deployments** → … on the latest deployment → **Redeploy**.

4. **Try the app directly**  
   If the root still 404s, open:  
   `https://your-project.vercel.app/py_world.html`  
   If that works, the files are deployed and the issue is the root redirect; then fix **Root Directory** as above and ensure `index.html` is in the repo root.

---

## Summary

- **Easiest if you use GitHub:** Option 1 (GitHub Pages).  
- **Easiest if you don’t want to use Git:** Option 2 (Netlify drag & drop).

The `index.html` in this repo redirects to `py_world.html`, so when someone visits the root of your site they’ll see your app.
