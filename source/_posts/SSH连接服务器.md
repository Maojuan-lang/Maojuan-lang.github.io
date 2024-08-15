---
title: SSH连接服务器
date: 2024-08-15
---

```
安装Git软件
ssh-keygen
在下面目录里找到公钥私钥
C:\Users\Administrator\.ssh
id_rsa私钥，id_rsa.pub公钥
打开vscode，安装好remote-ssh插件
设置填入ssh的Config File
C:\Users\Administrator\.ssh
将公钥放到用户目录的.ssh文件夹里
echo id_rsa.pub >> authorized_keys
使用命令连接
ssh -p xxxx username@ipaddress
```

