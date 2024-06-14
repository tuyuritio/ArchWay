# BspWM

> 前置：X

## 安装

```sh
$ sudo pacman -S bspwm sxhkd
```

- `bspwm` - 窗口管理器
- `sxhkd` - 快捷键绑定

## 新建配置

```sh
$ cd ~/.config
$ mkdir bspwm sxhkd

# 生成默认用户配置文件
$ cp /etc/X11/xinit/xintrc ~/.xinitrc
$ cp /usr/share/doc/bspwm/examples/bspwmrc ~/.config/bspwm/
$ cp /usr/share/doc/bspwm/examples/sxhkdrc ~/.config/sxhkd/
```

## 快捷键

`$ vim ~/.config/sxhkd/sxhkdrc`

|快捷键|命令|说明|
|-|-|-|
|`super + Return`|`kitty`|打开终端|
