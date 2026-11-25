# Install Clicky with your ChatGPT (Codex) subscription

[← Back to the start](../../README.md) · [עברית](../he/mac-codex.md) · [I use Claude instead](mac-claude.md)

> **This page is for a Mac.** The Codex option has only been checked on the Mac version of Clicky. Have Windows? [Go to the Windows page](windows-claude.md) (it uses Claude).

**Your time:** about 10 minutes, plus a few minutes of automatic downloads the first time you open Clicky.
**Cost:** nothing beyond the ChatGPT plan you already pay for. No API key.

---

## Before you start

| You need | Details |
|---|---|
| **A Mac** | Apple Silicon (M1, M2, M3 or M4) with macOS 14 or newer. 16 GB of memory is comfortable. |
| **A ChatGPT plan that includes Codex** | Plus, Pro, Team, Edu or Enterprise. See OpenAI's [sign-in page](https://learn.chatgpt.com/docs/auth) for what your plan includes. |
| **About 5 GB of free disk space** | Clicky downloads its speech and voice models the first time. |
| **Internet** | For the setup and for the first launch. |
| **A microphone** | The built-in one is fine. |

## How it fits together (30 seconds)

Clicky answers your questions with ChatGPT. It talks to ChatGPT through **Codex**, OpenAI's official command-line app, which is signed in with your ChatGPT account. So there are four small steps:

1. **Install Clicky.**
2. **Install Codex and sign in** (once).
3. **Tell Clicky to use ChatGPT (Codex).**
4. **Try it.**

You never open Codex yourself after step 2. Clicky uses it in the background, and only to **answer**: it runs Codex in read-only mode, in an empty temporary folder, so it can't touch your files, and it asks Codex not to keep a session on your disk.

> **Expect it to be a little slower than Claude.** Clicky was built and tuned with Claude first. With Codex an answer usually takes a few seconds longer to start (about 3 to 6 seconds), and the arrow that points at things may be less accurate. If you have both subscriptions, you can switch between them any time (see [Switching](#switching-between-claude-and-chatgpt)).

---

## Step 1: Download and install Clicky

1. Click **[Download Clicky-macOS.dmg](https://github.com/noambenzimra/clicky-for-the-people/releases/latest/download/Clicky-macOS.dmg)**. The file starts downloading right away and this page stays open. It is a single file, about 32 MB.
2. Double-click it. A window opens with **Clicky** and an **Applications** shortcut. Drag **Clicky** onto **Applications**.
3. Open **Clicky**: press `⌘ Space`, type **Clicky**, press Enter.
4. The first time, macOS says it can't open it, because Clicky isn't signed by Apple yet. This is expected. Do this once:
   **System Settings → Privacy & Security** → scroll down to **Security** → click **Open Anyway** next to Clicky → confirm with your password or Touch ID.
5. Allow the three things Clicky asks for:

   | Permission | Why |
   |---|---|
   | **Microphone** | To hear you while you hold the key. |
   | **Screen Recording** (called *Screen & System Audio Recording* on newer macOS) | To see your screen when you ask a question. |
   | **Accessibility** | To point at things, click for you, and read the text on a page. |

   macOS may ask you to **quit and reopen** Clicky after you turn on Screen Recording or Accessibility. Do it. Not sure what's still missing? Click the Clicky icon in the menu bar → **Setup & permissions…**.

✅ **You should see:** no window and no Dock icon. Clicky lives as a small **cursor-with-rays icon in the menu bar** at the top of the screen.

---

## Step 2: Install Codex and sign in (once)

### 2a. Open Terminal

Press `⌘ Space`, type **Terminal**, press Enter.

### 2b. Install Codex

Paste **this one line** and press Enter:

```bash
curl -fsSL https://chatgpt.com/codex/install.sh | sh
```

This is OpenAI's own installer, from the [Codex CLI page](https://learn.chatgpt.com/docs/codex/cli). It puts the `codex` command in `~/.local/bin` (where Clicky looks for it) and, if needed, adds that folder to your `~/.zprofile`. If it asks a question, press Enter to accept the default.

<details>
<summary>Other ways to install (Homebrew or npm)</summary>

If you already use Homebrew:

```bash
brew install --cask codex
```

If you already have Node.js:

```bash
npm install -g @openai/codex
```

</details>

### 2c. Check that it installed

**Close the Terminal window and open a new one**, then type:

```bash
codex --version
```

✅ **You should see** a version number, for example `codex-cli 0.172.0`.

⚠️ **If it says `command not found`:** run this once, then close the window, open a new one, and try again:

```bash
echo 'export PATH="$HOME/.local/bin:$PATH"' >> ~/.zshrc
```

### 2d. Sign in with your ChatGPT account

```bash
codex login
```

1. Your **browser opens**. Sign in with the **ChatGPT account that has your plan** and approve the access.
2. Back in Terminal you'll see **`Successfully logged in`**.

### 2e. Check that you're signed in

```bash
codex login status
```

✅ **You should see:** `Logged in using ChatGPT`.

> Use the **ChatGPT** sign-in, **not** an API key. The API-key sign-in is billed per use, separately from your plan.

---

## Step 3: Tell Clicky to use ChatGPT (Codex)

Clicky starts out set to Claude, so this step is **required**.

1. Click the **Clicky icon** in the menu bar.
2. Open **Vision model**.
3. Choose **ChatGPT subscription (Codex)**. It gets a **✓**.

⚠️ **If the row says `(install Codex CLI)`:** Clicky can't find Codex. Go back to step 2c, make sure `codex --version` works in a new Terminal window, then quit and reopen Clicky.

You can ignore the *Use my Claude subscription* line in the same menu.

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

✅ **You should see** the little animation, and Clicky answers out loud. With Codex, expect about **3 to 6 seconds** before it starts talking.

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

Every question counts toward your ChatGPT plan's Codex usage limits.

### Switching between Claude and ChatGPT

Have both? Menu → **Vision model** → pick **Cloud – Claude** or **ChatGPT subscription (Codex)**. The change applies to your next question. (To use Claude you also need Claude Code, see [the Claude page](mac-claude.md).)

---

## Something not working?

| What you see | What to do |
|---|---|
| **"Codex CLI is not installed"** | Do [Step 2](#step-2-install-codex-and-sign-in-once) again. Check that `codex --version` works in a **new** Terminal window. Then quit and reopen Clicky. |
| **"Codex needs you to sign in"** | In Terminal run `codex login`, sign in with your ChatGPT account, then check `codex login status`. |
| **The row says `(install Codex CLI)`** | Clicky can't find Codex. See step 3. |
| **`command not found: codex`** | Close Terminal and open a new window. Still not found: run the `export PATH=…` line in step 2c. |
| **An error about usage or a limit** | You've used up your plan's Codex allowance for now. Wait for it to reset, or switch to Claude (see above). |
| **Nothing happens when I hold the keys** | Menu → **Setup & permissions…** and turn on everything that's off (Accessibility and Screen Recording especially). Then quit and reopen Clicky. |
| **"I didn't hear anything" / Clicky doesn't hear me** | Check the microphone: System Settings → Sound → Input. Speak while the level bar moves. |
| **I can't hear Clicky** | Check the output device and the volume. If you use Bluetooth headphones, try the Mac's own speakers. |
| **Slow** | Right after opening, give it a minute (it's loading). Codex is also a few seconds slower than Claude by design. |
| **The answer is in the wrong language** | Menu → **Language**, or **Settings…** → "Answer in". |
| **Anything else** | Click the Clicky icon → **Diagnostics…**. It lists what's wrong and how to fix it. |

---

## Privacy

- **Your voice** is turned into text **on your Mac**. The recording never leaves it.
- When you ask something, a **screenshot of your screen and your question** are sent to **OpenAI**, through your own Codex sign-in. **Nothing is sent while you are not holding the key.**
- Clicky runs Codex **read-only**, in an **empty temporary folder**, and asks it **not to save a session** on your computer. Codex can't read or change your files through Clicky.
- Clicky doesn't keep screenshots. Your text history stays on your Mac (menu → **History…** to see or clear it).
- OpenAI's own data policies for your plan apply to what you send it.
