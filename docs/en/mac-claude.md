# Install Clicky with your Claude subscription

[← Back to the start](../../README.md) · [עברית](../he/mac-claude.md) · [I use ChatGPT / Codex instead](mac-codex.md)

> **This page is for a Mac.** Have Windows? [Go to the Windows page](windows-claude.md).

**Your time:** about 10 minutes, plus a few minutes of automatic downloads the first time you open Clicky.
**Cost:** nothing beyond the Claude subscription you already pay for. No API key.

---

## Before you start

| You need | Details |
|---|---|
| **A Mac** | Apple Silicon (M1, M2, M3 or M4) with macOS 14 or newer. 16 GB of memory is comfortable. |
| **A Claude subscription** | **Pro or Max** (Ultra, Team and Enterprise work too). The free claude.ai plan does **not** include Claude Code, and Clicky needs it. |
| **About 5 GB of free disk space** | Clicky downloads its speech and voice models the first time. |
| **Internet** | For the setup and for the first launch. |
| **A microphone** | The built-in one is fine. |

## How it fits together (30 seconds)

Clicky answers your questions with Claude. It talks to Claude through **Claude Code**, Anthropic's official app, which is signed in with your subscription. So there are four small steps:

1. **Install Clicky.**
2. **Install Claude Code and sign in** (once).
3. **Tell Clicky to use your Claude subscription.**
4. **Try it.**

You never open Claude Code again after step 2. Clicky uses it in the background.

---

## Step 1: Download and install Clicky

### Download

Click **[Download Clicky-macOS.dmg](https://github.com/noambenzimra/clicky-for-the-people/releases/latest/download/Clicky-macOS.dmg)**. The file starts downloading right away and this page stays open. It is a single file, about 32 MB.

### Install

1. Double-click `Clicky-macOS.dmg`. A window opens with **Clicky** and an **Applications** shortcut. Drag **Clicky** onto **Applications**.
2. Open **Clicky**: press `⌘ Space`, type **Clicky**, press Enter.
3. The first time, macOS says it can't open it, because Clicky isn't signed by Apple yet. This is expected. Do this once:
   **System Settings → Privacy & Security** → scroll down to **Security** → click **Open Anyway** next to Clicky → confirm with your password or Touch ID.
4. Allow the three things Clicky asks for:

   | Permission | Why |
   |---|---|
   | **Microphone** | To hear you while you hold the key. |
   | **Screen Recording** (called *Screen & System Audio Recording* on newer macOS) | To see your screen when you ask a question. |
   | **Accessibility** | To point at things, click for you, and read the text on a page. |

   macOS may ask you to **quit and reopen** Clicky after you turn on Screen Recording or Accessibility. Do it. Not sure what's still missing? Click the Clicky icon in the menu bar → **Setup & permissions…**.

✅ **You should see:** no window and no Dock icon. Clicky lives as a small **cursor-with-rays icon in the menu bar** at the top of the screen.

---

## Step 2: Install Claude Code and sign in (once)

### 2a. Open a terminal

Press `⌘ Space`, type **Terminal**, press Enter.

### 2b. Install Claude Code

Paste this line and press Enter:

```bash
curl -fsSL https://claude.ai/install.sh | bash
```

The installer shows no progress while it downloads. Wait until you get your prompt back.

These are the commands from Anthropic's own [setup page](https://code.claude.com/docs/en/setup).

### 2c. Check that it installed

**Close the terminal window and open a new one**, then type:

```bash
claude --version
```

✅ **You should see** a version number, for example `2.1.211 (Claude Code)`.

⚠️ **If it says `command not found`** run this once, then close the window, open a new one, and try again:

```bash
echo 'export PATH="$HOME/.local/bin:$PATH"' >> ~/.zshrc
```

### 2d. Sign in with your Claude account

In the terminal, type:

```bash
claude
```

and press Enter.

1. Your **browser opens**. Sign in with the **same account you use on claude.ai** (the one with your subscription) and approve the access.
2. If Claude Code asks how you want to sign in, choose your **Claude account / subscription**, **not** the Console / API option.
3. If it asks a few first-time questions (like a color theme), the default answers are fine.
4. Back in the terminal you'll see Claude Code waiting for a message. **You are signed in.**
5. Type `/exit` and press Enter to close it. You won't need to open it again.

---

## Step 3: Tell Clicky to use your Claude subscription

1. **Quit Clicky** (menu-bar icon → **Quit Clicky**) **and open it again** from Applications, so it notices Claude Code.
2. Click the Clicky icon. Make sure there is a **✓** next to **Use my Claude subscription (no API key)**. If not, click it.
3. In the same menu, open **Vision model**. **Cloud – Claude** should have the ✓.

---

## Step 4: The first launch (be patient, once)

The first time, Clicky downloads what it needs **by itself**, about **4 GB** in total: the speech models, the Hebrew voice, and a few helper packages. Progress shows in a small panel at the **top right** ("Getting ready…", "Downloading the Hebrew voice").

- Keep Clicky open and stay on Wi-Fi. It takes a few minutes.
- Until it finishes, Hebrew answers may use a simpler Mac voice, and the first answers may be slow.
- It happens only once. Later launches are quick (give it about a minute after opening).

---

## Step 5: Try it

1. Hold **fn + Control**.
2. Say: **"What's on my screen?"**
3. Let go.

✅ **You should see** the little animation and Clicky answers out loud within a few seconds.

Nothing? Go to [Something not working?](#something-not-working) below.

---

## Using Clicky

**Hold the key, talk, let go.**

| | Mac |
|---|---|
| **Do it for me.** Clicky clicks and types while you watch. | hold **fn + Control** |
| **Guide me.** Clicky points, you click. | hold **Right ⌘** |

The top of the Clicky menu always shows which key does what. To swap them: menu → the line that starts with your main key and says **does** → **Do it for me** or **Guide me**. Other keys: menu → **Settings…**.

**Good to know**

- **Circle something with the mouse** while you hold the key to show exactly what you mean.
- A **quick tap** on the key stops Clicky. **Esc** stops a task and clears the drawings.
- Say **"Read me this page"** and it reads the page out loud. Press the key to stop it.
- Say **"Explain how … works"** and it draws a visual explanation next to your screen.
- Clicky **asks before** anything you can't undo (sending, buying, deleting) and **never types passwords**.
- **Hebrew voice:** menu → **Hebrew voice** → Female or Male, any time. Speed: **Settings…** → Voice.
- **Language of the answers:** menu → **Language**, or **Settings…** → "Answer in".

Every question counts toward your Claude plan's usage limits, like using Claude normally. By default Clicky uses Claude's small, fast **Haiku** model.

---

## Something not working?

| What you see | What to do |
|---|---|
| **"Claude Code was not found"** | Do [Step 2](#step-2-install-claude-code-and-sign-in-once) again. Check that `claude --version` works in a **new** terminal window. Then quit and reopen Clicky. |
| **"Claude Code needs you to sign in again"** | In the terminal type `claude`, then `/login`, sign in, then `/exit`. |
| **`command not found: claude`** | Close the terminal and open a new one. Still not found: run the `export PATH=…` line in step 2c. |
| **Nothing happens when I hold the keys** | Menu → **Setup & permissions…** and turn on everything that's off (Accessibility and Screen Recording especially). Then quit and reopen Clicky. |
| **"I didn't hear anything" / Clicky doesn't hear me** | Check the microphone: System Settings → Sound → Input. Speak while the level bar moves. |
| **I can't hear Clicky** | Check the output device and the volume. If you use Bluetooth headphones, try the Mac's own speakers. |
| **Slow for the first minute after opening** | Normal: Clicky is loading its models. Give it a minute. |
| **The answer is in the wrong language** | Menu → **Language**, or **Settings…** → "Answer in". |
| **Anything else** | Click the Clicky icon → **Diagnostics…**. It lists what's wrong and how to fix it. |

If you hit an error and want to read what Claude Code itself says, run `claude doctor` in the terminal.

---

## Privacy

- **Your voice** is turned into text **on your computer**. The recording never leaves it.
- When you ask something, a **screenshot of your screen and your question** are sent to **Claude** (Anthropic), through your own Claude Code sign-in. **Nothing is sent while you are not holding the key.**
- Clicky doesn't keep screenshots. Your text history stays on your computer (menu → **History…** to see or clear it).
- Claude's own data policies for your plan apply to what you send it.
