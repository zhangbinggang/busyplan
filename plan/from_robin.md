# 目标
自动驾驶在我看来是一个和机器人差不多的问题，可以细分为感知／认知／决策／执行这4部分
我们需要搭建一个仿真环境，来模拟／测试我们对自动驾驶相关技术的理解和实现

## 感知
感知指的是汽车通过传感器感知周围环境信息和自身状态
1. 视觉：感知车辆前后左右的视觉信息，为最主要的输入，包括路况，交通标志，信号灯等
2. 雷达：测定与障碍物的距离，在不佳天气下作为视觉的补充
3. GPS：车辆位置，目标距离
4. 路况信息：用于线路规划

## 认知
对感知到的信息进行存储，推理，这一块涉及到比较多的知识，难度很大，在实现过程中看是否需要和是否有合适的人才

## 决策
对各种传感器得到的信息做整理，输出动作（方向，油门，刹车，信号灯等）


## 执行
输出控制信号到车辆控制总线，完成车辆的工作

## 框架
建议使用RL的框架，汽车作为一个Agent，道路，行人，其他车辆，路况作为环境，Agent通过观察其自身和路况，结合自身的目标，用DL作为决策模块，输出相应的动作给车辆执行，获取相应的reward来作为反馈信号训练

## 切入点
为避免工作过程中太过发散，建议约束一个场景(启动／泊车／紧急停靠／通过交叉路口／超车／掉头等)并迭代来作为主线，以过交叉路口为例，建议以下方式迭代
1.根据视觉检测到信号灯，这个可以使用YOLO／SSD等方式直接监督学习
2.根据信号灯信号，用RL来训练汽车停止，启动
3.加入拐弯信号
4.加入车道信息，车辆应在指定车道上直行／拐弯
5.加入其他车辆
6.学习通过没有信号灯的路口


泊车：
1 空旷停车场，车位停车 ，正常进车，左右无车
2 倒车进入，左右无车
3 侧方位停车 前后有车
4 垂直导入 左右有车
5 可选：卡车倒车
6 可选：视觉找车位 鱼眼摄像头，车位。
7 行人很多的场景 泊车


技术
神经网络视觉输入
神经网络视觉感知


tesla 是否开放接口。



## 模块 （待细化）
* 车辆／环境（主要考虑各种不同模拟／真车环境的切换）
  * 输入
  * 输出

* 训练系统
  * 分布式worker
  * Training server
  * Reward function

* 运行系统
  * 仿真环境
  * 真车
  

