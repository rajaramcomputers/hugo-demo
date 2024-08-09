---
title: "Creating the cluster"
draft: false
tags: ["k3s", "cluster"]
categories: ["post"]
summary: "this is an example of how to create the first post in hugo"
---
kmaster@raspberrypi:~ $ k get nodes -owide
NAME          STATUS   ROLES                  AGE     VERSION        INTERNAL-IP    EXTERNAL-IP   OS-IMAGE                           KERNEL-VERSION      CONTAINER-RUNTIME
raspberrypi   Ready    control-plane,master   293d    v1.27.6+k3s1   192.168.1.24   <none>        Debian GNU/Linux 11 (bullseye)     6.1.21-v8+          containerd://1.7.6-k3s1.27
rsworker2     Ready    <none>                 8m27s   v1.27.6+k3s1   192.168.1.21   <none>        Debian GNU/Linux 12 (bookworm)     6.1.0-rpi4-rpi-v8   containerd://1.7.6-k3s1.27
rsworker4     Ready    <none>                 2m40s   v1.30.3+k3s1   192.168.1.23   <none>        Debian GNU/Linux 12 (bookworm)     6.6.31+rpt-rpi-v8   containerd://1.7.17-k3s1
rsworker7     Ready    <none>                 28m     v1.30.3+k3s1   192.168.1.27   <none>        Debian GNU/Linux 12 (bookworm)     6.6.31+rpt-rpi-v8   containerd://1.7.17-k3s1
rsworker6     Ready    <none>                 3h41m   v1.30.3+k3s1   192.168.1.26   <none>        Debian GNU/Linux 12 (bookworm)     6.6.31+rpt-rpi-v8   containerd://1.7.17-k3s1
rsworker3     Ready    <none>                 5m59s   v1.30.3+k3s1   192.168.1.22   <none>        Debian GNU/Linux 12 (bookworm)     6.6.31+rpt-rpi-v8   containerd://1.7.17-k3s1
rsworker1     Ready    <none>                 15m     v1.27.6+k3s1   192.168.1.18   <none>        Raspbian GNU/Linux 11 (bullseye)   5.15.61-v8+         containerd://1.7.6-k3s1.27
rsworker5     Ready    <none>                 5s      v1.30.3+k3s1   192.168.1.25   <none>        Debian GNU/Linux 12 (bookworm)     6.6.31+rpt-rpi-v8   containerd://1.7.17-k3s1

------
1. After the installation, when no softwares are installed.
kmaster@raspberrypi:~ $ kubectl top nodes
NAME          CPU(cores)   CPU%   MEMORY(bytes)   MEMORY%
raspberrypi   359m         8%     1163Mi          14%
rsworker1     43m          1%     255Mi           3%
rsworker2     42m          1%     515Mi           6%
rsworker3     39m          0%     438Mi           5%
rsworker4     53m          1%     440Mi           5%
rsworker5     43m          1%     439Mi           5%
rsworker6     47m          1%     438Mi           5%
rsworker7     51m          1%     440Mi           11%
----
2. Helm installation steps
kmaster@raspberrypi:~ $ curl https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3 | bash
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100 11694  100 11694    0     0  12850      0 --:--:-- --:--:-- --:--:-- 12836
Downloading https://get.helm.sh/helm-v3.15.3-linux-arm64.tar.gz
Verifying checksum... Done.
Preparing to install helm into /usr/local/bin
helm installed into /usr/local/bin/helm
kmaster@raspberrypi:~ $ helm version
version.BuildInfo{Version:"v3.15.3", GitCommit:"3bb50bbbdd9c946ba9989fbe4fb4104766302a64", GitTreeState:"clean", GoVersion:"go1.22.5"}
----
3. Nodes top after helm installation
kmaster@raspberrypi:~ $ kubectl top nodes
NAME          CPU(cores)   CPU%   MEMORY(bytes)   MEMORY%
raspberrypi   243m         6%     1166Mi          14%
rsworker1     42m          1%     255Mi           3%
rsworker2     49m          1%     512Mi           6%
rsworker3     38m          0%     438Mi           5%
rsworker4     32m          0%     440Mi           5%
rsworker5     39m          0%     439Mi           5%
rsworker6     48m          1%     438Mi           5%
rsworker7     38m          0%     441Mi           11%
**Noticed no changes**
----
4. Prometheus and Grafana helm repo installed
kmaster@raspberrypi:~ $ helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
helm repo add grafana https://grafana.github.io/helm-charts
helm repo update
"prometheus-community" has been added to your repositories
"grafana" has been added to your repositories
Hang tight while we grab the latest from your chart repositories...
...Successfully got an update from the "grafana" chart repository
...Successfully got an update from the "prometheus-community" chart repository
----
5. monitoring namespace is created
kmaster@raspberrypi:~ $ kubectl create namespace monitoring
namespace/monitoring created
----
6. to check the username and password for Grafana
kmaster@raspberrypi:~ $ kubectl get secret prometheus-grafana -n monitoring -o jsonpath="{.data.admin-user}" | base64 --decode
adminkmaster@raspberrypi:~ $ kubectl get secret prometheus-grafana -n monitoring -o jsonpath="{.data.admin-password}" | base64 --decokmaster@raspberrypi:~ $ kubectl get secret prometheus-grafana -n monitoring -o jsonpath="{.data.admin-password}" | base64 --decode
prom-operatorkmaster@raspberrypi:~ $

