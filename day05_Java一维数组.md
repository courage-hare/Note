## 数组的学习

> 为什么要使用数组?
>
> * 学生成绩排序问题
>
> 数组:
>
> ​	数组是相同类型的数据按顺序组成的一种引用数据类型
>
> ​	数据类型:
>
> ​		1.基本数据类型
>
> ​		2.引用数据类型
>
> ​				类
>
> ​				接口
>
> ​				数组
>
> 学习内容:
>
> ​	一维数组
>
> ​		-声明
>
> ​		-创建
>
> ​		-初始化
>
> ​		-元素的引用
>
> ​		-长度
>
> ​		-数组的应用

### 1.一维数组

#### 1.1 数组的声明

> 语法格式:
>
> ```java
> 数据类型[] 数组名;
> 数据类型 数组名[];
> 
> 	int[] myIntArray;
> 	int myIntArray[];
> 	char[] ch;
> 	String[] strArray;
> ```

#### 1.2 数组的创建

> 语法格式一:
>
> 先声明后创建
>
> ```java
> 数据类型[] 数组名;
> 数组名 = new 数据类型[数组长度];
> 
> int[] arr;
> arr = new int[10];
> //创建一个长度为10的整型数组;
> ```
>
> 语法格式二:
>
> 声明的同时创建数组
>
> ```java
> 数据类型[] 数组名 = new 数据类型[数据长度];
> 
> int[] arr = new int[10];
> 创建长度为10的整型数组arr
> 
> 注:数组长度必须指定
> ```

#### 1.3 数组在内存中的存储

> 数组会被分配连续的内存空间
>
> ```java
> int[] a = new int [5];
> ```
>
> 内存展示:
>
> | a    | 0    |
> | :--- | ---- |
> |      | 0    |
> |      | 0    |
> |      | 0    |
> |      | 0    |
>
> 局部变量和数组的默认值问题
>
> 数组是有默认值的,其实是对象

#### 1.4 数组的初始化

> 声明数组的同时给数组赋值,叫做数组的初始化
>
> ```java
> int[] arr = {1,2,3,4,5,6,7,8,9,10};
> ```
>
> 数组的长度就是初始化时所给数组的元素个数.

#### 1.5 数组元素的引用

> 语法格式:
>
> ```java
> 数组名[下标];
> //注意:下标从0开始
> 
> int[] arr = {1,2,3,4,5,6,7,8,9,10};
> ```
>
> | 1    | 2    | 3    | 4    | 5    | 6    | 7    | 8    | 9    | 10   |
> | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- |
> | a[0] | a[1] | a[2] | a[3] | a[4] | a[5] | a[6] | a[7] | a[8] | a[9] |

#### 1.6 数组的长度

> 属性length表示数组的长度,如
>
> ```java
> int[] arr = {1,2,3,4,5,6,7,8,9,10};
> a.length;
> ```
>
> 引用方法length

### 2. 一位数组的应用

```java
package com.imooc.arry;

public class ArrayDemo {

	public static void main(String[] args) {
		//声明一个整型数组
		int[] intArray;
		//声明一个字符串类型数组
		String strArray[];
		//创建数组
		intArray = new int[5];
		strArray = new String[10];
		//声明数组的同时进行创建
		float[] floatArray = new float[4];
		//初始化数组
		char[] ch = {'a','b','c','d'};
		System.out.println("ch数组的长度为:"+ch.length);//4
		System.out.println("intArray数组的第二个元素为:"+intArray[1]);//0
		System.out.println("strArray数组的第五个元素为:"+strArray[4]);//null
		System.out.println("floatArray数组的最后一个元素为:"+floatArray[floatArray.length-1]);//0.0
		//循环为整型数组赋值
		for(int i = 0;i<intArray.length;i++) {
			intArray[i]=i+1;//intArray[0]=1;
		}
		//循环输出整型数组中的元素
		System.out.println("整型数组intArray的元素为:");
		for(int i = 0;i<intArray.length;i++) {
			System.out.print(intArray[i]+",");
		}
	}

}
```

### 3. 案例

> 求数组元素累加和
>
> [解析]
>
> ```java
> package com.imooc.arry;
> import java.util.*;
> public class ArrayDemo1 {
> 
> 	public static void main(String[] args) {
> 		// 求整型数组的累加和
> 		//	定义整型数组
> 		int[] a = new int[5];
> 		Scanner sc = new Scanner(System.in);
> 		//从键盘接收数据,为数组元素赋值
> 		for(int i = 0;i<a.length;i++) {
> 			System.out.println("请输入第"+(i+1)+"个元素:");
> 			a[i]=sc.nextInt();
> 		}
> 		System.out.println("数组元素的内容为:");
> 		for(int i = 0;i<a.length;i++) {
> 			System.out.print(a[i]+",");
> 		}
> 		//求数组元素的累加和
> 		int sum = 0;
> 		for(int i = 0;i<a.length;i++) {
> 			sum += a[i];
> 		}
> 		System.out.println();
> 		System.out.println("数组元素累加和为:"+sum);
> 	}
> 
> }
> ```
>
> 求数组元素的最大值
>
> [解析]
>
> ```java
> package com.imooc.arry;
> 
> public class ArrayDemo2 {
> 
> 	public static void main(String[] args) {
> 		// 求数组元素的最大值
> 		int[] a = {34,23,78,56,31};
> 		int max = a[0];//假设此时a[0]是最大的
> 		for(int i = 1;i<a.length;i++) {
> 			if(max<a[i]) {
> 				//将最大的赋值给max
> 				max=a[i];
> 			}
> 		}
> 	}
> 
> }
> ```

### 4.增强型for循环

> 又叫foreach循环
>
> foreach循环应用:
>
> ```java
> int[] arr = {1,2,3,4,5};
> for(int n:arr)
> 	System.out.println(n);
> ```
>
> 第一次执行arr[0]=n
>
> 第二次执行arr[1]=n
>
> ...
>
> 遍历一遍

如何对变量a,b的值进行交换

```java
int a = 3,b=5;
int temp;
temp = a;a=b;b=temp;
```

> | a    | b    | temp |
> | ---- | ---- | ---- |
> | 3    | 5    | 3    |
> | 5    | 5    | 3    |
> | 5    | 3    | 3    |

### 5. 冒泡排序

> 对一组整数按照从小到大的顺序进行排序.
>
> | 34   | 53   | 12   | 32   | 56   | 17   |
> | ---- | ---- | ---- | ---- | ---- | ---- |
> | 34   | 12   | 32   | 53   | 17   | 56   |
> | 12   | 32   | 34   | 17   | 53   | 56   |
> | 12   | 32   | 17   | 34   | 53   | 56   |
> | 12   | 17   | 32   | 34   | 53   | 56   |
> | 12   | 17   | 32   | 34   | 53   | 56   |
>
> 依次排比,
>
> [解析]
>
> ```java
> package com.imooc.arry;
> 
> public class SortDemo {
> 
> 	public static void main(String[] args) {
> 		// 冒泡排序
> 		//定义整型数组
> 		int[] a = {34,53,12,32,56,17};
> 		System.out.println("排序前的数组元素为:");
> 		for(int n:a) {
> 			System.out.print(n+",");
> 		}
> 		System.out.println();
> 		int temp;
> 		//外层多少次
> 		//内层找最大
> 		for(int i = 0;i<a.length-1;i++) {
> 			for(int j = 0;j<a.length-i-1;j++) {
> 				if(a[j]>a[j+1]) {
> 					temp = a[j];
> 					a[j]=a[j+1];
> 					a[j+1]=temp;					
> 				}
> 			}
> 		}
> 		System.out.println("从小到大排序后的数组元素为:");
> 		for(int n:a) {
> 			System.out.print(n+",");
> 		}
> 
> 	}
> 
> }
> ```
>
> ```java
> 作业:从大到小如何排序
>     int a = {123,4,32,21,52};
> ```
>
> | 123  | 4    | 32   | 21   | 52   |
> | ---- | ---- | ---- | ---- | ---- |
> | 123  | 32   | 21   | 52   | 4    |
> | 123  | 32   | 52   | 21   | 4    |
> | 123  | 52   | 32   | 21   | 4    |
> | 123  | 52   | 32   | 21   | 4    |
>
> ```java
> package com.imooc.arry;
> 
> public class SortDemo1 {
> 
> 	public static void main(String[] args) {
> 		// 冒泡排序,从大到小
> 		//初始化数据
> 		int[] a = {123,4,32,21,52};
> 		System.out.println("排序前的数组顺序为:");
> 		//遍历1遍
> 		for(int n:a) {
> 			System.out.print(n+",");
> 		}
> 		System.out.println();//换行
> 		
> 		//定义一个临时变量好比较
> 		int temp;
> 		//排序
> 		//外层决定次数
> 		//内层决定大小
> 		for(int i = 0 ;i<a.length-1;i++) {
> 			for(int j =0;j<a.length-i-1;j++) {
> 				if(a[j]<a[j+1]) {
> 					temp = a[j];
> 					a[j] = a[j+1];
> 					a[j+1] = temp;
> //					System.out.print(a[j]+",");
> 				}
> 			}
> 		}
> 		
> 		//来句提示语
> 		System.out.println("排序后的从大到小的顺序是:");
> 		//再次遍历输出
> 		for(int n:a) {
> 			System.out.print(n+",");
> 		}
> 
> 	}
> 
> }
> ```

### 6. 二维数组

> * 二维数组的声明和创建
> * 二维数组的初始化
> * 二维数组的引用
> * 案例演示
>
> 二维数组的应用场景
>
> |      | 语文 | 数学 | 英语 |
> | ---- | ---- | ---- | ---- |
> | 张三 | 85   | 89   | 90   |
> | 李四 | 75   | 65   | 85   |
> | 王五 | 80   | 84   | 95   |
>
> 案例解析
>
> ```java
> package com.imooc.arry;
> 
> public class ArrayDemo5 {
> 
> 	public static void main(String[] args) {
> 		// 二维数组的声明
> 		//三种形式
> 		//声明int类型的二维数组
> 		int[][] intArray;
> 		//声明float类型的二维数组
> 		float floatArray[][];
> 		//声明double类型的二维数组
> 		double[] doubleArray[];
> 		
> 		//创建一个三行三列的int类型数组
> 		intArray = new int[3][3];//第一个行,第二个列
> 		System.out.println("intArray数组的第3行第2列元素为:"+intArray[2][1]);
> 		//为第2行第3个元素赋值为9
> 		intArray[1][2]=9;
> 		System.out.println("intArray数组第2行第3列的元素为:"+intArray[1][2]);
> 		
> 		//声明数组的同时进行创建
> 		char[][] ch = new char[3][5];
> 		//创建float类型的数组时,只指定行数
> 		floatArray = new float[3][];//行数不可以省略
> //		System.out.println(floatArray[0][0]);
> 		//每行相当于一个一维数组,需要创建
> 		floatArray[0] = new float[3];//第一行有3列
> 		floatArray[1] = new float[4];//第二行有4列
> 		floatArray[2] = new float[5];//第三行有5列
> 		System.out.println(floatArray[0][0]);
> 		
> 		//二维数组初始化
> 		int[][] num = {{1,2,3},{4,5,6},{7,8,9}};
> 		System.out.println("num数组第1行第2列的元素为:"+num[0][1]);
> 		System.out.println("num数组的行数为:"+num.length);
> 		System.out.println("num数组的列数为:"+num[0].length);
> 		int[][] num1 = {{78,98},{65,75,63},{98}};
> 		System.out.println("num数组的第一行列数为:"+num1[0].length);
> 		//循环输出二维数组的内容
> 		//外层负责行
> 		//内层负责列
> 		for(int i = 0;i<num1.length;i++) {
> 			for(int j = 0;j<num1[i].length;j++) {
> 				System.out.print(num1[i][j]+",");
> 			}
> 			System.out.println();
> 		}
> 	}
> 
> }
> ```

### 总结

> * 一维数组
>   * 声明
>   * 创建
>   * 初始化
>   * 元素的引用
>   * 长度
>   * 数组的应用
> * 二维数组
> * 注意问题
>   * 数组是引用数据类型
>   * 创建数组时,会开辟连续性的内存空间
>   * 数组长度使用length属性获取
>   * 数组元素的下标从0开始
>   * 数组下标越界问题

