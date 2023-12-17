# Zsh

专为交互式使用而设计的 Shell。

> https://zsh.sourceforge.io/

## 安装

- `zsh` - 本体
- `zsh-autosuggestions` - 基于历史输入与自动补全的命令建议工具
- `zsh-git-prompt-git` - Git 状态提示
- `zsh-syntax-highlightling` - 语法提示

## 初始化

1. 运行 Zsh 。
  - `zsh`
2. 根据 *新用户向导（zsh-newuser-install）* 进行基础配置。
3. 切换默认 Shell 。
  - `chsh <USER> --shell /bin/zsh`
4. 编辑 `~/.zshrc` 进行自定义配置。

## 插件

```sh
# Plugin
source path/to/plugin.zsh
```

## 别名

```sh
# Alias
alias <ALIAS>=<COMMAND>
```

## 按键映射

```sh
# KeyBinding
bindkey '^[[1;5C' forward-word
bindkey '^[[1;5D' backward-word
bindkey '^H' backward-kill-word
```

## 大小写脱敏

```sh
# Completion
zstyle ':completion:*' matcher-list 'm:{[:lower:]}={[:upper:]}'
```

## 命令提示符

- 启用颜色代码
  - `autoload -Uz colors && colors`
- 转义字符
  - [Prompt Expansion](https://zsh.sourceforge.io/Doc/Release/Prompt-Expansion.html)

```sh
# Prompt
PROMPT=<LEFT_PROMPT_STRING>
RPROMPT=<RIGHT_PROMPT_STRING>
```
