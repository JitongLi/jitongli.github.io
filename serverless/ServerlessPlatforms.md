# Serverless平台简介
无服务器计算（Serverless Computing）是云计算领域中相当新的演进。Serverless 提供商允许开发者专注于其应用程序所需的功能及应用逻辑，而无需担心执行环境或任何其他较低级别的层。

为支持无服务器计算，各种商业及开源的平台被提出，商业平台主要包括主流的云计算提供商提供，如国外的Amazon，Microsoft，Google及国内的阿里云等。也有一些开源的Serverless平台，如

# 商业的Serverless平台

## [AWS Lambda](https://www.serverless.com/aws-lambda)
AWS Lambda是Serverless领域中最知名的提供商，亚马逊的 Lambda 服务于 2014 年推出，是最早引起市场广泛关注的提供商之一。

AWS Lambda 仍然是其他产品与之比较的主要服务，因为它具有稳定性、广泛的功能和普遍的熟悉度。

AWS Lambda为理想的计算服务，适用于需要快速扩展并在需求不足时缩减至零的应用场景，包括：

- 流处理：可使用Lambda和Amazon Kinesis处理实时数据，以进行应用程序的互动追踪，交易订单处理，点击流分析，数据清理，日志过滤，索引，社交媒体分析，IoT设备数据遥测和计量。

- Web应用

- 移动及IoT后端

- 文件处理

了解更多关于[AWS Lambda](https://docs.aws.amazon.com/lambda/latest/dg/welcome.html#:~:text=You%20can%20use%20AWS%20Lambda,operating%20system%20on%20provided%20runtimes)。

## [Microsoft Azure Functions](https://azure.microsoft.com/en-us/products/functions)
Microsoft Azure Functions 是 Azure 云生态系统的 Serverless 产品，于 2016 年发布。虽然 AWS Lambda 具有先发优势，但 Microsoft 能够以其示例为起点，开发自己的定价策略、定位和功能。

Microsoft Azure Functionsd用例：

- 智能应用

- 实时处理

- 工作流编排

了解更多关于[Microsoft Azure Functions](https://azure.microsoft.com/en-us/products/functions#ProductOverview)。

## [Google Cloud Run](https://cloud.google.com/functions?hl=zh_cn)
Google Cloud Run由最开始的Google Run Functions改名而来，
Google Cloud Platform 上提供的通用无服务器解决方案。Google Cloud Functions 于 2016 年发布，旨在弥合几年前 AWS Lambda 造成的差距。

同样的，Google Cloud Run支持以下使用场景：

- 与第三方服务及API集成

- 无服务器移动后端

- 无服务器物联网后端

- 实时文件处理

- 实时流处理

- 视频和图片分析

Google Cloud Run的[学习路线](https://cloud.google.com/learn?hl=zh_cn)。

## [Cloudflare Workers](https://workers.cloudflare.com/)
Cloudflare Workers 是 Cloudflare 提供的无服务器选项，它将函数即服务模型与边缘计算相结合。Cloudflare Workers 于 2018 年发布，鉴于 Cloudflare 更像是一家 Web 工具公司而非通用云提供商，因此决定从不同的角度解决问题。

Cloudflare Workers的[文档](https://developers.cloudflare.com/pages/)。

## [阿里云](https://serverless.aliyun.com/)

阿里云服务于音视频处理、Web、人工智能、数据处理、SaaS应用等多种场景。

阿里云Serverless架构的用户案例：

- 新浪微博：[函数计算助力新浪微博完成每日数十亿次个性图片处理](https://developer.aliyun.com/article/783379?spm=5176.21056263.J_2445950140.19.15b16912CIdvjn)。

- 石墨文档：[函数计算助力石墨文档突破性能瓶颈，有效节省58%服务器成本](https://developer.aliyun.com/article/783382?spm=5176.21056263.J_2445950140.21.15b16912CIdvjn)。

- 语雀：[函数计算助力语雀构建稳定且安全的业务架构](https://developer.aliyun.com/article/783383?spm=5176.21056263.J_2445950140.8.15b16912CIdvjn)。

- 伊对：[伊对App视频直播场景的Serverless技术实战](https://developer.aliyun.com/article/781232?spm=5176.21056263.J_2445950140.17.15b16912CIdvjn)。

- 高德地图：[Severless在“十一出行节”峰值场景中表现优秀，整体服务成功率均大于99.99%，总计100W+次触发/分钟，各场景的服务平均响应时间均在60ms以下](https://developer.aliyun.com/article/778869?spm=5176.21056263.J_2445950140.9.15b16912CIdvjn)。

- 爱奇艺体育：[Serverless可实现极致扩容，资源利用率提升50%](https://developer.aliyun.com/article/781737?spm=5176.21056263.J_2445950140.10.15b16912CIdvjn)。

关于阿里云Serverless的学习资源为[Serverless技术图谱](https://developer.aliyun.com/graph/serverless?spm=5176.21056263.J_9499459830.1.15b16912CIdvjn)。


# 开源Serverless平台

## [OpenFaas](https://www.openfaas.com/)
OpenFaaS是一套面向Kubernetes的开源无服务器框架，项目口号是“让无服务器函数更简单”。OpenFaaS属于云原生技术堆栈“PLONK”中的一部分，即Prometheus（监控系统与时间序列数据库）、Linkerd（服务网格）、OpenFaaS、NATS（安全消息传递与流媒体）以及Kubernetes。您可以使用OpenFaaS中的模板存储或Dockerfile，将相应的事件驱动函数及微服务部署到Kubernetes。

OpenFaaS的GitHub链接为 https://github.com/openfaas ，2025.05.23的stars为25.7k。

## [OpenWhisk](https://openwhisk.apache.org/)

Openwhisk是属于Apache基金会的开源Faas计算平台，由IBM在2016年公布并贡献给开源社区。IBM Cloud本身也提供完全托管的OpenWhisk Faas服务IBM Cloud Function。从业务逻辑来看，OpenWhisk同AWS Lambda一样，为用户提供基于事件驱动的无状态的计算模型，并直接支持多种编程语言。

的Github链接为 https://github.com/apache/openwhisk ，2025.05.23的stars为6.6k。

## [Kubeless](https://kubeless.io/)

Kubeless是一套开源Kubernetes原生无服务器框架，强调以Kubernetes集群为部署环境。Kubeless重现了AWS Lambda、微软Azure Functions以及Google Cloud Functions上的大部分功能。开发者可以使用Python、Node.js、Ruby、PHP、Golang、.NET以及Ballerina等语言编写Kubeless函数。Kubeless事件触发器使用的则是Kafka消息系统与HTTP事件。

Kubeless还使用Kubernetes定制资源定义（Kubernetes Custom Resource Definition）创建作为自定义Kubernetes资源的函数。在此之后，它会运行集群内控制器以监控各自定义资源，并按需启动运行时。控制器会动态将函数代码注入运行时，并通过HTTP或发布/订阅机制进行实际使用。

Kubeless已不再由VMware主动维护了，GitHub链接为 https://github.com/vmware-archive/kubeless ，2025.05.23的stars为6.9k。


### [Knative](https://knative.dev/docs/)
Knative项目由谷歌发起，先后获得50多家企业的贡献，用于在Kubernetes上构建并运行无服务器应用程序。Knative的各组件专注于解决常见但又令人头痛的任务，例如容器部署、使用蓝/绿部署进行流量路由与管理、根据需求自动扩展并调整工作负载，以及将运行的服务绑定至事件生态系统等。值得一提的是，Google Cloud Run就是基于Knative构建而成。

Knative的GitHub链接为 https://github.com/knative/docs ，2025.05.23的stars为4.7k。

