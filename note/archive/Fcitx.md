# Fcitx

## 安装

```sh
$ sudo pacman -S fcitx5 fcitx5-chinese-addons fcitx5-mozc			# 安装引擎
$ sudo pacman -S fcitx5-pinyin-zhwiki								# 安装词库
$ mkdir ~/.local/share/fcitx5/pinyin/dictionaries
$ cp /usr/share/fcitx5/pinyin/dictionaries/zhwiki.dict ~/.local/share/fcitx5/pinyin/dictionaries/
```

## 配置输入环境

`$ sudo vim /etc/environment`

```conf
GTK_IM_MODULE=fcitx
QT_IM_MODULE=fcitx
XMODIFIERS=@im=fcitx
SDL_IM_MODULE=fcitx
GLFW_IM_MODULE=ibus
```

## 开机自启

```conf
# XProfile
fcitx5 -d
```

## 配置布局

```sh
$ sudo pacman -S fcitx5-configtool
$ fcitx5-configtool
```

- 将`Pinyin`和`Mozc`加入到键盘布局中。
- **切换启用/禁用输入法：** 设置为`Control+左Shift`。
- **向前切换输入法：** 设置为`Control+空格`。
- **应用**。
