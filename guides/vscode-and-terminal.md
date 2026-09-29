# VS Code or the terminal?

Both. You **edit** files in an editor and **run** course commands in a terminal. They do different jobs, and you can have both in one window.

| | Editor | Terminal |
|---|---|---|
| You use it to | read lessons, write code, resolve merge conflicts | run `uv`, `git`, and `uv run academy` |
| Recommended | [VS Code](https://code.visualstudio.com/) with the Python extension | the terminal built into VS Code, or your system's own |

Any Python editor works. The course pages and commands assume VS Code, so questions about it are easier to answer.

## Set up VS Code

1. Install [VS Code](https://code.visualstudio.com/).
2. Open the Extensions view and install **Python** (by Microsoft).
3. **File → Open Folder** and choose the module folder, for example `module-1`. Open the folder, not a single file.
4. Command Palette (**Ctrl+Shift+P**, or **Cmd+Shift+P** on macOS) → **Python: Select Interpreter** → choose the project's `.venv`. It exists after `uv sync --locked`; see [Fork, clone, and set up a module](fork-clone-setup.md).

The interpreter choice only helps the editor: highlighting errors and completing names. It does not run the course checks.

## Use the terminal

Open VS Code's built-in terminal with **Terminal → New Terminal**. It starts in the open folder, which is where course commands must run.

Check where you are:

```console
pwd
```

The last part of the path is the module folder, for example `module-1`. If not, move there with `cd`.

Run course commands through uv:

```console
uv run academy test 1 2
```

`uv run` uses the project's Python and packages for you. You never activate an environment or use `pip`.

On Windows, the built-in terminal must be **PowerShell**. Choose it from the arrow next to **+** in the terminal panel if it opened something else.

## Two terminals

`uv run academy docs` keeps running while you read the course in the browser. Leave that terminal open and click **+** in the terminal panel for a second one in the same folder. Use the second one for lesson checks and Git. **Ctrl+C** stops the preview.

## Common problems

| You see | Means | Do |
|---|---|---|
| `command not found: uv` | The terminal started before uv was installed | Close it and open a new one |
| ``error: Failed to spawn: `academy` `` | The terminal is not in the module folder | `cd` into the module folder |
| Red underlines on every import | The editor uses another Python | **Python: Select Interpreter** → `.venv` |

Next: [Read, edit, and check a lesson](lesson-loop.md).
