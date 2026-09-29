# Read, edit, and check a lesson

Every coding lesson follows the same loop:

```text
read the lesson  →  edit src/chapter_NN/lesson_NN.py  →  save
      ↑                                                  ↓
      └──────  read the result  ←  uv run academy test CHAPTER LESSON
```

The module's practice guide lists every lesson, the file to edit, and its command. The examples below use Module 1, Chapter 1, Lesson 2.

## 1. Read the lesson

Open it with `uv run academy docs`, in VS Code, or on GitHub. Read the worked example before you edit anything.

Some lessons are written, not coded. `uv run academy test 1 1` then tells you which Markdown file to write in, such as `answers/chapter_01/lesson_01.md`. Use the lesson's self-check; there is no automated grade.

## 2. Run the checks first

```console
uv run academy test 1 2
```

On a new lesson the checks fail. That means the lesson is ready to solve, not that something is broken. A setup problem looks different: `command not found` or `PROJECT ERROR`.

## 3. Edit and save

The starter file gives you each function's signature, type hints, and docstring, with `pass` in place of the body:

```python
def frame_filename(shot: str, task: str, version: int, frame: int, extension: str) -> str:
    """Return the delivery filename for one frame, e.g. SH010_comp_v002.1001.exr."""
    pass
```

Keep the signature and type hints. Replace `pass` with your code and save. There is nothing to reinstall.

## 4. Check again and read the result

```console
uv run academy test 1 2
```

Read a failure from top to bottom:

```text
test_lesson_02.py::test_sequence_pattern[four-digit padding] FAILED
tests/chapter_01/test_lesson_02.py:40: in test_sequence_pattern
E   AssertionError: assert 'SH010_comp_v####.exr' == 'SH010_comp_v002.####.exr'
```

1. **Which check:** `test_sequence_pattern`, case `four-digit padding`.
2. **Where:** line 40 of the test file.
3. **Yours versus expected:** in `assert A == B`, A is what your code returned.

| Word | Means | Look at |
|---|---|---|
| `FAILED` | Your code ran and returned the wrong value | the difference between the two values |
| `ERROR` | Your code crashed before it could be checked | the last `E` line: exception, file, and line |

The checks include cases the lesson never showed, so a hardcoded answer won't pass. Change your code, never the checks.

## 5. When it passes

```text
PASS
Supplied checks passed.
```

PASS means the supplied checks passed, not every possible input. Answer the lesson's **Think** questions before opening their answers, then commit and push:

```console
git add src/chapter_01/lesson_02.py
git commit -m "Solve lesson 1.2"
git push
```

## Other ways to check

| Command | Checks |
|---|---|
| `uv run academy test 1 2` | one lesson |
| `uv run academy test 1` | a whole chapter |
| `uv run pytest tests/chapter_01/test_lesson_02.py -v` | one test file, with every case listed |

Read the test files to see the exact inputs.

Next: [Get course updates](course-updates.md).
