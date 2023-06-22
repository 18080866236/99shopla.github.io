---
abbrlink: ''
categories:
- - 使用教程
date: '2023-06-22T20:19:20.827726+08:00'
tags:
- AI智能
- AI绘画
- AI绘图
title: stable diffusion [ControlNet1.1使用分享]
updated: 2023-6-22T20:19:21.709+8:0
---
# [ControlNet1.1使用分享]

![Controlnet的使用-2048x1152.jpg](https://s2.loli.net/2023/06/22/48ZWREtiKCe6wDL.jpg)

1、Controlnet的底层逻辑：

> 首先我们要明白Controlnet开发的目的，之前我们跟小伙伴分享过了stable diffusion的底层逻辑，它的底层逻辑就是**==把我们脑海里面的画面具现出来==**，但是有些小伙伴对这个画面感可能不是很好去想象，突然让我们在脑海里面想象出一副画还是有点困难的，而且有时候我们想做出跟我们想象中差不多的图像，需要在提示词和参数部分反复调整，这种方案对我们来说不好去操控，所以Controlnet的出现就是为了把我们脑海里的画面具现化，辅助我们把这个轮廓提取出来，然后再通过Stable Diffusion去把它实现出来，比如：提**==取人物的轮廓、骨架、划分区域、提升分辨率==**等等，然后再从而达到能够更为**==精准控制==**图片的结果，也就相当于在一个参考物上去做出我们想要的效果。

2、官方项目地址：【[点击进入](https://github.com/Mikubill/sd-webui-controlnet)】

3、相关模型下载：【[点击进入](https://huggingface.co/lllyasviel/ControlNet-v1-1/tree/main)】

* 模型存放路径：**==\\stable-diffusion-webui-dev\\extensions\\sd-webui-controlnet-main\\models==**
* **==注：==**如果有些预处理第一次运行，需要下载资料，这个时候下载资料很容易不成功，如果下载不成功再打开就会出错，解决办法去到此文件夹，根据命令窗口的目录删掉文件，再次运行即可重新下载

```
\stable-diffusion-webui-dev\extensions\sd-webui-controlnet-main\annotator\downloads\Copy
```

![](https://naiyou001.tk/wp-content/uploads/2023/05/image-1024x138.png)

4、Controlnet参数：

* 模式：启用/Enable、低显存模式/Low VRAM、完美像素/Pixel Perfect、允许预览/Allow Preview（**==注意：这里要勾选启用，Controlnet才能生效，其他的根据自己的实际情况来选择==**）
* 预处理/Preprocessor和模型/Model要选择一样的
* 控制权重/Control Weight：简单的理解就是Controlnet的权重和Stable Diffusion的权重比例，1是正常权重，跟提示词的权重意思是一样的。例如：设为0，意思就是图片生成跟Stable Diffusion有关，跟Controlnet无关
* Starting Control Step和Ending Control Step这两个的作用大家可以这样去理解：Controlnet从什么时候开始发挥作用，举个例子：开始设为0.5，结束设为1，这里的意思就是0——0.5这个时间段内，Stable Diffusion会随机生成图片，在0.5——1的这个时间段内，开始根据Controlnet来生成图片，所以结果就是两张图片叠加
* Preprocessor resolution：预处理器分辨率，默认 512，数值越高线条越精细，数值越低线条越粗糙

5、各种模型用法参考：【[进入了解](https://zhuanlan.zhihu.com/p/626659571)】

![00014-2-1258x2048.png](https://s2.loli.net/2023/06/22/YxH4M6Dsh5cSyJm.png)
