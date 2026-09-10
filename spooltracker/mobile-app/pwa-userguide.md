# SpoolTracker App — User Guide

This guide explains how to use the SpoolTracker app day-to-day: logging in, scanning spools, working offline, and finding past scans. No technical background needed.

---

## 1. Logging In

When you open the app, you'll be asked for a code to connect to your project. There are two kinds of codes:

- **Project Code (8 characters)** — This is a "quick access" code. Anyone with this code can open that specific project right away — no account or password required. This is typically the code shared for a single jobsite or project.
- **Organization Code (10 characters)** — This code requires you to also sign in with a personal SpoolTracker account. Once signed in, you're not limited to one project — you can switch between every project your account belongs to.

The app remembers codes you've used before and will suggest them the next time you log in, so you don't have to re-enter them every time.

**Signing in with an account:**

- On the web (browser), tapping "Sign in with SpoolTracker" takes you to the SpoolTracker login page and brings you right back once you're signed in.
- On the mobile app (iPhone/Android), the same sign-in opens your phone's browser to complete the login, then returns you to the app automatically.

Either way, you'll end up back in the app, signed in and ready to go.

**What can I access?**

- If you logged in with a **Project Code**, you'll see that one project's dashboard and scan history.
- If you signed in with an **Organization Code and account**, you'll see a project picker and can switch between any project you're a member of, and your scan history/analytics will reflect the projects you have access to.

**Logging out:** Use the menu to "Logout" (leaves your current project) or "Logout [your name]" (also signs your account out of the app). Note that signing out of the app doesn't necessarily sign you out of the SpoolTracker website if you also use that separately.

---

## 2. Getting Around the App

The bottom of the screen has a navigation bar with a few stops:

- **Home** — Your main dashboard, showing recent scans for the project.
- **Scan** (the button in the middle) — Jumps straight to the camera to scan a spool.
- **Overview** — Charts and summaries of scanning activity (see Section 6).
- **Spooly** — A help/chat link if you need support.

At the top of the Home screen, a menu (☰) gives you access to language settings, light/dark mode, sharing your project code, switching projects, and signing out. Your account avatar (if signed in) lets you sign in or out of your personal account.

---

## 3. Creating a Scan

To record a scan of a spool:

1. Tap the **+ New Scan** button on the dashboard, or the **Scan** button in the bottom navigation.
2. The camera will open. The first time you do this, the app will ask permission to use your camera — allow it so scanning works. (If you accidentally denied permission earlier, the app will show you a button that takes you straight to your phone's settings to fix it.)
3. Point your camera at the QR code on the spool. You can also use a handheld barcode scanner if your team uses one — it works the same way.
4. When the code is read successfully, your phone will vibrate or beep and the screen will flash briefly to confirm the scan worked.
5. If you accidentally scan a spool that belongs to a different project, the app will warn you instead of silently accepting it.

**Scanning multiple spools in a row:** There's a "multi-scan" mode you can turn on if you're processing a batch of spools — it keeps the camera open so you can scan several in a row (up to a set limit) before finishing up.

**After scanning**, you'll see a short form to fill out:

- Choose the **status/type** of scan (e.g., what stage this spool is at).
- Optionally start a **timer**, if the task you're recording is timed.
- Add any **notes**.
- Attach up to **4 photos**.
- Your **location** is captured automatically — no need to type an address.

Tap **Confirm** to save. The scan appears in your dashboard immediately — you don't have to wait for it to finish uploading.

---

## 4. What Happens After You Confirm a Scan

- If you have an internet connection, the scan uploads in the background right away.
- If you don't have a connection, the scan is saved on your device and marked **"Pending Sync."** See the next section for what that means.
- Your location shows as raw coordinates at first; once the scan syncs, it's automatically converted into a readable street address.

---

## 5. Working Offline

The app is designed to keep working even with no signal — useful in warehouses, remote jobsites, or areas with poor coverage.

- If you lose your connection, an **orange banner** appears at the top of the screen letting you know you're offline. You can collapse this banner if it's in your way.
- **You can still scan spools while offline** — the camera, the form, photos, and location all work exactly the same without internet.
- Scans made offline are saved to your device and show up in your history tagged **"Pending Sync."**
- Once your connection comes back, pending scans **sync automatically** in the background. You'll briefly see a "Syncing…" message. There's also a **"Sync All"** button if you want to trigger it yourself.
- If a scan can't upload after a few tries, it will be clearly flagged so you know to check it — you can **Retry** it or **Delete** it if it was made in error. Nothing gets lost silently.
- Even without a connection (or without signing in), you can still browse everything you've already scanned and view full-size photos on your device.

**Bottom line:** you never need to wait for a connection to keep working. Scan as normal, and the app will catch up on uploads once you're back online.

---

## 6. Searching and Filtering Your Scans

On the Home dashboard, you can narrow down the scan list using the search bar:

- **Type a name** to search for a specific spool — the list filters as soon as you tap away from the search box.
- **Filter by date** — tap the calendar icon to pick a "From" and "To" date, then tap **Apply**. (The filter only kicks in once both dates are chosen, so partial date entries won't jump the gun.)
- **Filter by scanning a QR code** — tap the QR icon in the search bar to scan a spool's code directly; the list will filter to show just that item's history.
- A **Clear (X)** button appears whenever a filter is active, so you can quickly reset the list back to everything.

The list also supports **pull-to-refresh** (swipe down to refresh) and **loads more automatically** as you scroll.

---

## 7. Viewing Scan Details

Tap any scan in the list to open its details:

- View all photos attached to that scan, and pinch to zoom in.
- Read any notes that were added.
- Follow a link to open the full record in the SpoolTracker Dashboard website for more detailed information.

---

## 8. Analytics / Overview

The **Overview** tab in the bottom navigation shows summary charts of scanning activity:

- A breakdown of scans by type.
- Scan activity over time, which you can view by hour, day, week, or month.
- If you're signed in with an organization account, you can search and switch between projects right from this screen to see their activity.

---

## 9. Settings

You can reach the Settings screen from the menu (☰) on the Home screen. Here's what you'll find:

**Device Information**
- **Device ID** — a read-only reference number for this device. You can't change it, but it's useful if you ever need support and are asked to identify your device.
- **Device Name** — a name you can type in yourself (e.g., "Warehouse Tablet 2") to tell devices apart if your team shares equipment.

**Account**
- If you're signed in, you'll see "Signed in as [your name]," a shortcut to the Overview/analytics screen, and a **Sign Out** button (it will ask you to confirm before signing you out).
- If you're not signed in, you'll see a **Sign In** button instead.

**Scan Settings**
- **Multi-Scan Limit** — set how many spools you can scan in a row during multi-scan mode before it stops (anywhere from 2 to 100; default is 25).
- **Default Scan Type** — pick a scan status/type that's automatically pre-selected every time you start a new scan, so you don't have to choose it manually each time. You can also leave this set to "No default."

**Permissions**
This section shows the status of the three permissions the app relies on — **Camera**, **Location**, and **Notifications** — each labeled Granted, Denied, Not Requested, or Unsupported:
- If a permission hasn't been requested yet, there's a button to grant it right there.
- If a permission was denied and you're using the mobile app, a button takes you directly to your phone's settings for that permission.
- If you're using the app in a browser and denied a permission, you'll see either a link or simple written instructions for turning it back on.
- **Notifications** has an extra on/off switch once allowed, so you can turn notifications on or off without changing your phone's permission itself.
- Each permission includes a short note explaining why the app needs it. The screen automatically double-checks these whenever you come back to the app, so it's always showing the current status.

**Install the App** (web browser only — not shown in the iPhone/Android app, since it's already installed)
- Tells you whether your browser supports "installing" SpoolTracker to your home screen like a regular app.
- If it does, a button walks you through the install steps for your specific browser.
- If it doesn't, you'll see a short list of browsers that do support it.

**Share Access** (only appears if you logged in with a Project Code)
- Shows your project's share code as both text and a scannable QR code, plus a copyable link — an easy way to hand off access to a coworker without having to read the code out loud.

**App Information**
- Shows the current app version number.
- A **"View Updates"** button shows what's new in recent app updates.

---

## 10. Terms and Conditions

The first time you use the app, you'll be shown the Terms and Conditions and asked to **Accept** them before you can continue. You'll only need to do this once — after accepting, the app won't ask again.

---

## Quick Reference

| I want to... | Where to go |
|---|---|
| Log in | Enter your project or organization code on the login screen |
| Scan a spool | Tap **+ New Scan** or the **Scan** button in the bottom bar |
| Find a past scan | Use the search bar, date filter, or QR filter on Home |
| Work without internet | Just keep scanning — look for "Pending Sync" and the offline banner |
| See charts/trends | Tap **Overview** in the bottom bar |
| Switch projects | Use the menu (☰) → Change Project (organization accounts only) |
| Get help | Tap **Spooly** in the bottom bar |
| Change camera/location/notification permissions | Menu (☰) → Settings → Permissions |
| Set a default scan type or multi-scan limit | Menu (☰) → Settings → Scan Settings |
| Share your project access with a coworker | Menu (☰) → Settings → Share Access |
| Install the app to your home screen (browser only) | Menu (☰) → Settings → Install the App |

