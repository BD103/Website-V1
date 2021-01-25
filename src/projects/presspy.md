# [PressPy](https://pypi.org/project/presspy)

![PressPy](https://github.com/BD103/PressPy/raw/master/imgs/PressPy_README.png)

![Lines of code](https://img.shields.io/tokei/lines/github/BD103/PressPy?color=9cf&style=for-the-badge)
![Github release](https://img.shields.io/github/v/release/BD103/PressPy?color=9cf&include_prereleases&style=for-the-badge)
![PyPI - Python Version](https://img.shields.io/pypi/pyversions/presspy?color=9cf&style=for-the-badge)
![Latest commit](https://img.shields.io/github/last-commit/BD103/PressPy?color=9cf&style=for-the-badge)
![PyPI - Status](https://img.shields.io/pypi/status/presspy?color=9cf&style=for-the-badge)
![PyPI - License](https://img.shields.io/pypi/l/PressPy?color=9cf&style=for-the-badge)
![PyPI](https://img.shields.io/pypi/v/PressPy?color=9cf&style=for-the-badge)
![Github issues](https://img.shields.io/github/issues/BD103/PressPy?color=9cf&style=for-the-badge)
![Github milestones](https://img.shields.io/github/milestones/all/BD103/PressPy?color=9cf&style=for-the-badge)
![Github top language](https://img.shields.io/github/languages/top/BD103/PressPy?color=9cf&style=for-the-badge)

Presspy is a Python compression software.

## Intallation

Intall with Pip:
```console
pip install --upgrade presspy
```

Install latest Github version:
**May have many bugs!**
```console
pip install --upgrade git+https://github.com/BD103/presspy
```

## How to Use

PressPy is purely console based. Open up command prompt, or another console likewise, and type `presspy`.
This gives you a list of available commands and options. There are three main functions:

### Run

Runs a `.press` file.

Usage:
```console
presspy run file --keep
```

File:
The location of your `.press` file relative to your current directory.

--keep:
Use this flag if you wish to keep the extracted source after running.

### Press

Presses a Python program into a `.press` file.

Usage:
```console
presspy press path
```

Path:
The folder or directory your source code is in relative to your current directory. This folder must contain a press.json file. See the [Wiki](https://github.com/BD103/PressPy/wiki) for more information.

### Extract

Puts the source of a `.press` file into a folder.

Usage:
```console
presspy extract file
```

File:
The location of your `.press` file relative to your current directory.

---

Links:

- [Github](https://github.com/BD103/PressPy)
- [PyPI](https://pypi.org/project/presspy)
- [Website](https://bd103.github.io/projects/PressPy/)