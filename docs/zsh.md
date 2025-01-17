# zsh

- nerd font
- starship
- nvim

`cat ~/.zshrc`

```sh
# If you come from bash you might have to change your $PATH.
# export PATH=$HOME/bin:/usr/local/bin:$PATH

# Path to your oh-my-zsh installation.
export ZSH="$HOME/.oh-my-zsh"

ZSH_THEME="robbyrussell"

plugins=(
    git
    zsh-autosuggestions
    fast-syntax-highlighting
    direnv
)

source $ZSH/oh-my-zsh.sh

export PATH="$HOME/.local/bin:$PATH"

fpath+=${ZSH_CUSTOM:-${ZSH:-~/.oh-my-zsh}/custom}/plugins/zsh-completions/src

export PYENV_ROOT="$HOME/.pyenv"
command -v pyenv >/dev/null || export PATH="$PYENV_ROOT/bin:$PATH"
eval "$(pyenv init -)"

export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"  # This loads nvm
[ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"  # This loads nvm bash_completion

export PATH="$PATH:/opt/nvim/bin"
alias astronvim="NVIM_APPNAME=AstroNvim nvim"
alias mnvim="NVIM_APPNAME=mnvim nvim"
# alias nvide="NVIM_APPNAME=AstroNvim neovide --wsl"
# alias nvide="WAYLAND_DISPLAY= WINIT_UNIX_BACKEND=x11 NVIM_APPNAME=mnvim neovide --wsl"
alias nvide="NVIM_APPNAME=mnvim neovide"

# starship
eval "$(starship init zsh)"

# uv
eval "$(uv generate-shell-completion zsh)"
eval "$(uvx --generate-shell-completion zsh)"

eval "$(direnv hook zsh)"

eval "$(starship init zsh)"

# proxy for wsl
# eval "$(cat ~/proxy_clash.sh)"

# for wsl ip
export HOST_IP="$(ip route show | grep -i default | awk '{ print $3}')"
export WSL_IP="$(hostname -I | awk '{print $1}')"

# aventa.nvim openai
export OPENAI_API_KEY=""

unset_proxy() {
    unset http_proxy
    unset HTTP_PROXY
    unset https_proxy
    unset HTTPS_PROXY
    unset all_proxy
    unset ALL_PROXY
}

```
