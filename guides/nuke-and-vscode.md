# Nuke and VS Code

Module 2 lessons that show Nuke end with an optional "Run it in Nuke" step. The lessons start Nuke from a terminal, with `NUKE_PATH` and `PYTHONPATH` set by hand. This guide sets up the recommended way: you write code in VS Code, start Nuke from VS Code with the module's variables already set, and send a file to the running Nuke with one command.

Nothing in this guide is checked, and no lesson needs it. Do it once, after you [set up the module](fork-clone-setup.md).

| Tool                      | Why                                                                                   |
| ------------------------- | ------------------------------------------------------------------------------------- |
| Nuke 17                   | Runs your code for real                                                               |
| Nuke Tools (VS Code)      | Starts Nuke with the module's variables, and sends code to it                         |
| `nukeserversocket` (Nuke) | A small panel inside Nuke that receives the code Nuke Tools sends                     |
| Nuke Python stubs         | Lets VS Code complete and check names from Nuke's `nuke` module while you type        |

## 1. Get Nuke

Ask Foundry for the 30-day trial on its [try Nuke](https://www.foundry.com/products/nuke/nuke-indie/try-nuke-indie) page, and install Nuke 17. The trial has no restrictions and covers Nuke and NukeX.

> Foundry also offers a free Nuke Non-commercial. Its page says "Python scripting is limited" and third-party plug-ins aren't supported, so it may not run `nukeserversocket`. Use the trial.

Write down where Nuke's executable is; you need the full path in step 3. The default places for Nuke 17.1v2:

| System  | Executable                                                       |
| ------- | ---------------------------------------------------------------- |
| macOS   | `/Applications/Nuke17.1v2/Nuke17.1v2.app/Contents/MacOS/Nuke17.1` |
| Linux   | `/usr/local/Nuke17.1v2/Nuke17.1`                                 |
| Windows | `C:\Program Files\Nuke17.1v2\Nuke17.1.exe`                       |

## 2. Install Nuke Tools

Open the module folder in VS Code. Module 2 recommends Nuke Tools: when VS Code offers the recommended extensions, choose **Install**. If you missed the offer, open the Extensions view (**Ctrl+Shift+X**, or **Cmd+Shift+X** on macOS), search for `virgilsisoe.nuke-tools`, and install **Nuke Tools**.

Every Nuke Tools command starts with `Nuke:` in the Command Palette (**Ctrl+Shift+P**, or **Cmd+Shift+P** on macOS).

## 3. Tell Nuke Tools where Nuke is

The path is different on every computer, so it goes in your user settings, not in the module. Open the Command Palette → **Preferences: Open User Settings (JSON)**, and add one line with your path from step 1, for example on macOS:

```json
"nukeTools.executablePath": "/Applications/Nuke17.1v2/Nuke17.1v2.app/Contents/MacOS/Nuke17.1",
```

On Windows, write each `\` twice inside the quotes: `"C:\\Program Files\\Nuke17.1v2\\Nuke17.1.exe"`.

Check it: Command Palette → **Nuke: Launch main executable**. A terminal named after Nuke opens in VS Code, and Nuke starts from it. What your code prints in Nuke appears in that terminal, as in the lessons. Close Nuke before the next step.

## 4. Install `nukeserversocket`

> **Not ready for Nuke 17 yet.** The current `nukeserversocket` is written for PySide2, and Nuke 16 and 17 ship PySide6, so its panel doesn't load. This step will be written when a release for Nuke 17 is out. Until then, use steps 1–3 and 5 and the [package case](#a-package-the-plugin-from-the-lesson), which work without it.

<!-- Draft, for Virgil to confirm once the PySide6 release exists:
1. Command Palette → **Nuke: Add Packages** → **Nuke Server Socket**. Nuke Tools copies it to `~/.nuke/NukeTools/` and adds two lines to `~/.nuke/menu.py` that load it every time Nuke opens its interface.
2. **Nuke: Launch main executable**. In Nuke, open the nukeserversocket panel (which menu?) and click **Connect**.
-->

## 5. Install the stubs

Command Palette → **Nuke: Add Packages** → **Python Stubs**. Nuke Tools copies the stubs to `~/.nuke/NukeTools/stubs` and adds that folder to your user `python.analysis.extraPaths` setting.

Now `import nuke` in a lesson file has no red underline, and VS Code completes `nuke.` names. The stubs only help the editor: they hold Nuke's names, not its code. Your checks still run against the course stand-in, with `academy test`.

## Three ways to run course code in Nuke

### One file: Run Code Inside Nuke

For a file that runs on its own, like the Script Editor exercises of Chapter 2.

1. **Nuke: Launch main executable**, and click **Connect** in Nuke's nukeserversocket panel.
2. Open the file in VS Code. Select some lines to send only those, or select nothing to send the whole file.
3. Command Palette → **Nuke: Run Code Inside Nuke**, or the run button in the editor's upper-right corner.

Nuke runs the code as its Script Editor would, and VS Code shows the output in its **Output** panel, under **Nuke Tools**.

Python runs an `import` only once per Nuke session. If the file imports a module you then change, sending the file again still uses the old module: restart Nuke, or reload the module with `importlib.reload`.

### A package: the plugin from the lesson

For a plugin that Nuke loads at start, through its `menu.py`. The lessons set two variables in a terminal; Nuke Tools sets them for every Nuke it starts, from the `nukeTools.environmentVariables` setting.

Module 2 already has this setting in `.vscode/settings.json`, with the module's `src` folder on `PYTHONPATH`:

```json
{
  "nukeTools.environmentVariables": {
    "PYTHONPATH": ["${workspaceFolder}/src", "$PYTHONPATH"]
  }
}
```

`${workspaceFolder}` is the module folder. Nuke Tools joins the list with the right separator for your system. `$PYTHONPATH` at the end keeps whatever was already set.

Each lesson's plugin lives in its own folder, so point the two variables at the lesson you are on. For the plugin in `src/chapter_02/lesson_03/plugin`:

```json
{
  "nukeTools.environmentVariables": {
    "PYTHONPATH": ["${workspaceFolder}/src/chapter_02/lesson_03/plugin", "${workspaceFolder}/src", "$PYTHONPATH"],
    "NUKE_PATH": ["${workspaceFolder}/src/chapter_02/lesson_03/plugin/startup", "$NUKE_PATH"]
  }
}
```

Then **Nuke: Launch main executable**. The variables reach only the Nuke that Nuke Tools starts, and only when it starts: after you change the setting, close Nuke and launch it again.

Don't add the module's `.venv` to `PYTHONPATH`. It holds the course's own PySide6 and its Python version, and Nuke must use its own.

### A user interface: menus and panels

Interface code needs Nuke's interface, so it runs in two ways:

- **A menu entry** is added by the plugin's `menu.py`, which Nuke runs only when it opens its interface. Set the variables as in the package case and launch Nuke again after each change to `menu.py`.
- **A panel** you are working on can be sent with **Run Code Inside Nuke**, like any file. Nuke already has a running Qt application, so leave out `QApplication` and `app.exec()` and keep only the panel and its `show()`, as the lesson's "Run it in Nuke" shows. With `src` on `PYTHONPATH`, `from chapter_04.lesson_02 import ShotSetupPanel` works without touching `sys.path`.

To restart Nuke fast while you work on start-up code, set `"nukeTools.restartTerminalInstance": true` in your user settings: **Nuke: Launch main executable** then closes the Nuke it started before it starts a new one. Save your Nuke script first.

## Common problems

| You see                                                         | Means                                                  | Do                                                                                   |
| --------------------------------------------------------------- | ------------------------------------------------------ | ------------------------------------------------------------------------------------ |
| **Nuke: Launch main executable** does nothing, or "not found"   | `nukeTools.executablePath` is missing or wrong         | Copy the full path from step 1 into your user settings                               |
| **Run Code Inside Nuke** can't connect                          | Nuke isn't running, or its nukeserversocket isn't on   | Launch Nuke and click **Connect** in the nukeserversocket panel                      |
| No menu entry, and no traceback in Nuke's terminal              | `NUKE_PATH` doesn't reach the plugin's `startup` folder | Fix the `NUKE_PATH` line, then close Nuke and launch it again                        |
| `ModuleNotFoundError` in Nuke's terminal or the Output panel     | `PYTHONPATH` doesn't reach the package                  | Fix the `PYTHONPATH` line, then close Nuke and launch it again                       |
| A change to an imported module doesn't show                     | Python imported it once and reuses it                  | Restart Nuke, or `importlib.reload` the module                                       |
| Red underline on `import nuke`                                  | The stubs aren't installed                             | Step 5                                                                               |

Nuke Tools does more than this guide shows. Its [Marketplace page](https://marketplace.visualstudio.com/items?itemName=virgilsisoe.nuke-tools) lists every command and setting.
