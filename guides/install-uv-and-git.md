# Install uv, Git, GitHub CLI, and the academy command

You need five things before the first lesson:

| Tool | Why |
|---|---|
| uv | Runs Python and every course command |
| Git | Gets the course and its updates, and saves your work |
| GitHub account | Holds your copy of the course, your reviews, and your capstone handoff |
| GitHub CLI (`gh`) | Connects your terminal to GitHub and handles course GitHub workflows |
| `academy` command | Checks your lessons, opens the course, and checks your setup in every module |

You do **not** need to install Python. uv downloads the version each module needs.

A code editor is also useful; see [VS Code or the terminal?](vscode-and-terminal.md).

## Install uv

Use the **standalone installer** from the [official uv page](https://docs.astral.sh/uv/getting-started/installation/). It needs no Python and no admin rights.

macOS and Linux, in Terminal:

```console
curl -LsSf https://astral.sh/uv/install.sh | sh
```

Windows, in PowerShell:

```console
powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"
```

If the official page shows a different command, use that one.

**Close the terminal and open a new one**, then check:

```console
uv --version
```

It prints a version number. `command not found` usually means you are still in the old window.

## Install Git

Follow the [official Git page](https://git-scm.com/install/):

| System | How |
|---|---|
| macOS | Run `git --version` and accept the offer to install the command line tools |
| Windows | Run the Git for Windows installer and keep the defaults |
| Linux | Use your package manager, for example `sudo apt install git` on Ubuntu |

Check in a new terminal:

```console
git --version
```

## Tell Git who you are

Once per computer, before your first commit:

```console
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
```

Use your own name and the email associated with your GitHub account. Every commit records them.

## Install GitHub CLI

GitHub CLI gives you the `gh` command. We use it to work with GitHub directly from the terminal.

Follow the [official GitHub CLI installation instructions](https://cli.github.com/).

macOS with Homebrew:

```console
brew install gh
```

Windows with WinGet:

```console
winget install --id GitHub.cli
```

On Linux, follow the instructions for your distribution on the official page.

Check:

```console
gh --version
```

Then connect it to your GitHub account:

```console
gh auth login
```

Choose **GitHub.com** and follow the prompts. When asked which protocol to use for Git operations, choose **HTTPS** unless your instructor tells you otherwise.

Check that authentication worked:

```console
gh auth status
```

## Install the academy command

Once per computer, after uv and Git:

```console
uv tool install git+https://github.com/m74-academy/academy-cli
```

If uv says the command folder is not on your `PATH`, run:

```console
uv tool update-shell
```

Then close the terminal and open a new one.

The same `academy` command works in every module; `academy update` keeps it current.

## Check

In a **new** terminal, these commands should all work:

```console
uv --version
git --version
gh --version
gh auth status
academy --version
```

If they do, your computer is ready for the course.

- On Windows, run every course command in **PowerShell**.
- Installation blocked on a school or work computer? Ask your instructor or IT **before** the first lesson.

Next: [Fork, clone, and set up a module](fork-clone-setup.md).
