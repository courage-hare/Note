### 1.循环结构

> * while循环
> * do-while循环
> * for循环
> * 嵌套循环
> * break语句
> * continue语句

### 2.while循环

> * 语法格式
>
>   * ```java
>     while(循环条件){语句;}
>     ```
>
>     * 为避免死循环,小括号后面不要加分号
>
> * 执行流程
>
>   * 将小于5的整数打印输出
>
>   * ```java
>     int n = 1;
>     while(n>5){
>     	//输出n的值
>     	n++;
>     }
>     ```
>
>     * n的值必须先进行初始化
>
>     * 循环变量n的值必须被改变
>
>       * | n = 1 | n < 5 | 输出n | n++  |
>         | ----- | ----- | ----- | ---- |
>         | 1     | true  | 1     | 2    |
>         | 2     | true  | 2     | 3    |
>         | 3     | true  | 3     | 4    |
>         | 4     | true  | 4     | 5    |
>         | 5     | false | \     | \    |

>[案例1]
>
>需求:求1-5的和
>
>```java
>package com.Imooc.flow1;
>
>public class PlusDemo {
>	public static void main(String[] args) {
>//		求1到5的累加和
>//		1+2+3+4+5
>		int n = 1;
>		int sum = 0;//sum是存放和的变量
>		while(n<=5) {
>			sum =sum+n;
>			n++; 
>		}
>		System.out.println(sum);
>	}
>}
>
>```
>
>[分析]
>
>​	
>
>| n    | sum  | n<=5  | sum+=n                      | n++  |
>| ---- | ---- | ----- | --------------------------- | ---- |
>| 1    | 0    | true  | sum = sum + n = 0+1=1       | 2    |
>| 2    | 1    | true  | sum = sum + n = 1 + 2 = 3   | 3    |
>| 3    | 3    | true  | sum = sum + n = 3 + 3 = 6   | 4    |
>| 4    | 6    | true  | sum = sum + n = 4 + 6 = 10  | 5    |
>| 5    | 10   | true  | sum = sum + n = 10 + 5 = 15 | 6    |
>| 6    | 15   | false | /                           | /    |
>
>[案例2]
>
>​	需求:1,3,5,...15的和
>
>```java
>package com.Imooc.flow1;
>
>public class PlusDemo1 {
>	public static void main(String[] args) {
>		//求1,3,5,...15的合
>		int num = 1;//初始化数值
>		int num1 = 2;
>		int sum = 0;//定义和的变量
>		while(num<=15) {//判断num>=15时跳出
>			sum += num;//累积每次相加给sum
>//			System.out.println("sun="+sum);
>			num += num1;//累次每次叠加2
>//			System.out.println("num="+num);
>		}
>		System.out.println("求1,3,5,...15的和:"+sum);
>	}
>
>}
>
>```
>
>[案例3]
>
>​	循环输出26个英文字母,分两行输出

	>```java
	>package com.Imooc.flow1;
	>
	>public class CharDemo {
	>
	>	public static void main(String[] args) {
	>		// 循环输出26个英文字母,分两行输出
	>		char ch = 'a';
	>		int count = 1;//控制换行
	>		while(ch<='z'){
	>			System.out.print(ch+" ");
	>			ch++;
	>			if(count % 13 == 0) {
	>				System.out.print("\n");//换行
	>			}
	>			count++;//累加到13
	>		}
	>	}
	>
	>}
	>
	>```

#### 3.do-while循环

> * 语法格式
>
>   * ```
>     do{
>     语句;
>     }while(循环条件);
>     ```
>
>   * [注意事项]
>
>   * do-while循环至少循环一次
>
>   * 循环条件后的分号不能丢
>
>   * ```java
>     int n = 1;
>     do{
>     //输出n的值
>     	n++;
>     }while(n<5);
>     ```
>
>   * 局部变量使用前必须要初始化值
>
>     * | n的值 | 输出n的值 | n++  |
>       | ----- | --------- | ---- |
>       | 1     | 1         | 2    |
>       | 2     | 2         | 3    |
>       | 3     | 3         | 4    |
>       | 4     | 4         | 5    |
>       | 5     | /         | /    |
>
> * [案例1]
>
> * 需求:求1-5的和

>```java
>package com.Imooc.flow1;
>
>public class DoWhileDemo {
>
>	public static void main(String[] args) {
>		// 求1-5的累加和
>		int num = 1;//初始化
>		int sum = 0;//和
>		do{
>			sum+=num;
>			num++;
>		}while(num<=5);
>		System.out.println(sum);
>
>	}
>
>}
>
>```
>
>[分析]
>
>| num  | sum+=num          | num<=5 | sum  | num++ |
>| ---- | ----------------- | ------ | ---- | ----- |
>| 1    | sum+=sum+num=0+1  | true   | 1    | 2     |
>| 2    | sum+=sum+num=1+2  | true   | 3    | 3     |
>| 3    | sum+=sum+num=3+3  | true   | 6    | 4     |
>| 4    | sum+=sum+num=6+4  | true   | 10   | 5     |
>| 5    | sum+=sum+num=10+5 | true   | 15   | 6     |
>| 6    | /                 | false  | /    | /     |
>
>[案例2]
>
>需求:猜字游戏,要求猜一个介于1到10之间的数字.然后将猜测的值与实际值比较,并给出提示,以便能更加接近实际值,直到猜中为止.
>
>程序分析:
>
>*  给定要猜测的数字
>*  使用循环结构
>*  循环进行的条件:猜测的数值和实际值不相等
>* 循环体的内容:输入实际值,及进行判断
>*  输出猜到的值

```java
package com.Imooc.flow1;

import java.util.Scanner;

public class GuessDemo {
	public static void main(String[] args) {
		/* 给定要猜测的数字
		* 使用循环结构
		* 循环进行的条件:猜测的数值和实际值不相等
		* 循环体的内容:输入实际值,及进行判断
		* 输出猜到的值
		*/
		//设置猜测的数值
		int number = (int)(Math.random()*10+1);//[0,1)
//		System.out.print(number);
		int guess;//获取用户输入的值
		System.out.println("猜一个介于1-10之间的整数:");
		do {
			System.out.println("请输入您猜测的数:");
			Scanner sc = new Scanner(System.in);
			guess = sc.nextInt();//获取输入
			if(guess>number) {//当输入数值大于随机数时
				System.out.println("太大了!");
			}else if(guess<number) {//当输入数值小于随机时
				System.out.println("太小了!");
			}
		}while(number!=guess) ;//跳出
		System.out.println("您猜中了!答案为:"+number);
	}
}

```

### 4.for循环

> 语法格式
>
> ```java
> for(表达式1;表达式2;表达3){
> 	语句;
> }
> ```
>
> 表达式1:
>
> ​	int n = 1;
>
> 表达式2:
>
> ​	n <=5;
>
> 表达式3:
>
> ​	n++;
>
> [案例]
>
> 使用for循环,求1-5的累加和
>
> [解析]
>
> ```java
> package com.Imooc.flow1;
> 
> public class ForDemo {
> 
> 	public static void main(String[] args) {
> 		// TODO Auto-generated method stub
> 		int n = 1 , sum =0;
> 		for(n = 1;n<=5;n++) {
> 			sum += n ;
> 		}
> 		System.out.println("sum="+sum);
> 	}
> 
> }
> 
> ```
>
> [分析]
>
> * int n = 1; 在循环中执行一次
> * n<=5第二次执行
> * 循环体第三次执行
> * n++最后执行
>
> 局部变量
>
> ​	方法中定义的变量,都是局部变量
>
> ​	如上:n,sum都是局部变量
>
> ​	局部变量只在定义它的大括号内有效!

#### 4.1for循环的主要事项

> 三个表达式都可以省略
>
> ```java
> for(表达式1;表达式2;表达3){
> 	语句;
> }
> ```
>
> [案例]
>
> 需求:输入数字1-10并输出,如果输入0则跳出循环
>
> ```java
> package com.Imooc.flow1;
> 
> import java.util.Scanner;
> 
> public class NumberInput {
> 	public static void main(String[] args) {
> 		// 从键盘接收数据
> 		Scanner sc = new Scanner(System.in);
> 		int n;
> 		while (true) {
> 			n = sc.nextInt();
> 			if(n==0)break;
> 			System.out.print(n);
> 		}
> 		System.out.println("已经退出!");
> 	}
> }
> 
> ```

### 5.循环嵌套

> ```java
> while(循环条件){
> 	...
> 		while(循环条件){
> 			...
> 		}
> 	...
> }
> ```
>
> [例]
>
> 使用嵌套while循环输出10行10列的型号
>
> [解析]

```java
package com.Imooc.flow1;

public class StarDemo1 {
	public static void main(String[] args) {
		int m = 1;//外重循环的循环变量
		int n = 1;//内重循环的循环变量
		System.out.println("输出4行4列的星号:");
		//外重循环控制输出几行
		while(m<=4) {
			//内重循环控制每行输出几个行号
			n=1;//重新给n开始赋值,不然一直是6
			while(n<=4) {
				System.out.print("*");
				n++;
			}
			System.out.println("");
			m++;
		}
	}
}

```

> 案例
>
> 求1!+2!+...+10!的阶乘
>
> 解析

```java
package com.Imooc.flow1;

public class JieChengPlus {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		int s = 1,sum = 0;
		for(int i = 1;i <= 10;i++) {
			s=1;//重新定义
			for(int j = 1;j <= i;j++) {
				//乘积结果
				s *= j;
			}
			sum += s;//累加和
		}
		System.out.println("1!+2!+3!+4!="+sum);
	}

}

```

### 6.break语句

作用:

> * break语句可以结束当前循环的执行
> * 执行完break语句后,循环体中位于break语句后面的语句就不会被执行
> * 在多重循环中,break语句只向外跳一层 

### 7.continue语句

作用

> * continue语句只能用在循环里
> * continue语句可以结束当前循环的执行,但是要继续下一次循环的执行
>
> | i=1  | sum = 0 + 1=1  |
> | ---- | -------------- |
> | i=2  | continue;      |
> | i=3  | sum = 1 + 3 =4 |
> | i=4  | \              |
> | i=5  | sum=4+5=9      |

### 8.debug入门

> 调试的作用:
>
> ​	让程序员能看清程序的每一步的效果,在需要查看结果的时候,使用debug查看实际结果是否与预期结果一致
>
> * 1.设置断点(双击蓝色区域)
> * 2.逐步调试
> * 3.单步调试(f6)

### 总结:

* 流程控制语句:顺序,选择,循环
  * 选择结构
    * if语句
    * if-else语句
    * 多重if-else语句
    * 嵌套if-else语句
    * switch语句(常量)
  * 循环结构
    * while循环
    * do-while循环
    * for循环
    * 嵌套循环
    * break语句和continue语句
* 调试

