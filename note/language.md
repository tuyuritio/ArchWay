# Language

## 配置编码项

```conf
# /etc/locale.gen
# 取消以下注释
zh_CN.UTF-8
ja_JP.UTF-8
```

## 生成编码

```sh
$ sudo locale-gen
```

## 安装字体

```sh
$ sudo pacman -S adobe-source-han-sans-cn-fonts adobe-source-han-serif-cn-font
```

## 开机生效

```sh
# /etc/environment
# Language
LANG=zh_CN.UTF-8
```
