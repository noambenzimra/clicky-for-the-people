# Install Clicky on Windows (with your Claude subscription)

[← Back to the start](../../README.md) · [עברית](../he/windows-claude.md) · [I have a Mac](mac-claude.md)

> **This page is for Windows 10 or 11.** Have a Mac? [Go to the Mac page](mac-claude.md).
> On Windows, Clicky works with a **Claude** subscription. (The ChatGPT / Codex option is Mac-only for now.)

**Your time:** about 10 minutes, plus a few minutes of automatic downloads the first time you open Clicky.
**Cost:** nothing beyond the Claude subscription you already pay for. No API key.

---

## Before you start

| You need | Details |
|---|---|
| **A Windows PC** | Windows 10 or 11. |
| **A Claude subscription** | **Pro or Max** (Ultra, Team and Enterprise work too). The free claude.ai plan does **not** include Claude Code, and Clicky needs it. |
| **About 5 GB of free disk space** | Clicky downloads its speech and voice models the first time. |
| **Internet** | For the setup and for the first launch. |
| **A microphone** | The built-in one is fine. |

## How it fits together (30 seconds)

Clicky answers your questions with Claude. It talks to Claude through **Claude Code**, Anthropic's official app, which is signed in with your subscription. So there are four small steps:

1. **Install Clicky.**
2. **Install Claude Code and sign in** (once).
3. **Make sure Clicky uses your Claude subscription.**
4. **Try it.**

You never open Claude Code again after step 2. Clicky uses it in the background.

---

## Step 1: Download and install Clicky

### Download

> **The Windows installer is not on this page yet.** It is being moved here. Check back soon, or open an issue on this repository and say you're waiting for it.

### Install

1. Double-click the Clicky installer (`.exe`). No administrator password is needed.
2. If Windows shows **"Windows protected your PC"** (Clicky isn't code-signed yet), click **More info → Run anyway**. This is expected.
3. Finish the installer. Clicky starts and appears in the **system tray**, the small cursor icon by the clock. Don't see it? Click the **^** arrow next to the clock.

> If Windows refuses to run it at all ("blocked by an Application Control policy"), **Smart App Control** is on. Clicky can't run with it on until it is code-signed.

---

## Step 2: Install Claude Code and sign in (once)

### 2a. Open PowerShell

Open the Start menu, type **PowerShell**, open it.

### 2b. Install Claude Code

Paste this line and press Enter:

```powershell
irm https://claude.ai/install.ps1 | iex
```

The installer shows no progress while it downloads. Wait until you get your prompt back. It may ask you to install **Git for Windows** first: install it and run the line again.

This is the command from Anthropic's own [setup page](https://code.claude.com/docs/en/setup).

### 2c. Check that it installed

**Close the PowerShell window and open a new one**, then type:

```powershell
claude --version
```

✅ **You should see** a version number, for example `2.1.211 (Claude Code)`.

### 2d. Sign in with your Claude account

In PowerShell, type:

```powershell
claude
```

and press Enter.

1. Your **browser opens**. Sign in with the **same account you use on claude.ai** (the one with your subscription) and approve the access.
2. If Claude Code asks how you want to sign in, choose your **Claude account / subscription**, **not** the Console / API option.
3. If it asks a few first-time questions (like a color theme), the default answers are fine.
4. Back in PowerShell you'll see Claude Code waiting for a message. **You are signed in.**
5. Type `/exit` and press Enter to close it. You won't need to open it again.

---

## Step 3: Make sure Clicky uses your Claude subscription

1. **Quit Clicky and open it again**, so it notices Claude Code: right-click the tray icon → **Quit Clicky**, then open Clicky from the Start menu.
2. Click the Clicky icon. Make sure there is a **✓** next to **Use my Claude subscription (no API key)**. If not, click it.
3. In the same menu, open **Vision model**. **Cloud – Claude** should have the ✓.

---

## Step 4: The first launch (be patient, once)

The first time, Clicky downloads what it needs **by itself**: the speech models and a few helper packages. It can be several gigabytes in total. Progress shows in a small panel at the **top right** of the screen.

- Keep Clicky open and stay on Wi-Fi. It takes a few minutes.
- Until it finishes, the first answers may be slow.
- It happens only once. Later launches are quick (give it about a minute after opening).

---

## Step 5: Try it

1. Hold **Right Ctrl**.
2. Say: **"What's on my screen?"**
3. Let go.

✅ **You should see** the little animation and Clicky answers out loud within a few seconds.

Nothing? Go to [Something not working?](#something-not-working) below.

---

## Using Clicky

**Hold the key, talk, let go.**

| | Windows |
|---|---|
| **Do it for me.** Clicky clicks and types while you watch. | hold **Right Ctrl** |
| **Guide me.** Clicky points, you click. | hold **Right Alt** |

Right-click the tray icon to see which key does what and to change the settings.

**Good to know**

- **Circle something with the mouse** while you hold the key to show exactly what you mean.
- A **quick tap** on the key stops Clicky. **Esc** stops a task and clears the drawings.
- Say **"Read me this page"** and it reads the page out loud. Press the key to stop it.
- Clicky **asks before** anything you can't undo (sending, buying, deleting) and **never types passwords**.
- **Language of the answers:** in the tray menu, choose **Language**, or open **Settings…** → "Answer in".

Every question counts toward your Claude plan's usage limits, like using Claude normally. By default Clicky uses Claude's small, fast **Haiku** model.

---

## Something not working?

| What you see | What to do |
|---|---|
| **"Claude Code was not found"** | Do [Step 2](#step-2-install-claude-code-and-sign-in-once) again. Check that `claude --version` works in a **new** PowerShell window. Then quit and reopen Clicky. |
| **"Claude Code needs you to sign in again"** | In PowerShell type `claude`, then `/login`, sign in, then `/exit`. |
| **Nothing happens when I hold the key** | Right-click the tray icon → **Settings…** and check the keys. Then quit and reopen Clicky. |
| **"I didn't hear anything" / Clicky doesn't hear me** | Check the microphone: Settings → System → Sound → Input. Speak while the level bar moves. |
| **I can't hear Clicky** | Check the output device and the volume. If you use Bluetooth headphones, try the PC's own speakers. |
| **Slow for the first minute after opening** | Normal: Clicky is loading its models. Give it a minute. |
| **The answer is in the wrong language** | Tray menu → **Language**, or **Settings…** → "Answer in". |
| **Anything else** | Right-click the tray icon → **Diagnostics…**. It lists what's wrong and how to fix it. |

If you hit an error and want to read what Claude Code itself says, run `claude doctor` in PowerShell.

---

## Privacy

- **Your voice** is turned into text **on your computer**. The recording never leaves it.
- When you ask something, a **screenshot of your screen and your question** are sent to **Claude** (Anthropic), through your own Claude Code sign-in. **Nothing is sent while you are not holding the key.**
- Clicky doesn't keep screenshots. Your text history stays on your computer.
- Claude's own data policies for your plan apply to what you send it.
