---
abbrlink: b5e6
categories:
  - - 免费资源
  - - 基础教程
date: '2023-06-23T17:18:24.434059+08:00'
tags:
  - AI智能
  - AI绘画
  - AI绘图
title: SD WEBUI 基础教程（二）
updated: '2023-6-23T20:12:12.191+8:0'
---
# 给新人的sd webui安装教程

## prompt提示词结构

一个好的prompt应该是详细而具体的。比如，如果你只输入"cat"（猫），生成的图片结果会非常广泛。但是如果你能够缩小范围，例如限定猫的品种、颜色甚至姿势，那么生成的图片就会更接近你的预期。通过提供更具体的描述，可以缩小模型的预测范围，从而更容易得到你想要的结果。
那么如何尽可能地缩小模型的预测范围？或者说，如何撰写一个详细而具体的提示？一个好的提示应该具备以下要素：

1. 主体：明确指出所期望生成图像的主要内容，例如动物、植物或其他物品。包括主体动作、表情、眼睛状态、服饰、装饰物等，以丰富主体的特征。
2. 背景：描述主体所处的环境，包括室内或室外，光线条件等，以帮助模型更好地理解所期望的情境。
3. 构图：包括景别、拍摄角度、景深等，以控制图像的组成和视角。
4. 风格：指定所期望的图像风格，例如插画、卡通、水彩、3D、超现实、复古等，同时考虑画面明暗、对比度等视觉效果。
5. 媒介：说明绘画使用的特定材料或媒介，例如油画、电子绘画、铅笔画等。
6. 画面清晰度：使用能提高画面锐度的关键词，避免模糊的描述。
7. 灯光效果：指定所期望的灯光效果，例如侧光、逆光、环境光等，以增强图像的氛围和视觉效果。
8. 颜色氛围：输入合适的颜色关键词，可以改变整个画面的色调
   通过综合运用这些要素，你可以撰写一个详细而具体的提示词，从而更精确地指导模型生成符合你期望的图像。刚开始接触绘画的新人先按照这个模板撰写提示词，融会贯通之后就可以自由改变提示词了。

## 举个例子

### 1、主体

主体（Subject）即是你希望在图像中呈现的主要内容。然而，许多新人常犯的一个错误是未能对主体进行足够详尽的描述。
比如，如果你想要生成一个精灵的图片，许多初次接触AI绘画的新手可能会这样写：
Prompt: an elf (一个精灵)
这样的表述过于简洁，给模型圈定的生成范围还很庞大。这个精灵是在坐着还是站着？表情是怎样的？穿着怎样的衣服？这些都是我们需要详细描述清楚的，否则范围就会很广，生成的图片内容也会变化很大。
因此，为了更准确地指导模型生成预期的图像，我们就需要提供更具体的描述。例如：
模型：Realistic Vision V2.0
Prompt: a beautiful girl as an enchanting forest elf sitting on a tree, serene expression, wearing a flowing green dress with intricate details, (一个如迷人的森林精灵般的美丽女孩坐在一棵树上，表情安宁，穿着一件带有复杂细节的飘逸绿色连衣裙)

![05c2db0f0cf3d7cae14c17bbb71fbe096963a9a3.jpg](https://s2.loli.net/2023/06/23/yb6irZotHdPIDMf.jpg)

### 2、背景

主体描述已经完善，但是我们还需要提供主体所处的环境信息，以便更好地指导模型生成图像。通过输入环境关键词就可以进一步限制图像生成的范围。
因此，主体所属的环境也是需要进行描述的。将地点，时间，环境元素，天气，光线条件等等都可以输入进prompt来影响背景效果。
在这个例子中，精灵是在树林里的，当然也可以在其它地方，可以结合你自己的想象力去创造更新颖的画面。在这里我就将环境设定在树林里。
Prompt：a beautiful girl as an enchanting forest elf sitting on a tree, serene expression, wearing a flowing green dress with intricate details, forest dominated by towering trees, sunny, warm sunlight, (一个如迷人的森林精灵般的美丽女孩坐在一棵树上，表情安宁，穿着一件带有复杂细节的飘逸绿色连衣裙，参天大树构成的森林，晴天，温暖的阳光)

![56f3e0550923dd54acbd8ca59409b3de9e824817.jpg](https://s2.loli.net/2023/06/23/vrGp7MLCxob38qK.jpg)

### 3、构图

构图包括景别、拍摄角度、景深等等。
景别即人物占画面比例的大小，比如full shot（全景）能够显示被拍摄对象的整个身体，包括头到脚的范围。full shot更通俗的表达式full body，即全身。需要注意的是，有些模型不能识别full shot，需要尝试使用full body才能产生效果。相似的，upper body或者half body则指的是上半身，即腰部以上。更多的关键词，下期我再专门总结一篇。
从上面生成的图片来看，很多都是上半身的图像，但我更想要全身的图像，那么我继续添加关键词：
Prompt：a beautiful girl as an enchanting forest elf sitting on a tree, serene expression, wearing a flowing green dress with intricate details, forest dominated by towering trees, sunny, warm sunlight, full body, (一个如迷人的森林精灵般的美丽女孩坐在一棵树上，表情安宁，穿着一件带有复杂细节的飘逸绿色连衣裙，参天大树构成的森林，晴天，温暖的阳光，全身像)

![ac4d62ee76094b3661503020e6cc7cd98f109d1b.jpg](https://s2.loli.net/2023/06/23/Tb8BpPJeIa9CKyn.jpg)

可以发现，当我添加full body之后，确实可以生成全身像，但是能发现一个明确缺点，即容易产生畸形人物，这在半身像中却是不常见的。生成全身像会导致任务畸形是许多模型共同的缺点，这可能是因为训练模型使用的材料缺乏这类图片的原因。

### 4、风格

设定风格能够对图片产生非常大的影响，不同的风格能够给人不同的感觉，可以使用的关键词有很多。例如fantasy（幻想虚拟风格）、hyperrealistic（超现实主义的）、Modernist（现代主义的）、illustration（插画）等等。这里分享一下小技巧，一个能够准确且有效的改变画面风格的方法是加入特定的画家的名字。比如我加入Alan Lee，他是一个插画家：
Prompt: a beautiful girl as an enchanting forest elf sitting on a tree, serene expression, wearing a flowing green dress with intricate details, forest dominated by towering trees, sunny, warm sunlight, full body, by Alan Lee, fantasy, hyperrealistic, (一个如迷人的森林精灵般的美丽女孩坐在一棵树上，表情安宁，穿着一件带有复杂细节的飘逸绿色连衣裙，参天大树构成的森林，晴天，温暖的阳光，全身像，Alan Lee画的，幻想、超现实的)

![3a6660167f3e6709dd256f327ec79f3df9dc5533.jpg](https://s2.loli.net/2023/06/23/yBtJsPjX27lrWYR.jpg)

可以发现，风格的确发生了一些变化，已经出现了Alan Lee的绘画风格了。效果不是很明显，但是没关系，先用着。

### 5、媒介

媒介即绘画使用的特定材料，例如油画、电子绘画、铅笔画、水彩、墨水等等。
不同媒介对画面的质感能够产生显著的影响，比如：油画能够使整个画面产生特殊的纹理；胶片则会给画面添加颗粒感；
我觉得这个水彩效果对这个主题来说更合适，所以我添加了watercolor（水彩）
Prompt：a beautiful girl as an enchanting forest elf sitting on a tree, serene expression, wearing a flowing green dress with intricate details, forest dominated by towering trees, sunny, warm sunlight, full body, by Alan Lee, fantasy, hyperrealistic, watercolor, (一个如迷人的森林精灵般的美丽女孩坐在一棵树上，表情安宁，穿着一件带有复杂细节的飘逸绿色连衣裙，参天大树构成的森林，晴天，温暖的阳光，全身像，Alan Lee画的，幻想的，超现实的，水彩)

![b8ff3ccbd1c8a786c3a159c32209c93d72cf5051.jpg](https://s2.loli.net/2023/06/23/mANihbfJCs4cWIE.jpg)

可以发现，添加watercolor关键词已经使画面产生了水彩的效果。

### 6、画面清晰度

使用能提高画面锐度的关键词，避免产生模糊的图片。highly detailed和sharp focus是很好的关键词
Prompt：a beautiful girl as an enchanting forest elf sitting on a tree, serene expression, wearing a flowing green dress with intricate details, forest dominated by towering trees, sunny, warm sunlight, full body, by Alan Lee, fantasy, hyperrealistic, watercolor, sharp focus, highly detailed, (一个如迷人的森林精灵般的美丽女孩坐在一棵树上，表情安宁，穿着一件带有复杂细节的飘逸绿色连衣裙，参天大树构成的森林，晴天，温暖的阳光，全身像，Alan Lee画的，幻想的，超现实的，水彩，锐利聚焦、高度详细)

![601a0650f3deb48f6c08bc13b51f3a292ff578f8.jpg](https://s2.loli.net/2023/06/23/4ieLCoNhjmSYcQf.jpg)

### 7、光效

指定所期望的光线效果，例如侧光、逆光、环境光等，以增强图像的氛围和视觉效果。
这里我添加了cinematic lighting（电影灯光）
Prompt：a beautiful girl as an enchanting forest elf sitting on a tree, serene expression, wearing a flowing green dress with intricate details, forest dominated by towering trees, sunny, warm sunlight, full body, by Alan Lee, fantasy, hyperrealistic, watercolor, sharp focus, highly detailed, cinematic lighting, high contrast(一个如迷人的森林精灵般的美丽女孩坐在一棵树上，表情安宁，穿着一件带有复杂细节的飘逸绿色连衣裙，参天大树构成的森林，晴天，温暖的阳光，全身像，Alan Lee画的，幻想的，超现实的，水彩，锐利聚焦，高度详细，电影灯光，高对比)

![601a0650f3deb48f6c08bc13b51f3a292ff578f8.jpg](https://s2.loli.net/2023/06/23/4ieLCoNhjmSYcQf.jpg)

### 8、颜色

整个画面只有绿色，我觉得有些单调，我还想添加更多颜色进去，比如金色。
Prompt：a beautiful girl as an enchanting forest elf sitting on a tree, serene expression, wearing a flowing green dress with intricate details, forest dominated by towering trees, sunny, warm sunlight, full body, by Alan Lee, fantasy, hyperrealistic, watercolor, sharp focus, highly detailed, cinematic lighting, high contrast, radiant gold color vibe, (一个如迷人的森林精灵般的美丽女孩坐在一棵树上，表情安宁，穿着一件带有复杂细节的飘逸绿色连衣裙，参天大树构成的森林，晴天，温暖的阳光，全身像，Alan Lee画的，幻想的，超现实的，水彩，锐利聚焦，高度详细，电影灯光，高对比，闪耀的金黄色颜色氛围)

![9c099000213fb80eb0087d1a73d12f2ebb389400.jpg](https://s2.loli.net/2023/06/23/jY1CRdXyHnT45IL.jpg)

### 反向关键词

如果你才刚开始接触AI绘画，还不太懂怎么调整反向关键词，那么就先使用下面这个通用的negative prompt吧
negative prompt：ugly, tiling, poorly drawn hands, poorly drawn feet, poorly drawn face, out of frame, extra limbs, disfigured, deformed, body out of frame, bad anatomy, watermark, signature, cut off, low contrast, underexposed, overexposed, bad art, beginner, amateur, distorted face, blurry, draft, grainy
后面掌握了反向关键词再自己调整。

### 总结

可能你已经注意到，即使我只是使用了很少的关键词，但是生成的图片效果也已经很不错了。
所以在写prompt的时候，需要注意，你不需要包含以上所有类别的关键词，你可以挑选其中几种搭配使用。另外，关键词顺序可以自己更换，顺序越靠前，权重越高，就越大概率生成符合该关键词的结果。
将关键词分类的意义是方便记忆。当在你需要生成某些特定图片的时候，你就知道应该从哪些方面去限定生成的范围，这样就可以生成更接近你预期的图片。
入门之后自己多摸索摸索，keep creative！！！
