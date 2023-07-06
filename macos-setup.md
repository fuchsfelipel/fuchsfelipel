# MacOS Setup
This document details how I setup a formatted MacBook.

## Downloads
- Browsers: Microsoft Edge, Google Chrome, Firefox
- 1Password
- XCode + XCode CLI (just open terminal and type `git`. It will install XCode CLI)
- JetBrains Toolbox: RubyMine, WebStorm, DataGrip, Fleet
- VSCode
- WhatsApp, Microsoft Teams and Slack
- Microsoft 365
- Magnet
- Docker

> Sign in to 1Password, open Settings > Developer and setup the SSH Host. Then, click on your Git GPG key and click on the `configure` banner.

## Terminal Setup
1. Install [Homebrew](https://brew.sh)
2. Configure Git Aliases
```shell
brew install coreutils libyaml git gh libpq icu4c
gh auth login
```
```shell
git config --global color.ui true
git config --global user.name "YOUR NAME"
git config --global user.email "YOUR@EMAIL.com"
git config --global alias.st status
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.ci commit
git config --global core.editor 'code --wait'
```
3. Install iTerm2

4. Install ZSH from Homebrew
```shell
brew install zsh
chsh -s /opt/homebrew/bin/zsh
```

5. Install `OhMyZSH`, `powerlevel10k`, `ASDF`, and plugins
```shell
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
git clone https://github.com/zsh-users/zsh-autosuggestions $ZSH_CUSTOM/plugins/zsh-autosuggestions
git clone https://github.com/asdf-vm/asdf.git ~/.asdf --branch v0.11.3
```

6. Install the Meslo Nerd Font ([instructions](https://github.com/romkatv/powerlevel10k#fonts))

7. Open iTerm2:
  - On `Profiles --> Window` set transparency to `15%`
  - On `Profiles` set the font to `Meslo NF`

8. Copy the `.zshrc and .p10k.zsh` file in this repo into `~` and restart the terminal

## ASDF for Ruby on Rails
1. Install the Plugins and current Ruby version
```shell
asdf plugin add ruby
asdf plugin add nodejs

asdf install ruby latest
asdf global ruby latest

asdf install nodejs 18.16.1 # Change this to LTS
asdf global nodejs 18.16.1 # Change this to LTS
$SHELL
```

2. Confirm you're running the correct Ruby and Node versions `ruby -v` and `node -v`

3. Globally install some packages:
```shell
npm install -g yarn
gem install rails standard
```
