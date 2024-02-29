# Aliases

Personal aliases can be added to .bash_rc, .zshrc etc. to access commonly run commands

```
# Personal aliases are placed here. Run `aliases` to view personal aliases
# For a full list of active aliases, run `alias`.
alias aliases="cat ~/.zshrc | grep alias"
alias clean-js="rm -rf node_modules .next"
alias copy=cp
alias git-log="git log --perl-regexp --author='^((?!system).*)$'"
alias igrep="grep -i"
alias rand="openssl rand -hex 12"
```
