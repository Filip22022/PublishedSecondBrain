---
title: Windows Command-line
Date created: 2024-04-15 12:25
Aliases:
tags: 
  - Public
---

Sometimes I find myself in the need to use cmd for something more complicated than checking my ip address. Unfortunately I usually find that I forgot everything about how to use it since the last time, so here's a list of useful commands.

### Navigation

#### Change Directory
`cd <path>`
##### Go to Root
`cd\`
##### Go to Parent
`cd ..`
#### Change Drive
- `<DriveLetter>:` ex: `d:`
- `cd /d <path>`

### Files and Directories
#### View Directory Content
`dir`
#### Make Directory
`mkdir <name>`
`md <name>`
#### Rename
`ren <folder> <new name>`
#### Delete
`del <name>`

#### Create File
`echo "" > <file>`

### Admin Privileges
#### Activate Privileges from Open Cmd
`runas /user:<adnim username> cmd`


---
[[Command Linne Interface]]