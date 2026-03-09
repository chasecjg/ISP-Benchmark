# ISP-Benchmark
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
