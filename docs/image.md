# 图形图像风格指南

## 格式

1. 颜色值少于256色的图片使用png-8格式
2. 颜色值丰富的图片使用jpg格式，并保存合理的压缩比，60% 至 80%
3. Alpha 通道图片使用png 32位格式
4. 动画图片使用gif格式

## 导出
PS导出图片时，不要选择带有metadata信息

## 压缩
jpg是有损压缩，在视觉可接受的范围内压缩到最低值，一般60%压缩比效果较好。
png图片可以使用pngout工具进行压缩。

## 单张图片字节
尽量避免过大图片，控制单张图片字节数，暂定100k因内，保证加载速度。

## CSS Sprites
小图片需要合并之后使用，颜色相近的图片合并在一起，使用png 8位索引透明存储。
保留合并图的源文件PSD，便于修改。