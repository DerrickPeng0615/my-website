# my-website

## 视频 / 动画工具(已在 package.json 声明)

新会话如果没有 `node_modules`,先运行 `npm install`。

生成视频、动画、动态图时,先选对工具再动手,不要凭空手写帧循环或只用 CSS 糊弄:

- **Remotion**(`remotion`、`@remotion/cli`):有时间线的视频,例如讲解、数据动画、字幕、转场。用 React 组件按帧编写,渲染成 mp4。
- **three.js**(`three`、`@remotion/three`):需要 3D 物体、镜头运动、粒子或光影的画面。在 Remotion 里用 `@remotion/three` 的 `ThreeCanvas` 嵌入。
- **HyperFrames**(`hyperframes` CLI):用 HTML/CSS 写视频合成,适合排版类动画,出片快。常用命令:`npx hyperframes init|preview|lint|check|render`;不确定用法先 `npx hyperframes docs`。

选择原则:
- 2D 动效不要上 three.js;纯静态图不要做成视频。
- 3D 画面放进 Remotion 的 `ThreeCanvas`,用 `useCurrentFrame()` 驱动动画,保证渲染可复现。
- 先出预览或关键帧让用户确认,再完整渲染。
- 用 HyperFrames 时,渲染前跑 `check`/`lint`;渲染后告诉用户输出文件路径。
- 渲染依赖 FFmpeg 和 Chrome,环境缺失时先 `npx hyperframes doctor`。
