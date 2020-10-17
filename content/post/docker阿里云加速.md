+++
date="2020-10-15T22:00:00+08:00"
title="docker阿里云加速"
tags=["docker"]
categories=["运维"]
+++ 

## 阿里云提供的个人加速
*在linux下执行以下命令即可*
```
sudo mkdir -p /etc/docker
sudo tee /etc/docker/daemon.json <<-'EOF'
{
  "registry-mirrors": ["https://a4fyjv0u.mirror.aliyuncs.com"]
}
EOF
sudo systemctl daemon-reload
sudo systemctl restart docker
```