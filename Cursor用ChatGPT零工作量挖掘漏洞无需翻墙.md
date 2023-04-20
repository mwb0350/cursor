# 使用Cursor工具配合ChatGPT零工作量挖掘漏洞（无需翻墙）

2023-03-21 10:00本文共 1441 字阅读完需 6.5 分钟

> 使用Cursor工具配合ChatGPT零工作量挖掘漏洞（无需翻墙）



# 免责声明

本文中涉及到的工具、代码和软件应用仅面向合法授权的企业安全建设行为，如您需要测试本工具的可用性，请自行搭建靶机环境。
在使用本工具进行检测时，您应确保该行为符合当地的法律法规，并且已经取得了足够的授权。请勿对非授权目标进行扫描。
如您在使用本工具的过程中存在任何非法行为，您需自行承担相应后果，我们将不承担任何法律及连带责任。

# 写在前面

最近很火的一个IDE叫**cursor**，集成了GPT-3（据大佬分析，其实是GPT4的可能性很高），不用翻墙，也不用付费，我就想试试能不能用来辅助漏洞挖掘。

# 一、安装

## 1、下载

官网地址：https://www.cursor.so 支持 Mac 、Windows 和 Linux 操作系统，根据自己电脑的系统进行下载。

项目地址：https://github.com/getcursor/cursor

安装只需要点开安装包，就会开始读条，读条结束会自动在桌面生成图标并自动打开主界面，选择自己喜欢的界面风格后点击“continue”即可。

## 2、连接 Copilot 

> 建议跳过，后续使用顺利，可不填。

打开软件后，你可以在 Welcome 页面配置 Copilot ，也可以在打开之后点击右侧设置来登录 Github Copilot 。 当然这步并不是必须的，（建议跳过，后续使用顺利，可不填）因为 Cursor 内部已经整合了 GitHub Copilot 。



# 二、使用

## 1、建立一个通用POC

无论是日常渗透测试，或是src中的漏洞挖掘，一个通用的poc框架都是必要的，这样就可以在需要的时候进行简单的修改即可完成poc操作

下面简单介绍一下如何使用cursor完成一个通用的poc框架

建立一个存放poc的文件夹，然后使用Cuisor打开

![图片](https://mmbiz.qpic.cn/mmbiz_png/Uzia3lCRCbBFicq4FTWl5ib8LYCgJQbia0fDXvm7czX2TuXAqNsb4lYviaO2bzbGFtKic77W3icWHKM9PWQxI7n8ibJR4Q/640?wx_fmt=png) 

打开后，鼠标悬停在poc文件夹上，点击新建文件夹

![图片](https://mmbiz.qpic.cn/mmbiz_png/Uzia3lCRCbBFicq4FTWl5ib8LYCgJQbia0fDUiatHlQcRVf0k8jHiaVafDmRLSCANxflpRiahSGXwa1HxJlrZBIGkOAbA/640?wx_fmt=png) 

然后为新文件夹命名，这里用来分类存放poc，有些师傅需要做的渗透工作不仅限于web，所以养成这个习惯有助于系统化进行渗透测试

![图片](https://mmbiz.qpic.cn/mmbiz_png/Uzia3lCRCbBFicq4FTWl5ib8LYCgJQbia0fD1xnKb3EEafAcstSQsqj7m5t7VygnicFhJBk26euqhpjujvJE8CWgQiag/640?wx_fmt=png) 

然后新建一个文件，这里第一个文件我命名为poc_gen.py（一定要指定文件类型，否则GPT无法识别），意为通用poc，目的是编写一个简易的poc框架，实际使用的时候只需要进行简单修改即可进行测试

![图片](https://mmbiz.qpic.cn/mmbiz_png/Uzia3lCRCbBFicq4FTWl5ib8LYCgJQbia0fDNfkm3ibYNCG4AMlxBtPmVjpNXtziaxZEG7YwUAOibhj01s2yicwK8FtDOA/640?wx_fmt=png) 

之后我们按下ctrl+k来打开对话窗口，输入我们的需求

![图片](https://mmbiz.qpic.cn/mmbiz_png/Uzia3lCRCbBFicq4FTWl5ib8LYCgJQbia0fDlK2rLwldwwTQ01BNSicduFfa1ribGKtnToPtb9nSfOX0IT5kXibrDw7Pg/640?wx_fmt=png) 

然后按下回车，即可生成

![图片](https://mmbiz.qpic.cn/mmbiz_png/Uzia3lCRCbBFicq4FTWl5ib8LYCgJQbia0fDafYUD0aQbVic5icTI8vMSYVgPMKeibQXsx4zuHHiah8bAUqG6pbuRSmesw/640?wx_fmt=png) 

这里是ChatGPT自动为我们生成的代码，实测在没有科学上网的情况下可以正常使用且响应速度很快，这里20行代码只用了两三秒钟

当然我们也可使用ctrl+L进入对话模式

![图片](https://mmbiz.qpic.cn/mmbiz_png/Uzia3lCRCbBFicq4FTWl5ib8LYCgJQbia0fD0Sd7JicpKEE18He5A3oic12Am18VDT2eYfj6I0RMjK9D5HbsKrmX3CKQ/640?wx_fmt=png) 

生成的效果如下

![图片](https://mmbiz.qpic.cn/mmbiz_png/Uzia3lCRCbBFicq4FTWl5ib8LYCgJQbia0fDiaiatDnFWcOYb6OgSNRBGHfGQJbsVibZEVZtO39RfZzDwz7hRhqUzLzqw/640?wx_fmt=png) 

这样我们可以自由选择，是完全照搬GPT生成的代码还是自行优化，又或者用更清晰的方式向GPT描述需求以获取更高效的代码。

## 2、为SRC刷洞做准备

我们有了一个通用的框架，这个时候我们就要想，在注入Src的场景中，大家都是在抢分，这个时候效率很关键，因此，一些常见漏洞的框架就显得尤为重要，所以我们这里以2021年震惊整个安全圈的Log4j2远程命令执行漏洞（CVE-2021-44228）为例，要求GPT为我们生成一个poc框架

同样新建一个文件，命名为Log4j2，然后让chatgpt生成poc框架，生成完成直接点击复制按钮，再粘贴，就得到了一个poc

![图片](https://mmbiz.qpic.cn/mmbiz_png/Uzia3lCRCbBFicq4FTWl5ib8LYCgJQbia0fDKSFJmMLMpblSYZ9D8iaTtuYCHFFIfVRagWQNc7XwAt7NrAtw4uULNog/640?wx_fmt=png) 

整个过程用时不超过五秒钟，效率极高。

## 3、修改代码

在实际使用的时候，我们甚至可以按需求让GPT帮我们自动改写通用poc框架，例如我在fofa上搜索一个OA系统，随后我将结果导出为一个txt，这里我需要用到多线程、读取文本文件等功能，那么我可以直接这样描述“请为我改写poc_gen.py，使其具有读取运行目录下domain.txt文件下的IP并实现多线程poc的功能”。



![图片](https://mmbiz.qpic.cn/mmbiz_png/Uzia3lCRCbBFicq4FTWl5ib8LYCgJQbia0fDpKNOPwbWKe3pBvuxJWsHh6m6Z7ZDEkKvRu3cicnYNAskdnXiaPPQQoMg/640?wx_fmt=png) 

这里GPT给我的是改写思路，我可以要求GPT将代码整合为一整个程序

![图片](https://mmbiz.qpic.cn/mmbiz_png/Uzia3lCRCbBFicq4FTWl5ib8LYCgJQbia0fDQ1rjSyhsZYyFW1kuSDa6ln5Zq1ZHzzuXMEpCuXtjVnyPfQubLYnaNg/640?wx_fmt=png) 

然后就是简单的复制粘贴即可。

## 4、修正代码

虽然ChatGPT很强大，但是真正使用的时候难免会出现一些问题，这个时候我们就需要自行对代码进行修正，但是修改后的代码常常因为高强度的工作而出现一些错误，我们就可以用到GPT来对我们的代码进行自动修改全选代码，然后ctrl+k，输入“修正代码”并回车，这时候GPT会逐行扫描代码并给出修改的代码位置。

![图片](https://mmbiz.qpic.cn/mmbiz_png/Uzia3lCRCbBFicq4FTWl5ib8LYCgJQbia0fDqRKPqCz8mFwKAGMwaXQCFiaERJd9gvIibrU9VjAvQ1U8kUvCXBSDEVow/640?wx_fmt=png) 

效果如下图

![图片](https://mmbiz.qpic.cn/mmbiz_png/Uzia3lCRCbBFicq4FTWl5ib8LYCgJQbia0fDNDCJ7ZDiaRzJU7hHVgBonttFibOiaB1QFBqgD8mJqxFcrjylu7n76hIqg/640?wx_fmt=png) 

