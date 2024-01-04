# 安装

一开始基础 ArchLinux 时，的确觉得其安装过程过于繁琐（虽然事实如此），但是经过多次虚拟机、系统重装等经历之后，发现有迹可循。

对于一个完全纯净的系统，无非以下几点：

0. 预备
1. **分区**
2. **安装**
3. **引导**
4. 调整

其余繁琐的内容，也都是为这些核心的点服务的。

## 0. 预备

## 1. 分区

### 磁盘擦除

```sh
dd if=/dev/zero of=/dev/sda bs=4M status=progress
```

`dd` 命令用于写入字节，即用 零字符（`/dev/zero`）写满打算安装的磁盘（`/dev/sda` 或 `/dev/nvme0n1` etc.），设置单次写入的块大小为 `4M` ，以加快写入速度，设置状态为 `progress` 以查看写入进度。

### 分区

```sh
cfdisk /dev/sda
```

分区类型为 `GPT` 。

| 分区 | 挂载点 | 大小 | 类型 |
|-|-|-|-|
| `/dev/sda1` | `/boot` | 256MB | EFI System |
| `/dev/sda2` | `[SWAP]` | 同内存大小 | Linux swap |
| `/dev/sda3` | `/` | 30GB | Linux filesystem |
| `/dev/sda4` | `/home` | 剩余 | Linux filesystem |

### 格式化

```sh
mkfs.fat -F32 /dev/sda1
mkswap /dev/sda2
mkfs.ext4 /dev/sda3
mkfs.ext4 /dev/sda4
```

### 挂载

```sh
mount /dev/sda3 /mnt
mkdir /mnt/boot /mnt/home
mount /dev/sda1 /mnt/boot
mount /dev/sda4 /mnt/home
swapon /dev/sda2
```

## 2. 安装

### 联网

联网大致有三种方式：

1. 网线直连
2. USB 网络共享
3. `iwctl` 无线网络连接

### 设置 NTP

```sh
timedatectl set-ntp true
```

### 安装

```sh
pacman -Sy archlinux-keyring # 更新 GPG 证书
pacstrap /mnt base base-devel linux linux-firmware
```

> 境外数据传输问题请自行解决。

### 定义分区

```sh
genfstab -U /mnt > /mnt/etc/fstab
```

## 3. 引导

### 微码

```sh
pacstrap /mnt intel-ucode # Intel
pacstrap /mnt amd-ucode # AMD
```

### 引导

主流的引导方式有两种：

1. GRUB2
2. systemd-boot

#### systemd-boot

1. 基础安装

```sh
arch-chroot /mnt
bootctl install --path=/boot
systemctl enable systemd-boot-update
cp /usr/share/systemd/bootctl/arch.conf /boot/loader/entries/arch.conf
```

2. 编辑启动项

- 通过 `blkid` 命令获取根分区 UUID `<PARTUUID>`。

```sh
# /mnt/boot/loader/entries/arch.conf
title          Arch Linux
linux          /vmlinuz-linux
initrd         /initramfs-linux.img
options        root=PARTUUID=<PARTUUID> rw
```

3. 能够正常开机后，可根据情况添加静默启动，屏蔽内核报错。

```sh
# /mnt/boot/loader/entries/arch.conf
...
options        root=PARTUUID=<PARTUUID> quite loglevel=0 rw
```

至此，一个完全纯净的 ArchLinux 安装完成。

## 4. 调整

- 用户密码
- 安装基础软件
    - neovim
    - zsh
    - iwd
        - 网络管理器

### 无线网络连接

```sh
pacman -S networkmanager
systemctl start NetworkManager
systemctl enable NetworkManager
```
