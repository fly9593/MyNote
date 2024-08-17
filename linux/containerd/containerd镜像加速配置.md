# 参考：
https://blog.csdn.net/IOT_AI/article/details/131975562
https://zhuanlan.zhihu.com/p/702497587

# 生成默认配置
mkdir -p /etc/containerd
containerd config default > /etc/containerd/config.toml

# containerd配置文件位置：
cd /etc/containerd/config.toml

# 复制镜像文件到目录


# 重启containerd
systemctl restart containerd


# 测试镜像加速是否配置成功
## 先查看containerd运行状态
systemctl status containerd


## 写入镜像
mkdir -p /etc/containerd/certs.d/docker.io
cat > /etc/containerd/certs.d/docker.io/hosts.toml << EOF
server = "https://docker.io"

[host."https://docker.m.daocloud.io"]
  capabilities = ["pull", "resolve"]

EOF

## 查看镜像
cat /etc/containerd/certs.d/docker.io/hosts.toml

## 再使用containerd随便下载一个镜像试试
参考：
### 下载镜像
ctr image pull docker.io/library/nginx:latest

### 查看镜像列表
ctr image ls

### 删除镜像
ctr image rm docker.io/library/nginx:latest
ctr image rm docker.io/library/nginx:alpine

## 登录
docker login -u fly9593 -p fly123456

ctr containers login -u fly9593 -p fly123456

# crictl版本命令