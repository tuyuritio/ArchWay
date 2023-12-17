# Fcitx5

轻量级内核的输入法框架。

> https://fcitx-im.org/wiki/Fcitx_5

## 安装

- `fcitx5-im` - 包组，含 `fcitx5` `fcitx5-configtool` `fcitx5-gtk` `fcitx5-qt`
    - `fcitx5-configtool` - GUI 配置工具
    - `fcitx5-gtk` - GTK 程序兼容模块
    - `fcitx5-qt` - QT 程序兼容模块
- `fcitx5-chinese-addons` - 中文输入组件
- `fcitx5-mozc` - 日本語入力パッケージ
- `fcitx5-skin-fluentdark-git` - FluentDark 主题

## 环境变量

```
GTK_IM_MODULE=fcitx
QT_IM_MODULE=fcitx
XMODIFIERS=@im=fcitx
```
