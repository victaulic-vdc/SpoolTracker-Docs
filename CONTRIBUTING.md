# Contributing to the Victaulic Docs

This guide is for non-developers on Windows who want to edit these documentation pages and submit changes for review. No prior git experience is required.

You will:

1. Install three free tools (one-time).
2. Get a copy of this repository on your computer (one-time).
3. Open the folder in Obsidian and edit pages.
4. Save your changes and submit them for review (a "pull request").

If you only want to read the docs, ignore this file — they are published at the SpoolTracker dashboard `/docs` page.

---

## 1. One-time setup

### 1a. Get a GitHub account

If you do not already have one, create a free account at <https://github.com>. Use your Victaulic email so the maintainer can identify you.

Then **send your GitHub username to Daniel Cleary** and ask to be added as a collaborator on `victaulic-vdc/SpoolTracker-Docs`. This lets you submit edits without forking the repo.

### 1b. Install GitHub Desktop

GitHub Desktop is a visual tool that hides the git command line. It is the recommended way to interact with this repo if you are not a developer.

1. Download from <https://desktop.github.com/> and run the installer.
2. When it opens, sign in with your GitHub account.
3. When prompted for your name and email, use your real name and your Victaulic email.

### 1c. Install Obsidian

Obsidian edits markdown files, which is exactly what this repo is made of.

1. Download from <https://obsidian.md/> and run the installer.
2. You do not need an Obsidian account.

### 1d. Configure Obsidian once you open the vault

After cloning the repo (next section), open it in Obsidian. Then go to **Settings → Files & Links** and set:

- **Use [[Wikilinks]]** → **Off**
- **New link format** → **Relative path to file**

This keeps Obsidian's link style consistent with the rest of the repo. If you skip this, your new links will look different from existing ones and may break on the published site.

---

## 2. Get a copy of the repository

This step happens once per computer.

1. Open GitHub Desktop.
2. **File → Clone repository** (or `Ctrl+Shift+O`).
3. Choose the **URL** tab and paste:

   ```
   https://github.com/victaulic-vdc/SpoolTracker-Docs
   ```

4. **Local path** — pick a folder you'll remember, e.g. `C:\Users\<you>\Documents\GitHub\SpoolTracker-Docs`. Avoid OneDrive folders — they sometimes interfere.
5. Click **Clone**. GitHub Desktop downloads the repo.

Now open it in Obsidian:

1. Open Obsidian.
2. **Open folder as vault** → select the folder you just cloned.
3. Apply the settings from step 1d above.

You're set up. From now on, you only need to do the workflow in the next section.

---

## 3. The editing workflow

Every time you want to make changes, follow these four steps in order. Do not skip step 1 or step 2 — they prevent the most common problems.

### Step 1 — Get the latest changes

1. Open GitHub Desktop.
2. Make sure **Current branch** at the top says `master`. If it does not, click it and pick `master`.
3. Click **Fetch origin** (top right). If it changes to **Pull origin**, click that too.

This pulls down anything other people have changed since your last edit.

### Step 2 — Create a branch for your edits

A "branch" is a private workspace for your changes. Never edit directly on `master`.

1. In GitHub Desktop, click **Current branch** at the top → **New branch**.
2. Name it after what you're changing, e.g. `update-mobile-app-screenshots` or `fix-typo-overview`. Use dashes, no spaces.
3. Click **Create branch**.

The top of the GitHub Desktop window should now show your new branch name.

### Step 3 — Edit in Obsidian

1. Switch to Obsidian. Open the markdown file you want to change in the left-hand file tree.
2. Edit normally. Obsidian saves automatically — no Ctrl+S needed.
3. To **add an image**, drag-and-drop it into the editor. Important: Obsidian by default puts images at the vault root. **Move the image into the nearest `images/` folder** that sits beside the markdown file you are editing (e.g. `spooltracker/dashboard/images/`), then update the link path. This keeps things organized and matches how the rest of the docs are structured.
4. To **preview** how your page will look published, switch Obsidian to Reading view (top-right toggle, or `Ctrl+E`).

### Step 4 — Save your changes and submit them

1. Switch to GitHub Desktop. You'll see a list of files you changed on the left.
2. Tick the boxes next to the files you want to include (usually all of them).
3. At the bottom-left, fill in a **Summary** — one short sentence, e.g. *"Update mobile-app screenshots for new login screen"*. Description is optional.
4. Click **Commit to <your-branch-name>**.
5. Click **Publish branch** (top right). This sends your branch to GitHub.
6. GitHub Desktop will then offer **Create Pull Request**. Click it. Your browser opens to GitHub.com.
7. On the pull request page:
   - **Base branch** should be `master`.
   - **Compare branch** should be your branch.
   - Write a brief description of what changed and why.
   - Click **Create pull request**.

Your edits are now submitted. **Daniel will get notified, review your changes, and either merge them or request changes.**

---

## 4. After the pull request is opened

- **If reviewer requests changes**: edit the same files in Obsidian, then in GitHub Desktop commit again on the same branch, then click **Push origin**. The pull request updates automatically — you do not open a new one.
- **Once merged**: switch GitHub Desktop's branch back to `master` and click **Fetch / Pull origin** to pick up your now-merged changes. You can delete your old branch (Branch menu → Delete) — it's no longer needed.

---

## 5. Tips and rules

- **One topic per pull request.** If you're updating mobile app docs and fixing a typo in the VTFR overview, make those two separate branches and two separate pull requests. It makes reviews much faster.
- **Commit often.** Small commits with clear messages are easier to review than one huge commit at the end.
- **Don't edit on `master` directly.** If GitHub Desktop ever shows you have changes while on `master`, stop and ask before doing anything — there's a recovery procedure but it's easier to just avoid the mistake.
- **Images** belong in the nearest `images/` folder. Use lowercase, dashes, descriptive filenames: `mobile-app-login-screen.png`, not `IMG_1234.PNG`.
- **Don't commit** `.docx` files or anything in `.obsidian/` — these are already ignored, but double-check the file list before committing.
- **If you're unsure**, ask before pushing. Daniel would rather answer a question than untangle a merged mistake.

---

## 6. Trouble?

| Problem | What to do |
|---|---|
| GitHub Desktop says "this branch is X commits behind master" | Switch to `master`, **Pull origin**, switch back to your branch, then **Branch → Update from master**. |
| Obsidian shows broken image links | Confirm the image is in an `images/` folder next to the markdown file, and the link path is relative (e.g. `images/foo.png`, not `/images/foo.png`). |
| You committed to `master` by mistake | Don't push. Tell Daniel — there's a clean fix but it's easier with a second pair of eyes. |
| You can't push (permission denied) | You probably weren't added as a collaborator yet. Ping Daniel with your GitHub username. |
| Anything else weird | Take a screenshot of GitHub Desktop and send it. |

---

## Alternative: tiny edits without installing anything

For a quick typo fix, you can skip everything above:

1. Open the file on GitHub.com.
2. Click the pencil icon (top right of the file view).
3. Edit, then scroll down and fill in **Propose changes** with a short summary.
4. Click **Propose changes** → **Create pull request**.

GitHub handles the branch and pull request automatically. This is fine for one-line fixes, but for anything bigger, use the Obsidian workflow above.
