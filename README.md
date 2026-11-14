# 链接照片仿视频

从视频号、抖音或亚马逊商品页提取参考视频，再用一组照片复刻成同格式成片的可复用 Skill。

完整配方在 [`skills/link-photo-imitate-video/SKILL.md`](skills/link-photo-imitate-video/SKILL.md)。

## 适用场景

- 只给了视频链接，要下载原片（视频号、抖音、亚马逊商品视频，或用户已另存的文件）
- 给了参考视频（链接或文件）和一组照片，要按参考视频的构图、节奏和转场做成一条相同格式的成片

只要下载、不要成片时，提取并交付后即可停止，不要自动进入复刻。

## 流程摘要

1. 提取参考视频：优先用用户已保存的文件；否则按平台解析下载，并用 ffprobe 核验。
2. 只要下载就交付副本。
3. 若要复刻：拆镜序，把照片对到各镜，按参考构图做静帧，再生成视频、混入参考音轨后交付。

## 平台与工具

- 视频号：只处理 `weixin.qq.com/sph` 分享链接，解析接口见 [v.mtotech.com](https://v.mtotech.com/api/resolve)
- 抖音：使用 [lyf9528/douyin-dl](https://github.com/lyf9528/douyin-dl) 免登录下载
- 亚马逊商品视频：用 [amazon.ca](https://www.amazon.ca/) 同 ASIN 页面提取 `productVideoOptimized.mp4`
