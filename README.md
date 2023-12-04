<p align="center">
<img src="https://raw.githubusercontent.com/apache/nuttx/master/Documentation/_static/NuttX320.png" width="175">
</p>

* Introduction
* Community
  - Getting Help
  - Mailing Lists
  - Issue Tracker
  - Source Code
  - Website Source Code
* Environments
  - Installing Cygwin
  - Ubuntu Bash under Windows 10
  - Using macOS
* Installation
  - Download and Unpack
  - Semi-Optional apps/ Package
  - Installation Directories with Spaces in the Path
  - Downloading from Repositories
  - Related Repositories
  - Notes about Header Files
* Configuring NuttX
  - Instantiating "Canned" Configurations
  - Refreshing Configurations
  - NuttX Configuration Tool
  - Finding Selections in the Configuration Menus
  - Reveal Hidden Configuration Options
  - Make Sure that You are on the Right Platform
  - Comparing Two Configurations
  - Making defconfig Files
  - Incompatibilities with Older Configurations
  - NuttX Configuration Tool under DOS
* Toolchains
  - Cross-Development Toolchains
  - NuttX Buildroot Toolchain
* Shells
* Building NuttX
  - Building
  - Re-building
  - Build Targets and Options
  - Native Windows Build
  - Installing GNUWin32
* Cygwin Build Problems
  - Strange Path Problems
  - Window Native Toolchain Issues
* Documentation

# Steiner Brodaktschns

Relay Pin: PB7, see GPIO_OUT1 in board.h of stm32f429i-disco

tasks.json:
{
    "version": "2.0.0",
    "tasks": [
        {
            "label": "pyocd gdbserver",
            "type": "shell",
            "command": "pyocd gdbserver --target STM32F429ZITx"
        },
        {
            "label": "pyocd program",
            "type": "shell",
            "command": "pyocd load ./nuttx/nuttx --target STM32F429ZITx --format elf",
            "problemMatcher": []
        },
        {
            "label": "openocd gdbserver",
            "type": "shell",
            "command": "openocd -f board/stm32f429disc1.cfg",
            "problemMatcher": []
        }
    ]
}

launch.json:
{
    "version": "0.2.0",
    "configurations": [
        {
            "name": "Cortex Debug",
            "cwd": "${workspaceFolder}",
            "executable": "./nuttx/nuttx",
            "request": "attach",
            "type": "cortex-debug",
            "runToEntryPoint": "__start",
            "servertype": "external",
            "gdbTarget": "localhost:3333",
            "preResetCommands": [
                "mon halt",
                "mon reset"
            ]
        }
    ]
}

# INTRODUCTION

![POSIX Badge](https://img.shields.io/badge/POSIX-Compliant-brightgreen?style=flat&label=POSIX)
[![License](https://img.shields.io/badge/License-Apache%202.0-blue
)](https://nuttx.apache.org/docs/latest/introduction/licensing.html)
![Issues Tracking Badge](https://img.shields.io/badge/issue_track-github-blue?style=flat&label=Issue%20Tracking)
[![Contributors](https://img.shields.io/github/contributors/apache/nuttx
)](https://github.com/apache/nuttx/graphs/contributors)
[![GitHub Build Badge](https://github.com/apache/nuttx/workflows/Build/badge.svg)](https://github.com/apache/nuttx/actions/workflows/build.yml)
[![Documentation Badge](https://github.com/apache/nuttx/workflows/Build%20Documentation/badge.svg)](https://nuttx.apache.org/docs/latest/index.html)

Apache NuttX is a real-time operating system (RTOS) with an emphasis on
standards compliance and small footprint. Scalable from 8-bit to 64-bit
microcontroller environments, the primary governing standards in NuttX are POSIX
and ANSI standards. Additional standard APIs from Unix and other common RTOSs
(such as VxWorks) are adopted for functionality not available under these
standards, or for functionality that is not appropriate for deeply-embedded
environments (such as fork()).

For brevity, many parts of the documentation will refer to Apache NuttX as simply NuttX.

## Getting Started
First time on NuttX? Read the [Getting Started](https://nuttx.apache.org/docs/latest/quickstart/index.html) guide!
If you don't have a board available, NuttX has its own simulator that you can run on terminal.

## Documentation
You can find the current NuttX documentation on the [Documentation Page](https://nuttx.apache.org/docs/latest/).

Alternatively, you can build the documentation yourself by following the Documentation Build [Instructions](https://nuttx.apache.org/docs/latest/contributing/documentation.html).

The old NuttX documentation is still available in the [Apache wiki](https://cwiki.apache.org/NUTTX/NuttX).

## Supported Boards
NuttX supports a wide variety of platforms. See the full list on the [Supported Platforms](https://nuttx.apache.org/docs/latest/platforms/index.html) page.

## Contributing
If you wish to contribute to the NuttX project, read the [Contributing](https://nuttx.apache.org/docs/latest/contributing/index.html) guidelines for information on Git usage, coding standard, workflow and the NuttX principles.

## License
The code in this repository is under either the Apache 2 license, or a license compatible with the Apache 2 license. See the [License Page](https://nuttx.apache.org/docs/latest/introduction/licensing.html) for more information.
