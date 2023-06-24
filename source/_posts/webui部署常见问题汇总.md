---
abbrlink: 479a
categories:
  - - 免费资源
  - - 基础教程
date: '2023-06-23T19:05:29.906173+08:00'
tags:
  - AI智能
title: webui部署常见问题汇总
updated: '2023-6-23T19:5:30.634+8:0'
---
# webui部署常见问题汇总

## 问1：执行结果是一直到读取模型打开web页面都正常，然后点画图的时候进度不动，提示Missing system database file: gfx1030_14.kdb Performance may degrade.

第一次跑图会自动编译miopen，稍等一下一个就会开始跑图了。

## 问2：成功在lxc下安装，就是在终端执行代码后关了终端，网页端还在继续，linux小白，请问如何返回终端查看进程，退出程序该如何退出

lxc应该是一种容器吧，关闭终端不能容器还在运行的，停掉容器应该就停了。可以每次关闭终端前按Ctrl+c就可以关闭程序了。

## 问3：请问一下虚拟化环境下装显卡驱动是识别不到显卡吗，我这边一直提示gpu not found。

虚拟化除非可以直通显卡，比如esxi或pve可以，其他的不行。VM workstation宿主型虚拟化，为了流畅会把显卡虚拟化成SVGA显卡，是不能跑图的。

## 问4：请问出现Running on local URL:http://127.0.0.1:6006  To create a public link,set 'share=true' in 'launch'之后应该怎么操作？需要手动打开浏览器吗？浏览器在哪里呢？

如果Linux有图形界面就打开浏览器就可以，如果需要其他设备链接需要在start.sh args里加--listen

## 问5：xformers是不是不支持A卡？

是的，这是n卡才可以使用的。

## 问6：对linux环境有要求吗，我都被python3.8和3.10搞得人都傻了，到底要用哪个？

部署包没有要求，但显卡驱动有要求，一般要与驱动相匹配的Ubuntu系统，amd的部署包是python3.8的，3.8与amd显卡好像兼容性更高一些，如果是n卡直接3.10就行

## 问7：我看教程里都是连带着装了torch rocm 还有miopen，这些也是amdgpu驱动的一部分吗？

torch不是其他的是，部署包自带一个rocm5.1.1+1.13的torch,如果运行webui不报cuda错，那就代表torch和显卡链接正常。

## 问8：自带rocm和torch的话，我在装显卡驱动这一步就装了是不是会有影响？

不会的，部署包的环境在conda虚拟环境中，不会对系统的产生影响。

## 问9：AssertionError: Torch is not able to use GPU; add --skip-torch-cuda-test to COMMANDLINE_ARGS variable to disable this check，不知道怎么处理了_(:з」∠)_

这是没有支持的显卡或是显卡torch和显卡驱动不匹配导致的。

## 问10：是不是也是在webui文件夹下进入终端并且进入（sdwebui）虚拟环境后再输入该指令，还是进入终端后（base）就直接执行指令？

需要切到（sd-webui）环境下运行。

## 问11：什么配置可以运行webui？

CPU：2核以上；内存：32GB（包括SWAP交换空间，以7GB模型运行为标准）至少需要8GB（不包括SWAP交换）；一张支持cuda或rocm的显卡，显存8GB及以上（可以训练），最低4GB（只能小分辨率跑图）。

## 问12：这个用a卡能调用全部显存吗？

由于pytorch本身要占用一些显存，使用这个其实都可以全部调用。

## 问13：这个部署是可以自动更新的吗?和其他大佬做的整合包有什么不同？

启动时是不会更新的，可以使用脚本或手动gitpull更新，没有进行魔改，其实和其他没什么区别。

## 问14：这个是要自己安装插件吗?能否出个详细教程。

插件已经自带了一些，一般是不用自己再装了，如果需要的插件没有，可以按照下面方法下载使用：

浏览器打开这个链接：

```
https://raw.githubusercontent.com/wiki/AUTOMATIC1111/stable-diffusion-webui/Extensions-index.md
```

按Ctrl+F在浏览器中搜索插件的名字，复制url的那个地址，然后在webui的extensions文件夹下，执行：

```
git clone https://github.com/Mikubill/sd-webui-controlnet.git
```

重启webui

## 问15：请问linux必须是配备了显卡的gpu计算型实例么？

是的  需要有GPU  镜像也要选带GPU的。一般会自带驱动。

## 问16：我想知道如何接上公网，然后可以在手机里生成呢，这个up知道吗？

有公网ip的话 start.sh args里加个--listen 就行，没有 就加--share ，--gradio-auth 用户名:密码 是设置webui的用户名和密码。

## 问17：我用你的整合包，然后我自己之前装的都是分辨率一调大就自动关机6750xt的显卡只能跑512*768以下的不然就自动关机，有啥办法吗？12g的显存

有的a卡就是这样跑不了太大的图的，而且可能驱动有bug，会超功率跑关机，目前是没有办法的。

## 问18：请问一下您的stable diffusion部署教程中，pip install -r stable-diffusion-webui/requirements_versions.txt 这个安装依赖命令输入后提示找不到此路径，是什么问题啊？

一般是没有在webui文件夹下，终端先cd到stable-diffusion-webui下，再运行上面这条命令就行了。

## 问19：这个webui安装完，相当于只是做了一个前端页面？还得导入模型后，才能正常使用文字生成图片吗?

是的，需要导入模型，命令：

```
mv {你的模型文件名.ckpt} stable-diffusion-webui/models/Stable-diffusion/
mv {你的模型文件名.safetensors} stable-diffusion-webui/models/Stable-diffusion/
mv {你的vae文件名.vae.ckpt} stable-diffusion-webui/models/VAE/
mv {你的lora模型文件名.ckpt} stable-diffusion-webui/models/lora/
mv {你的lora模型文件名.safetensors} stable-diffusion-webui/models/lora/
```

## 问20：还有个问题，我的显卡是6900xt，然后这边显示gfx1030，正常吗？

6900xt要模拟成gfx1030运行，这是正常的。

## 问21：问下这些大部分是用novalAI的模型自己训练出来的么，比如civitai这个，好像novalai也有一个7g左右的完整模型。

是的 一般二次元一般都是novel的底膜，三次元一般sd1.5 或其他版本的。

## 问22：服务器上有8张卡，可以选具体哪些卡跑吗？

可以，指定其中某张显卡来跑图，在start.sh加"--device-id {显卡id}"参数，显卡id是需要跑图的显卡编号，webui跑图现在只能一张显卡跑.

## 问23：我在扩展那一栏加载时，它显示建立安全链接失败，如何解决呀?

浏览器打开这个链接：

```
https://raw.githubusercontent.com/wiki/AUTOMATIC1111/stable-diffusion-webui/Extensions-index.md
```


## 问24：我遇到一个问题，我想试试不同种类的底模，文件也放到对应路径models\Stable-diffusion，但是输入tag开始绘图后控制台经常提示找不到模型文件，然后自动调用另一个底模，想问问这种情况怎么解决？

好像是因为直接复制tag导致的，会把作者使用的模型也复制过来，本地找不到tag中的模型就用其他已存在的替代了。

## 问25：请问一下，我在autodl上安装一键包，如果重新安装conda环境，能正常安装，但是这个实例在这次关闭之后就会显示Jupiterlab发生错误，再也打不开了，不重新安装conda环境，解压cache包的时候就会显示找不到这个文件，之后无法conda activate，请问该如何解决呢？

使用一键包覆盖conda的话会导致autodl的Jupiterlab打不开，可以在运行部署包脚本时在“是否覆盖conda”选否，显示部署完成后先执行conda init命令再bash命令应该就正常了

## 问26：好像版本不兼容咋办呢？

WARNING【XFORMERS】: xFormers can't load C++/CUDA extensions. xFormers was built for:PyTorch 1.13.1+rocm5.2 with CUDA None (you have 1.13.1+rocm5.2) Python  3.10.9 (you have 3.10.9) Please reinstall xformers (seehttps://github.com/facebookresearch/xformers#installing-xformers)
A卡是不支持xformers的。

## 问27：win系统，一键安装sd-webui install.sh 输入了1 然后回车 窗口就闪退了.... 请问是什么情况呀？

部署包是针对linux的，win的话肯定会闪退啊

## 问28：这个是自动安装miniconda然后建立了一个conda虚拟环境吗？整合包里有dreambooth吗？最近从github原仓库安装webui要疯了，装dreambooth插件好多依赖版本对不上。

是的，已经带了环境和dreambooth插件。

## 问29：我刚装了你的包。但是我用dreambooth的时候页面上的学习率明明是0.000002，但在后台打印的学习率是0.002，你有这个现象吗，包括训练的进度条那里显示的学习率也是0.002

这个可能是插件的bug，可以试试使用git pull更新一下插件。
