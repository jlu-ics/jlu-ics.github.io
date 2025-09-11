---
title: ICS Lab 一项研究成果被FGCS接收
date: 2025-07-02 10:00
published: true
# excerpt: 实验室量子计算方向工作被FGCS（中科院二区）接收，论文题目为“Denoising Diffusion Models with Optimized Quantum Implicit Neural Networks for Image Generation”。
---

实验室量子计算方向工作被FGCS（中科院二区）接收，论文题目为“Denoising Diffusion Models with Optimized Quantum Implicit Neural Networks for Image Generation”。该论文提出了一种名为Optimized Quantum Implicit Denoising Diffusion Model (OQIDDM)的创新性框架，结合优化的量子隐式神经网络（OQINNs）与一致性模型（Consistency Models），显著提升了量子图像生成的质量与效率，为量子生成任务开辟了新路径。该论文第一作者为实验室2022级博士张嘉乐，通讯作者为实验室负责人胡俊成老师，主要合作者包括吉林大学车喜龙教授、实验室2024级硕士樊宇哲、吉林大学软件学院本科生彭顺、电子科技大学博士生陈庚和信息工程大学博士生马权公。

## 研究背景

图像生成是计算机视觉领域的核心研究方向，广泛应用于数据合成、艺术创作等领域。传统去噪扩散模型（DDMs）在生成高质量图像方面表现出色，但量子扩散模型常依赖复杂的混合U-net架构或混合态操作，需频繁的量子-经典数据转换，导致训练效率低、噪声中间尺度量子（NISQ）设备兼容性差。如何在减少参数量、提升图像质量的同时，适配NISQ设备，成为亟待解决的挑战。OQIDDM通过优化量子隐式神经网络结构，结合一致性模型的单步采样优势，为高效量子图像生成提供了全新解决方案。

## 实验设计

![](640.png)

如图1所示，OQIDDM通过经典正向扩散过程和量子逆向去噪过程实现高效图像生成。其核心设计包括：
1. 正向扩散：采用经典高斯噪声逐步扰动输入数据，生成完全高斯分布的噪声样本，节省量子资源。
2. 逆向去噪：利用OQINNs拟合一致性模型的映射函数，通过单步去噪直接从噪声样本生成干净图像，降低多步迭代需求。
3. OQINNs架构：优化传统量子隐式神经网络（QINNs），仅使用两个经典线性层进行维度处理，核心网络为全量子模块，减少量子-经典数据交换，提升NISQ设备兼容性。

OQINNs通过N层数据重上传模块（data re-uploading）实现高效特征提取，每层包含旋转门（Rz）和强纠缠层（CNOT），理论证明其可作为任意平方可积函数的通用逼近器。OQIDDM的训练复杂度显著降低，采样过程仅需O(1)步，优于传统量子扩散模型的O(T)步。

## 实验结果

实验在MNIST、Fashion-MNIST、E-MNIST以及复杂人脸数据集CelebA上进行，并在IBM量子平台的模拟器（qasm）及三台超导量子计算机（ibm_sherbrooke、ibm_kyiv、ibm_brisbane）上验证。关键结果包括：
1. 图像质量：在MNIST数据集上，OQIDDM的PSNR值达10.44-14.18，优于Qdense（7.14-7.99）和QNN（10.32-13.03），接近经典U-net（8.06-14.34），且参数量仅为576。
2. 复杂数据集：在CelebA 64×64人脸生成任务中，OQIDDM首次实现量子去噪扩散模型在复杂数据集上的应用，成功捕捉人脸结构，优于Qdense等模型。
3. 噪声鲁棒性：OQIDDM对退极化噪声和旋转角度误差表现出更强鲁棒性，SSIM和PSNR值在噪声强度0.05-0.1下下降较慢。
4. 硬件表现：在ibm_sherbrooke上，OQIDDM生成图像的量子态分布更接近模拟结果，优于ibm_kyiv和ibm_brisbane，展现出更高的NISQ设备适应性。

![](640_1.png)
![](640_2.png)
![](640_3.png)
![](640_4.png)
![](640_5.png)
![](640_6.png)

OQIDDM通过优化量子隐式神经网络与一致性模型的结合，不仅显著降低了量子参数量和采样复杂度，还提升了图像生成质量与噪声鲁棒性。实验验证了其在标准及复杂数据集上的优越性，以及在NISQ设备上的适用性。未来，实验室将探索OQIDDM在人体姿态预测等下游任务中的应用潜力。

FGCS全称为Future Generation Computer Systems，是计算机科学领域的重要国际期刊，专注于未来计算机系统与技术的理论方法研究及实践应用。该期刊由Elsevier出版，在JCR和中科院分区中均具有较高评价，影响因子稳定在6.2以上，自引率低至4.8%，审稿周期约2个月，是混合开放获取期刊。其核心研究领域覆盖分布式计算、云计算、物联网等前沿技术，尤其注重系统架构与理论创新。
