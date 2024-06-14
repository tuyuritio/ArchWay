# Paru

**Arch 用户仓库（AUR）** 助手之一。

> https://github.com/morganamilo/paru

## 安装

```sh
sudo pacman -S rustup # 安装 Cargo 包管理器
rustup default stable
git clone https://aur.archlinux.org/paru.git
cd paru/
makepkg -si
```

## 配置

- 彩色输出
    - `/etc/pacman.conf` 中，取消注释 `Color` 。
- 倒序输出（此时最相似的结果距离命令行光标处最近）
    - `/etc/paru.conf` 中，取消注释 `BottomUp` 。

## 解锁 Pacman 数据库

```sh
sudo rm /var/lib/pacman/db.lck
```
