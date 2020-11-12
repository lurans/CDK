# CDK
Container Duck - Zero Dependency Docker/K8s Penetration Toolkit

# 介绍
本工具适用于攻入容器环境后的横向移动场景，解决以下问题：
  
1. 生产环境的容器是缩减后的linux系统，往往没有常用的linux命令和python等脚本环境，传统渗透工具无法使用。本工具提供golang实现的原生渗透工具集。
2. 集成docker/k8s场景特有的 逃逸、横向移动、持久化利用方式，插件化管理。
  
目前大部分功能仍在开发中，建议/反馈请提issue或mail: `i[at]cdxy.me`

# 功能

search模块——容器内部信息收集

```
cdk search [--full]
```

|功能|已支持|用例|
|---|---|---|
|os基础指纹|✔||
|容器内可用于逃逸的capabilities|||
|容器内部可用的linux命令|✔||
|mount到容器中的目录|✔||
|env中的敏感服务|✔||
|进程中的敏感服务|✔||
|本地敏感文件扫描|✔||
|本地漏洞扫描|||

run模块——执行指定的脚本（插件化维护poc/exp）

```
cdk run --list
cdk run <exploit-name> [options]
```

|类别|功能|已支持|用例|
|---|---|---|---|
|逃逸|docker runc exploit|️||
|逃逸|dirtycow exploit|||
|逃逸|攻击docker.sock|||
|逃逸|挂载目录写文件|||
|逃逸|进程注入|||
|权限提升|本地K8s service account认证|||
|横向移动|K8s api-server鉴权不当|||
|横向移动|etcd鉴权不当|||
|信息窃取|本地代码AK扫描|✔||
|信息窃取|K8s secrets dump|||
|信息窃取|K8s config dump|||
|持久化|webshell植入|||
|持久化|分发K8s后门Pod|||
|持久化|部署shadow K8s api-server|||
|持久化|部署K8s cronjob|||

工具命令——还原部分linux指令及常见的渗透工具

```
cdk nc [options]
cdk ps
```

|命令|功能|已支持|用例|
|---|---|---|---|
|nc|文件/shell通道|✔||
|ps|进程信息|✔||
|ifconfig|网络信息|✔||
|vi|文件编辑|✔||
|curl|HTTP发包|||
|kubectl|轻量级K8s管理|||
|probe|内网扫描|||
|tunnel|隧道|||