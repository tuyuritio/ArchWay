# Feh

```sh
$ sudo pacman -S feh
```

## 设置背景图片

> 建议路径： `~/.config/background.jpg`

```sh
$ feh --bg-max <path>
$ feh --bg-fill <path>
$ feh --bg-center <path>
$ feh --bg-tile <path>
$ feh --bg-scale <path>
```

## 开机生效

`$ vim ~/.xinitrc`

```conf
feh --bg-<type> <path>
```
