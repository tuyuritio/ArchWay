# Useable

## Step 1. 用户配置

```sh
passwd # 设置 root 密码
```

```sh
useradd -m -G wheel <user> # 新建标准用户
passwd <user>
```

```sh
# /etc/sudoers
...
wheel # 取消注释
...
```

## Step 2. 安装桌面环境

[KDE](kde.md)

## Step 3. 文本编辑器

neovim

## Step 4. 语言配置

[Language](language.md)

## Step 5. 用户文件夹配置

[XDG User Dirs](xdg-user-dirs.md)

## Step 6. 安装 Git

git

## Step 7. 安装 AUR 助手

[Paru](paru.md)

## Step 字体管理

- `ttf-maple`

## TroubleShooting

### 未检测到音频设备

- `sof-firmware` 。
<!-- `alsa-ucm-conf` -->

---

zsh
keyd
firefox
fcitx
