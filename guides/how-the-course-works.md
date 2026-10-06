# How the course works

M74 Academy is five modules taken one after another. Each module is a set of chapters, each chapter a set of short lessons, and each module ends with a capstone: a tool you build in your own repository.

## Lessons

Each lesson teaches one concept through a production problem, then gives you a function to write and checks you run with `academy test`. A chapter's opening lesson can be reading only, with nothing to check. [Read, edit, and check a lesson](lesson-loop.md) shows the loop.

## Core and Gold

Every lesson is **Core** or **Gold**. Core lessons, with the Core capstone, are the complete path: they teach what a tool needs to work correctly and fail clearly, and finishing them completes the module. A Gold lesson is optional: it extends an earlier lesson with hardening, proof, or tooling, and its page says which lesson it extends. Some Core lessons also end with a **Gold** section, whose checks live in a separate `tests/chapter_NN/test_lesson_NN_gold.py` file.

`academy test CHAPTER` checks the Core lessons; add `--gold` to check the Gold lessons and the Gold sections too. Completing a module with Gold means the Core capstone plus every Gold lesson passed.

## Labs

Labs revisit a chapter's concepts on a changed case: you predict, run, and compare. They have no automatic grade. Write lab scripts, copies, and notes in your module's `work/` folder and commit them with the rest of your work, so a peer or instructor can review them on your fork.

## The capstone

The capstone brief fixes the tool's outside: its command, exit codes, and output format. Everything inside is your design. Its **Core** requirements complete the module; its **Gold challenges** are optional. You build it in a repository of your own, with your own tests. Peer review and a simulated Lead TD review happen where your course includes them; they never decide completion.

## Updates

When a module gets a new release, `academy health` says so; `academy update` brings it in and keeps the lesson code you already wrote.
