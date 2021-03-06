---
tags : 
- java基础

flag: blue
---

@toc

# JavaDay09 面向对象

## 一、类对象内存分析图

![类对象的内存分析图]($resource/%E7%B1%BB%E5%AF%B9%E8%B1%A1%E7%9A%84%E5%86%85%E5%AD%98%E5%88%86%E6%9E%90%E5%9B%BE.png)

## 二、局部变量
   
  在Java语言中，局部变量指的是在大括号里面定义的变量
 
```java
for (int i = 0; i < 10; i++) {    
}

for (int i = 0; i < 10; i++) {   
}
```
   以上两个变量i相互之间没有任何关系，因为他们都各自属于自己的for循环体，作用的范围是在for循环大括号以内
    
* ==作用域==：局部变量的作用域是在【大括号】以内
- ==生存期==：局部变量的生存期也是在【大括号】以内
    
## 三、 成员变量
==成员变量会默认指定初始化，但是局部变量（普通变量）必须自行初始化==
  【补充知识】
  类对象成员变量的 "0" 值
  不同的数据类型，"0"值表示的情况是不一样的
  
  byte,short,int
  以上数据的 "0" 值 都是 0
  long的 "0" 值   0L 或者 0l
  boolean         false
  char            '\0'
  float           0.0f
  double          0.0
  所用的【类对象】或者【引用数据类型】都是 null
  
  [零值的底层概念(了解)]当前数据空间里面的所有二进制位都是0

区别情况 | 成员变量 | 局部变量
---|---|---
定义位置|定义在类的内部 | 定义在函数或者代码块里
作用区别|描述事物共有的属性 | 提供给函数或者代码块保存数据的内存空间
初始值区别|在没有赋值的情况下，创建新的对象，里面的成员变量都是的"0"值 | 局部变量不赋值不能用，没有赋值的局部变量都是"野值"(其他语言) 
生存周期【重点】|随着对象的创建而创建，随着对象的销毁而销毁【JVM的垃圾回收机制】【内存的堆区】|变量定义语句定义的时候出现，当函数或者代码块执行完毕销毁 【内存的栈区】


## 四、多类组合
    
  - 汽车：可以看做是一个类
      属性：name，color，轮胎个数
      行为：飙车
  
 -  修理厂：可以看做一个类
      属性：地址，名字，电话
      行为：修车
  
  - 【重点】修车方法，需要外部提供一辆车，而这辆车是汽车类的对象
  
  **【一个类对象，是另一个类中方法的参数】**

## 五、匿名对象
- Java中提供了一种方式，称之为：匿名对象
	
- 匿名对象的格式：`new 类名().调用的方法();`

- 总结：
  - 匿名对象可以用来简化代码的书写，提高效率
  - 匿名对象**不会使用成员变量**，语法没有问题，但是没有实际意义，有去无回
  - 匿名对象的使用方式都是 new 类名().调用的方法(); 这种方式才有意义
  
- 前景预告
    匿名对象的终极挑战：
        匿名内部类的匿名对象直接调用方法
        Android
- 作用范围:   
   1.直接通过匿名对象，调用成员方法
   2.匿名对象作为函数/方法的参数
    
预告：文件IO操作
   new BufferedInputStream(new FileInputStream(new File(文件地址)).read();

## 六、面向对象的三大特征 之 封装

### （一） 面向对象的三大特征：    
1. 封装
2. 继承
3. 多态

- 问题:
代码中，程序只会严格的执行语法规范，数据类型检查，但是不会判断你传入的参数是否和生活实际有冲突。
有一些代码可以符合代码的逻辑，但是完全不符合生活逻辑，不符合生活逻辑的代码是没有任何意义的。

- 思考：
在对成员变量进行赋值的时候，基于语法规范的情况下，要对数据进行一定的约束和判断，让它符合生活逻辑

### （二）封装思想

- 权限修饰符
	public：公开的，公用的。使用public修饰的成员变量或者说成员方法任何人都可以通过对象直接使用
	
	private: 私有的。如果使用private修饰的成员变量或者说成员方法只能在【类内】使用，类外谁都不能用

问题又来了：
用private修饰的成员变量和成员方法发现，类外都不能使用的？怎么给成员变量进行赋值操作

【解决问题 setter 和 getter 方法】
setter方法是提供给【类外】用来设置【私有化成员变量的方法】
getter方法是提供给【类外】用来获取【私有化成员变量的数据】

问题双来了
选择使用了封装思想，使用了private 权限修饰，也用了setter方法，但是
数据还是没有符合生活逻辑

【解决问题】
要对setter方法进行限制，让代码符合语法逻辑和生活逻辑

- 【封装的好处】
1. 提高了代码的安全性
2. 操作数据简单
3. 可以隐藏一部分代码 JAR

【要求】
打今儿起，所有的类里面成员变量全部封装，并且按照语法规范和生活逻辑
提供对应的setter和getter方法

## 选择排序
详见【Demo5.java】

