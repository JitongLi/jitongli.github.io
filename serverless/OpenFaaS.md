# OpenFaaS
OpenFaaS是最受欢迎的开源Serverless项目，由[Alex Ellis](https://www.alexellis.io/)于2016年创建，其官方网站为 https://www.openfaas.com ，Github链接为 https://github.com/openfaas 。

![OpenFaaS](https://blog.alexellis.io/content/images/2017/08/faas_side.png)

如无服务器计算（Serverless Computing）所提供的函数即服务（Function as a Service，FaaS）服务一样，OpenFaaS旨在使开发者更容易地将事件驱动的函数和微服务部署到Kubernetes，而无需重复编写样板代码。开发者可将代码或二进制文件打包到Docker镜像中，实现自动扩展。
## Hightlights

* 可移植：可在任何云平台或本地运行，无需担心厂商锁定

* 可使用任何语言编写函数，并可将其打包到Docker/OCI格式的容器中

* 易于使用：内置UI，强大的CLI和一键安装

* 按需扩展：可应对流量高峰，并在空闲时缩减

* 良好生态：具有良好的函数社区市场和语言模版
## OpenFaaS版本

如链接 https://www.openfaas.com/pricing/ 所示，OpenFaaS提供了社区版（Community Edition）、标准版（Standard）、企业版（Enterprises）及边缘版（Edge）。

社区版仅供个人使用，提供15个函数，1个命名空间，可以商用60天，部署在Kubernetes上。

标准版$1200每月，适用于企业的产品，提供500个函数，1个命名空间。

企业版更强大，需要定制。企业版和标准版都是针对商业及产品使用，部署在Kubernetes上。

边缘版需要商业许可证，部署在虚拟机（VM）或裸机上（无需Kubernetes），提供25-250个函数。
## 版本选择

社区版仅个人使用免费，60天的商业使用免费，部署在Kubernetes上。


OpenFaaS 标准版及企业版针对商业及产品，部署在Kubernetes。


faasd可在任何云或本地免费使用，可在单个虚拟机上运行（无需集群或Kubernetes）。
