### 1.方法

> 什么是方法?
>
> main主方法,程序执行的入口,
>
> ```java
> Scanner sc = new Scanner(System.in);
> 
> sc.nextInt();
> 
> sc.next();
> ```
>
> 对象名.后面的就是方法;
>
> ```java
> System.out.println();
> ```
>
> 所谓的方法,就是用来解决一类问题的代码的有序组合,是一个功能模块.
>
> * 方法的声明与调用
> * 方法的重载概念

#### 1.2 方法声明

> 语法格式:
>
> ​	访问修饰符 返回类型 方法名(参数列表){
>
> ​		方法体
>
> ​	}
>
> ​	访问修饰符
>
> ​		程序允许访问的权限
>
> ​		protected	保护
>
> ​		prvite	私有
>
> ​	返回类型
>
> ​		void 无返回类型
>
> ​	方法名
>
> ​		小驼峰写法
>
> ​	参数列表
>
> ​		可以省略
>
> ​		多个参数需要','隔开

#### 1.3 方法分类

> 根据方法是否带参数,是否返回值,可分为四类:
>
> ​	-无参无返回值方法
>
> ​	-无参带返回值方法
>
> ​	-带参无返回值方法
>
> ​	-带参带返回值方法

### 2. 无参无返回值方法

> 例:一行打印输出一串星号
>
> ```java
> package com.imooc.method;
> 
> import java.util.Scanner;
> 
> public class MethodDemo {
> 	// 打印输出星号的方法
> 	public void printStar() {
> 		System.out.println("******************");
> 	}
> 
> 	public static void main(String[] args) {
> //		Scanner sc = new Scanner(System.in);
> //		sc.next();
> 		//创建一个MethodDemo类的对象myMethodDemo
> 		MethodDemo myMethodDemo = new MethodDemo();
> 		//使用对象名.方法名()调用方法
> 		myMethodDemo.printStar();
> //		System.out.println("******************");
> 		System.out.println("欢迎来到java的世界");
> //		System.out.println("******************");
> 		myMethodDemo.printStar();
> 	}
> 
> }
> 
> ```
>
> 冒泡排序问题
>
> 只调用方法.
>
> 可以减少代码量
>
> 注意:方法在类的内部定义

### 3. 无参带返回值方法

> * 求长方形的面积
>
>   ```
>   public int area(){}
>   ```
>
> Scanner 类
>
> next()方法,返回值是String类
>
> ```java
> package com.imooc.method;
> 
> public class Rectangle {
> 	//求长方形面积的方法
> 	public int area() {
> 		int length = 10;
> 		int width = 5;
> 		int getArea = length* width;
> 		return getArea;//返回语句
> 	}
> 	public static void main(String[] args) {
> 		Rectangle rc = new Rectangle();
> 		System.out.println("长方形的面积为:"+rc.area());
> 	}
> 
> }
> ```

### 4. 带参无返回值方法

> * 定义一个求两个float类型数据最大值的方法,在方法中将最大值打印输出.
>
>   ```java
>   public void max (float a , float b){}
>   ```
>
> ```java
> package com.imooc.method;
> 
> public class MaxDemo {
> 	
> 	//求最大值的方法
> 	public void max(float a , float b) {
> 		float max;
> 		if(a>b) {
> 			max = a;
> 		}else {
> 			max = b;
> 		}
> 		System.out.println("两个数"+a+"和"+b+"的最大值为:"+max);
> 	}
> 	public static void main(String[] args) {
> 		MaxDemo maxDemo = new MaxDemo();
> 		int a = 5,b = 3;
> 		maxDemo.max(a, b);
> 		float m = 5.6f,n = 9.8f;
> 		maxDemo.max(m, n);
> 		maxDemo.max(9.8f, 123.9f);
> 	}
> 
> }
> 
> ```

### 5. 带参有返回值方法

> * 定义一个求n! 的方法,然后在求1!+2!+3!+4!+5!
>
>   ```
>   public int fac(int n){}
>   ```
>
>
> ```java
> package com.imooc.method;
> 
> public class FacDemo {
> 
> 	// 方法不可以嵌套定义
> 	// 求!n的方法
> 	public int fac(int n) {
> 		int s = 1;
> 		for (int i = 1; i <= n; i++) {
> 			s *= i;
> 		}
> 		return s;
> 	}
> 
> 	public static void main(String[] args) {
> 		FacDemo facDemo = new FacDemo();
> //		int fac =facDemo.fac(3);
> //		System.out.println("3!="+fac);
> 		int fac = 0;
> 		//求1!+2!+3!+4!+5!
> 		for(int i = 1;i<=5;i++) {
> 			fac += facDemo.fac(i);
> 		}
> 		System.out.println("1!+2!+3!+4!+5!="+fac);
> 	}
> 
> }
> ```

### 6. 数组作为方法参数

> * 打印输出数组元素的值
>
>   ```java
>   public void printArray(int[] arr){}
>   ```
>
> ```java
> package com.imooc.method;
> 
> public class ArrayMethod {
> 	
> 	//打印输出数组元素的值
> 	public void printArray(int[] arr) {
> 		for(int i = 0 ;i < arr.length;i++) {
> 			System.out.print(arr[i]+",");
> 		}
> 		System.out.println();//多次使用方法好换行
> 	}
> 	public static void main(String[] args) {
> 		int[] arr = {1,23,4,345};
> 		ArrayMethod am = new ArrayMethod();
> 		am.printArray(arr);
> 
> 	}
> 
> }
> ```
>
> * 例:查找数组元素的值
>
>   * 方法参数:数组,要查找的元素
>   * 返回值:boolean类型
>
>   ```java
>   public boolean search(int n,int[] arr){}
>   ```
>
> ```java
> package com.imooc.method;
> 
> import java.util.Scanner;
> 
> public class ArraySearch {
> 	//查找数组元素值的方法
> 	public boolean search(int n, int[] arr) {
> 		boolean flag = false;//默认没找到
> 		for(int i = 0;i<arr.length;i++) {
> 			if(arr[i] == n) {
> 				flag = true;//找到了
> 				break;//提高效率
> 			}
> 		}
> 		return flag;
> 	}
> 	public static void main(String[] args) {
> 		int[] arr = {10,20,30,40,50,60};
> 		
> 		System.out.println("请输入要查找的数据:");
> 		Scanner sc = new Scanner(System.in);
> 		int n = sc.nextInt();
> 		
> 		ArraySearch as = new ArraySearch();
> 		boolean flag = as.search(n, arr);
> 		if(flag) {
> 			System.out.println("找到了!");
> 		}else {
> 			System.out.println("没找到!");
> 		}
> 	}
> 
> }
> ```

### 7. 方法重载

> 方法名相同,参数列表不同
>
> ```java
> public void max(double a ,double b) {}
> public void max(float a , float b) {}
> ```
>
> 判断下列哪些方法是重载方法
>
> ```java
> public void hello(){}
> public int hello(){}false
> public void hello(String s){}true
> public void hello(int n){}true
> public void hello(float f1,float f2){}true
> public void hello1(){}false
> ```
>
> 定义三个方法,实现int,double 和数组类型和的问题
>
> ```java
> package com.imooc.method;
> 
> public class MathDemo {
> 
> 	//求两个int类型数的和
> 	public int plus(int m, int n) {
> 		return m+n;
> 	}
> 	//求两个double类型数的和
> 	public double plus(double m, double n) {
> 		return m+n;
> 	}
> 	//求数组元素的累加和
> 	public int plus(int[] arr) {
> 		int sum =0 ;
> 		for(int i = 0;i<arr.length;i++) {
> 			sum+=arr[i];
> 		}
> 		return sum;
> 	}
> 	public static void main(String[] args) {
> 		int m = 5,n=10;
> 		int[] arr= {1,2,3,4,5,6,};
> 		MathDemo mathDemo = new MathDemo();
> 		System.out.println("int类型的和:"+mathDemo.plus(m, n));
> 		System.out.println("double类型的和:"+mathDemo.plus(23.4,234.2));
> 		System.out.println("数组元素的和:"+mathDemo.plus(arr));
> 
> 
> 	}
> 
> }
> 
> ```

### 8. 基础数据类型的传值

> 交换方法
>
> ```java
> package com.imooc.method;
> 
> public class ExchangeDemo {
> 
> 	//交换方法
> 	public void swap (int a,int b) {
> 		int temp;
> 		System.out.println("交换前:a="+a+",b="+b);
> 		temp = a;
> 		a = b;
> 		b = temp;
> 		System.out.println("交换后:a="+a+",b="+b);
> 	}
> 	public void swapTest() {
> 		int m = 4,n = 5;
> 		System.out.println("交换前:m="+m+",n="+n);
> 		swap(m, n);
> 		System.out.println("交换后:m="+m+",n="+n);
> 	}
> 	public static void main(String[] args) {
> 		ExchangeDemo ed = new ExchangeDemo();
> 		ed.swapTest();
> 	}
> 
> }
> 
> ```
>
> 单独数值更改
>
> ```java
> package com.imooc.method;
> 
> public class ExchangeDemo1 {
> 
> 	public void add(int n) {
> 		n++;
> 		System.out.println("方法中n="+n);
> 	}
> 	public static void main(String[] args) {
> 		// TODO Auto-generated method stub
> 		int n = 10;
> 		System.out.println("方法调用前n的值:"+n);
> 		ExchangeDemo1 ed = new ExchangeDemo1();
> 		ed.add(n);
> 		System.out.println("方法调用后n的值:"+n);
> 
> 	}
> 
> }
> 
> ```
>
> * 方法中改变的值,并不对主方法中的变量产生影响

#### 8.1 数组的传值问题(不一样)

> 在数组传值中,方法中传值对主方法也产生了影响
>
> ​	因为指向是同一内存空间的数组
>
> ```java
> package com.imooc.method;
> 
> public class ArrayDemo {
> 
> 	//定义一个用于修改某个数组元素值的方法
> 	public void updateArray(int[] arr) {
> 		arr[3] = 15;
> 		System.out.println("数组arr的元素为:");
> 		for(int n:arr) {
> 			System.out.print(n+",");
> 		}
> 		System.out.println();
> 	}
> 	public static void main(String[] args) {
> 		ArrayDemo ad = new ArrayDemo();
> 		int[] arr = {1,2,3,4,56,};
> 		System.out.println("方法调用前arr的元素为:");
> 		for(int n:arr) {
> 			System.out.print(n+",");
> 		}
> 		System.out.println();
> 		
> 		ad.updateArray(arr);
> 		System.out.println("方法调用后arr的元素为:");
> 		for(int n:arr) {
> 			System.out.print(n+",");
> 		}
> 	}
> 
> }
> 
> ```

### 9. 可变参数列表

> 例:
>
> ```java
> public void sum (int... n){}
> ```
>
> (可变原参数)
>
> ```java
> package com.imooc.method;
> 
> public class ArgsDemo {
> 
> 	//求和的方法
> 	public void sum (int... n) {
> 		int sum = 0;
> 		for(int i: n) {
> 			sum+=i;
> 		}
> 		System.out.println("sum="+sum);
> 	}
> 	public static void main(String[] args) {
> 		ArgsDemo ad = new ArgsDemo();
> 		ad.sum(1);
> 		ad.sum(1,2,4,5);
> 
> 	}
> 
> }
> 
> ```
>
> 参数列表中如果有俩个以上的参数,可变参数一定是放在最后的!
>
> 可以将数组传递给可变参数列表
>
> 在方法定义中,认为当前是两个search方法重载定义,而不是重载
>
> 数组作为参数时,是不能将多个值传递给数组的
>
> 一个方法中,只能有个一个参数列表
>
> ```java
> package com.imooc.method;
> 
> public class ArgsDemo1 {
> 
> 	//查找问题
> 	public void search(int n,int... a) {
> 		boolean flag = false;
> 		for(int a1:a) {
> 			if(a1 == n) {
> 				flag=true;
> 				break;
> 			}
> 		}
> 		if(flag) {
> 			System.out.println("找到了!"+n);
> 		}else {
> 			System.out.println("没找到!"+n);
> 		}
> 	}
> 	public static void main(String[] args) {
> 		ArgsDemo1 ad = new ArgsDemo1();
> 		ad.search(6,1,2,3,4,5);
> 		int[] a1 = {1,2,3,4,5};
> 		ad.search(3, a1);
> 	}
> 
> }
> 
> ```

#### 9.1 当可变参数列表作为方法参数的重载问题

> 可变参数列表所在的方法是最后被访问的.
>
> ```java
> package com.imooc.method;
> /**
>  * 关于可变参数列表和重载的问题
>  * @author hare
>  * @version 1.0
>  *
>  */
> public class ArgsDemo3 {
> 
> 	//可变参数列表所在的方法是最后被访问的.
> 	public int plus(int a, int b) {
> 		System.out.println("不带可变参数方法被调用!");
> 		return a+b;
> 	}
> 	public int plus(int... a) {
> 		int sum = 0;
> 		for(int n:a) {
> 			sum+=n;
> 		}
> 		System.out.println("带可变参数方法被调用");
> 		return sum;
> 	}
> 	public static void main(String[] args) {
> 		ArgsDemo3 ad = new ArgsDemo3();
> 		System.out.println("和为:"+ad.plus(1,2));
> 	}
> 
> }
> ```
>
> 

#### 9.2 文档注释的生成

> ```
> javadoc -d doc 文件名.java
> ```

### 10. 方法的调试

> * F6逐步执行
> * F5跳进方法内部
> * F7返回方法调用处

### 总结:

> * 方法声明的语法格式
>
>   * 修饰符有
>     * public
>     * private
>     * protected
>     * 默认
>   * 返回类型可以是void或者任何数据类型
>   * 方法名
>     * 和变量命名规则一样
>   * 参数列表
>     * 可以是基本数据类型
>     * 引用数据类型
>
>   ```java
>   访问修饰符 返回类型 方法名(参数列表){方法体}
>   ```
>
> * 方法调用
>
>   ```java
>   Demo d = new Demo();
>   d.show();
>   ```
>
> * 方法的重载
>
>   * 方法名相同,参数列表不同(唯一条件)
>
> * 可变参数列表:
>
>   * 可变参数一定是方法中最后一个参数
>   * 数组可以传递给可变参数的方法,反之不行
>   * 在重载中,含有可变参数列表是在最后被选中
>
> * 方法传值问题
>
>   * 基本数据类型传值
>     * 方法中对参数的修改,不会对主方法中传来的变量值产生影响
>   * 引用数据类型传值
>     * 方法中对数组的变化,会影响主方法传来的数组.
>
> * 方法调试问题

