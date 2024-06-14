# 系统安装

## Step 0.1. 获取安装镜像

- [Download](https://archlinux.org/download/)

> 校验（Windows）：`certutil -hashfile .\archlinux-<VERSION>-x86_64.iso SHA256`

## Step 0.2. 制作安装介质

- [Ventoy](https://github.com/ventoy/Ventoy/releases)

## Step 1. **`UEFI` 模式确认**

```sh
$ ls /sys/firmware/efi/efivars              # 若存在该目录，则当前为`UEFI`模式
```

## Step 2. **磁盘分区**

```sh
$ fdisk -l          # 列举当前磁盘，如`/dev/sda`

$ fdisk /dev/sda
Command (m for help): n                     # 创建引导分区
Select (default p):
Partition number (1-4, default 1):
First sector (2048-*, default 2048):
Last sector +/-sectors or +/-size{K,M,G,T,P} (2048-*, default *): +512M
Create a new partition 1 of type 'Linux' and of size 256 MiB.

Command (m for help): n                     # 创建根分区
Select (default p):
Partition number (2-4, default 2):
First sector (*-*, default <LEFT>):
Last sector +/-sectors or +/-size{K,M,G,T,P} (*-*, default <LEFT>):
Create a new partition 2 of type 'Linux' and of size <LEFT> GiB.

Command (m for help): w                     # 保存更改
The partition tablehas been altered.
```

## Step 3. **磁盘格式化**

当前分区:
|分区|类型|大小|
|-|-|-|
|`/dev/sda1`|`EFI`|512MiB|
|`/dev/sda2`|`/`|剩余|

```sh
$ mkfs.fat -F 32 /dev/sda1      # 格式化引导分区
$ mkfs.ext4 /dev/sda2           # 格式化根分区
```

## Step 4. **磁盘挂载**

> 挂载顺序严格！

```sh
$ mount /dev/sda2 /mnt          # 挂载根分区
$ mkdir /mnt/boot               # 创建引导分区
$ mount /dev/sda1 /mnt/boot     # 挂载引导分区
```

## Step 5. **网络配置**

```sh
$ networkctl                    # 查看可用网络接口
$ networkctl status <INTERFACE> # 查看网络接口状态
$ networkctl enable <INTERFACE> # 启用网络接口
$ ping bing.com                 # 测试网络连通性
```

## Step 6. **系统时间设置**

```sh
$ timedatectl set-ntp true                      # 同步网络时间
$ timedatectl set-timezone Asia/Shanghai        # 设置时区
$ timedatectl status                            # 查看当前日期时间
```

## Step 7. **镜像源设置**

```sh
$ reflector --verbose -c China --latest 10 --sort rate --threads 100 --save /etc/pacman.d/mirrorlist    # 设置国内镜像源
```

## Step 8. **基础安装**

```sh
$ pacstrap /mnt base base-devel linux linux-firmware
# 若报错`fail to install to new root`，需重启并再次格式化
```

## Step 9. **交换文件**

```sh
$ dd if=/dev/zero of=/mnt/swapfile bs=1G count=16 status=progress
$ chmod 0600 /mnt/swapfile
$ mkswap -U clear /mnt/swapfile
$ swapon /mnt/swapfile
$ vim /mnt/etc/fstab
/swapfile none swap defaults 0 0
```

> 移除交换文件
> ```sh
> $ swapoff /swapfile
> $ rm -f /swapfile
> ```

## Step 10. **`fstab` 文件配置**

```sh
$ genfstab -U /mnt >> /mnt/etc/fstab
```

## Step 11. **引导安装**

```sh
$ arch-chroot /mnt          # 进入系统

# 安装引导组件
$ pacman -S grub efibootmgr intel-ucode     # Intel CPU
$ pacman -S grub efibootmgr amd-ucode       # AMD CPU

# 写入引导程序
$ grub-install --target=x86_64-efi --efi-directory=/boot --bootloader-id=Arch
$ grub-mkconfig -o /boot/grub/grub.cfg
```

## Step 12. **基本应用安装**

```sh
$ pacman -S networkmanager vim
```

## Step 13. **用户配置**

```sh
$ passwd                        # 设置`root`密码

$ visudo /etc/sudoers           # 配置sudo权限
%wheel ALL=(ALL:ALL) ALL

$ useradd <user> -G wheel -m    # 创建普通用户
    # -G wheel 加入 wheel
    # -m 自动生成家目录
$ passwd <user>                 # 设置用户密码
```

## Step 14. **完成安装**

```sh
$ exit
$ reboot
```

---

参考资料：

- https://zhuanlan.zhihu.com/p/596227524

<!--
    passroot1337
    realtana)@31!
-->