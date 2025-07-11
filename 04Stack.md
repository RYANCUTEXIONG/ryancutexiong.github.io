# 栈

### 定义

只能==从一端操作==的一维结构
==先进后出（First In Last Out FILO）==
![[008HaQLZgy1i396qtgkayj308206zdfw.jpg (290×251)](https://i0.wp.com/wx1.sinaimg.cn/mw690/008HaQLZgy1i396qtgkayj308206zdfw.jpg)]
**栈顶**：允许进行插入、删除操作的一端
**栈底**：是固定端
**空栈**：没有元素时栈为空
![[008HaQLZgy1i396qxodv5j305x06j0sm.jpg (213×235)](https://i0.wp.com/wx2.sinaimg.cn/mw690/008HaQLZgy1i396qxodv5j305x06j0sm.jpg)]


### C++实现

#### STL Stack

```C++
#include<stl> // STL库
```

##### 用法
```C++
stack<char>s; // 声明
s.push('A'); // 入栈
int m = s.size(); // 获取s的元素个数
char k = s.top(); // 获取栈顶元素
s.pop(); // 栈顶元素出栈
bool n = s.empty(); // 判断栈是否是空栈
```
以上的**STL Stack**基本函数的复杂度均为O(1)

#### 手写栈

用一个数组实现

```C++
stack<int>s;
int t, top;
```

#### 用法

| STL          | 手写              |
| ------------ | --------------- |
| `s.push(x);` | `s[top+1] = x;` |
| `s.top()`    | `s[top];`       |
| `s.pop();`   | `top -= 1;`     |
| `s.empty()`  | `top == 0`      |
| `s.size()`   | `top`           |
#### 对比

对于栈而言，更推荐使用手写版本，因为：
1. 手写版本对比STL没有明显区别
2. 手写版本的数组常数小，速度快
3. 手写版本用的都是C++的基础操作，速度快
4. 手写版本用的是数组，可以访问top以下的元素，方便差错~~（尽管逻辑上不符合栈的定义）~~


### 栈模拟
#### 25. 车厢调度
有一个火车站，每辆火车从A驶入，再从B方向驶出，同时它的车厢可以重新组合。假设从A方向驶来的火车有n节（n<=1000），分别按照顺序编号为1，2，3，…，n。假定在进入车站前，每节车厢之间都不是连着的，并且它们可以自行移动到B处的铁轨上。另外假定车站C可以停放任意多节车厢。但是一旦进入车站C，它就不能再回到A方向的铁轨上了，并且一旦当它进入B方向的铁轨，它就不能再回到车站C。 负责车厢调度的工作人员需要知道能否使它以a1,a2,…,an的顺序从B方向驶出，请来判断能否得到指定的车厢顺序。

第一行为一个整数n，其中n<=1000，表示有n节车厢，第二行为n个数字，表示指定的车厢顺序
如果可以得到指定的车厢顺序，则输出一个字符串YES，否则输出NO
![[008HaQLZgy1i396r3hjl5j30hn09vmxz.jpg (635×355)](https://i0.wp.com/wx3.sinaimg.cn/mw690/008HaQLZgy1i396r3hjl5j30hn09vmxz.jpg)

#### 三角行走

从坐标原点走到(n,n)，每次只能往右或往上走1单位且中途不能越过对角线，求有几种走法？

![008HaQLZgy1i39yhnnpvej30l80li0tb.jpg (197×200)](https://i0.wp.com/wx4.sinaimg.cn/small/008HaQLZgy1i39yhnnpvej30l80li0tb.jpg)

图片可以怎么解答？

![008HaQLZgy1i39yht1dlnj30y40m30t2.jpg (690×447)](https://i0.wp.com/wx4.sinaimg.cn/mw690/008HaQLZgy1i39yht1dlnj30y40m30t2.jpg)

当如上图时，走法的数量为$$C_{n+m}^m$$
但是题目又有一个要求：中途不能越过对角线，有2种方法：
1. **标数法**，但是复杂度为O(n<sup>2</sup>)
2. **补集转化思想** - 卡特兰数 Catalan数$$ans = C_{2n}^n-C_{2n}^{n-1}=\frac{(2n)!}{(n+1)!(n-1)!}$$ 用总方案数减去越过对角线的方案数（(0, 0)到(n+1, n-1)的一种方案）

### 卡特兰数

![008HaQLZgy1i3a09bxnfhj30gj0crgmb.jpg (595×459)](https://i0.wp.com/wx2.sinaimg.cn/mw690/008HaQLZgy1i3a09bxnfhj30gj0crgmb.jpg)


### 作业

![](https://i0.wp.com/wx4.sinaimg.cn/mw690/008HaQLZgy1i3a09frj30j30j30d5gmt.jpg)

