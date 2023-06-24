---
abbrlink: '2882'
categories:
  - - 免费资源
  - - 基础教程
date: ''
tags:
  - AI智能
title: SD WEBUI 常见错误汇总
updated: '2023-6-23T18:31:8.296+8:0'
---
# 收集的一些运行SDWEBUI常见错误汇总

## 启动SD-WebUI时产生错误:+无找到启动所需的Git+组件

这个错误提示通常是由于缺少Git组件导致的。您可以按照以下步骤来解决此问题：打开SD-WebUI所在的目录，并确保其中包含Git组件。如果您没有安装Git组件，请从Git官网（https://git-scm.com/downloads）下载并安装它。如果您已经安装了Git组件，则可以尝试将其添加到系统路径中。在Windows系统中，您可以按照以下步骤进行操作：右键单击“我的电脑”或“本机”，然后选择“属性”。在左侧的面板中，单击“高级系统设置”。在“系统属性”对话框中，单击“环境变量”按钮。在“系统变量”中，找到“Path”变量，并单击“编辑”按钮。在“编辑环境变量”对话框中，单击“新建”按钮，并添加Git组件所在的路径。单击“确定”按钮，关闭所有对话框。重新启动SD-WebUI，看看是否仍然出现相同的错误提示。如果您还是无法解决问题，请考虑重新安装SD-WebUI，并确保您已经正确安装了Git组件。

## (sd webui)报错mat1 and mat2 shapes cannot be multiplied的处理

在用webui转换游戏图标的风格时，使用controlnet固定图标样式，运行报错：RuntimeError: mat1 and mat2 shapes cannot be multiplied (154x1024 and 768x320)，报错说的是pytorch在进行矩阵乘法运算时，第一个矩阵的行数与第二矩阵的列数不相等，无法作乘法。

解决方法
一头雾水，查了github，google,百度都未找到解决方法，为了后续人少踩坑，把写问题记一下。当更换当前大模型后，再用同样的参数画图，然后就没报错了。
所以，解决方法是：更换大模型！
声明：不一定对，仅供参考，不喜勿喷。

## 127.0.0.1:7860拒绝访问

变数太多，提供几个可能解决方案：

1. 请确认开启网址终端是否还开着，并有显示Running on Local URL : http://127.0.0.1:7860的字样
2. 网址改用http://localhost:7860访问
3. 用记事本开启C:\\Windows\\System32\\drivers\\etc\\hosts，确认里面有无127.0.0.1 localhost这一行。
4. 请确认电脑没有执行其他程序，导致端口占用或存在冲突。
5. 开启CMD终端，执行ipconfig /flushdns指令刷新DNS纪录
6. 暂时关闭防火墙

## RuntimeError: unexpected EOF, expected more bytes. The file might be corrupted.

可能是文件毁损，删除这些文件夹：stable-diffusion-webui\\models\\GFPGAN、stable-diffusion-webui\\models\\Codeformer、stable-diffusion-webui\\repositories\\CodeForme

然后重启SD WebUI让它重新下载脸部模型。

## modules.devices.NansException: A tensor with all NaNs was produced in Unet.

此错误可能会发生在含有VAE的模型算图的时候，会导致算出来结果是黑图。

开启webui-user.bat，COMMANDLINE\_ARGS后面额外加上--no-half --no-haf-vae引数。

## AssertionError: extension access disabled because of commandline flags

webui-user.bat(或webui-user.sh)的COMMANDLINE\_ARGS有加入--share或--listen引数就会无法从网页安装扩展功能，这是出于安全性考虑。

你可以：

1. 将该引数删除。
2. 额外加上--enable-insecure-extension-access引数试试。
3. 改用Git clone的方式来安装扩展功能：关闭SD WebUI。于stable-diffusion-webui\\extensions资料夹开启终端，输入git clone <仓库地址>下载扩展功能。

## fatal: unable to access Recv failure: Connection was reset

网路问题，访问Github的延迟，导致相关文件下载失败。

## **No module named pip**

于stable-diffusion-webui文件夹，右键＋SHIFT，开启终端，执行python3 -m ensurepip安装pip

然后删除venv文件夹，重新执行webui-user.bat

## RuntimeError: CUDA Out of memory

显卡的VRAM不足。Stable Diffusion WebUI的显示卡VRAM最低要求为4GB，要无压力的玩建议8GB以上。

开启webui-user.bat，在COMMANDLINE\_ARGS后面加入--mdevram或--lowvram引数，降低VRAM使用量。如果还是在算图时出现此讯息，建议降低算图的解析度，或是买张更好的显示卡，或是改用Google Colab。

## 扩展功能导致的错误

有时除了Stable Diffusion WebUI本身问题外，也有可能是你安装的扩充功能导致出错。

要Debug请尝试删除stable-diffusion-webui\\extensions下的某个新安装的扩展功能文件夹，再尝试启动SD WebUI。

## 提示:检测到SD-WebUI 进程退出状态不正常，建议前往疑难解答页面扫描错误记录或寻求其他帮助。

方法 1、

git出问题了，不要管了，用这个方法重装
我原先软件本体代码就是下的zip解压的，会出现问题。GIT的hash散列值会是none，
你们应该装了GIT吧，建个新文件夹，在新建文件夹界面点地址栏输入cmd，打开cmd后输入
git clone [http://github.com/AUTOMATIC1111/stable-diffusion-webui.git](http://jump2.bdimg.com/safecheck/index?url=rN3wPs8te/r8jfr8YhogjfUWFoMgIRa8DFG/XFAIQTAB/czLV3s78yUaNGxmyGJ34ySHx5raF9/GR4ncXUE2RSQJxFQ8FKqzy1KfUEdkPsP81hnVHhB8OZq5GKXvE2RIQz6PXpFQamF+4pkc674n/SPfBnJmIvV7CuPHU/2lzfuvRUaqI1zgng3QlbumM9NVMDxm7iZ2BjQ=)
直接下一份新的本体程序，其它操作照常。还是不行的话别问我了，我也不知。

方法2、

去检查一下你们windows的cmd.exe文件是不是还在system32下面，如果还在执行一下 B启动报错、卡加载修复v3.bat 然后就能好了。如果被移动到SysWOW64下，那就复制一个回原来的地方，其它一样。

## sdwebui换去其他盘就启动不了

解决方法。
1、打开SDWebUI的安装目录，找到config文件夹，打开config文件夹，找到config.json文件。
2、用文本编辑器打开config.json文件，找到其中的root字段，将其值修改为当前使用的盘符路径。
3、保存修改后的config.json文件，并重新启动SDWebUI。

## SD-WebUI（黑图）怎么解决？

SD-WebUl（黑图）通常是由于浏览器缓存或者网络问题导致的。你可以尝试以下方法来解决这个问题：1. 清除浏览器缓存：在浏览器中按下Ctrl + Shift + Delete键，打开清除浏览器数据的选项，选择清除缓存，然后重新加载网页。2. 检查网络连接：确保你的网络连接正常，可以尝试重新连接网络或者重启路由器。3. 更换浏览器：如果以上方法都无法解决问题，可以尝试更换浏览器，或者升级浏览器版本。4. 检查网站是否正常：如果以上方法都无法解决问题，可能是网站本身出现了问题，你可以尝试等待一段时间，或者联系网站管理员寻求帮助。
