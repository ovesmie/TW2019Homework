# ThoughtWorks 2019 校园招聘编程作业 （基础部分）
## 1 如何运行：
1. 在MyEclipse中导入归档文件Drone.zip
2. 运行/src/main文件夹中的DroneMain.java
3. 在控制台中输入测试数据，例如：
```
4 6
GRRGGGGGGRFFFFRGGFFGRRFF
```
4. 则输出的字符串为：
```
GRRGGG
FFRGGG
FFRGGF
FFRRGF
```
（本项目在MyEclipse10.7.1版本中开发，JRE1.6）
***
## 2 文件结构
```
Drone
│——bin
└——src
    |——test.txt             #用于测试100*100网格的数据文本
    │——main
        |——Drone.java       #无人机类
        |——DroneMain.java   #无人机运行程序
        |——DataUtils.java   #数据处理工具类
        |——ScopeTest.java   #无人机最大范围测试
        └——MyException.java #自定义异常类
    └——test
        └——UnitTest.java    #单元测试类，使用JUnit4框架


```
***
## 3 单元测试
### 3.1 JUnit4测试框架
```
测试方法：运行JUnit测试类UnitTest.java
测试内容：2个测试用例，5个有效性检查，1个最大范围测试
结论：Drone的代码覆盖率为97.7%，除去扩展性的要求而预留的代码，其余代码均完全覆盖，因此认为Drone测试通过。
```
### 3.2 输入有效性的检查
#### 3.2.1 不正确网格：
### Input:
```
//非整数，此处异常仅会发生在控制台输入数据时
a b
FFF
```
```
//位数大于2
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
#### 3.2.2 无效地形：非FGR字符组
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
#### 3.2.3 数据不匹配：网格面积不等于字符串长度
### Input:
```
//长度不匹配
3 4
FFFF
```
### Output:
```
Data mismatch.
```
### 3.3 数据最大范围测试
#### 根据题意，无人机飞行距离限制，探测网格的长和宽都不能超过100。
#### 在实际测试中，由于控制台仅能存储8190个字符，不能直接在控制台进行测试，因此创建了一个文本文件进行测试。测试结果表明能满足要求。
#### 运行Scope.java即可获得测试结果