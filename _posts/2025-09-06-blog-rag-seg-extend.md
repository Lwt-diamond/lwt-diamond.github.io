---

title: 'RAG-SEG For Medicine'
date: 2025-07-29
permalink: /posts/2025-07-29-blog-post-vis/
tags:
  - cool posts
  - category1
  - category2
---


**Paper Link: https://arxiv.org/abs/2508.15313**

# RAG-SEG 在医学数据集 Kvasir-Sessile 的测试结果  
*RAG-SEG Evaluation on the Medical Dataset Kvasir-Sessile*  

我们在医学影像数据集 **Kvasir-Sessile** 上测试了 RAG-SEG 的效果，结果如下：  
*We evaluated the performance of **RAG-SEG** on the medical imaging dataset **Kvasir-Sessile**. The results are shown below:*  

<p align="center">
  <img src="/images/rag_seg_medicine/faiss_save_dinov2s-kvasir-sessile_IP_224_vdb8192-TOP-1-SAM2.1-0.3-POS10_0.99-NEG10_0.05-NOCRF.png" 
       alt="RAG-SEG 在 Kvasir-Sessile 的结果 / RAG-SEG results on Kvasir-Sessile" style="max-width: 100%; height: auto;" />
</p>

<p align="center">
  <img src="/images/rag_seg_medicine/Snipaste_2025-09-06_13-40-16.png" 
       alt="Kvasir-Sessile 结果细节示例 / Kvasir-Sessile detailed results" style="max-width: 100%; height: auto;" />
</p>

---

## 说明 / Explanation  

RAG-SEG 在常见的自然图像数据集上表现良好，但在医学数据集（如息肉检测）中效果有限。  
*RAG-SEG performs well on natural image datasets but shows limited effectiveness on medical datasets such as polyp detection.*  

原因主要在于：  
*The main reasons are:*  

- **特征域差异 / Domain gap**：DINOV2/SAM2 仅在常见的 RGB 自然图像上训练，已很好地捕捉通用视觉特征；但这些特征难以区分医学场景中细微的病变结构。  
  *DINOV2/SAM2 is trained only on common RGB natural images and has learned strong general-purpose features, but these features are less effective in capturing subtle lesion structures in medical images.*  



---

## 提升方向 / Future Directions  

因此，在医学场景中，若要提升 RAG-SEG 的性能，需要考虑：  
*Therefore, to improve RAG-SEG in medical scenarios, it is necessary to consider:*  

1. 使用医学领域的预训练模型（如医学专用的 ViT 或 CLIP 变体）。  
   *Using medical-specific pretrained models (e.g., domain-specific ViT or CLIP variants).*  

2. 引入领域自适应方法，缩小自然图像与医学影像的特征分布差距。  
   *Introducing domain adaptation methods to reduce the distribution gap between natural and medical images.*  
