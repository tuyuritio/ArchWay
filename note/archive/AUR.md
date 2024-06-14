# ArchLinux User Repository

> 需能够访问 Github 。

## 安装

```sh
$ git clone https://aur.archlinux.org/paru.git
$ cd paru
$ makepkg -si
$ paru
$ cd ..
$ rm -rf paru/
```

## 启用颜色

```sh
$ sudo vim /etc/pacman.conf
Color       # 取消注释
```

## 滚动更新

```sh
$ paru -Syyu
```

## 操作

- 安装
    - `paru -S <PACKAGE>`
- 更新
    - `paru -Syu`
    - `paru`
- 卸载
- 评论
    - `paru -Gc <PACKAGE>`
