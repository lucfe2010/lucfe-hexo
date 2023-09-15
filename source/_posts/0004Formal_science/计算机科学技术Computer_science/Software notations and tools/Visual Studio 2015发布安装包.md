# VS2015发布安装包1

编译工程

编写并调试你的工程，保证工程能编译运行

2
查看框架

项目   ->   xx属性(P)...   ->   应用程序

查看目标框架（修改后请重新编译工程以确保可行性）

![Alt text](/assets/images/VS2015%E5%8F%91%E5%B8%83%E5%AE%89%E8%A3%85%E5%8C%85/image.png)

生成

生成   ->   配置选择release
![Alt text](/assets/images/VS2015%E5%8F%91%E5%B8%83%E5%AE%89%E8%A3%85%E5%8C%85/image-1.png)

创建数字签名证书（已有可跳过此步）

使用OFFICE工具下的VBA项目的数字证书工具生成一个证书

* 或自行搜索数字证书生成方法

![Alt text](/assets/images/VS2015%E5%8F%91%E5%B8%83%E5%AE%89%E8%A3%85%E5%8C%85/image-2.png)

签名

签名   ->   选中为clickonce清单签名   ->   从存储区选择

![Alt text](/assets/images/VS2015%E5%8F%91%E5%B8%83%E5%AE%89%E8%A3%85%E5%8C%85/image-3.png)

发布准备

发布   ->   发布文件夹位置（生成的安装包的位置）

发布   ->   应用程序文件（查看需要打包的文件）

发布   ->   系统必备组件（选择需要安装的必备组件）

发布   ->   选项（设置发布语言，发行者名称等）

发布   ->   发布版本（就是版本号）

![Alt text](/assets/images/VS2015%E5%8F%91%E5%B8%83%E5%AE%89%E8%A3%85%E5%8C%85/image-4.png)

准备系统必备组件（以 .NET Framework 4.5.2为例）

发布   ->   系统必备组件

选中  创建用于安装系统必备组件的安装程序

选中  Microsoft .NET Framework 4.5.2 (x86 和 x64)

选中  从与我的应用程序相同的位置下载系统必备组件

![Alt text](/assets/images/VS2015%E5%8F%91%E5%B8%83%E5%AE%89%E8%A3%85%E5%8C%85/image-5.png)

准备系统必备组件安装包（以 .NET Framework 4.5.2为例）

点击立即发布

在错误列表中查看缺失的安装包

从网上下载对应的离线安装包

微软下载<https://www.microsoft.com/en-us/search/DownloadResults.aspx?FORM=DLC&ftapplicableproducts=%5e%22AllDownloads%22&sortby=+weight&q=developer+software>

![Alt text](/assets/images/VS2015%E5%8F%91%E5%B8%83%E5%AE%89%E8%A3%85%E5%8C%85/image-6.png)

准备系统必备组件安装包（以 .NET Framework 4.5.2为例）

离线安装包下载完后

把英文版安装包（ENU）拷贝到  %VS安装目录%\SDK\Bootstrapper\Packages\DotNetFX452\

把语言包（CNS等）拷贝到  %VS安装目录%\SDK\Bootstrapper\Packages\DotNetFX452\zh-Hans（或其他对应语言）\

  *默认VS安装目录为 C:\Program Files (x86)\Microsoft Visual Studio 14.0

  ![Alt text](/assets/images/VS2015%E5%8F%91%E5%B8%83%E5%AE%89%E8%A3%85%E5%8C%85/image-7.png)

准备系统必备组件安装包（以 .NET Framework 4.5.2为例）

再次点击立即发布

如果有以下警告，可参照下一步

也可以忽略警告，跳过下一步

![Alt text](/assets/images/VS2015%E5%8F%91%E5%B8%83%E5%AE%89%E8%A3%85%E5%8C%85/image-8.png)

特性值不匹配警告（以 .NET Framework 4.5.2为例）

右键英文版安装包   ->   属性   ->   数字签名   ->   选中列表   ->   详细信息   ->   查看证书   ->   详细信息   ->   公钥   ->   复制内容到文本文档并删除空格

右键编辑英文版安装包位置下  %VS安装目录%\SDK\Bootstrapper\Packages\DotNetFX452\product.xml

用上述公钥内容替换掉PublicKey的值

中文语言包安装包操作方法同上

![Alt text](/assets/images/VS2015%E5%8F%91%E5%B8%83%E5%AE%89%E8%A3%85%E5%8C%85/image-9.png)

![Alt text](/assets/images/VS2015%E5%8F%91%E5%B8%83%E5%AE%89%E8%A3%85%E5%8C%85/image-10.png)

发布

点击立即发布

发布成功后，你就可以把整个发布文件夹打包发给别人安装了

* Application Files 文件夹内存放有所有历史版本的信息，你可以把旧版本的文件夹删除，只保留最新的版本文件夹

* dotnetfx452 文件夹内存放的是系统必备组件安装包

* setup.exe 就是安装程序

![Alt text](/assets/images/VS2015%E5%8F%91%E5%B8%83%E5%AE%89%E8%A3%85%E5%8C%85/image-11.png)
