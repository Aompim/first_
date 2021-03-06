#BP神经网络

### 分类（拓扑结构，图）
* 层次型
    - 输入层：神经元接受
    - 中间层：含隐层（信息变换），一层多层，最后一层传入输出层神经元
    - 输出层：输出信息处理结果

* 互联型
    - 全互联型
    - 局部互联型
    - 

### 分类（信息流向）

* 前馈:信息传递具有方向性，一般不存在反馈环路，串联成多层前馈网络，不会返回误差eg 多层感知器
* 反馈（递归）：每个节点都可以输入输出，eg,Hopfield网络

### 分类（学习规则）

* 监管：需要训练规则，训练规则会调节所以需要的权重，eg delta rule(单层感知器)
* 非监管：不需要教师，所产生输出会进一步评估（准确率比上面的低）

### 基本功能

* 分类与识别
* 优化计算
* 非线性映射

### 基本模型
'''mermaid
graph LR
A[输入信号] -->B [突触全值]
    B -->C [求和链接]
    C -->D [激活函数]
    D -->E [输出]
'''

输入信号-->突触全值-->求和链接-->激活函数-->输出

#### 激活函数

* 线性函数
* 限幅函数
* s(sigmoid)函数
* 阈值或偏置
### 神经网络的使用性

只有当常规方法解决不了或效果不佳，用神经网（ANN）方法才有优越性，尤其是对问题的机理不了解或者不能用数学模型来来表示的系统（黑箱），eg.故障诊断，特征提取和预测，ANN效果比较好

### bp网络

误差反向传播算法（bp算法）解决多层感知器解决不了的 亦或 问题，
解决了求解非线性连续函数的多层前馈神经网络

* 学习类型：有导师学习
* 核心思想： 输出误差以某种形式通过隐层向输入层反穿
* 学习过程： 信号的正向与误差的反向传播
* 学习本质： 对连接权值的动态调整
* 学习规则： 权值调整规则，在学校过程中网络中各神经元的连接权

- 正向传播
    - 输入样本 输入层 各隐层 输出层
- 判断是否转入反向传播阶段
    -输出层的实际输出与期望输出（教师期望）不符
- 误差和反传
-   -误差以某种形式在各层表示--修正各层神经元

### bp网络的标准学习算法

* 网络结构
  n,p,q
* 定义变量
 输入变量--隐含层输入--隐含层输出--输出层输入--输出层输出--期望输出

 激活函数，输入变量是以知，其余可知或可算出

 误差函数
 > $e=\dfrac{1}{2}\sum_{o=1}^{q}(d_{o}(k)-yo_{o}(k))^{2}$

### 算法
 * 第一步 网路初始化
>给各个连接权值分别赋予（-1，1）内的随机数，给定误差函数e,精度，次数，$ϵ$,M

* 第二步，随机选取第k个输入样本及对应期望的输出
* 第三步， 计算隐含层各神经元的输入和输出
* 第四步，计算输出层各神经元的输入和输出
* 第五步，计算误差函数对输出层各神经元的偏导数
  >$x^{k+1}=x^{k}+\lambda d^{k}$
* 0
*  -
*  ⁽
*  第九步，计算全局误差
  >
* 判断误差是否满足要求，
   >权值按梯度下降算法


>缺陷：收敛速度慢，局部极小值，不稳定性（聚子点）（贪心)

* 算法改进
  >增加动量项（减少震荡，与前几次迭代组合）
  >可变学习速度的反向传播算法
  >学习率的自适应调节
  >引入陡度因子（转移函数）

* 加速算法
  >共轭梯度法：误差反向传播和网络权值更新是两个过程且是分开的，本质上相互独立，可以避免聚子现象
  >LM算法训练BP网络的牛顿算法
  >RPROP是一种简单高效的训练方法，克服了雅可比矩阵计算量过大的问题
  >b&b算法