# 1.基础设施知识  

## 1.1 global.json

 &ensp;&ensp; **global.json** 定义在运行.netcli命令时使用的 **.netsdk** 的版本，与运行时无关，**sdk**版本指示使用哪个版本的 **.netcli**.

&ensp;&ensp; 通常使用最新的global.json,但是在某些高级方案中可能需要控制sdk的版本，.net sdk在当前目录或者某个父目录中查找global.json文件。

&ensp;&ensp;了解计算机上安装了哪些版本的sdks，然后再global.json中设置，.net cli命令cmd运行：

  1. dotnet&ensp;&ensp;--list-sdks  &ensp;&ensp;    //检查sdk版本
  2. dotnet&ensp;&ensp;--list-runtimes  &ensp;&ensp; //检查运行时版本
  3. dotnet&ensp;&ensp; --info    &ensp;&ensp; //查看sdk版本和运行时版本

## 1.2
