# qt5.14.2 + msvc2017 



1. visual studio 2022 installer 中修改->单个组件 -> 搜索2017  找到x64/x86 生成工具 安装  要三个 

visual studio installer中安装三个①x64/x86 生成工具  ②SDK	③使用C++的桌面开发

2. 编译器中 初始化 添加：VisualStudio2022\2022\Community\VC\Auxiliary\Build\vcvars64.bat