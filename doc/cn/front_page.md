[English Version](/en/front_page_en.md)
<div align=left ><img src="https://raw.githubusercontent.com/darrenyao87/tnn-models/master/TNN.png"/>

## 快速开始

使用TNN非常简单，如果你有一个已经训练好的模型, 那么一般而言通过以下三个步骤就能完成模型在目标平台上的部署。
1. 第一步是把训练好的模型转换成TNN的模型，为此我们提供了丰富的工具来帮助你完成这一步，无论你使用的是Tensorflow、Pytorch、或者Caffe，都可以轻松完成转换。
详细的手把手教程可以参见这里[如何转换模型](./user/convert.md)。

2. 当你完成了模型的转换，第二步就是编译目标平台的TNN引擎了，你可以根据自己的目标平台的硬件支持情况，选择CPU/ARM/OpenCL/Metal等加速方案。
   对于这些平台，TNN都提供了一键编译的脚本，使用非常方便。详细步骤可以参考这里[如何编译TNN](./user/compile.md)。

3. 最后一步就是使用编译好的TNN引擎进行推理，你可以在自己的应用程序中嵌入对TNN的调用，这方面我们提供了丰富而详实的demo来帮助你完成。
    *  [从0开始跑通一个iOS Demo](./user/demo.md)
    *  [从0开始跑通一个Android Demo](./user/demo.md)

## 技术方案

TNN作为一个移动端高性能、轻量级的推断框架，同时拥有跨平台、高性能、模型压缩、代码裁剪等众多突出优势。TNN框架借鉴了业界主流开源框架的优点，沉淀和整合了优图实验室Rapidnet，ncnn框架上的积累，并联合深度学习框架OTeam各个部门（PCG，TEG，IEG），共同打造公司级统一移动端推断框架。
目前，TNN已在各大实际业务中上线，其具有的以下特性获得了广泛的好评。

* 计算优化
    * 针对不同架构在硬件指令发射、吞吐、延迟、缓存带宽、缓存延迟、寄存器数量等特点，深度优化底层算子，极致利用硬件算力
    * 主流硬件平台(CPU: ARMv7， ARMv8， GPU: Mali， Adreno， Apple) 深度调优
    * CNN核心卷积运算通过Winograd， Tile-GEMM， Direct Conv等多种算法实现，保证不同参数、计算尺度下高效计算
    * Op融合：离线分析网络计算图，多个小Op（计算量小、功能较简单）融合运算，减少反复内存读取、kernel启动等开销

* 低精度优化
    * 支持INT8， FP16低精度计算，减少模型大小、内存消耗，同时利用硬件低精度计算指令加速计算
    * 支持INT8 WINOGRAD算法，（输入6bit）， 在精度满足要求的情况下，进一步降低模型计算复杂度
    * 支持单模型多种精度混合计算，加速计算同时保证模型精度

* 内存优化
    * 高效”内存池”实现：通过DAG网络计算图分析，实现无计算依赖的节点间复用内存，降低90%内存资源消耗
    * 跨模型内存复用：支持外部实时指定用于网络内存，实现“多个模型，单份内存”。

* 主流模型性能对比：TNN性能优于主流开源移动端高性能框架

    * 麒麟970：

    <div><img src="https://raw.githubusercontent.com/darrenyao87/tnn-models/master/doc/cn/imgs/970.jpg"/>

    * 骁龙835：

    <div><img src="https://raw.githubusercontent.com/darrenyao87/tnn-models/master/doc/cn/imgs/835.jpg"/>


* TNN架构图：


   <div><img src="https://raw.githubusercontent.com/darrenyao87/tnn-models/master/doc/cn/imgs/tnn_architect.jpg"/>

* 通过ONNX支持TensorFlow， Pytorch， MxNet， Caffe等多种训练框架，充分利用和融入不断完善的ONNX开源生态。当前支持ONNX算子55个，近期会完善到约80个，覆盖主流CNN网络
* 支持主流安卓、iOS、embedded Linux，windows操作系统，支持ARM CPU， GPU硬件平台（近期还会加入达芬奇NPU支持）
* 模块化设计，将模型解析、计算图构建、优化、底层硬件适配、高性能kernel实现各部分抽象隔离，通过Factory Mode注册、构建设备，方便接入更多的底层硬件、加速方案。
* Runtime无任何第三方库依赖，CPU动态库尺寸仅约400KB，并提供基础图像变换操作，调用简单便捷。跨平台模型统一、调用接口统一，通过单个配置参数快速切换。

## 能力展示
* [支持](./user/support.md)
* 支持OP: [支持](./user/support.md)中支持OP
* 支持网络: [支持](./user/support.md)中支持OP
* 支持硬件: [支持](./user/support.md)中支持OP
* [Benchmark&测试方法](./user/test.md)

## 使用手册
* [使用流程概览]()
* [从源码编译](./user/compile.md)
* [工具集]()
    * [模型转换](./user/convert.md)
    * [模型量化](./user/quantization.md)
    <!---[模型可视化]() -->
    * [profile工具](./development/profiling.md)
    * [对齐工具](./development/model_check.md)

## API文档
* [API调用](./user/api.md)

## 贡献者须知
* [开发基础须知](./development/contributing.md)
* [架构详解](./development/architecture.md)
* [新增OP](./development/add_op.md)

## Roadmap
* [Road map]()

## FAQ
* [FAQ 常见问题](./faq.md)