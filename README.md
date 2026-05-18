# IAA,IQA,AWB-Benchmark
ISP相关任务的一些benchmark，包括但不限于，白平衡，曝光，色彩等

# 白平衡
## 数据集

| 序号 | 数据集名称 | 域(raw/srgb) | 单光源还是多光源 | 发表学校/实验室/公司等 | 发表年份 | 发表期刊/会议 | 数据组成 |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| 1 | [SFU Laboratory](https://www.cs.sfu.ca/~colour/data/) | raw & sRGB | 单光源 | Simon Fraser University | 2002 | IEEE TIP | 321张实验室严格受控图像，涵盖30个物体场景与11种精密标定光源 |
| 2 | [Gehler-Shi Dataset](https://www.cs.sfu.ca/~colour/data/shi_gehler/) | raw (线性化) | 单光源 | MPI / Simon Fraser Univ. | 2008 | CVPR / F-ICCV | 568张不同色温的室内外实景图像，由2款相机拍摄，带标准ColorChecker色卡 |
| 3 | [MIT-Adobe FiveK](https://data.csail.mit.edu/graphics/fivek/) | raw & sRGB | 单光源 (侧重美学与白平衡) | MIT / Adobe | 2011 | CVPR | 5000张高精度原始图像，提供5位专家的白平衡与色彩美学精调真值 |
| 4 | [NUS Dataset](http://cvil.eecs.yorku.ca/projects/public_html/illuminant/illuminant.html) | raw | 单光源 | NUS / York University | 2014 | JOSA A | 1736张图像，来自8款不同相机，每个场景带ColorChecker色卡 |
| 5 | [Cube Dataset](http://ipg.fer.hr/ipg/resources/color_constancy) | raw | 单光源 (含双向GT) | Univ. of Zagreb (FER) | 2015 | MIPRO | 1707张实景图像，包含SpyderCube立体校色块，支持多方向光照真值 |
| 6 | [Rendered WB](https://github.com/mahmoudnafifi/Rendered_WB_dataset) | sRGB | 单光源 (错误渲染) | York University / Adobe | 2019 | CVPR | 65000+张sRGB图像，包含不同白平衡错误设置的图像及正确的参考真值 |
| 7 | [MID Dataset](https://github.com/marc-f-me/multi-illumination) | raw & HDR | 多光源 (重光照) | MIT CSAIL | 2019 | ICCV | 1016个室内场景，每个场景在25种不同方向光源下拍摄，共25000+张图像 |
| 8 | [Cube++ Dataset](http://ipg.fer.hr/ipg/resources/color_constancy) | raw | 单光源 (含双向GT) | Univ. of Zagreb (FER) | 2020 | IEEE Access | 4890张高分辨率图像（Cube的扩充版），提供更丰富的光照条件与方向真值 |
| 9 | [PPR10K](https://github.com/csjliang/PPR10K) | raw & sRGB | 单光源 (人像与美学) | 腾讯 / 厦门大学 | 2021 | ICCV | 11161张高质量高分辨率人像原图，提供3位专家的修图真值与区域掩膜 |
| 10 | [LSMI Dataset](https://github.com/eunilCS/LSMI-dataset) | raw & sRGB | 多光源 (混合) | Yonsei Univ. / Samsung | 2021 | ICCV | 7486张图像，包含2762个多光源混合场景，提供像素级光照真值与混合比例 |
| 11 | [INTEL-TAU](https://github.com/boomb0om/Intel-TAU) | raw | 单光源 | Tampere Univ. / Intel | 2021 | IEEE Access | 7022张高分辨率图像，来自3款不同相机，已完成针对人脸等隐私的脱敏屏蔽 |


## 算法
### sRGB域

##### sRGB White Balance (sRGB-WB) Algorithms Summary

本仓库整理了近年来针对 **sRGB 域的白平衡（sRGB-WB）校正** 的核心算法。与传统的 Raw-WB 方法不同，sRGB-WB 旨在直接修复经过相机图像信号处理器（ISP）非线性转换后产生的色偏。

以下是代表性算法的汇总列表：

| 序号 | 算法名称 | 单光源/多光源 | 发表机构 | 发表年份 | 发表期刊/会议 | 核心思路与特点 | 论文与代码 |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| 1 | **KNN** | 单光源 | York University / Adobe | 2019 | CVPR | **基于样本检索**。提取输入图像颜色直方图特征，从渲染数据集中匹配相似图像并应用非线性映射。 | [Paper](https://openaccess.thecvf.com/content_CVPR_2019/papers/Afifi_When_Color_Constancy_Goes_Wrong_Correcting_Improperly_White-Balanced_Images_CVPR_2019_paper.pdf) \| [Code](https://github.com/mahmoudnafifi/WB_sRGB) |
| 2 | **Deep-WB** | 单光源 | York University / Adobe | 2020 | CVPR | **单光源 CNN 网络**。采用端到端的深度卷积神经网络，直接对 sRGB 图像进行特征学习与色彩校正。 | [Paper](https://openaccess.thecvf.com/content_CVPR_2020/papers/Afifi_Deep_White-Balance_Editing_CVPR_2020_paper.pdf) \| [Code](https://github.com/mahmoudnafifi/Deep_White_Balance) |
| 3 | **Mixed-WB** | 多光源 | York University / Adobe | 2022 | WACV | **多版本权重融合**。为输入图像生成多个不同预设色温的白平衡版本，通过网络预测权重图进行平均融合。 | [Paper](https://openaccess.thecvf.com/content/WACV2022/papers/Afifi_Auto_White-Balance_Correction_for_Mixed-Illuminant_Scenes_WACV_2022_paper.pdf) \| [Code](https://github.com/mahmoudnafifi/mixedillwb) |
| 4 | **SWBNet** | 单/多光源 | 北京邮电大学 | 2023 | AAAI | **频域特征细化**。在 DCT 频域中使用 Transformer 细化颜色敏感特征，结合对比损失提升网络跨色温稳定性。 | [Paper](https://github.com/ChunxiaoLe/SWBNet/blob/master/paper/9786.ChunxiaoLi.pdf) \| [Code](https://github.com/ChunxiaoLe/SWBNet) |
| 5 | **WBFlow** | 单光源 | 北京邮电大学 | 2023 | IJCAI | **可逆神经流空间映射**。通过可逆流模型将色偏图像映射回伪 Raw (pseudo-raw) 特征空间进行校正，具备少样本相机自适应能力。 | [Paper](https://github.com/ChunxiaoLe/WBFlow/blob/main/1152.ChunxiaoLi.pdf) \| [Code](https://github.com/ChunxiaoLe/WBFlow) |
| 6 | **WB LUTs** | 单光源 | Northeastern University | 2024 | CVPR | **3D 查找表与对比学习**。引入 3D LUTs 替代传统的图像到图像转换模型，结合困难样本挖掘，极大提升推理速度。 | [Paper](https://arxiv.org/abs/2404.10133) \| [Code](https://github.com/skrmanne/3DLUT_sRGB_WB)) |
| 7 | **ABC-Former** | 单光源 | 国立政治大学 | 2025 | CVPR | **跨模态全局特征交互**。利用辅助模型学习 sRGB 与 CIELab 的全局直方图特征，通过交互式通道注意力 (ICA) 模块重加权目标特征。 | [Paper](https://openaccess.thecvf.com/content/CVPR2025/papers/Chiu_ABC-Former_Auxiliary_Bimodal_Cross-domain_Transformer_with_Interactive_Channel_Attention_for_CVPR_2025_paper.pdf) \| [Code](https://github.com/ytpeng-aimlab/ABC-Former) |
| 8 | **Revisiting-MiWB**| 多光源 | 多伦多大学 / 约克大学 | 2025 | ICCV | **基于 Transformer 的多光源融合**。使用 Transformer 架构捕获空间依赖性来混合多个 WB 预设，提升多光源场景校正能力。 | [Paper](https://arxiv.org/pdf/2503.14774) \| [Code](https://github.com/davidserra9/revisitingMIWB) |

> **💡 说明**：上述表格涵盖了从经典的基于样本检索的方法（如 KNN）到最新的基于跨模态 Transformer（如 ABC-Former）的演进过程。随着研究的深入，算法正逐渐从局部像素级调整转向结合全局色彩分布的跨域特征融合。
