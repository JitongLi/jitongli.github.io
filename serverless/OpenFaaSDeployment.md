# OpenFaaS部署
OpenFaaS可被部署到各种容器编排器中，如Kubernetes，K3s，OpenShift，或可用faasd部署至单机中。

## OpenFaaS 社区版 -- 针对Kubernetes

OpenFaaS社区版仅供个人使用，商业使用期限为60天。

官方推荐三种方式将OpenFaaS安装到Kubernetes集群：

* 使用CLI安装器 [arkade](https://arkade.dev/) （推荐）

* 使用Helm chart，Flux或ArgoCD（GitOps工作流）

* 使用静态生成的YAML文件（不推荐）

部署至Kubernetes -- https://docs.openfaas.com/deployment/kubernetes/

## OpenShift - 3.x / 4.x
[OpenShift](https://www.redhat.com/en/technologies/cloud-computing/openshift)为Red Hat出品的Kubernetes的变体，可使用标准的Helm chart作为单个Kubernetes说明部署到OpenShift中，OpenShift通常为每个命名空间分配随机的用户ID，可在创建openfaas和openfaas-fn命名空间后在Helm char的values.yaml文件中设置这些ID。

部署至OpenShift -- https://docs.openfaas.com/deployment/openshift/


<font color=blue>除了以上两种社区版的部署方式外，下面的标准及边缘版都是针对商业用途的，实验学习可以不用继续往下看了。有商业需要的可以留言一起学习，目前博主没有接触商业的部署。</font>

## OpenFaaS Pro - 标准版或企业版（生产、商业用途）
OpenFaaS Pro是OpenFaaS的商业支持版本，其专为生产用途设计或授权，OpenFaaS Pro提供两种版本：

* OpenFaaS 标准版：适用于单个团队或单租户环境。

* OpenFaaS 企业版：适用于希望将函数集成到其产品的大型公司或SaaS供应商。

部署OpenFaaS Pro -- https://docs.openfaas.com/deployment/pro


## OpenFaaS 边缘版（faasd-pro）/faasd CE - Serverless for everyone else

`faasd`为FaaS Daemon的缩写，为一个运行在主机上的二进制文件，用户管理有状态的服务和函数。

faasd是OpenFaaS的重新构想，摒弃了Kubernetes的复杂性及成本，需求非常低，能够在单机上良好运行，并且与OpenFaaS在Kubernetes上的API兼容。其底层使用[containrd](https://containerd.io/)和容器网络接口（[Container Networking Interface](https://github.com/containernetworking/cni)，CNI），和OpenFaaS的核心组件相同。

faasd CE仅限于单个命名空间，支持有限的15个函数，OpenFaaS Edge为faasd的商业发行版，具有附件功能和更高的限制。

OpenFaaS Edge为faasd的商业发行版，具有来自[OpenFaaS Pro](https://docs.openfaas.com/openfaas-pro/introduction/)的提升及附件的特征:

* 从OpenFaaS Pro升级到Cron Connector，JetStream Queue Worker及Classic Scale to Zero

* 部署多达250个函数

* 配置私有DNS服务器

* Airgap友好，安装捆绑在OCI镜像中

* 支持多命名空间

该版本旨在作为更广泛解决方案进行转售，可被部署到工业和本地环境中。

部署OpenFaaS Edge -- https://docs.openfaas.com/deployment/edge
