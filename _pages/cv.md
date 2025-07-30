---
layout: archive
title: "CV"
permalink: /cv/
author_profile: true
redirect_from:
  - /resume
---

{% include base_path %}




教育经历
======
* 2019-2023: 长沙理工大学, 软件工程, 学士学位
* 2023-2026: 南京航空大学, 计算机应用技术, 硕士学位 (ing)

研究方向
======
* 伪装目标检测
* 扩散模型 Diffusion & 流匹配 Flow Matching
* 检索增强生成 RAG
* 多模态大模型

技能证书
======
* CET-6 
* CSP认证:200分

项目经历
======
* 基于RAG的伪装目标分割
  * 使用 DINOv2 获取图像特征向量，采用 KMeans 降维；以 Faiss 构建向量数据库，进行 Top-1 暴力检索；并对比了 Faiss、Milvus、ChromaDB、LanceDB、Qdrant 等多个数据库的性能。
  * 使用 RAG 生成的伪分割掩码作为 prompt 输入 SAM2，获得了优异的分割结果。
  
* 使用 LoRA 微调 SD 生成和分割伪装目标图像
  * 使用 Flow Matching 分割伪装目标
  * 使用 CLIP、BLIP、BLIP2、LLAVA、Florence2 等模型生成伪装目标的 caption，并通过 ControlNet-HED 模型提取边缘信息。
  * 基于 accelerate、transformers、diffusers 等工具，对 SD1.5、SD2.0 及 InstructPix2Pix 模型进行 LoRA 微调。
  * 由于 caption 不准确、数据量较少,训练存在挑战。

* 基于 uni-app 的健康打卡信息系统（毕业设计）
  * 实现了用户信息管理、健康打卡（体温、心情）、打卡提醒等功能。

  * 前端基于 uni-app（Vue.js），后端使用 Spring Boot；集成 PyTorch 训练的表情识别模型以提升系统智能化程度。

Skills
======
* 熟悉Python,C++,Java,Vue等编程语言, 熟悉PyTorch框架。
* 掌握基本的数据结构和算法知识，有一定的代码实现能力 。


Publications
======
  <ul>{% for post in site.publications reversed %}
    {% include archive-single-cv.html %}
  {% endfor %}</ul>
  
<!-- Talks
======
  <ul>{% for post in site.talks reversed %}
    {% include archive-single-talk-cv.html  %}
  {% endfor %}</ul>
  
Teaching
======
  <ul>{% for post in site.teaching reversed %}
    {% include archive-single-cv.html %}
  {% endfor %}</ul>
  
Service and leadership
======
* Currently signed in to 43 different slack teams -->
