---

title: 'RAG-SEG: A Training-free Framework for Segmentation'
date: 2025-07-29
permalink: /posts/2025-07-29-blog-post-vis/
tags:
  - cool posts
  - category1
  - category2
---

以下展示的 SEG 结果来源于网络截图，仅用于学术交流。若涉及您的合法权益，请及时联系我们（wutaoliu@nuaa.edu.cn），我们将及时处理。  
The SEG results shown below are sourced from online screenshots and are intended for academic use only. If these materials infringe on your rights, please contact us at wutaoliu@nuaa.edu.cn for prompt resolution.



### 感谢

**以下排名不分先后：陈虹伊，《无间道》，《百家讲坛》，《教父》，《状元苏乞儿》，谭维维，张碧晨，《甄嬛传》,张国荣, 泽连斯基，特朗普。**



## 分布外分割的一些说明  
## Notes on Out-of-Distribution (OOD) Segmentation

> 📌 我们的方法在分布外场景下依然能够取得较好的效果，但部分场景仍存在一定噪声，后续我们将继续优化。  
> 📌 Our method performs well even in out-of-distribution scenarios, although some noise remains in specific cases. We will continue to refine our approach.

---

### 视频展示 
### Video Demonstration

> 📌 这些视频结果直接源自我们的 Train-Free 方法，仅依赖视觉检索与分割，而没有任何针对视频序列的训练或优化。  
> 📌 These video results are directly generated from our train-free pipeline, relying solely on visual retrieval and segmentation without any temporal training or optimization.

> 对比已有的一些方法（如 SAM2 中通过 label id 实现跨帧一致性），我们**刻意没有引入此类技术**，而是力求方案尽量**简单、通用**。  
> Unlike some existing methods (e.g., SAM2 using label IDs for cross-frame consistency), we intentionally avoided such mechanisms to keep our approach **simple,  and generalizable**.

尽管在连续帧中可能出现一定闪烁或不稳定情况，但整体物体的定位与边界保持较好，尤其是在复杂背景和遮挡场景下，依然能够准确地聚焦目标区域。  
Although some flickering or instability may occur between frames, our method still accurately locates and segments objects, especially in complex backgrounds and occlusion-heavy scenes.

我们逐帧进行推理。
 We perform inference on a movie frame by frame.

---

#### 🎥 示例视频 1：人物运动  
#### 🎥 Example Video 1: Human Movement

<video controls width="100%">
  <source src="{{ site.baseurl }}/images/rag_vis/hongyi.mp4" type="video/mp4">
  Your browser does not support the video tag.
</video>

---

#### 🎥 示例视频 2：电影片段 (OOD)  
#### 🎥 Example Video 2: Movie Scene (OOD)

<video controls style="max-width: 100%; height: auto;">
  <source src="{{ site.baseurl }}/images/rag_vis/wujiandao.mp4" type="video/mp4">
  Your browser does not support the video tag.
</video>
本部分充分展示了方法在处理分布外样本方面的能力，尤其在**手枪与手铐**等物体的分割任务中表现突出。
 This section demonstrates the strong generalization ability of our method on out-of-distribution (OOD) data, particularly in segmenting challenging objects such as **handguns** and **handcuffs**.

### Image 结果展示  

🌟 请注意，我们展示的结果从左到右依次为：原图、初始分割结果、后处理结果以及叠加图（Overlay）。
🌟 Please note that the results are presented from left to right in the following order: original image, initial segmentation result, post-processed result, and overlay.



### Image Results

> 💡 虽然初始步骤中存在一定噪声，但得益于我们的后处理机制，部分干扰信息已被有效过滤，因此整体效果依然令人满意。 💡 Although some noise appears in the initial stage, our post-processing effectively filters most artifacts, resulting in satisfactory outcomes.

#### 样例场景涵盖电影片段、网络视频及真实生活画面等多种复杂环境：  
#### The sample scenes include movie clips, online videos, and real-life settings with diverse complexity:

---

#### 简单场景  
#### Simple Scene
<p align="center">
  <img src="/images/rag_vis/Snipaste_2025-01-04_21-27-56.png_comparison.png" alt="Simple Scene" style="max-width: 100%; height: auto;" />
</p>

#### 低光环境 + 遮挡  
#### Low-Light with Occlusion
<p align="center">
  <img src="/images/rag_vis/Snipaste_2025-03-18_12-56-10.png_comparison.png" alt="Low Light and Occlusion" style="max-width: 100%; height: auto;" />
</p>

#### 低光环境  
#### Low-Light Scene
<p align="center">
  <img src="/images/rag_vis/Snipaste_2025-05-09_21-15-18.png_comparison.png" alt="Low Light" style="max-width: 100%; height: auto;" />
</p>

#### 简单场景  
#### Simple Scene
<p align="center">
  <img src="/images/rag_vis/Snipaste_2025-05-09_21-21-38.png_comparison.png" alt="Simple Scene" style="max-width: 100%; height: auto;" />
</p>

#### 多人物场景  
#### Multi-Person Scene
<p align="center">
  <img src="/images/rag_vis/Snipaste_2025-05-09_21-23-16.png_comparison.png" alt="Multi-person Scene" style="max-width: 100%; height: auto;" />
</p>

#### 简单场景  
#### Simple Scene
<p align="center">
  <img src="/images/rag_vis/Snipaste_2025-05-09_21-40-31.png_comparison.png" alt="Simple Scene" style="max-width: 100%; height: auto;" />
</p>

#### 简单场景  
#### Simple Scene
<p align="center">
  <img src="/images/rag_vis/Snipaste_2025-05-09_21-41-49.png_comparison.png" alt="Simple Scene" style="max-width: 100%; height: auto;" />
</p>

#### 多人物场景  
#### Multi-Person Scene
<p align="center">
  <img src="/images/rag_vis/Snipaste_2025-05-12_19-04-59.png_comparison.png" alt="Multi-task Scene" style="max-width: 100%; height: auto;" />
</p>

#### 古装人物（影视）  
#### Costumed Characters (Historical Drama)
<p align="center">
  <img src="/images/rag_vis/Snipaste_2025-05-22_19-46-42.png_comparison.png" alt="Costumed Characters" style="max-width: 100%; height: auto;" />
</p>

#### 极暗光环境  
#### Very Low-Light Scene
<p align="center">
  <img src="/images/rag_vis/Snipaste_2025-05-26_18-54-58.png_comparison.png" alt="Very Low Light" style="max-width: 100%; height: auto;" />
</p>
<p align="center">
  <img src="/images/rag_vis/Snipaste_2025-05-26_18-11-39.png_comparison.png" alt="Very Low Light" style="max-width: 100%; height: auto;" />
</p>
#### 简单自拍场景  
#### Simple Selfie Scene
<p align="center">
  <img src="/images/rag_vis/mygirl.png_comparison.png" alt="Selfie Scene" style="max-width: 100%; height: auto;" />
</p>

#### 真实场景  
#### Real-World Scene
<p align="center">
  <img src="/images/rag_vis/Snipaste_2025-05-14_21-36-14.png_comparison.png" alt="Real Scene" style="max-width: 100%; height: auto;" />
</p>


<!-- ## Additional Notes

> Headings are cool 😎  
> You can have many headings...  
> Aren't headings cool? -->

