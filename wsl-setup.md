# Windows Subsystem for Linux Setup
Here are the steps I use to setup a brand new WSL2 environment.

## Before we begin...
1. Install VSCode insiders
2. Install WSL2 and the default Ubuntu Distro (`wsl --install`)
3. Run `sudo apt update && sudo apt upgrade -y`

## Configure Git on WSL
1. Run `sudo apt install git`
2. Install the [GitHub CLI](https://github.com/cli/cli/blob/trunk/docs/install_linux.md)
3. Configure Git:
git config --global color.ui true
git config --global user.name "YOUR NAME"
git config --global user.email "YOUR@EMAIL.com"
git config --global alias.st status
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.ci commit
git config --global core.editor 'code --wait'

## Setup ASDF for NodeJS
1. Install ASDF `git clone https://github.com/asdf-vm/asdf.git ~/.asdf --branch v0.12.0`

2. Install the the NodeJS Plugin
```shell
asdf plugin add nodejs
asdf install nodejs 18.16.1 # Change this to LTS
asdf global nodejs 18.16.1 # Change this to LTS
$SHELL
```

3. Confirm you're running the correct Node version `node -v`

4. Globally install Yarn: `npm install -g yarn`

## Install Ruby with ASDF
1. Install apt dependencies:
```shell
sudo apt-get update
sudo apt-get install git-core zlib1g-dev build-essential libssl-dev libreadline-dev libyaml-dev libsqlite3-dev sqlite3 libxml2-dev libxslt1-dev libcurl4-openssl-dev software-properties-common libffi-dev libpq-dev uuid-dev
```
2. `asdf plugin add ruby`
3. `asdf install ruby latest`
4. `asdf global ruby latest`
5. `gem update --system`

Optional: Install Rails with `gem install rails`

## Install Overmind
1. `sudo apt-get install tmux`
2. `asdf plugin add go` 
3. `asdf install go latest`
4. `go install github.com/DarthSim/overmind/v2@latest`
5. Add Go PATH to your `.zshrc` with `export PATH="$(go env GOPATH)/bin:$PATH"`

## Install Minio
```shell
wget https://dl.min.io/server/minio/release/linux-amd64/archive/minio_20230718174940.0.0_amd64.deb -O minio.deb
sudo dpkg -i minio.deb

curl https://dl.min.io/client/mc/release/linux-amd64/mc \
  --create-dirs \
  -o $HOME/minio-binaries/mc

chmod +x $HOME/minio-binaries/mc
export PATH=$PATH:$HOME/minio-binaries/

mc --help
```

## Install and Setup ZSH & OhMyZsh (ASDF-Comptabile)
1. Install ZSH and make it the default:
```shell
sudo apt install zsh
```
> On VSCode, Click `Control + Shift + P` --> Terminal: Select Default Profile, and set it to ZSH.

2. Install `OhMyZSH`, `powerlevel10k`, `ASDF`, and plugins
```shell
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
git clone https://github.com/zsh-users/zsh-autosuggestions $ZSH_CUSTOM/plugins/zsh-autosuggestions
```

3. Copy the `.zshrc and .p10k.zsh` file in this repo into `~` 
4. Install the [Meslo NerdFont](https://github.com/romkatv/powerlevel10k#fonts) on your Windows Host (Right click and run as admin)
5. Open VSCode's User Settings UI, Search for `terminal.integrated.fontFamily` and set it to `MesloLGS NF`
6. On the new Windows Terminal, open Settings, click on Defaults, click Appearance and set Font face to MesloLGS NF.
4. Restart the terminal with `$SHELL`

## Setup VSCode
1. Install the WSL Extention and run the Connect to WSL command 

> On WSL, we need to setup an alias which opens VSCode insiders with `code` instead of `code-insiders`. This is done on the .zshrc file
