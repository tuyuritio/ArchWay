# Paru

**Arch 用户仓库（AUR）** 助手之一。

> https://github.com/morganamilo/paru

## 安装

1. 克隆源码

```sh
git clone https://aur.archlinux.org/paru.git
```

2. 编译

```sh
cd paru/
makepkg -si
```

> 在选择编译依赖时会弹出 `(1) rust (2) rustup`，目前似乎只能使用 `rust` 顺利编译。

## 配置

- 彩色输出
    - `/etc/pacman.conf` 中，取消注释 `Color` 。
- 倒序输出（此时最相似的结果距离命令行光标处最近）
    - `/etc/paru.conf` 中，取消注释 `BottomUp` 。
