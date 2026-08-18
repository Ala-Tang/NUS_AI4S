# Installing Miniconda

Miniconda is a small installer that gives you the `conda` command. You need it
once, before the setup steps in `STUDENT_GUIDE.md`. If `conda --version` already
prints a version on your computer, skip this page.

Miniconda ships its own Python, but the version does not matter here: the course
environment pins Python 3.11 for you.

## 1. Download the installer

Open the official download page and scroll to **Miniconda Installers**:

<https://www.anaconda.com/download/success>

Pick the installer that matches your computer:

| Computer | Installer |
|---|---|
| Mac with Apple silicon (M1/M2/M3/M4) | `Miniconda3-latest-MacOSX-arm64.pkg` |
| Mac with Intel processor | `Miniconda3-latest-MacOSX-x86_64.pkg` |
| Windows 64-bit | `Miniconda3-latest-Windows-x86_64.exe` |

To check which Mac you have, open the Apple menu → **About This Mac** and look at
the **Chip** line. Every installer is also listed at
<https://repo.anaconda.com/miniconda/>.

## 2. Run the installer

**macOS** — double-click the downloaded `.pkg` file and accept the default
options. Install for "me only" if you are asked.

**Windows** — double-click the downloaded `.exe` file and accept the default
options. Choose "Just Me" when it asks who to install for.

## 3. Check that it worked

Close any terminal window that was already open, then open a new one:

- **macOS** — open **Terminal** (find it with Spotlight: `Cmd + Space`, type
  `Terminal`).
- **Windows** — open **Anaconda Prompt** from the Start menu. Use this window,
  not the ordinary Command Prompt.

Run:

```bash
conda --version
```

You should see something like `conda 25.5.1`. The exact number does not matter.

## 4. Next step

Go back to `STUDENT_GUIDE.md`, section 1, and follow **Option A — Conda**.

## Troubleshooting

**`conda: command not found` on macOS.** The installer needs a fresh shell.
Quit Terminal completely (`Cmd + Q`) and reopen it. If it still fails, run:

```bash
~/miniconda3/bin/conda init zsh
```

then reopen Terminal.

**`conda` is not recognized on Windows.** Use **Anaconda Prompt** from the Start
menu instead of Command Prompt or PowerShell.

**The download page looks confusing.** It offers both Anaconda and Miniconda.
Scroll down to the **Miniconda Installers** section — Miniconda is the small one,
and it is all you need.
