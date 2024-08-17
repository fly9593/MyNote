# k8s如果配置了多个cri，每次执行命令需要手动选择使用那个cri,可以在配置文件中指定
/etc/crictl.yaml
/var/lib/kubelet/config.yaml
/etc/systemd/system/kubelet.service.d/10-kubelet.conf


在 Kubernetes 中，你可以使用不同的 Container Runtime Interface (CRI) 来管理容器，比如 Docker、containerd 或 CRI-O。如果你的 Kubernetes 集群中有多个 CRI 选择，你需要在以下文件中配置和指定使用哪个 CRI：

1. Kubelet 配置文件
Kubelet 是 Kubernetes 中运行在每个节点上的核心组件，它负责启动和管理容器。你需要在 Kubelet 的配置文件中指定使用的 CRI。

配置文件路径：通常位于 /var/lib/kubelet/config.yaml。
配置项：containerRuntimeEndpoint 和 runtimeRequestTimeout。
在 config.yaml 中，你可以指定 containerRuntimeEndpoint，比如：

yaml
复制代码
containerRuntimeEndpoint: unix:///var/run/containerd/containerd.sock
runtimeRequestTimeout: 15m
containerRuntimeEndpoint：指定要使用的 CRI 的 Unix 套接字文件路径。例如：
Docker: unix:///var/run/dockershim.sock
containerd: unix:///var/run/containerd/containerd.sock
CRI-O: unix:///var/run/crio/crio.sock
2. Kubelet 启动参数
你也可以通过命令行参数来指定 Kubelet 使用哪个 CRI，这通常在使用 systemd 管理 Kubelet 时配置。

配置文件路径：通常在 /etc/systemd/system/kubelet.service.d/10-kubelet.conf 中，或者在 /var/lib/kubelet/kubeadm-flags.env 中。
在 10-kubelet.conf 或 kubeadm-flags.env 文件中，添加或修改如下参数：

bash
复制代码
KUBELET_EXTRA_ARGS="--container-runtime-endpoint=unix:///var/run/containerd/containerd.sock"
3. 重启 Kubelet
修改配置后，你需要重启 Kubelet 以应用更改：

bash
复制代码
systemctl daemon-reload
systemctl restart kubelet
4. Kubeadm 初始化配置（如果适用）
如果你是使用 kubeadm 初始化的集群，你可以在 kubeadm 配置文件中指定 criSocket 参数：

yaml
复制代码
apiVersion: kubeadm.k8s.io/v1beta2
kind: InitConfiguration
nodeRegistration:
  criSocket: "unix:///var/run/containerd/containerd.sock"
然后通过 kubeadm init --config <config-file> 进行初始化。

总结
你需要在 Kubelet 的配置文件或启动参数中指定所使用的 CRI，并确保路径正确指向所选的 CRI 的 Unix 套接字文件。修改完成后，记得重启 Kubelet 服务以使更改生效。