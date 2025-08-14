---
title: WSL Translate
description: This is a small portable shell script built for translating Windows paths in a WSL environment, and optionally performing functions on the result.
pubDate: Aug 13 2025
heroImage: ../../../public/images/wsl_translate-hero.png
---
# Project Link: <a href="https://github.com/Alexzander-Hurd/WSL_Translate"><img src="https://img.shields.io/badge/GitHub-%23121011.svg?logo=github&logoColor=white"/></a>

**Quick Stats:**

- Tech stack - Bash, Zsh, Shell
- Current version - Beta 0.1 (Mostly complete may need tweeks)
- Planned features - None
- GitHub stars/forks/issues - 
<p><a href="https://github.com/Alexzander-Hurd/WSL_Translate/stargazers">
  <img src="https://img.shields.io/github/stars/Alexzander-Hurd/WSL_Translate?style=for-the-badge" alt="GitHub stars" />
</a>
<a href="https://github.com/Alexzander-Hurd/WSL_Translate/network/members">
  <img src="https://img.shields.io/github/forks/Alexzander-Hurd/WSL_Translate?style=for-the-badge" alt="GitHub forks" />
</a>
<a href="https://github.com/Alexzander-Hurd/WSL_Translate/issues">
  <img src="https://img.shields.io/github/issues/Alexzander-Hurd/WSL_Translate?style=for-the-badge" alt="GitHub issues" />
</a>
<a href="https://github.com/Alexzander-Hurd/WSL_Translate/blob/master/LICENSE">
  <img src="https://img.shields.io/github/license/Alexzander-Hurd/WSL_Translate?style=for-the-badge" alt="GitHub license" />
</a></p>

# Overview

WSL Translate is a minimal, zero-dependency Bash/Zsh utility that bridges the gap between Windows file paths and the Linux file system used in Windows Subsystem for Linux (WSL). It can be used purely as a path converter or extended to execute common shell commands directly on the translated paths.

The tool works with:

- Standalone invocation to convert paths
- Optional inline functions such as cd, ls, mv, cp, rm, mkdir, and touch
- Sourced mode for persistent context changes in the current shell session
- Bash and Zsh environments, with shell-specific behaviour handled automatically

# Purpose

I use WSL heavily, and I wanted a simple, zero-dependency tool that lets me work with Windows directories without manually translating paths from other programs. WSL Translate allows basic operations, or more complex workflows via piping the stdout mode, directly on Windows paths.

The project solves a straightforward problem while ensuring compatibility with both Bash and Zsh, and remains fully portable across environments.

# Demo

![[wsl_translate-demo.gif]]

# Features

- Converts paths such as  
  C:\Users\Name\Documents → /mnt/c/Users/Name/Documents
- Supports optional functions:
  - stdout (default) – output the translated path
  - cd – change directory (only in sourced mode)
  - ls – list directory contents
  - mv, cp, rm, mkdir, touch
- .env configuration support for:
  - Default function (e.g. always run ls after translation)
  - Mount point override (e.g. /mnt/d instead of /mnt/c)
- No dependencies beyond the shell itself

# Usage Examples

**Basic translation**
```bash
./wsl_translate.sh "C:\Users\Name\Documents"
# /mnt/c/Users/Name/Documents
```

**Run a command on the translated path**
```bash
WSL_TRANSLATE_FUNC=ls ./wsl_translate.sh "C:\Windows"
```

**Sourced mode (persistent context)**
```bash
source ./wsl_translate.sh "C:\Users"
```
This allows changing directory within your current shell session.

# Installation

Clone the repository and make the script executable:

```bash
git clone https://github.com/Alexzander-Hurd/WSL_Translate.git
cd WSL-Translate
chmod +x wsl_translate.sh
```

Optionally, add the script to your $PATH for global use.

# Links

- [View on GitHub](https://github.com/Alexzander-Hurd/WSL_Translate)

# Status

The core functionality is complete and stable. Planned enhancements include:

- Flags and options parsing (--dry-run, --force, etc.)
- Configurable mounts per drive
- Shell function wrappers for persistent aliases
- WSL 2 path convention support
