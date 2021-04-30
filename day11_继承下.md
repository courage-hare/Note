### 继承下

> Object类
>
> final 关键字使用
>
> 注解简介

### Objcet类

> Object类是所有类的父类
>
> 一个类没有使用extends关键字明确标识继承关系,则默认继承Object类(包括数组)
>
> java中每个类都可以使用Object中定义的

#### equals()

```java
/**
		 * equals:
		 * 1.继承Object中的equals方法,比较的是两个引用的是否指向同一个对象
		 * 2.子类可以通过重写equals方法的形式,改变比较的内容
		 * 
		 */
```



```java
package com.imooc.test;

import com.imooc.animal.Animal;

public class TestThree {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		Animal one = new Animal("hh",2);
		Animal two = new Animal("hh",2);
		//equals:继承Object中的equals方法,比较的是两个引用的是否指向同一个对象
		boolean b = one.equals(two);
		System.out.println(b);
		System.out.println((one == two));
		
		String str = new String("a");
		String str2 = new String("a");
		boolean flag = str.equals(str2);
		System.out.println(flag);
		System.out.println(str == str2);
	}
	

}

```

#### toString()

```java
 		/**
		 * toString测试
		 * 1.输出对象时,默认会直接调用toString
		 * 2.继承Object中的toString()方法时,输出对象的字符串表示形式:类型信息+地址信息
		 * 3.子类可以通过重写toString,改变输出的表现内容以及表现形式
		 */
```

### final

1.  修饰类表示不允许被继承
2. 修饰方法表示不允许被子类重写
   1. final修饰的方法可以被继承
   2. 不能修饰构造方法
3. 修饰变量表示不允许修改
   1. 方法内部的局部变量>>在使用之前被初始化赋值即可
   2. 类中的成员变量>>只能在定义时,构造方法,构造代码块进行
   3. 基本数据类型>>初始化赋值之后不能更改
   4. 引用数据类型>> 初始化之后不能再指向另一个对象,但对象的内容是可变的
4. 可配合static使用
   1. 方法 属性
   2. public static final String URL="www.hare.com"
5. 使用final修饰可以提高性能,但会降低可扩展性

### 注解

* JDk1.5版本引入的一个特性
* 可以声明在包,类,属性,方法,局部变量,方法参数等的前面,用来对这些 元素进行说明,注解



* 按照运行机制分
  * 源码注解	@Override 注解只在源码阶段保留,在编译阶段会被丢失
  * 编译时注解 注解会在编译时期保留,在加载class文件时会被丢弃
  * 运行时注解 运行阶段还起作用,甚至会影响运行逻辑的注解
* 按照来源分
  * 来自JDk的注解
  * 来自第三方的注解
  * 我们自定义的注解

元注解



### 总结

* Object类
  * Object类是所有类的父类
  * Java中的每个类都可以使用Object中定义的方法
    * equals()
    * toString()
* final
  * 修饰类不允许被继承
  * 修饰方法不允许被子类重写
  * 修饰变量不允修改
  * final修饰方法可以继承
  * 引用数据类型的变量:初始化之后不能再指向另一个对象,但指向对象的内容是可变的 
  * 可配合static使用