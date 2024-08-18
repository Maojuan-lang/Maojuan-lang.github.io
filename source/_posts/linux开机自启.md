---
title: linux开机自启
date: 2024-08-18
---

```
screen -dm 后台新建一个screen并执行命令bach -c "xxxx"


#!/bin/bash

# 会话名称
SESSION_NAME="bot"

# 检查是否已经存在该会话
if screen -list | grep -q "$SESSION_NAME"; then
  echo "Screen session '$SESSION_NAME' already exists. Attaching..."
  screen -r "$SESSION_NAME"
else
  echo "Starting new screen session: $SESSION_NAME"
  screen -S "$SESSION_NAME" -dm bash -c "cd /opt/Miao-Yunzai && npm run app; exec bash"
  echo "NPM dev started in new screen session."
fi
```

```
#使用nano新建一个文件,Ctrl+o保存,Ctrl+x退出
sudo nano /etc/systemd/system/npm-dev.service
#确保你的脚本有执行权限
chmod +x /path/to/your/run_npm_dev.sh
#重启systemctl
sudo systemctl daemon-reload
#启动服务
sudo systemctl start npm-dev.service
#启用服务
sudo systemctl enable npm-dev.service
#查看脚本状态
sudo systemctl status npm-dev.service
#WorkingDirectory 执行命令的目录

[Unit]
Description=NPM Dev Screen Service
After=network.target

[Service]
ExecStart=/path/to/your/run_npm_dev.sh
WorkingDirectory=/path/to/your/project
StandardOutput=inherit
StandardError=inherit
Restart=always
User=your-username

[Install]
WantedBy=multi-user.target
```

```
支持rc.local的系统，可以在里面添加要运行的脚本
/etc/rc.local
bash /path/to/startup.sh
```

