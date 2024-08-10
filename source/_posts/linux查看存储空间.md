---
title: linux查看存储空间
date: 2024-08-10
---

```
查看全部的空间占用情况，-h表示人类可读性，df是disk free
df -h
df --human-readable
查看文件夹的占用情况，-s表示--summarize，-h表示--human-readable，du表示disk usage
du -sh
列出所有可用的存储块设备以及它们的分区
lsblk
查看或修改磁盘分区表
sudo fdisk -l
查看磁盘的S.M.A.R.T信息，判断磁盘健康状态
sudo smartctl -a /dev/sda
```

