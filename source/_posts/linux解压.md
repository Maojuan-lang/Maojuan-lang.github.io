---
title: linux解压
---

```
linux tar命令 压缩、打包、解压 详解

1、常用压缩命令

tar –czvf 压缩后的文件.tar.gz 要压缩的文件

2、常用解压命令

tar –xzvf 解压后的文件.tar.gz 【要解压的目录】

3、参数意义

-c: 建立压缩档案

-f： 使用档案名字，切记，这个参数是最后一个参数，后面只能接档案名。

-j：有bz2属性的

-O：将文件解开到标准输出

-r：向压缩归档文件末尾追加文件

-t：查看内容

-u：更新原压缩包中的文件

-v：显示所有过程

-x：解压

-z：有gzip属性的

-Z：有compress属性的

4、总结

*.tar 用 tar –xvf 解压

*.gz 用 gzip -d或者gunzip 解压

*.tar.gz和*.tgz 用 tar –xzf 解压

*.bz2 用 bzip2 -d或者用bunzip2 解压

*.tar.bz2用tar –xjf 解压

*.Z 用 uncompress 解压

*.tar.Z 用tar –xZf 解压

*.rar 用 unrar e解压

*.zip 用 unzip 解压
```

