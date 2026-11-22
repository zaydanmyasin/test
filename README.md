# Ledakin-Repo

This repository is made to be a beginner friendly git hands-on made for Kaderisasi Wilayah STEI-K'26. 

## Intro
`Git` is a free, open-source distributed version control system used to track changes in source code and manage project files over time. Originally created in 2005 by Linus Torvalds for developing the Linux kernel, it allows multiple developers to work together on the same project without overwriting each other's work (Most of the times).

Funfact, Git has tracked its own source code almost from the very beginning. So its possible to see Linus's original commit and README.md

## Setup Instructions
To start with the hands-on, simply create a new repository with this one as a template. This can be done by clicking the `Use Template` button on the github page.

After creating the repository click the `< > code` button on the github repository page and copy the link.

1. Ensure git is installed
    ```bash
    git --version
    ```
    If it doesn't return git version, follow the instructions in [INSTALLATION](doc/INSTALLATION.md)

2. Clone repository to you computer

    ```bash
    git clone <copied-url>
    ```

3. Move to the repository root directory
    ```bash
    cd <repo-name>
    ```

## Repository Directory Structure
```text
Ledakin-Repo/
├── README.md          # Intro, Instructions, Extras
├──doc/
│  ├── CHEATSHEET.md   # Git Command Cheatsheet 
│  └── INSTALLATION.md # Git Install Guids
├── Module-1/          # Basics
├── Module-2/          # Ignoring and Keeping
├── Module-3/          # Branching
├── Module-4/          # Merging
└── Module-5/          # Merge Conflicts
```

## Extras
<ol>
<li> This <a href="./doc/INSTALLATION.md"> INSTALLATION.md </a> contains the installation process of git and its required initial configuration.
<li> This <a href="./doc/CHEATSHEET.md"> CHEATSHEET.md </a> contains some commonly used git commands and a short explanation of its purpose and usage.
<li> It is recomendded to use <a href="https://www.conventionalcommits.org/en/v1.0.0/"> Semantc Commits </a> in commit messages. Examples of semantic commits can be seen in <a href="https://github.com/WimarW/Ledakin-Repo/commits/main/"> This Repository </a> or <a href="https://github.com/WimarW/IF2150-RPL-K03-G09/commits/main/"> This One </a>