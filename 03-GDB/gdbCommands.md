# GDB 简易调试笔记

## 1. GDB简介

GDB（GNU Debugger）是 Linux 下常用的 C/C++ 调试工具。

主要功能：

- 设置断点
- 单步执行
- 查看变量
- 查看调用栈
- 定位程序崩溃原因


---

# 2. 编译调试版本

普通编译：

```bash
g++ main.cpp -o main
```

无法查看源码信息。


调试编译：

```bash
g++ main.cpp -g -o main
```

`-g`：

生成调试信息，让 GDB 可以关联源码。


---

# 3. 启动 GDB

```bash
gdb ./main
```

进入：

```text
(gdb)
```


退出：

```gdb
quit
```

或者：

```gdb
q
```


---

# 4. 基本调试流程


## 设置断点

指定函数：

```gdb
break main
```

简写：

```gdb
b main     //是停在函数开始的位置
```


指定行号：

```gdb
b 10
```


查看断点：

```gdb
info breakpoints
```


删除断点：

```gdb
delete 1
```


---

# 5. 运行程序


运行：

```gdb
run
```

简写：

```gdb
r
```


程序会运行到断点位置暂停。


---

# 6. 单步执行


## next

执行下一行代码：

```gdb
next
```

简写：

```gdb
n
```


不会进入函数内部。


---

## step

进入函数：

```gdb
step
```

简写：

```gdb
s
```


---

## continue

继续运行：

```gdb
continue
```

简写：

```gdb
c
```


---

# 7. 查看变量


查看变量：

```gdb
print 变量名
```

简写：

```gdb
p 变量名
```


例如：

```gdb
p count
```


输出：

```text
$1 = 10
```


---

查看当前函数局部变量：

```gdb
info locals
```

每次运行查看:

```gdb
display x
display y
delete display 1 //删除某个 //按照前面的编号来
```




---

# 8. 查看程序调用栈


程序崩溃：

```text
Segmentation fault
```


查看调用关系：

```gdb
bt
```


例如：

```text
#0 dfs()
#1 numIslands()
#2 main()
```


表示：

```
main
 |
numIslands
 |
dfs
```


---

# 9. 查看源码


查看当前位置：

```gdb
list
```


简写：

```gdb
l
```


---

# 10. 常见调试场景


## 1. 段错误 Segmentation fault


例如：

```cpp
int* p = nullptr;

*p = 10;
```


运行：

```bash
gdb ./main
```

然后：

```gdb
run
```

崩溃后：

```gdb
bt
```


定位错误位置。


---

## 2. 查看指针


查看地址：

```gdb
p pointer
```


查看内存：

```gdb
x address
```


---

# 11. 常用命令速查


|命令|作用|
|:--|-|
|r / run|运行程序|
|b / break|设置断点|
|n / next|下一步|
|s / step|进入函数|
|c / continue|继续运行|
|p / print|查看变量|
|l / list|查看源码|
|bt|查看调用栈|
| q                       | 退出         |
| display/ delete display | 每次运行查看 |


---

# 12. C++开发调试流程


```
代码
 |
 ↓
g++ -g 编译
 |
 ↓
gdb启动
 |
 ↓
设置断点 b
 |
 ↓
run运行
 |
 ↓
n/s单步
 |
 ↓
p查看变量
 |
 ↓
bt定位崩溃
```


---

# 13. Qt/Linux项目中的应用

常见问题：

- 程序崩溃
- 野指针
- 空指针
- 内存访问错误
- 多线程异常


排查：

```bash
gdb 程序名
```

进入：

```gdb
run
```

崩溃：

```gdb
bt
```


查看调用位置。


---

## 记忆重点

最常用五个命令：

```gdb
b main      # 设置断点

r           # 运行

n           # 下一步

p xxx       # 查看变量

bt          # 查看调用栈
```