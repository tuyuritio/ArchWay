# Clash Premium CLI

> [Release Premium](https://github.com/Dreamacro/clash/releases/tag/premium)

> Premium 版本具有 Rule Providers 功能。

## 脚本

```sh
# !/bin/bash
wget http://trip.geter.cc:34718/clash-linux-amd64-2023.03.18.gz
wget http://trip.geter.cc:34718/Country.mmdb
gzip -d clash-linux-amd64-*.gz && mv clash-linux-amd64-* clash
mkdir -p ~/.config/clash
```

## 获取

> `https://github.com/Dreamacro/clash/releases/download/premium/clash-linux-amd64-<version>.gz`

> `https://raw.githubusercontent.com/alecthw/mmdb_china_ip_list/release/Country.mmdb`

- U 盘挂载
- SCP 复制
- Wget 拉取

## 解压

```sh
$ gzip -d clash-linux-amd64-*.gz && mv clash-linux-amd64-* clash
```

## 赋权

```sh
$ chmod +x clash
```

## 装载

```sh
$ sudo mv clash /usr/local/bin/clash
```

## 订阅

```sh
$ wget http://url/to/server -O config.yaml
$ mv config.yaml ~/.config/clash/
```

## 服务配置

`$ sudo vim /lib/systemd/system/clash.service`

```ini
[Unit]
Description=Clash Service.

[Service]
Type=simple
User=<USER>
Group=<USER>
WorkingDirectory=/usr/local/bin/

ExecStart=/usr/local/bin/clash

[Install]
WantedBy=multi-user.target
```

## 代理设置

`$ vim ~/profile`

```sh
export HTTP_PROXY=http://127.0.0.1:7890
export HTTPS_PROXY=http://127.0.0.1:7890
export NO_PROXY=localhost
```
