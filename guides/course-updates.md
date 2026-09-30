# Get course updates without losing your work

The course changes while you take it. Get each update in four steps: **commit → pull → sync → push**. Run them in the module folder.

## 1. Commit your work

```console
git status
git add src/chapter_01/lesson_02.py
git commit -m "Solve lesson 1.2"
```

Never pull on top of changes you haven't committed.

## 2. Pull from the course

```console
git pull --no-rebase --no-edit upstream main
```

| Part | Does |
|---|---|
| `upstream main` | takes the course's `main` branch |
| `--no-rebase` | merges it with your commits; without it, Git stops with "Need to specify how to reconcile divergent branches" |
| `--no-edit` | keeps Git's merge message, so no text editor opens |

Your commits and the course's commits are both kept:

```console
git log --oneline --graph -5
```

## 3. Sync, 4. Push

```console
uv sync --locked
git push
```

An update can change the project's packages, so sync after every pull.

## When there's a conflict

```text
CONFLICT (content): Merge conflict in README.md
Automatic merge failed; fix conflicts and then commit the result.
```

You and the course changed the same lines. Nothing is lost.

1. Open the file. VS Code shows both versions.
2. Keep your work **and** the course's change, then save.
3. Finish the update:

```console
git add README.md
git commit --no-edit
uv sync --locked
git push
```

Never reset or delete your work to make an update apply. Stuck? Ask in [Discussions](https://github.com/orgs/m74-academy/discussions).

## The academy command updates itself

`academy` is installed once on your computer, not in each module, so course updates
do not change it. Run `academy update` now and then: it upgrades the command and
tells you when the course has a newer release.

**Moving from `uv run academy`:** Module 1 before 0.8.0 and Module 2 before 0.2.0
had the command inside the project. [Install the `academy`
command](install-uv-and-git.md#install-the-academy-command) once, before or after
pulling those releases. After the pull, `uv sync --locked` removes the old copy; from then on type `academy …`
instead of `uv run academy …`.

## Keep your work

Your fork lasts while you have access to the course. Before that access ends, push your work to a repository of your own.
