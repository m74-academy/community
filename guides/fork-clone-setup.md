# Fork, clone, and set up a module, step by step

Each module README starts with one command that does all of this:

```console
gh repo fork m74-academy/module-1 --clone
```

This guide explains what it does, and how to do the same by hand. The examples use `module-1`; for another module, replace `module-1` with its name.

```text
m74-academy/module-1       the course      → remote: upstream
        │ Fork
        ▼
YOUR-USERNAME/module-1     your fork       → remote: origin
        │ Clone
        ▼
module-1/                  on your computer
```

- **Fork:** your own copy of the course on GitHub. You push your work there. It is private, and it lasts while you have access to the course.
- **Clone:** that copy downloaded to your computer, in a `module-1` folder.
- **Remotes:** `origin` is your fork; `upstream` is the course. `academy update` gets course updates from `upstream`.

You need [your computer set up](install-uv-and-git.md) first, with `gh auth login` done.

## By hand, in the browser

1. Open the module repository, for example [m74-academy/module-1](https://github.com/m74-academy/module-1), and click **Fork**, then **Create fork**. The result is `YOUR-USERNAME/module-1`.
2. Clone your fork. With GitHub CLI this also adds `upstream`:

   ```console
   gh repo clone YOUR-USERNAME/module-1
   ```

   With Git alone, clone and add `upstream` yourself:

   ```console
   git clone https://github.com/YOUR-USERNAME/module-1.git
   cd module-1
   git remote add upstream https://github.com/m74-academy/module-1.git
   ```

3. Check the remotes from inside the folder:

   ```console
   git remote -v
   ```

   ```text
   origin    https://github.com/YOUR-USERNAME/module-1.git (fetch)
   origin    https://github.com/YOUR-USERNAME/module-1.git (push)
   upstream  https://github.com/m74-academy/module-1.git (fetch)
   upstream  https://github.com/m74-academy/module-1.git (push)
   ```

## Set up the project

In the module folder:

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

Then check everything:

```console
academy health
```

Every required check prints `OK`, and the last line says `Setup looks good.` A `FAIL` line comes with a fix. `WARN` and `INFO` lines are advice.

Back to the module README's **Start here** for the next step.
