# Network

```sh
$ sudo NetworkManager										# 启动NetworkManager
$ sudo systemctl enable NetworkManager						# 开机自启
$ nmcli device wifi list									# 遍历周围Wifi，如<wifi>
$ nmcli device wifi connect <wifi> password <password>		# 连接至<wifi>
$ ping bing.com												# 测试网络连通性
```
