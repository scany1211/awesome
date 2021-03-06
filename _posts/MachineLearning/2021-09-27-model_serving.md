---

layout: post
title: 推理服务
category: 架构
tags: MachineLearning
keywords:  mpi

---

## 简介（未完成）

* TOC
{:toc}




[Morphling：云原生部署 AI ， 如何把降本做到极致？](https://mp.weixin.qq.com/s/Kl4Bimy6YCfGLZbK12pGcg) 专门整了一个论文
推理业务相对于传统服务部署的配置有以下特性：

1. 使用昂贵的显卡资源，但显存用量低：GPU 虚拟化与分时复用技术的发展和成熟，让我们有机会在一块 GPU 上同时运行多个推理服务，显著降低成本。与训练任务不同，推理任务是使用训练完善的神经网络模型，将用户输入信息，通过神经网络处理，得到输出，过程中只涉及神经网络的前向传输（Forward Propagation），对显存资源的使用需求较低。相比之下，模型的训练过程，涉及神经网络的反向传输（Backward Propagation），需要存储大量中间结果，对显存的压力要大很多。我们大量的集群数据显示，分配给单个推理任务整张显卡，会造成相当程度的资源浪费。然而如何为推理服务选择合适的 GPU 资源规格，尤其是不可压缩的显存资源，成为一个关键难题。
2. 性能的资源瓶颈多样：除了 GPU 资源，推理任务也涉及复杂的数据前处理（将用户输入 处理成符合模型输入的参数），和结果后处理（生成符合用户认知的数据格式）。这些操作通常使用 CPU 进行，模型推理通常使用 GPU 进行。对于不同的服务业务，GPU、CPU 以及其他硬件资源，都可能成为影响服务响应时间的主导因素，从而成为资源瓶颈。
3. 容器运行参数的配置，也成为业务部署人员需要调优的一个维度：除了计算资源外，容器运行时参数也会直接影响服务 RT、QPS 等性能，例如容器内服务运行的并发线程数、推理服务的批处理大小（batch processing size）等。

 AI 推理任务的优化部署相关主题包括：AI 模型的动态选择、部署实例的动态扩缩容、用户访问的流量调度、GPU 资源的充分利用（例如模型动态加载、批处理大小优化）等。

## 推理服务规格调优



1. 人为经验，倾向于配置较多的资源冗余
2. 基于资源历史水位画像，在更通用的超参调优方面，Kubernetes 社区有一些自动化参数推荐的研究和产品，但业界缺少一款直接面向机器学习推理服务的云原生参数配置系统。 Tensorflow 等机器学习框架倾向于占满所有空闲的显存，站在集群管理者的角度，根据显存的历史用量来估计推理业务的资源需求也非常不准确。[KubeDL 加入 CNCF Sandbox，加速 AI 产业云原生化](https://mp.weixin.qq.com/s/7SUhnW4cnk_3G9Q7lIytcA) 分布式训练尚能大力出奇迹，但推理服务的规格配置却是一个精细活。显存量、 CPU 核数、BatchSize、线程数等变量都可能影响推理服务的质量。纯粹基于资源水位的容量预估无法反映业务的真实资源需求，因为某些引擎如 TensorFlow 会对显存进行预占。理论上存在一个服务质量与资源效能的最优平衡点，但它就像黑暗中的幽灵，明知道它的存在却难以琢磨。

对于 AI 推理任务，我们在 CPU 核数、GPU 显存大小、批处理 batch size、GPU 型号这四个维度（配置项）进行“组合优化”式的超参调优，每个配置项有 5～8 个可选参数。这样，组合情况下的参数搜索空间就高达 700 个以上。基于我们在生产集群的测试经验积累，对于一个 AI 推理容器，每测试一组参数，从拉起服务、压力测试、到数据呈报，需要耗时几分钟。

KubeDL-Morphling 组件实现了推理服务的自动规格调优，通过主动压测的方式，对服务在不同资源配置下进行性能画像，最终给出最合适的容器规格推荐。画像过程高度智能化：为了避免穷举方式的规格点采样，我们采用贝叶斯优化作为画像采样算法的内部核心驱动，通过不断细化拟合函数，以低采样率（<20%）的压测开销，给出接近最优的容器规格推荐结果。

[携程AI推理性能的自动化优化实践](https://mp.weixin.qq.com/s/jVnNMQNo_MsX3uSFRDmevA)

## 基于镜像的模型管理
