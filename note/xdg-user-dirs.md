# XDG user directories

## 安装

- `xdg-user-dirs` - 本体

## 创建配置

```sh
# 创建本地化的用户目录
xdg-user-dirs-update

# 创建英语目录
LC_ALL=C xdg-user-dirs-update --force
```

- `~/.config/user-dirs.dirs` - 用户目录配置。
- `~/.config/user-dirs.locale` - 用户目录所指定语言。

## 更新配置

```sh
xdg-user-dirs-update --set <DIRECTORY> $HOME/<PATH>
```

> 修改目录前需确保目标路径存在。

## 查询配置

```sh
xdg-user-dirs <DIRECTORY>
```
