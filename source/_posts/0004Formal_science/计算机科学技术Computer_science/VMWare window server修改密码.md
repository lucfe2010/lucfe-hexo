# VMWare window server修改密码

VMWare——window server 2008/2012 administrator 密码忘记，设置重置密码
用VMWare安装window server 2008或者2012忘记密码后，想要修改密码满麻烦的。

以下过程是我成功修改密码的过程：

1.首先需要需要链接一个ISO文件

![Alt text](</assets/images/VMWare window server修改密码/image.png>)

需要特别注意把“启用连接”勾上，这个地方坑了我好长时间。不勾上，系统启动没办法CD-ROM Drive进入的。

2.关闭虚拟机。以下面的方式打开虚拟机：

![Alt text](</assets/images/VMWare window server修改密码/image-1.png>)

3进入BIOS界面—>选择Boot:确保启动方式是以CD-ROM Driver

![Alt text](</assets/images/VMWare window server修改密码/image-2.png>)

4.然后重新启动。重新启动后，会进入到安装系统界面。

![Alt text](</assets/images/VMWare window server修改密码/image-3.png>)

5.点击下一步，在下一个界面左下面，第一行：Repair your computer（修复你的计算机），点击这个；

![Alt text](</assets/images/VMWare window server修改密码/image-4.png>)

6.之后会进入到选择界面，选择Troubleshoot（故障排除）：

![Alt text](</assets/images/VMWare window server修改密码/image-5.png>)

7.之后新的界面Advanced options（高级选项）,选择Command Prompt（命令提示）选项：

![Alt text](</assets/images/VMWare window server修改密码/image-6.png>)

8.这个时候会出现一个命令提示框，需要输入以下命令：

d:（注：根据实际情况，系统盘文件放置的位置）
cd windows\system32
ren Utilman.exe Utilman.exe.old
copy cmd.exe Utilman.exe

![Alt text](</assets/images/VMWare window server修改密码/image-7.png>)

![Alt text](</assets/images/VMWare window server修改密码/image-8.png>)

8.关闭命令提示框，点击Continue(继续)；当出现欢迎界面，点击Windows key +U：

![Alt text](</assets/images/VMWare window server修改密码/image-9.png>)

9.出现命令，输入以下命令：net user administrator "new password",关闭提示框，这个时候就可以使用你新设的密码登录了。

![Alt text](</assets/images/VMWare window server修改密码/image-10.png>)

以上步骤成功修改了vmware虚拟机window server 2008/2012的密码。
