# Windows Subsystem for Linux Setup
Here are the steps I use to setup a brand new WSL2 environment.

## Before we begin...
1. Install VSCode insiders
2. Install [PowerShell Core](https://github.com/PowerShell/PowerShell0)
3. Install the new Windows Terminal
4. Install 1Password (Use its agent to Authenticate with GitHub) and its [CLI](https://developer.1password.com/docs/cli/get-started/#install)

# 1Password
1. Install and Login
2. Open settings and Install and Setup the 1Password CLI
3. Restart Terminal App if it was already open (don't just quit the shell, restart the whole app to reload PATH)
4. Setup SSH Agent (don't forget to disable OpenSSH)

## Configure Git
1. Install Git [from here](https://git-scm.com/download/win)
2. Configure Git:
git config --global color.ui true
git config --global user.name "YOUR NAME"
git config --global user.email "YOUR@EMAIL.com"
git config --global alias.st status
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.ci commit
git config --global core.editor 'code --wait'


## Setup OhMyPosh
1. `winget install XP8K0HKJFRXGCK`
2. Restart Terminal App if it was already open (don't just quit the shell, restart the whole app to reload PATH)
3. Create the `$PROFILE` with `New-Item -Path $PROFILE -Type File -Force`
4. Add the following to the end of the `$PROFILE` file
```
New-Alias code code-insiders
oh-my-posh init pwsh | Invoke-Expression
```
5. Run `. $PROFILE` to load changes

> Note: on Windows, we need to setup an alias which opens VSCode insiders with `code` instead of `code-insiders`.
