---
title: Angular ng Commands
Date created: 2024-04-16 13:21
Aliases:
tags: 
  - Public
---

[Documentation page](https://angular.io/cli)
## Syntax

### Basic Syntax
`ng <command> <options>`

### Option Syntax
`--option` / `-alias`
#### Boolean Options
`--option` / `--no-option`
#### Array Options
`--option val1 val2` / `--option val1 --option val2`

| COMMAND                   | ALIAS | DESCRIPTION                                                                                               |
| ------------------------- | ----- | --------------------------------------------------------------------------------------------------------- |
| `add`                     |       | Adds support for an external library to your project.                                                     |
| `analytics`               |       | Configures the gathering of Angular CLI usage metrics.                                                    |
| `build`                   | `b`   | Compiles an Angular application or library into an output directory named dist/ at the given output path. |
| `cache`                   |       | Configure persistent disk cache and retrieve cache statistics.                                            |
| `completion`              |       | Set up Angular CLI autocompletion for your terminal.                                                      |
| `config`                  |       | Retrieves or sets Angular configuration values in the angular.json file for the workspace.                |
| `deploy`                  |       | Invokes the deploy builder for a specified project or for the default project in the workspace.           |
| `doc`                     | `d`   | Opens the official Angular documentation (angular.io) in a browser, and searches for a given keyword.     |
| `e2e`                     | `e`   | Builds and serves an Angular application, then runs end-to-end tests.                                     |
| `extract-i18n`            |       | Extracts i18n messages from source code.                                                                  |
| [[ng generate\|generate]] | `g`   | Generates and/or modifies files based on a schematic.                                                     |
| `lint`                    |       | Runs linting tools on Angular application code in a given project folder.                                 |
| `new`                     | `n`   | Creates a new Angular workspace.                                                                          |
| `run`                     |       | Runs an Architect target with an optional custom builder configuration defined in your project.           |
| `serve`                   | `s`   | Builds and serves your application, rebuilding on file changes.                                           |
| `test`                    | `t`   | Runs unit tests in a project.                                                                             |
| `update`                  |       | Updates workspace and its dependencies                                                                    |
| `version`                 | `v`   | Outputs Angular CLI version.                                                                              |