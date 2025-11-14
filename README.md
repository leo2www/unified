# Examples
统一接口允许开发者集中代码描述算法，增强项目可维护性，优化用户体验。
## VGON unified interface
`example\VGON` 

1. 数据导向，用户提供 实验建模（cvxpy）和损失函数（torch中的Loss function），程序内部利用torch训练VGON并返回训练成功的模型；支持导出或基于torch直接运行。
    
    1.1 ~~简单封装 损失函数 可能过量复制变量~~ 重新整理VGON 代码，以更简便的方式使用 CvxpyLayers，并将测试样例生成、已用损失函数等作为 utils 封装。
        
        注意，封装并非系统性。
    
    1.2 ~~共享内存|原生数据结构：diffcp 已经提供~~
    
    1.3 triton 重构 diffcp 以支持GPU
2. 独立接口，借助 UOI 描述和求解优化问题，进一步集成自动微分；
    
    2.1 统一 UOI 的 问题数据结构 （SCS diffcp；ATen ）<-Cpp
    
    2.2 开发 UOI 的 complex parameter 支持 （DPP + JuMP）
    
    2.3 抽象求解器：JAXopt 借助JAX 对复杂算子的自动微分功能提供
    
    2.4 开发 UOI 的动态化简功能 (MOI)
    
    2.5 抽象求解器 的 GPU solver 支持 <-DLPack
3. 抽象自动微分框架，抽离torch依赖
    3.1 keras 直接支持 torch+tf+jax
    3.2 MindSpore
4. 自动构建模型：已知线路和简化的数学表达式，自动构建量子问题的优化模型。
    4.1 场景封装
    4.2 MindQuantum