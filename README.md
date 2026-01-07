<p align="center">
  <img src="logo.png" alt="PocketCode" width="600">
</p>

> ☁️ **Want more power?** Run on a $4/month cloud server instead → [**$4PocketCode**](https://github.com/rajbreno/4PocketCode)

# PocketCode

**Run AI coding agents (OpenCode, Claude Code, Gemini CLI) on Android.**

**Features:**
- **Secure Sandbox** — Your code stays private, other apps can't access it
- **Fast** — Runs natively on your phone's CPU, no cloud lag
- **One Command Setup** — Copy-paste and you're ready to code
- **Web + Terminal** — Use browser UI or terminal, your choice

> Works with **OpenCode**, **Claude Code**, **Codex**, and **Gemini CLI**.  
> This guide uses [OpenCode](https://opencode.ai).

---

## What You Need

- Android phone (6GB+ RAM, 5GB free storage)
- [Termux](https://play.google.com/store/apps/details?id=com.termux) from Play Store

---

## 🚀 Setup

> **Paste this single command in Termux and wait ~5 minutes:**

```
curl -sL https://raw.githubusercontent.com/rajbreno/PocketCode/main/setup.sh | bash
```

✅ **Done!** Type `pocketcode` to enter Linux, then `opencode` to start.

---

## 📁 Setting Up Your Project Folder (Acode)

**Step 1: Install Acode**
- Download [Acode](https://play.google.com/store/apps/details?id=com.foxdebug.acodefree) from Play Store

**Step 2: Connect Acode to Termux**
1. Open Acode → tap **☰ hamburger menu** (top left)
2. Tap **Open Folder** → **Add Storage** → **Select Folder**
3. Your phone storage opens → tap **☰ hamburger menu** again
4. Select **Termux** → tap **Use This Folder**
5. Back in Acode → tap **OK**
6. A **Home** folder appears → select it → tap **✓** (bottom right)

**Step 3: Create Your Projects Folder**
1. Go to **File Manager** in Acode → you'll see the **Home** folder
2. Long press **Home** → select **New Folder**
3. Name it `projects` → tap **OK**

✅ Done! Now create project folders inside `projects`.

---

## How to Use

Every time you open Termux, run:
```
pocketcode
```

**First time only** — link your Acode folder:
```
ln -s /data/data/com.termux/files/home/projects ~/projects
```

**Go to your project:**
```
cd projects/my-app
```

Then choose how you want to use the AI:

### 💻 Option 1: Terminal
```
opencode
```
Chat directly in Termux.

### 🌐 Option 2: Web Interface
```
opencode-web
```
Open Chrome → `localhost:4096`

---

## Building Your First Project

**Try it:** Tell the AI *"Create a website with a blue background"*

**Preview your website:**

| Project Type | Command | Port |
|--------------|---------|------|
| HTML / Static | `npx serve` | 3000 |
| Vite / React | `npm run build && npm run preview` | 4173 |
| Next.js | `npm run build && npm start` | 3000 |
| Expo | `npx expo start --tunnel` | Scan QR |

> **Tip:** `xdg-open http://localhost:<port>` opens the URL in your Android browser.

---

## Saving Your Work

⚠️ **Warning:** Uninstalling Termux deletes all your projects!

| Method | Best For | What It Does |
|--------|----------|--------------|
| **GitHub** ⭐ | Recommended | Saves to cloud, access from any device |
| **Local Backup** | Offline / No GitHub | Saves zip file to Downloads folder |

### ⭐ GitHub (Recommended)

**One-time setup:**
```
ssh-keygen -t ed25519 && cat ~/.ssh/id_ed25519.pub
```
Copy the key (select all the text that appears) and add it to [GitHub Settings](https://github.com/settings/keys).

**Save your project:** (replace `YOU` and `project` with your GitHub username and repo name)
```
cd ~/my-project && git init && git add . && git commit -m "save" && git remote add origin git@github.com:YOU/project.git && git push -u origin main
```

### 📁 Local Backup

Run these commands **from Termux** (exit Linux first):
```
exit
```
```
termux-setup-storage && tar -czvf ~/storage/downloads/pocketcode-backup.tar.gz ~/.proot-distro/
```
Your backup will be in the **Downloads** folder.

---

## Troubleshooting

| Problem | Fix |
|---------|-----|
| "Address already in use" | `pkill node` |
| Termux closes randomly | Pull down notification → tap **Acquire Wakelock** |
| Termux still closes | Settings → Apps → Termux → Battery → Unrestricted |

---

**Made with ❤️ for mobile developers.**
