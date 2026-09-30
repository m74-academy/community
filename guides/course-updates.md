# Get course updates without losing your work

The course changes while you take it. In the module folder, commit your work, then run one command:

```console
git add -A
git commit -m "Save my work"
academy update
```

`academy update` upgrades the `academy` command, and when the course has a newer release it:

1. gets it from the course (`git pull --no-rebase --no-edit upstream main`), keeping your commits and the course's;
2. updates the project's packages (`uv sync --locked`).

Then save the result to your fork:

```console
git push
```

`academy update --check` only reports what is available and changes nothing. The module's `CHANGELOG.md` lists what each release changes.

## When it stops

`academy update` never commits, discards, or pushes your work for you. It stops in two cases.

**COMMIT FIRST:** you have changes you haven't committed. Commit them, as above, and run `academy update` again.

**COURSE UPDATE STOPPED** with a list of files: you and the course changed the same lines. Nothing is lost.

1. Open each listed file. VS Code shows both versions.
2. Keep your work **and** the course's change, then save.
3. Finish the update:

```console
git add -A
git commit --no-edit
uv sync --locked
git push
```

Never reset or delete your work to make an update apply. Stuck? Ask in [Discussions](https://github.com/orgs/m74-academy/discussions).

## Moving from `uv run academy`

Module 1 before 0.8.0 and Module 2 before 0.2.0 had the command inside the project, so `academy update` isn't there yet. [Install the `academy` command](install-uv-and-git.md#5-install-the-academy-command) once, then get that first update by hand:

```console
git pull --no-rebase --no-edit upstream main
uv sync --locked
git push
```

`uv sync --locked` removes the old copy; from then on type `academy …` instead of `uv run academy …`.

## Keep your work

Your fork lasts while you have access to the course. Before that access ends, push your work to a repository of your own.
