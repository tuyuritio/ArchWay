# Neofetch

## 安装

```sh
$ sudo pacman -S neofetch
```

## 生成LOGO素材

```sh
$ sudo pacman -S jp2a       # 安装JPG转ASCII工具
$ jp2a <picture_path> --width=43 > ~/.config/neofetch/<LOGO>.ascii
```

## 编辑LOGO色彩

`$ vim ~/.config/neofetch/<LOGO.ascii>`

```conf
# 最前面加上
${c1}
```

## 配置LOGO路径

`$ vim ~/.config/neofetch/config.conf`

```conf
image_source="/home/<user>/.config/neofetch/<LOGO>.ascii"
```
