# 2、java运算符

## 2.1表达式

> 表达式有运算符和操作数组成
>
> 如：
>
> 5
>
> num1
>
> num1+num2
>
> sum = num1 + num2(1、加法运算 2、赋值运算)

## 2.2运算符

> 算术运算符
>
> ​	算术运算符主要用于基本的算术运算，如加法减法、乘法和除法等。
>
> ​		\+		加法	5+10=15
>
> ​		\-		减法	10-5=5
>
> ​		\*		乘法	3*6=18
>
> ​		/		除法	36/4 = 9
>
> ​		%		求余数	13%3=1
>
> ​		++		自增1	int n = 3; n++
>
> ​		--		自减1	int n = 4 ; n--
>
> ```java
> 		System.out.println(num1+"+"+num2+"="+result);
> 		//字符串连接
> 		System.out.println(""+num1+num2);
> ```
>
> 以上分两种结果（即为字符串连接时直接进行连接，如没有则相加结果）
>
> ```
> 10+5=15
> 105
> ```
>
> ```
> 		//分子父母都是整型时，结果为整除后的结果
> 		System.out.println(13/5);
> 		//解决方案
> 		System.out.println("13.0/5"+13.0/5);
> ```
>
> 以上为丢失精准度，解决方案为将分子或分母后加.0即可，并且有优先级说法，先执行乘除在进行字符串连接
>
> ```
> 2
> 13.0/52.6
> ```
>
> 先加后赋值
>
> ```
> num2 = ++num1;
> num1=num1+1; 
> num2=num1;
> 
> result:
> num1=2;
> num2=2;
> ```
>
> 先赋值后加
>
> ```
> num2=num1++;
> num2=num1;
> num1=num1+1;
> 
> result:
> num1=2;
> num2=1;
> ```
>
> ----
>
> 赋值运算符
>
> * 格式：变量=表达式；
> * 例：int n = 3; //将3赋值给变量n
> * 注意：赋值运算符是从右向左运算！ 
>
> **例**
>
> * double d = 123.4;double d1 = d;
>
> * 错误的写法：double d ; 123.4 = d;
>
> * 注意：赋值运算符的左边不能是常量；
>
>   **复合赋值运算符**
>
>   运算符		表达式		计算		结果（x=15）
>
>   +=				x+=5			x=x+5	20
>
>   -=				x-=5			x=x-5	10
>
>   *=				x\*=5			x=x\*5	75
>
>   /=				x/=5			x=x/5	3
>
>   %=			x%=5			x=x%5	0
>
> ---
>
> 关系运算符
>
> * 比较运算符用于判断两个数据的大小，如大于
>
> * 比较的结果是一个布尔值
>
>   运算符		名称		表达式		结果
>
>   \>				大于		5>3				true
>
>   \<				小于		5<3				false
>
>   \>=			大于等于	5>=3			true
>
>   <=			小于等于	5<=3			false
>
>   ==			等于		5==3				false
>
>   !=			不等于		5!=3				true
>
> * 例：
>
> * 'A'>'B'结果为false，比较的是两个字符的ASCII值
>
> * 5!=6结果为true，比较数值是否相等
>
> * true == false 结果为false，两个布尔值是不相等的
>
> * float f = 5.0f；long l = 5；f == l； 结果为true，浮点数与整数比较，只要值相等就返回true
>
> ---
>
> 逻辑运算符
>
> ​	名称		运算符			表达式	
>
> ​	与			&&或&			operator1&&operator2
>
> ​	或			||或|			operator1||operator2
>
> ​	非			！					！operator
>
> ​	注意：逻辑运算符的操作数都是布尔型的
>
> * **逻辑“与”运算符**
>
> * 有一个为false，结果为false（&&为短路运算）
>
> * 问题：升学考试、英语、数学、c语言三门总成绩大于等于230，并且英语成绩大于等于60，才能升学
>
> * 三门总成绩大于等于230，表示：sum>=230
>
> * 英语成绩大于等于60，表示en>=60
>
> * **逻辑“或”运算符**
>
> * 有一个为true，结果为true
>
> * ```java
>   int = 3;
>   boolean b = (3<7)|((n++)<2)问：b=？，n=？
>   			true	false
>   b = true
>   n = 4
>   ```
>
> * ||运算符
>
> * ```java
>   int = 3;
>   boolean b = (3<7)||((n++)<2)问：b=？，n=？
>       		true	
>   b = true
>   n = 3
>   ```
>
> * **!运算符**
>
> * 对原条件进行取反
>
> * 例：！（3<5）,结果为false
>
> * 例：输入一个整数，判断是否能被3整除，并且输出相应的提示信息。
>
> ---
>
> 条件运算符
>
> * java中的条件运算符是三目运算符
>
> * 语法：
>
> * 布尔表达式？表达式1：表达式2
>
> * 当布尔表达式为true，则返回表达式1的值，否则返回表达式2的值
>
> * 例。求两个数的最大值
>
> * ```java
>   public class ConditionDemo
>   {
>   	public static void main(String[] args){
>   		//求两个数的最大值
>   		int a = 10,b = 7;
>   		//求a和b的最大值
>   		int max;	//存放最大值
>   		if(a>b){
>   			max = a;
>   		}else{
>   			max = b;
>   		}
>   		System.out.println("max="+max);
>   		//三目运算
>   		max = a > b ? a : b ;
>   		System.out.println("max="+max);
>   		boolean b1 = a>b?(3<6):(true == false);
>   		System.out.println(b1);
>   	}
>   }
>   ```
>
>   
>
> **条件结构**
>
> * 简单if语句的格式：
>
>   ```
>   if(条件){
>   	<语句块>
>   }
>   ```
>
> * 例：商场打折，如果两件商品的总价大于100则减20，并把原价和折扣价分别输出·
>
> ```
> public static void main(String[] args){
> 		//例：商场打折，如果两件商品的总价
> 		//大于100则减20，并把原价和折扣价分别输出
> 		//定义两个变量，分别存放两件衣服的价格
> 		double price1,price2;
> 		price1 = 120;
> 		price2 = 55;
> 		//计算两件商品的总价格
> 		double sum = price1 + price2;
> 		//输出原价
> 		System.out.println("原价为："+sum);
> 		//if语句判断是否满足
> 		if(sum>=100){
> 			sum-=20;
> 			System.out.println("您打过折的价格为："+sum);
> 		}
> 	}
> ```
>
> * if - else 语句的形式
>
>   ```
>   if(true){
>   	<语句块>
>   }else{
>   	<语句块>
>   }
>   ```
>
> * 例：判断一个整数是奇数还是偶数，并将结果打印出来。
>
>   ```
>   import java.util.Scanner;
>   class ConditionDemo2
>   {
>   	public static void main(String[] args){
>   		//判断一个整数是奇数还是偶数，并将结果打印出来。
>   		//定义变量储存数据
>   		//int n = 10;
>   		//从键盘接收数据
>   		System.out.println("请输入一个整数：");
>   		Scanner s = new Scanner(System.in);
>   		int n = s.nextInt();
>   		if(n%2==0){
>   			System.out.println(n+"为偶数");
>   		}else{				
>   			System.out.println(n+"为奇数");
>   		}
>   	}
>   }	
>   ```
>
> 位运算符

## 2.3运算符的优先级

> 运算符						描述

> ()								圆括号

> !,++,--						逻辑非，自增，自减

> *,/,%						乘法，除法，取余

> +,-							加法，减法

> <,<=,>,>=				小于，小于等于，大于，大于等于

> ==,!=						等于，不等于

> &&							逻辑与

> ||							逻辑或

> =,+=,*=,/=,%=,-=		赋值运算符，复合赋值运算符

* 已知int x = 4 ， y = 6;

* n = x * y + ( x % 2 ) - ( x / y )

* n = x * y + 0 - 0

* n = 24 

* n = ?

* n = 24

  ### 综合案例1

  > 用if-else语句判断输入的年份是否为闰年
  >
  > 闰年的判断规则：能被4整除但不能被100整除的年份，或者能被400整除的年份。
  >
  > ```java
  > import java.util.Scanner;
  > public class LeapYearDemo
  > {
  > 	public static void main(String[] args){
  > 		//用if-else语句判断输入的年份是否为闰年
  > 		System.out.println("请输入年份：");
  > 		Scanner sc = new Scanner(System.in);
  > 		int year = sc.nextInt();
  > 		//闰年的判断规则：能被4整除但不能被100整除的年份，或者能被400整除的年份。
  > 		if(((year % 4 == 0) & (year % 100 !=0)) | (year % 400 == 0)){
  > 			System.out.println(year + "是闰年！");
  > 		}else{
  > 			System.out.println(year + "不是闰年！");
  > 		}
  > 	}
  > }
  > ```

## 总结：

> * 什么是表达式？
>   * 5
>   * a
>   * m+3
>   * sum = a + b
>   * n = x * y
> * 运算符