# ignore case

A repo to test the case-sensitive feature of git on different OS.

> This repo is created on Linux (Ubuntu)

```bash
$ tree -a -I .git
.
├── ABC
│   └── .gitkeep
├── ABc
│   └── .gitkeep
├── AbC
│   └── .gitkeep
├── Abc
│   └── .gitkeep
├── README.md
├── aBC
├── aBc
├── abC
└── abc

5 directories, 9 files
```

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

```batch
$ tree /f
Folder PATH listing for volume C
Volume serial number is XXXX-XXXX
C:.
    abc
    README.md

No subfolders exist
```

---

Update on Linux, touching files in dirs with different names, then test again.

```bash
$ tree -a -I .git
.
├── ABC
│   └── 00
├── ABc
│   └── 01
├── AbC
│   └── 10
├── Abc
│   └── 11
├── README.md
├── aBC
├── aBc
├── abC
└── abc

5 directories, 9 files
```

---

Pulling on Windows, the files are deleted, the dirs are merge into one named `ABC`, and in which has the files `00 01 10 11`.

```batch
$ tree /f
Folder PATH listing for volume C
Volume serial number is XXXX-XXXX
C:.
│   README.md
│
└───ABC
        00
        01
        10
        11

```

---

Record on Linux, there are still dirs `ABC ABc AbC Abc` and their files in.

That is a filesystem difference.

```bash
$ tree -a -I .git
.
├── ABC
│   └── 00
├── ABc
│   └── 01
├── AbC
│   └── 10
├── Abc
│   └── 11
└── README.md

5 directories, 5 files
```

---

End record on Windows.
