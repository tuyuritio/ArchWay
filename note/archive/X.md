# X

```sh
$ sudo pacman -S xorg-server
```

- `xorg-server` - X 服务器

## 启动脚本

> https://wiki.archlinux.org/title/Xprofile

`/etc/X11/xinit/xinit.d/`













## 配置高分辨率

`$ vim ~/.Xresources`

```conf
! 注释方式：`! 内容`
! Xft
Xft.dpi:			144
```

## 配置合成器

> 若无法正常启动。

`$ vim ~/.config/picom/picom.conf`

```conf
vsync = false
```

## 开机启动项

`vim ~/.xinitrc`

> 替换原有启动项。

```sh
sxhkd &
xrdb ~/.Xresources
picom -f &
```
