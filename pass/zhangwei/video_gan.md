1.Temporal Generative Adversarial Nets with Singular Value Clipping

从随机采样的z0生成整个视频序列
A uniform distribution is used to sample z0.
- temporal generator ，一维反卷积，将初始隐变量映射到一个隐变量序列，G0:z0-->{z1,z2,z3,z4....zn}
- image generator 一维向量到二维图像反卷积，G1:(z0,z1)->frame1,(z0,z2)->frame2...
- 生成的video序列可表示为[G1(z0,z1),G1(z0,z2),G1(z0,z3),G1(z0,z4),G1(z0,z5)...G1(z0,zt)]
- 真实的video序列可表示为[x1,x2,....xt]
- 判别器spatio-temporal 3D convolu- tional layers，判别两个视频序列的真假

2.Generating Videos with Scene Dynamics

从随机采样的z0生成整个视频序列
- 引入了静态的背景和动态的前景的先验知识，用于对物体动作跟踪问题的建模
- Foreground Stream 3D convolution,从一维向量z0反卷积生成，3维的动态前景图像序列
- Background Stream 2D convolutions,从一维向量z0反卷积生成，2维的静态背景图像
- 将静态动态合成一个视频序列

应用：Video Representation Learning
视频表示学习，利用训练好的判别器，输入视频序列，取出最后一个全连接层作为输出的特征。在这基础上fine-tune 一个回归或者分类模型，预测方向盘转角或者其他。

3.Learning to Generate Time-Lapse Videos Using Multi-Stage Dynamic Generative Adversarial Networks

给定一张静态图像，生成视频序列

- 两个Gan叠加，第一个Base Gan生成粗糙/模糊的图像，第二个REfine Gan在第一个的基础上进行精细化
- Base Gan，输入的是初始图像复制叠加形成的图像序列X，输出图像序列Y1。生成器采用Unet结构，损失函数是判别器的loss和L1 loss
- Refine net输入Base Gan输出的图像序列Y1，输出图像序列Y2。生成器取消Unet中的skip connection，损失函数为判别器的loss和L1 loss，加上Gram matrix loss ，根据Y，Y1，Y2在判别器某一层输出计算的Gram matrix。采用Gram matrix loss的目的是避免Y2只是简单的逼近Y1。


