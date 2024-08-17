# 重启
systemctl restart containerd

# 下载镜像



# 测试

## 下载
ctr images pull docker.io/library/nginx:alpine

ctr images pull docker.io/library/nginx:latest

ctr --debug=true i pull docker.io/library/nginx:latest

ctr --debug=true i pull --hosts-dir=/etc/containerd/certs.d docker.io/library/nginx:latest

ctr --debug=true i pull --hosts-dir=/etc/containerd/certs.d registry.k8s.io/sig-storage/csi-provisioner:v3.5.0

ctr images pull --hosts-dir=/etc/containerd/certs.d docker.io/library/nginx:latest
ctr images pull --hosts-dir=/etc/containerd/certs.d docker.io/library/nginx:alpine
ctr images pull --hosts-dir=/etc/containerd/certs.d docker.io/mysql:latest
ctr --debug=true images pull --hosts-dir=/etc/containerd/certs.d docker.io/library/nginx:alpine

## 查看文件
ctr image ls

## 删除
ctr image rm docker.io/library/nginx:latest
ctr image rm docker.io/library/nginx:alpine

## 镜像
cat /etc/containerd/certs.d/docker.io/hosts.toml
## dns
cat -n /etc/resolv.conf

