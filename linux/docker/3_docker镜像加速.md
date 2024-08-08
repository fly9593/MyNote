[root@k8s-node3 ~]# cat /etc/docker/daemon.json
{
    "registry-mirrors": [
        "https://hub.uuuadc.top",
        "https://docker.anyhub.us.kg",
        "https://dockerhub.jobcher.com",
        "https://dockerhub.icu",
        "https://docker.ckyl.me",
        "https://docker.awsl9527.cn",
    "https://dockerproxy.cn"
    ],
    "exec-opts": ["native.cgroupdriver=systemd"]
}

可以使用如下命令测试镜像是否连通
ping -c 4 hub.uuuadc.top
ping -c 4 docker.anyhub.us.kg
ping -c 4 dockerhub.jobcher.com
ping -c 4 dockerhub.icu
ping -c 4 docker.ckyl.me
ping -c 4 docker.awsl9527.cn
ping -c 4 dockerproxy.cn


{
    "registry-mirrors": [
    "https://dockerproxy.cn",
        "https://docker.anyhub.us.kg",
        "https://dockerhub.jobcher.com",
        "https://dockerhub.icu"
    ],
    "exec-opts": ["native.cgroupdriver=systemd"]
}


# 使用命令：

sudo sh -c 'cat > /etc/docker/daemon.json <<EOF
{
    "registry-mirrors": [
        "https://rqvg4v5d.mirror.aliyuncs.com",
        "https://hub.uuuadc.top",
        "https://docker.anyhub.us.kg",
        "https://dockerhub.jobcher.com",
        "https://dockerhub.icu",
        "https://docker.ckyl.me",
        "https://docker.awsl9527.cn"
    ],
    "exec-opts": ["native.cgroupdriver=systemd"]
}
EOF'

#重启docker服务
sudo systemctl restart docker


https://rqvg4v5d.mirror.aliyuncs.com