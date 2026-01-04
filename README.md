<p align="center">
  <img src="logo.png" alt="PocketCode" width="600">
</p>

# PocketCode

**Run AI coding agents (OpenCode, Claude Code, Gemini CLI) on Android.**

**Features:**
- **Secure Sandbox** — Your code stays private, other apps can't access it
- **Fast** — Runs natively on your phone's CPU, no cloud lag
- **2 Commands Setup** — Copy-paste and you're ready to code
- **Web + Terminal** — Use browser UI or terminal, your choice

> Works with **OpenCode**, **Claude Code**, **Codex**, and **Gemini CLI**.  
> This guide uses [OpenCode](https://opencode.ai).

---

## What You Need

- Android phone (6GB+ RAM, 5GB free storage)
- [Termux](https://play.google.com/store/apps/details?id=com.termux) from Play Store

---

## ⚡ Option A: Quick Setup (2 Commands)

> **Choose this OR Option B below — not both!**

**In Termux, run:**
```
pkg update -y && pkg upgrade -y && pkg install proot-distro -y && proot-distro install debian && proot-distro login debian
```

**Inside Linux (when your prompt changes to `root@localhost`), run:**
```
apt update && apt install curl git build-essential python3 -y && curl -fsSL https://deb.nodesource.com/setup_20.x | bash - && apt install nodejs -y && curl -fsSL https://opencode.ai/install | bash && echo 'alias opencode-web="opencode web --hostname 127.0.0.1 --port 4096"' >> ~/.bashrc && source ~/.bashrc
```

✅ **Done!** Skip to [How to Use](#how-to-use).

---

## 📝 Option B: Step-by-Step Setup

> **Skip this if you already did Option A above.**

Open Termux and run each command. Copy one block at a time.

**Step 1: Update Termux**
```
pkg update -y && pkg upgrade -y
```

**Step 2: Install Linux**
```
pkg install proot-distro -y && proot-distro install debian
```

**Step 3: Enter Linux**
```
proot-distro login debian
```
✅ Success! Your prompt should change to `root@localhost`

**Step 4: Install Tools**
```
apt update && apt install curl git build-essential python3 -y
```

```
curl -fsSL https://deb.nodesource.com/setup_20.x | bash - && apt install nodejs -y
```

**Step 5: Install OpenCode**
```
curl -fsSL https://opencode.ai/install | bash
```

**Step 6: Create Shortcut** (so you can type `opencode-web` instead of long commands)
```
echo 'alias opencode-web="opencode web --hostname 127.0.0.1 --port 4096"' >> ~/.bashrc && source ~/.bashrc
```

✅ **Setup complete!**

---

## How to Use

Every time you open Termux, run:
```
proot-distro login debian
```

Then choose how you want to use the AI:

### 🌐 Option 1: Web Interface
```
opencode-web
```
Open Chrome → `localhost:4096`

### 💻 Option 2: Terminal Only
```
opencode
```
Chat directly in Termux.

---

## Building Your First Project

**Try it:** Tell the AI *"Create a website with a blue background"*

**Preview your website:**

| Project Type | Command | Browser URL |
|--------------|---------|-------------|
| HTML / Static | `python3 -m http.server 8080` | `localhost:8080` |
| React / Next.js | `npm run dev` | `localhost:3000` |

---

## File Management (Optional)

**Using Acode App:**
1. Install [Acode](https://play.google.com/store/apps/details?id=com.foxdebug.acode)
2. Open Acode → Files → Add Path → Termux → home
3. Edit files visually

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
| Commands not found | `source ~/.bashrc` |
| Termux closes randomly | Settings → Apps → Termux → Battery → Unrestricted |

---

**Made with ❤️ for mobile developers.**
