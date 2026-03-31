# That's BS — Episode Planner
### Shine FM 99.9

A broadcast episode planner with Firebase Realtime Database sync and Google Sign-In.

---

## 🚀 Deploy to GitHub Pages

### Step 1 — Create a GitHub repository

1. Go to [github.com/new](https://github.com/new)
2. Name it anything, e.g. `thatsbs-planner`
3. Set it to **Public** (required for free GitHub Pages)
4. Click **Create repository**

### Step 2 — Upload the files

Either use the GitHub web UI (drag & drop `index.html` into the repo), or via Git:

```bash
git init
git add index.html
git commit -m "Initial deploy"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/thatsbs-planner.git
git push -u origin main
```

### Step 3 — Enable GitHub Pages

1. In your repo, go to **Settings → Pages**
2. Under **Source**, select **Deploy from a branch**
3. Choose branch: `main`, folder: `/ (root)`
4. Click **Save**

Your site will be live at:
```
https://YOUR_USERNAME.github.io/thatsbs-planner/
```

---

## 🔥 Configure Firebase

### Step 4 — Add your GitHub Pages domain to Firebase Auth

Google Sign-In will be blocked unless your domain is whitelisted.

1. Go to the [Firebase Console](https://console.firebase.google.com/)
2. Open your **that-s-bs** project
3. Go to **Authentication → Settings → Authorized domains**
4. Click **Add domain**
5. Enter: `YOUR_USERNAME.github.io`
6. Click **Add**

### Step 5 — Set Firebase Realtime Database rules

In the Firebase Console:

1. Go to **Realtime Database → Rules**
2. Replace the rules with the following:

```json
{
  "rules": {
    "users": {
      "$uid": {
        ".read": "$uid === auth.uid",
        ".write": "$uid === auth.uid"
      }
    }
  }
}
```

3. Click **Publish**

This ensures each signed-in user can only read and write their own data.

---

## 🗂 Data structure in Firebase

Episodes are stored at:
```
/users/{uid}/episodes/{episodeId}
```

Each episode contains: `id`, `title`, `airDate`, `topic`, `guests`, `notes`, `segments[]`, `createdAt`.

---

## ✅ That's it!

Visit your GitHub Pages URL, click **Sign in with Google**, and your episodes will sync to Firebase in real time.

