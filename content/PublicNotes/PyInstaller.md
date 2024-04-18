---
title: PyInstaller
tags: Public
Aliases:
Date created: 2024-03-06 15:31
---

A python package for packaging python programs into executable files.

## Documentation
https://pyinstaller.org/en/stable/

## Commands
### Package Script
`pyinstaller <script_path>`

#### Options
- `-y / --noconfirm` auto accept replacing output directory
- `-F / --onefile` package into one file instead of one folder (which is default)
- `--distpath <directory>` specify where to put packaged app (default: ./dist)
- `--icon=<iconfile.ico>` specify the icon for the file
- `--noconsole` prevent the exe file from opening a console 

#### Example
 `pyinstaller -y -F  --distpath ./executable "src/background/exe_test.py"`
 will output exe_test.exe one file into ./executable replacing any previously present content without asking.

## Running from Code
Running from python script involves using function __main__.run with the same arguments like command line

```python
import PyInstaller.__main__

PyInstaller.__main__.run([
    'my_script.py',
    '--onefile',
    '--distpath', './sth'
])
```
