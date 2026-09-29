# Fork, clone, and set up a module

Each module is a private repository in this organization. You work in your own copy of it. The examples use `module-1`; for another module, replace `module-1` with its name.

```text
m74-academy/module-1       the course      → remote: upstream
        │ Fork
        ▼
YOUR-USERNAME/module-1     your fork       → remote: origin
        │ git clone
        ▼
module-1/                  on your computer
```

Before you start, accept the course invitation from your email or GitHub notifications, and [install uv and Git](install-uv-and-git.md).

## 1. Fork the course

1. Open the module repository, for example [m74-academy/module-1](https://github.com/m74-academy/module-1).
2. Click **Fork**, keep the defaults, and click **Create fork**.

The result is `YOUR-USERNAME/module-1`. Your fork is private; classmates can't see it.

## 2. Clone your fork

On **your fork**, choose **Code → HTTPS** and copy the address. It contains your username, not `m74-academy`.

```console
git clone https://github.com/YOUR-USERNAME/module-1.git
cd module-1
```

## 3. Connect it to the course

```console
git remote add upstream https://github.com/m74-academy/module-1.git
git remote -v
```

```text
origin    https://github.com/YOUR-USERNAME/module-1.git (fetch)
origin    https://github.com/YOUR-USERNAME/module-1.git (push)
upstream  https://github.com/m74-academy/module-1.git (fetch)
upstream  https://github.com/m74-academy/module-1.git (push)
```

Push your work to **origin**. Get course updates from **upstream**.

**Shortcut:** with the [GitHub CLI](https://cli.github.com/) installed and signed in, `gh repo fork m74-academy/module-1 --clone` does steps 1 to 3 in one command. Then `cd module-1`.

## 4. Set up the project

```console
uv sync --locked
```

uv reads three files that come with the module:

| File | Says |
|---|---|
| `.python-version` | which Python |
| `pyproject.toml` | the project and its packages |
| `uv.lock` | the exact tested versions |

It downloads Python if needed and creates `.venv/`. `--locked` stops without changing anything if the lock file doesn't match.

## 5. Check it works

```console
uv run academy --help
```

The help for the `academy` command appears. Then check the whole setup:

```console
uv run academy health
```

Every required check prints `OK`, and the last line says `Setup looks good.` A `FAIL` line comes with a fix. `WARN` and `INFO` lines are advice. The `health` command is available from Module 1 version 0.7.5.

## 6. Open and read the course

1. Open the module folder in VS Code; see [VS Code or the terminal?](vscode-and-terminal.md).
2. Run `uv run academy docs`. The course opens in your browser; the first run downloads its reading tools. If no browser opens, copy the `http://localhost` address from the terminal.

You can also read the Markdown files directly in VS Code or on GitHub.

## Checklist

- [ ] Fork `YOUR-USERNAME/module-1` exists
- [ ] Cloned, with `origin` and `upstream` remotes
- [ ] `uv sync --locked` finished
- [ ] `uv run academy health` ends with `Setup looks good.`
- [ ] Folder open in VS Code with the `.venv` interpreter

Commit your work as you go and `git push` it to your fork.

Next: [Read, edit, and check a lesson](lesson-loop.md).
