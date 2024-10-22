# JyfVideoCrafter 教程与代码示例

## 简介
**JyfVideoCrafter** 是一个可以帮助开发者在浏览器中创建和编辑 WebM 视频的 JavaScript 库。它允许你从 Canvas 绘制帧并将它们转换为 WebM 格式的视频。这个库支持处理视频帧、生成 WebM 视频格式，并且非常适合需要在网页上快速处理视频的开发者。

## 如何引入库
对于不同的使用环境，JyfVideoCrafter 支持多种方式加载：

- **Node.js 环境**：通过 `require` 引入模块
- **AMD 环境**：通过 `define` 加载模块
- **浏览器环境**：直接在浏览器中使用 `window` 全局对象

### 浏览器环境下的示例：(注意,由于浏览器的安全机制,直接双击打开index是无法预览的)
```html
<script src="path_to/JyfVideoCrafter.js"></script>
<script>
  const { JyfVideo } = JyfVideoCrafter;
</script>
``` 

快速入门示例：生成 WebM 视频
以下是一个简单的示例，展示如何使用 JyfVideoCrafter 库来创建视频。

创建一个 JyfVideo 对象：
使用 JyfVideo 类，可以创建一个视频对象，设置帧速率（FPS）和图像质量。
```html
// 创建视频对象，设定帧速率为 30fps，图像质量为 0.8
const video = new JyfVideo(30, 0.8);
``` 

添加帧到视频：
你可以通过 canvas 画布创建的帧来添加视频帧，每一帧可以设置持续时间。
```html
const canvas = document.createElement('canvas');
const context = canvas.getContext('2d');

// 设置画布宽高
canvas.width = 640;
canvas.height = 360;

// 绘制一些图像到画布
context.fillStyle = 'blue';
context.fillRect(0, 0, canvas.width, canvas.height);

// 将当前画布内容作为一帧加入视频，持续时间默认为 33.33ms (对应30fps)
video.add(canvas);
``` 

编译并生成 WebM 视频：
将所有帧编译为 WebM 格式，最后可以获取二进制数据或者 Blob 对象。
```html
video.compile(false, function (webmBlob) {
  // 使用 Blob 对象创建一个视频链接
  const url = URL.createObjectURL(webmBlob);
  
  // 将视频链接插入到页面中的 <video> 标签
  const videoElement = document.createElement('video');
  videoElement.src = url;
  videoElement.controls = true;
  document.body.appendChild(videoElement);
});
```

TODO LIST:
更多高级功能（未来更新）：
- 合并多个视频片段
- 调整视频的播放速度
- 同步音频到视频
- 检测浏览器对视频功能的支持


























