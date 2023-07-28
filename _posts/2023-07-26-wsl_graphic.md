---
title: "为WSL2配置图形化界面"
tags: WSL2
---

原始的WSL只有命令行界面，有时候用起来很不方便；VcXsrv是微软Windows的开源显示服务器，利用它可以为WSL2配置图形化界面。

### 安装VcXsrv
* [下载地址](https://sourceforge.net/projects/vcxsrv/)
* 无脑选择【Next】+【Install】，完成安装

### 防止VcXsrv闪退
* 首先以管理员权限打开Powershell，执行命令`net stop winnat`
* 然后打开【控制面板】->【系统和安全】->【允许应用通过Windows防火墙】->【更改设置】->【允许其他应用】，添加xlaunch.exe和VcXsrc.exe
    * ![](https://lrel7.github.io/assets/images/2023-07-28-11-40-00.png)

### 启动VcXsrv
* 双击XLaunch，选择【下一页】，【下一页】，第三页记得勾选【Disable access control】，否则WSL2连接时可能会权限不足，最后点【完成】
  * ![](https://lrel7.github.io/assets/images/2023-07-28-11-44-00.png)
  * ![](https://lrel7.github.io/assets/images/2023-07-28-11-44-14.png)
  * ![](https://lrel7.github.io/assets/images/2023-07-28-11-44-59.png)
  * ![](https://lrel7.github.io/assets/images/2023-07-28-11-45-14.png)
* 查看最小化托盘，如果有VsXsrc的图标，就说明启动成功了

### 验证
* 在WSL2里安装x11-apps：`sudo apt install x11-apps`
* 输入命令：`xeyes`，可以看到一双随着鼠标转动的眼球，说明图形化界面已经配置成功！
  * ![](https://lrel7.github.io/assets/images/2023-07-28-11-49-14.png)