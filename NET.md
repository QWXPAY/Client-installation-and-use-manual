# .NET问题解决方案

## 1.安装客户端失败的几种现象

1.1 运行客户端提示“dmprinter.exe已停止工作

1.2 安装失败提示0x80240037 或 0x0000135

1.3 直接提示“安装失败”

1.4 任务栏显示已经运行，但是打不开

1.5 运行提示“若要运行此应用程序，您必须首先安装.NET Framework的以下版本之一”

### 解决方法：

打开工具包，找到点net安装包，双击安装

![](/image/image39.png)



## 2.安装.net失败的几种现象

2.1 安装时出现灾难性故障

![图片](img\b001.png)

2.2 安装时出现oxc8000247

![图片](img\b002.png)

点开【日志文件】后，会有如下提示。

![图片](img\b003.png)



2.3 安装时发生严重错误

![图片](img\b004.png)

点开【日志文件】后，会有如下提示

![图片](img\b005.png)

### 解决方法

##### ① 给磁盘（C、E、F….）添加【UERS】组的读写权限
注意：windowXP下默认【安装】是隐藏的，打开方法：工具 > 文件夹选项 > 查看 > 取消【使用简单文件共享】功能的勾选 > 应用 > 确认。

![图片](img\b006.png)

![图片](img\b007.png)

![图片](img\b008.png)

##### ② 查看windows更新服务【wuauserv】是否正常
如服务启动时发生错误，则需要先将服务初始化

（1）开始-运行-cmd-确定

![图片](img\b009.png)

（2）在弹出的窗口中输入： net start wuauserv  回车

![图片](img\b010.png)

（3）启用windows更新服务，输入：sc config wuauser start= auto  回车

![图片](img\b011.png)

（4）启动服务，输入：net start wuauserv   回车

![图片](img\b012.png)

##### ③ 当【wuauserv】服务正常运行后，我们需先将该服务暂停
（1）开始-运行-cmd-确定

![图片](img\b013.png)

（2）在弹出的窗口输入：net stop wuauserv

![图片](img\b014.png)

（3）打开C:\windows目录 ，找到【SoftwareDistribution】文件夹，右键【重命名】，修改为【Slod】

![图片](img\b015.png)

（4）返回到CMD窗口，输入：net start wuauserv

![图片](img\b016.png)

##### ④ 修改注册表权限
开始》运行》输入：regedit 确定，然后点开  HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Internet Explorer\MAIN，按照下图所示操作

![](img\b017.png)

![图片](img\b018.png)

![图片](img\b019.png)

![图片](img\b020.png)

![图片](img\b021.png)

![图片](img\b022.png)

![图片](img\b023.png)

##### ⑤ 重新安装.NET4.0，使用安装包内的bat文件安装
![图片](img\b024.png)

