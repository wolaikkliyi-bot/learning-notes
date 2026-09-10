# qt5.14.2 + msvc2017 



1. visual studio 2022 installer 中修改->单个组件 -> 搜索2017  找到x64/x86 生成工具 安装  要三个 

visual studio installer中安装三个①x64/x86 生成工具  ②SDK	③使用C++的桌面开发

2. 编译器中 初始化 添加：VisualStudio2022\2022\Community\VC\Auxiliary\Build\vcvars64.bat



# 找不到xxx.dll

环境变量 -》系统路径中添加路径

```
D:\C_software\QT\Qt5.14.2\5.14.2\msvc2017_64\bin
```



# 别人项目自己run不成功，双击exe可以运行

管理员身份运行qt creator，文件夹受信任受限 被windows系统拦截
