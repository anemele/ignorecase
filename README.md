# ignore case

A repo to test the case-sensitive feature of git on different OS.

> This repo is created on Linux (Ubuntu)

---

Cloning repo on Windows, git throws a warning:

```text
warning: the following paths have collided (e.g. case-sensitive paths
on a case-insensitive filesystem) and only one from the same
colliding group is in the working tree:

  'aBC'
  'aBc'
  'abC'
  'abc'
  'ABC/.gitkeep'
  'ABc/.gitkeep'
  'AbC/.gitkeep'
  'Abc/.gitkeep'
```

and only checks out one file `abc`, other files disappear, dirs deleted.

---

Update on Linux, touching files in dirs with different names, then test again.

---

Pulling on Windows, the files are deleted, the dirs are merge into one named `ABC`, and in which has the files `00 01 10 11`.
