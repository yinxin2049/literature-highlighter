# 文献划线工具 · Literature Highlighter

把文献图片做成「划线 + 翻译 + 动画」的视频或透明 MOV，纯前端、零依赖、单文件 HTML。打开就能用，离线也行。

## 功能

- **划线动画**：色块 / 荧光笔 / 负片（黑底白字）三种风格，支持透明度、粗细、圆角、辉光描边、动画时长、起始停留、结尾定格
- **OCR 关键词查找**：基于 Tesseract.js（中英），框选自动识别原文，整篇关键词搜索一键划线
- **多种翻译方式**：整段翻译（连贯字幕） / 分句翻译（每条划线独立字幕），译文可手动编辑
- **字幕排版**：字号 / 颜色 / 加粗 / 描边 / 阴影 / 底色块 / 内边距 / 圆角 / 偏移 / 拖拽改变位置和大小
- **画面表现**：文献阴影、入画动画（淡入 / 翻页 / 滑入 / 缩放）、3D 透视（X/Y/Z 轴 + FOV）、文献缩放 / 平移 / 平面旋转
- **底图风格**：文献颜色反转（黑底白字 / 发光笔记效果）、纯文字透明背景（自动识别背景色，对任意底色通用）
- **画布与导出**：横屏 16:9 / 竖屏 9:16 / 原图尺寸；MP4 含背景、MOV 含背景、⭐ MOV 透明通道、PNG 序列（含背景 / 透明）
- **编辑体验**：撤回 / 重做（Ctrl+Z / Ctrl+Shift+Z），划线拖动改位置和大小，键盘上手就知道怎么用

## 怎么用

直接在浏览器里打开 `index.html` 就好。如果想让别人从网页直接访问，部署到 GitHub Pages 即可（仓库 Settings → Pages → 选 main 分支根目录）。

典型流程：

1. 拖一张文献截图到左边「导入文献」区
2. 在画面上框选要划的句子（或先用关键词搜索批量框选）
3. 右边「划线样式」选风格、颜色、动画时长
4. 右边「字幕翻译」选整段或分句，点「翻译全部划线」
5. 画布右下角的「▶ 播放预览」看效果
6. 右边「导出」选分辨率，按需导出 MOV / MP4 / PNG

## 技术细节

- 单文件 HTML，纯前端实现，没有构建步骤
- Canvas 2D 画底图、划线、字幕；可选 WebGL 做 3D 透视
- OCR：[Tesseract.js](https://github.com/naptha/tesseract.js)（CDN 引入，首次用会下载约 10–15MB 模型）
- 翻译：免密钥的 Google / MyMemory 接口（前端直连，无需服务器）
- 视频导出：MediaRecorder API（MP4 / WebM）+ JSZip（PNG 序列）+ 自实现 MOV 透明通道封包
- 离线可用：除翻译和首次 OCR 模型下载外，所有功能不依赖网络

## 浏览器兼容

推荐 Chrome / Edge / Safari 最新版。MOV 透明通道导出在 Chromium 系浏览器上效果最好。

## 许可证

MIT License — 见 [LICENSE](./LICENSE)。

---

**English summary**: A single-file HTML tool to turn document screenshots into highlight-and-translate animation videos. Drag in an image, draw highlights, translate, then export as MP4 / MOV (with transparency) / PNG sequence. Pure frontend, no build step, no server. Open `index.html` in any modern browser.
