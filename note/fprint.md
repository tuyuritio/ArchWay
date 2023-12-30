# fprint

消费级指纹识别设备支持。

> https://wiki.archlinux.org/title/Fprint

## 可用性检查

- 使用 `lsusb` 命令（`usbutils` 软件包）查看指纹识别设备信息。
- 查阅[兼容设备清单](https://fprint.freedesktop.org/supported-devices.html)以确定该设备是否受支持。

## 安装

- `fprintd` - 本体

## 身份认证组件

| 桌面环境 | 身份认证组件 | 组件文件 |
|:-:|-|-|
| LXQt | `lxqt-policykit` | `/usr/bin/lxqt-policykit-agent` |
| LXDE | `lxsession` | `/usr/bin/lxpolkit` |
| MATE | `mate-polkit` | `/usr/lib/mate-polkit/polkit-mate-authentication-agent-1` |
| GNOME | `polkit-gnome` | `/usr/lib/polkit-gnome/polkit-gnome-authentication-agent-1` |
| KDE | `polkit-kde-agent` | `/usr/lib/polkit-kde-authentication-agent-1` |
| theShell | `ts-polkitagent` | `/usr/lib/ts-polkitagent` |
| Xfce | `xfce-polkit` | `/usr/lib/xfce-polkit/xfce-polkit` |
| Enlightenment | `polkit-efl-git` | `/usr/bin/polkit-efl-authentication-agent-1` |
| - | `polkit-dumb-agent-git` | `/usr/bin/polkit-dumb-agent` |

- Cinnamon、Deepin、GNOME、KDE、Xfce 等桌面环境已预装其相应的认证组件，否则请自行选择安装。
- 将已安装的组件添加**自动启动**。
- 重新载入会话。

## 指纹管理

> 据[某驱动文档](https://github.com/iafilatov/libfprint?tab=readme-ov-file#common-problems)描述，`libfprint` 需要较大的指纹图像以供识别。即为了使**非滑动识别器**或**面积小于144x96的矩形识别器**准确识别指纹，需要在录入时 ***稳定且相对缓慢*** 地滑动手指，验证时点触即可。

### 录入指纹

```sh
fprint-enroll [-f <FINGER>]
```

- `-f <FINGER>` 选项：
    - left-thumb
    - left-index-finger
    - left-middle-finger
    - left-ring-finger
    - left-little-finger
    - right-thumb
    - right-index-finger
    - right-middle-finger
    - right-ring-finger
    - right-little-finger
- 留空则由设备自动选择。

### 验证指纹

```sh
# 单次验证
fprint-verify

# 多次验证
while true; do fprintd-verify; done | grep result
```

### 删除指纹

```sh
fprint-delete <USER>
```
