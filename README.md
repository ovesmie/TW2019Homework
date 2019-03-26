# ThoughtWorks 2019 校园招聘编程作业 （基础部分）
## 1 如何运行：
1. 在JDK1.8的运行环境下运行DroneTest.java
2. 在控制台输入测试用例，例如，如果给定输入：
```
4 6
GRRGGGGGGRFFFFRGGFFGRRFF
```
3. 则输出的字符串为：
```
GRRGGG
FFRGGG
FFRGGF
FFRRGF
```
***
## 2 文件结构
```
Drone
│————README.md
└————Drone.java         #无人机类
└————DroneTest.java     #测试控制台运行程序
└————ScopeTest.java     #无人机最大范围测试
└————MyException.java   #自定义异常类
└————test.txt           #用于测试100*100网格的数据文本
```
***
## 3 测试
### 3.1 本次测试将针对输入有效性的检查进行，分为四个部分：
#### 1. 不正确网格：
### Input:
```
//非整数，此处异常仅会发生在控制台输入数据时
a b
FFF
```
```
//小于0
4 6 8
FFF
```
```
//小于0
-1 -2
FFF
```
```
//大于100
101 1
FFF
```
### Output:
```
Incorrect mesh size.
```
***
#### 2. 无效地形：非FGR字符组
### Input:
```
//数字字符
2 3
111111
```
```
//非FGR字符组
3 2 
WFWFWR
```
```
//小写字符
2 3
fgfrg
```
```
//包含空格
3 2
FG FF 
```
### Output:
```
Invalid cell type.
```
***
#### 3. 数据不匹配：网格面积不等于字符串长度
### Input:
```
//长度不匹配
3 4
FFFF
```
### Output:
```
Data mismatch
```
### 3.2 数据取值范围测试
#### 根据题意，无人机飞行距离限制，探测网格的长和宽都不能超过100。
#### 在实际测试中，由于控制台仅能存储8190个字符，不能直接在控制台进行测试，因此创建了一个文本文件进行测试。测试结果表明能满足要求。
#### 运行Scope.java即可获得测试结果