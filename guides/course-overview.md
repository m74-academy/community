# Course overview

M74 Academy teaches VFX pipeline development: the Python tools that move shots, files, and versions between the people who make a film's visual effects. It is for people who can already program and want to work as pipeline TDs. It is not a beginner Python course, and you need no visual-effects experience to start.

## What you do

You learn by building. Each lesson teaches one concept through a production problem, then you write a function and run a check. Each module ends with a capstone: a working tool in your own repository that another person can review and run. [How the course works](how-the-course-works.md) explains lessons, Core and Gold, labs, and the capstone.

## One pipeline, five modules

The five modules come one after another, and each capstone extends the same pipeline.

| Module | You build | What it adds |
|---|---|---|
| [0 — Shot Inventory](https://github.com/m74-academy/module-0) | A script that groups image frames into sequences and finds missing ones | A free introduction; try the lesson routine before you commit |
| 1 — Scripting & Interfaces | A read-only delivery validator | Checks that a shot delivery arrived complete, without changing it |
| 2 — Pipeline Development | Shot Setup for Nuke | Opens a shot in Nuke: reads its context, shows a preview, builds a versioned script |
| 3 — Pipeline Systems & OpenUSD | An asset and shot registry | Records shots, assets, and versions; publishing registers a new version |
| 4 — Delivery & Operations | A release of your pipeline tool | Launcher, configuration, packaging, CI, and a clean install on another machine |
| 5 — AI Tooling | An AI-assisted tool | Tags or checks registered items through an AI service, with human approval |

Modules 3 to 5 are in preparation; their details may change. If your earlier capstone is incomplete, each module offers a starter project, so you can continue.

## The idea that repeats

Every module applies the same production reasoning, each time at greater depth:

1. Define the data: what comes in, what goes out, who owns it.
2. Resolve the production context explicitly: which show, shot, and task.
3. Validate before you change anything or call an external service.
4. Act through a small, visible boundary.
5. Record results and failures.
6. Package the work so another person can review and run it.

## Where to start

1. [Install the software](install-uv-and-git.md), once.
2. Open [Module 0](https://github.com/m74-academy/module-0) and follow its **Start here**. If its lessons feel easy, you are ready for Module 1.
3. [Read, edit, and check a lesson](lesson-loop.md).
4. [How the course works](how-the-course-works.md): lessons, Core and Gold, labs, and the capstone.

Videos will accompany these pages as they are released. Everything you need is already in the text; the videos add to it, they do not replace it.
