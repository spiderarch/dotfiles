# dotfiles
my dotfiles of nvim kitty &amp; zsh 
i use vim.plug and oh my zsh 
zsh config



export ZSH="$HOME/.oh-my-zsh"
ZSH_THEME="muse"

ENABLE_CORRECTION="true"

plugins=(
	git
	zsh-autosuggestions
	zsh-syntax-highlighting
	zsh-history-substring-search
)

source $ZSH/oh-my-zsh.sh



function dir_icon {
	if [[ "$PWD" == "$HOME" ]]; then
		echo "%B%F{#ffffff}%f%b"
	else
		echo "%B%F{#ffffff}%f%b"
	fi
}

function parse_git_branch {
	local branch
	branch=$(git symbolic-ref --short HEAD 2> /dev/null)
	if [ -n "$branch" ]; then
		echo " [$branch]"
	fi
}
ZSH_HIGHLIGHT_STYLES[command]='fg=#8B0000,bold'
ZSH_HIGHLIGHT_STYLES[alias]='fg=#8B0000,bold'
ZSH_HIGHLIGHT_STYLES[builtin]='fg=#8B0000,bold'
ZSH_HIGHLIGHT_STYLES[unknown-token]='fg=8B0000'
ZSH_HIGHLIGHT_STYLES[arg0]='fg=8B0000'
PROMPT='%F{#8B0000} %f %F{#ffffff}%n%f $(dir_icon) %F{#ffffff}$(parse_git_branch)%f %(?.%B%F{#8B0000}~.%F{#8B0000}~)%f%b '
