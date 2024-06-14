# ZSH

## 安装

```sh
$ sudo pacman -S zsh							# Shell
$ sudo pacman -S zsh-theme-powerlevel10k 		# 主题
$ paru -S ttf-nerd-fonts-symbols-2048-em        # 字体
$ chsh -s /bin/zsh
# 按`0`保持默认配置
```

## 配置主题

`$ vim .zshrc`

```sh
source /usr/share/zsh-theme-powerlevel10k/powerlevel10k.zsh-theme
```

## 生效主题

```sh
$ source .zshrc
```

## 自动补全

`$ vim .zshrc`

```conf
autoload -U compinit
compinit
```

## 删除原有配置

```sh
$ rm .bash*
```
