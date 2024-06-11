<div align="center">

# files-mirrors

[![Auth](https://img.shields.io/badge/Auth-gebangfeng-ff69b4)](https://github.com/gebangfeng)
[![GitHub contributors](https://img.shields.io/github/contributors/gebangfeng/files-mirrors)](https://github.com/gebangfeng/files-mirrors/graphs/contributors)
[![GitHub Issues](https://img.shields.io/github/issues/gebangfeng/files-mirrors.svg)](https://github.com/gebangfeng/files-mirrors/issues)
[![GitHub Pull Requests](https://img.shields.io/github/issues-pr/gebangfeng/files-mirrors)](https://github.com/gebangfeng/files-mirrors/pulls)
[![GitHub Pull Requests](https://img.shields.io/github/stars/gebangfeng/files-mirrors)](https://github.com/gebangfeng/files-mirrors/stargazers)
[![HitCount](https://views.whatilearened.today/views/github/gebangfeng/files-mirrors.svg)](https://github.com/gebangfeng/files-mirrors)
[![GitHub license](https://img.shields.io/github/license/gebangfeng/files-mirrors)](https://github.com/gebangfeng/files-mirrors/blob/main/LICENSE)

<p> 多平台文件下载代理服务,支持 GitHub, k8s, Helm 等网站. </p>

<img src="https://cdn.jsdelivr.net/gh/gebangfeng/tu@main/img/image_20240420_214408.gif" width="800"  height="3">
</div><br>

## 背景
在服务器上需要下载Github上的一个文件，或者要clone一个仓库，网络原因，下载速度很慢。

## 方案
- 通过增加一个域名前缀，利用代理服务器加速下载。
- 稳定可靠，更新实时。
- 可以直接用于 github, k8s, helm 等网站的文件下载。
## 使用方法

在原始 URL 上面加入 `file.kubesre.xyz` 的 *前缀* 就可以使用。比如：

```bash
# Helm 下载原始URL
wget https://get.helm.sh/helm-v3.9.1-linux-amd64.tar.gz

# 加速后的 URL
wget https://file.kubesre.xyz/https://get.helm.sh/helm-v3.9.1-linux-amd64.tar.gz
```

即可加速下载, 代理服务器不缓存文件，文件从原站直接返回给客户端。
## 支持代理的网站
 这是人工配置的, 有需求提 Issue.
 
github.com
- https://gist.github.com
- https://github.com
- https://raw.githubusercontent.com
- https://gist.githubusercontent.com
- https://objects.githubusercontent.com

k8s.io
- https://cdn.dl.k8s.io
- https://dl.k8s.io

helm.sh
- https://get.helm.sh

## 最佳实践

## 使用场景1 - 安装 Helm

```bash
cd /tmp
export HELM_VERSION="v3.9.3"

wget "https://file.kubesre.xyz/get.helm.sh/helm-${HELM_VERSION}-linux-amd64.tar.gz"
tar -zxvf helm-${HELM_VERSION}-linux-amd64.tar.gz
mv linux-amd64/helm /usr/local/bin/helm
helm version
```
## 使用场景2 - Clone Github 仓库
```bash
cd /tmp
git clone https://file.kubesre.xyz/https://github.com/kubesre/docker-registry-mirrors.git
```
欢迎贡献更多的场景
