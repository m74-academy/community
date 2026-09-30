# Set up your computer

Do this once per computer, before your first lesson. It takes about 20 minutes.

| Tool | Why |
|---|---|
| VS Code | Where you read, write code, and type commands |
| uv | Runs Python and every course command; you do **not** install Python yourself |
| Git | Gets the course and its updates, and saves your work |
| GitHub CLI (`gh`) | Signs your computer in to GitHub, so Git can reach the private course |
| `academy` command | Checks your lessons, opens the course, and checks your setup |

You also need a GitHub account, the one your instructor invited.

On a school or work computer where installing is blocked, ask your instructor or IT **before** the first lesson.

## 1. Install VS Code

Download it from [code.visualstudio.com](https://code.visualstudio.com/) and install it. Open it, go to the Extensions view, and install **Python** (by Microsoft).

Now open a terminal inside VS Code: **Terminal → New Terminal**. Type every command below there. On Windows it must say **PowerShell**; choose it from the arrow next to **+** if not.

## 2. Install uv

macOS and Linux:

```console
curl -LsSf https://astral.sh/uv/install.sh | sh
```

Windows:

```console
powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"
```

These come from the [official uv page](https://docs.astral.sh/uv/getting-started/installation/); if it shows a different command, use that one.

**Close the terminal (trash icon) and open a new one**, then check:

```console
uv --version
```

It prints a version number. `command not found` means the terminal is still the old one.

## 3. Install Git

| System | How |
|---|---|
| macOS | Run `git --version` and click **Install** when macOS offers the command line developer tools |
| Windows | Download [Git for Windows](https://git-scm.com/install/) and run the installer with its default choices |
| Linux | Use your package manager, for example `sudo apt install git` on Ubuntu |

Open a new terminal and check:

```console
git --version
```

Then tell Git who you are. Use your name and the email of your GitHub account; every commit records them:

```console
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
```

## 4. Install GitHub CLI and sign in

The course repositories are private, so Git needs your GitHub sign-in. GitHub CLI sets that up.

| System | How |
|---|---|
| macOS | Download the **macOS installer** from [cli.github.com](https://cli.github.com/) and open it. With [Homebrew](https://brew.sh/) you can instead run `brew install gh` |
| Windows | Run `winget install --id GitHub.cli` in the terminal, or download the **Windows installer** from [cli.github.com](https://cli.github.com/) |
| Linux | Follow the instructions for your distribution on [cli.github.com](https://cli.github.com/) |

Open a new terminal, then sign in:

```console
gh auth login
```

Answer the questions:

1. Where do you use GitHub? **GitHub.com**
2. Preferred protocol? **HTTPS**
3. Authenticate Git with your GitHub credentials? **Yes**
4. How to authenticate? **Login with a web browser**, then paste the code it shows into the page that opens.

Check:

```console
gh auth status
```

It says you are logged in to github.com.

## 5. Install the academy command

```console
uv tool install git+https://github.com/m74-academy/academy-cli
```

If uv says its tool folder is not on your `PATH`, run `uv tool update-shell`, then open a new terminal.

The same `academy` command works in every module; `academy update` keeps it and the course current.

## Check

In a **new** terminal, each of these prints a version or a status, not an error:

```console
uv --version
git --version
gh auth status
academy --version
```

`academy --help` lists every command with examples; `academy` alone shows the same.

Your computer is ready. Next: open [Module 1](https://github.com/m74-academy/module-1) and follow its **Start here**.
