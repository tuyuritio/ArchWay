# KDE

## 安装

- `plasma` - 包组
    - `bluedevil`
    - `breeze`
    - `breeze-gtk`
    - `breeze-plymouth`
    - `discover`
    - `drkonqi`
    - `flatpak-kcm`
    - `kactivitymanagerd`
    - `kde-cli-tools`
    - `kde-gtk-config`
    - `kdecoration`
    - `kdeplasma-addons`
    - `kgamma`
    - `kglobalacceld`
    - `kinfocenter`
    - `kmenuedit`
    - `kpipewire`
    - `kscreen`
    - `kscreenlocker`
    - `ksshaskpass`
    - `ksystemstats`
    - `kwallet-pam`
    - `kwayland`
    - `kwin`
    - `kwrited`
    - `layer-shell-qt`
    - `libkscreen`
    - `libksysguard`
    - `libplasma`
    - `milou`
    - `ocean-sound-theme`
    - `oxygen`
    - `oxygen-sounds`
    - `plasma5support`
    - `plasma-activities`
    - `plasma-activities-stats`
    - `plasma-browser-integration`
    - `plasma-desktop`
    - `plasma-disks`
    - `plasma-firewall`
    - `plasma-integration`
    - `plasma-nm`
    - `plasma-pa`
    - `plasma-sdk`
    - `plasma-systemmonitor`
    - `plasma-thunderbolt`
    - `plasma-vault` - 删除
    - `plasma-welcome` - 删除
    - `plasma-workspace`
    - `plasma-workspace-wallpapers` - 删除
    - `plymouth-kcm`
    - `polkit-kde-agent`
    - `powerdevil`
    - `print-manager` - 删除
    - `qqc2-breeze-style`
    - `sddm-kcm`
    - `systemsettings`
    - `wacomtablet` - 删除
    - `xdg-desktop-portal-kde`
- `konsole` - 终端模拟器
- `kwalletmanager` - 密码库管理器
- `power-profiles-daemon` - 电源管理
- `ufw` - 防火墙
- `gwenview` - 图片查看器
- `fprint` - 指纹识别

### 依赖安装

- qt6-multimedia-backend - `qt6-multimedia-ffmpeg`
- jack - `pipewire-jack`
- ttf-font - `noto-fonts`
- emoji-font - `noto-fonts-emoji`
- frpint - `fprintd`

## 启用网络

```sh
systemctl enable NetworkManger
```

## KDE 密码库

- 传统方式，blowfish 加密文件
- 密码库密码留空即可在系统启动后无需输入
