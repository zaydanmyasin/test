# Installation
This document details the steps of installing git and configuring it to work with github.

# Table of Contents
<ol>
    <li> <a href="#installing-git">Installing Git</a>
        <ul>
            <li> <a href="#windows"> Windows </a>
            <li> <a href="#macos"> macOS </a>
            <li> <a href="#linux"> Linux </a>
            <li> <a href="#verify-installation"> Verify Installaion </a>
        </ul>
    <li> <a href="#configuring-identity">Configuring Identity</a> 
</ol>

# Installing Git 
## Windows
For windows users, there are two methods of installing git CLI.<br>

1. Official Git Installer <br>
Download the installer from the <a href="https://git-scm.com/install/"> Git Download Page </a> and run the installer
2. `WinGet` <br>
If you have WinGet installed. Simply run in `command prompt` or `powershell` this command.
```bash
winget install --id Git.Git -e --source winget
```

## macOS
For mac users, there are two methods of installing git CLI<br>
1. `Homebrew` <br>
If you have homebrew installed, open the terminal and run
```bash
brew install git
```
2. `Xcode Command Line Tools`
Running `git --version` in the terminal will prompt you to install the Xcode Command Line Tools, if not installed

## Linux
### Debian or Ubuntu
```bash
sudo apt update && sudo apt install git
```

### Fedora 
```bash
sudo dnf install git 
```

## Verify Installation
To verify git installation, in the terminal run
```bash
git --version
```

# Configuring Identity
1. Set Username and Email

    ```bash
    git config --global user.name "Your Name"
    git config --global user.email "your_email@example.com"
    ```
2. Set main as default branch in new local repositories

    ```bash
    git config --global init.defaultBranch main
    ```

3. Verify your settings
    ```bash
    git config --list
    ```

