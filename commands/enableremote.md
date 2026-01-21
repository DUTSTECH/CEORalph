---
description: One-shot Remote UI + HTTPS tunnel setup
argument-hint: []
allowed-tools: [Bash, Read, Write, Edit, AskUserQuestion]
---

# /ceo-ralph:enableremote

One-shot command to set up the Remote UI, start it locally, and expose it via a free HTTPS tunnel.

## Usage

```
/ceo-ralph:enableremote
```

## What It Does

- Prompts you to set and confirm a password
- Starts the Remote UI server
- Launches Cloudflare Quick Tunnel
- Prints the public HTTPS URL
 
Requires `cloudflared` installed (auto-checked below).

## Step 1: Check Cloudflared

```bash
cloudflared --version 2>&1 || echo "CLOUDFLARED_MISSING"
```

If you see `CLOUDFLARED_MISSING`, ask the user to install it and stop here.

**Windows (PowerShell):**
```powershell
winget install --id Cloudflare.cloudflared
```

**macOS (Homebrew):**
```bash
brew install cloudflared
```

**Linux (Debian/Ubuntu):**
```bash
sudo apt-get update && sudo apt-get install -y cloudflared
```

Then re-run:

```
/ceo-ralph:enableremote
```

## Step 2: Enable Remote UI

If `cloudflared` is installed, run:

```bash
python remote-ui/remote_ui.py enable
```
