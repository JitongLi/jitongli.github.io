# Gateway
使用OpenFaaS操作者faas-provider的概念设计，每个函数都构建在一个不可变的Docker镜像中，然后通过faas-cli, UI或REST API进行部署。部署时，每个函数会根据用户请求的最小和最大扩展参数创建1至多个Pods或容器，通过使用OpenFaaS Pro自动扩展器或OpenFaaS Pro REST API，函数也可缩小至零或再次返回。
![](https://docs.openfaas.com/images/of-conceptual-operator.png)

API Gateway提供了函数外部路由并通过Prometheus收集云原生指标（Cloud Native metrics），网关也内置了UI以用于部署自己的OpenFaaS函数商店的函数，并调用这些函数。如前所述，网关可修改Kubernetes API中的副本数量扩展函数，AlertManager生成的自定义警报在	`/system/alert`端点上接收。

总而言之，其功能包括：

>* 内置UI门户
>
>* 部署Function Store或自己的函数
>
>* 通过Prometheus收集指标
>
>* 通过AlertManager和Prometheus自动扩容（从零开始扩容）
>
>* 可用REST API
## 函数提供者（Function Providers）

函数提供者可使用Golong中的faas-provider接口编写函数，该接口提供与网关交互的REST API。
## CORS

默认情况下，唯一允许的CORS路径为Function Store，其由Github RAW CDN服务。
## UI Portal

内置的UI门户通过绑定在`/ui/`路径的静态文件提供服务，UI采用Angular 1.x编写并使用jQuery进行交互，并使用Angular Material主题实现视觉效果和组建（其源代码在[assets](https://github.com/openfaas/faas/blob/master/gateway/assets)文件夹）。
## 函数商店（[Function Store](https://github.com/openfaas/store)）
函数商店通过GitHub RAW CDN提供的静态JSON文件进行渲染，函数商店也可以通过[OpenFaaS Cli](https://github.com/openfaas/faas-cli)使用。
## Logs
日志可通过API在函数级获取，也可以安装Docker日志驱动汇总日志，默认情况下函数不会将请求和响应主题写入到stdout，可通过设置请求的`read_debug`和响应的`write_debug`切换行为。
## 追踪（Tracing）
“X-Call-Id”头应用于通过网关的每个调用，可用于追踪和监控调用，使用UUID表示此字符串，每个函数中以`Http_X_Call_Id`方式使用。
## 环境覆盖（Environmental overrides）
可通过以下环境变量配置网关：

| 选项（Option）| 用法 |
| --- | --- |
|`write_timeout`|函数写入响应体的HTTP超时时间（以秒为单位），默认为8|
|`read_timeout`|从客户端调用者读取有效负载的HTTP超时时间（以秒为单位），默认为8|
|`functions_provider_url`|上游函数提供者([functions provider](https://github.com/openfaas/faas-provider/))的URL，即Swarm，Kubernetes，Nomad等|
|`logs_provider_url`|上游函数日志api提供者的URL，可选，当为空时使用`functions_provider_url`|
|`faas_nats_address`|NATS Streaming可访问的主机，异步模式必需|
|`faas_nats_port`|NATS Streaming可访问的端口，异步模式必需|
|`faas_nats_cluster_name`|目标NATS Streaming集群的名称，默认为`faas-cluster`以向后兼容|
|`faas_nats_channel`|要使用NATS Streaming信道的名称，默认为`faas-request`以向后兼容|
|`faas_prometheus_host`|连接Prometheus的主机，默认为`"prometheus"`|
|`faas_prometheus_port`|连接Prometheus的端口，默认为`9090`|
|`direct_functions`|`true`或`false` - 函数通过DNS名称overlay网络直接调用，无需通过提供者|
|`direct_functions_suffix`|提供DNS后缀以直接通过overlay网络调用函数|
|`basic_auth`|设置为`true`或`false`以在/sysetm和/ui端点上启用嵌入式基本身份验证（推荐）|
|`secret_mount_path`|设置安装`basic-auth-user`和`basic-auth-password`的位置，默认为`/run/secrets/`|
|`scale_from_zero`|启用拦截代理，该代理可将任意函数的副本数从0扩展到所需数量|

