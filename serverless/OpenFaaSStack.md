# OpenFaaS Stack
无论是本地环境，自托管的集群，还是使用AWS Elastic Kubernetes Service （EKS），OpenFaaS推荐的部署平台为Kubernetes。OpenFaaS栈如下图所示：
![alt name](https://github.com/openfaas/faas/raw/master/docs/of-layer-overview.png)
## CI/GitOps层
OpenFaaS运行函数，也可以运行HTTP微服务，每个运行都构建在容器镜像中，并发布在容器注册表中。

通常使用`faas-cli`手动实现开发和评估。

对于生产环境，可以使用CI工具构建资源控制管理（Source Control Management，SCM）系统。

通过运行`faas-cli deploy`或`faas-cli up`，GitHub Actions或GitLab提供了最快构建和部署函数的选项。

可以使用ArgoCD或Flux持续更新OpenFaaS或OpenFaaS函数，GitOps方式通常涉及在新版本可用时涉及持续部署，部署通过从特殊配置的仓库中提取所需的状态。
## 应用层
* OpenFaaS Gateway 提供了REST API以管理函数，记录指标并对函数进行扩展。

* Prometheus 提供了指标并可实现社区版和OpenFaaS Pro版的自动扩展。

* NATS 用于异步函数执行和排队。

组成OpenFaaS的项目（Prometheus，Linux，OpenFaaS，NATS及Kubernetes）被称为PLONK栈，PLONK栈可运行事件驱动的函数和传统基于HTTP的微服务。
>* Prometheus: 用于捕获参数的时间序列数据库
>
>* Linux：提供容器的基础操作系统
>
>* OpenFaaS：计算资源的管理和自动扩展 - PaaS/FaaS，开发者友好型抽象，每个函数或微服务都构建为不可变的Docker容器或OCI格式的镜像
>
>* NATS：用于延迟执行的异步消息总线/队列
>
>* Kubernetes：声明式、可扩展、横向扩展、自修复集群

这些应用可通过Helm charts安装，使用类似ArgoCD或Flux的GitOps操作。
## 基础设施层

* 执行函数的单位为Pod的，由containerd或Docker所管理。

* 容器注册表将每个函数保存为不可变的构建，可通过REST API，UI或CLI将其部署到OpenFaaS网关。

* Kubernetes为允许函数扩展到多个主机的平台。
## 概念工作流程
![faas-netes](https://raw.githubusercontent.com/openfaas/faas/master/docs/of-workflow.png)
Gateway可通过REST API，CLI或UI访问，所有的服务或函数都会公开一个默认的路由，每个端点也可使用自定义域名。

Prometheus收集可通过Gateway的API获取的指标，这些指标用于自动扩容。

通过将函数的URL从`/function/NAME`改为`/async-function/NAME`，可以使用NATS Streaming在队列中运行调用，也可以传递可选的回调URL。

faas-netes为OpenFaaS最流行的编排提供者，社区也开发了Docker Swarm, Hashicorp Nomad, AWS Fargate/ECS, and AWS Lambda，提供者通过[faas-provider SDK](https://github.com/openfaas/faas-provider)构建。
