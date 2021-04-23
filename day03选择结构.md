# 1、流程控制

> * 三大流程控制语句：顺序，选择，循环
> * **主要内容**
> * 选择结构
>   * if结构，if-else结构
>   * 多重if
>   * 嵌套if
>   * switch结构
> * 循环结构
>   * while，do-while，for
>   * 循环嵌套

## 1.2选择结构

> ```java
> if（条件）语句；
> if（条件）｛语句｝；
> if（条件）语句1；else语句2；
> ```
>
> * 案例
>   * 需求描述：
>   * 编写一个程序，根据考试成绩，输出相应的评定信息。
>   * 成绩大于等于90分，输出“优秀”；
>   * 成绩大于等于80分切小于90分，输出“良”；
>   * 成绩大于等于60分小于80分，输出"中"；
>   * 成绩小于60分，输出“不及格”；
>   
>   【解析】
>   
>   ```java
>   import java.util.Scanner;
>   class ScoreAssess
>   {
>   	public static void main(String[] args){
>   		/*
>   		* 编写一个程序，根据考试成绩，输出相应的评定信息。
>   		* 成绩大于等于90分，输出“优秀”；
>   		* 成绩大于等于80分切小于90分，输出“良”；
>   		* 成绩大于等于60分小于80分，输出"中"；
>   		* 成绩小于60分，输出“不及格”；
>   		*/
>   		System.out.println("请输入成绩：");
>   		Scanner sc = new Scanner(System.in);
>   		int score = sc.nextInt();
>   		if(score>=90)
>   			System.out.println("优");
>   		else if(score>=80)//相当于score>=80 & score<90
>   			System.out.println("良");
>   		else if(score>=60)//相当于score>=60 & score<80
>   			System.out.println("中");
>   		else
>   			System.out.println("不及格");
>   	}
>   }
>   ```

### 2.嵌套if结构

> if（表达式1）
>
> ​	if（表达式2）
>
> ​		if（表达式3）
>
> ​				语句；
>
> else
>
> ​	语句；
>
> 【案例】
>
> * 从键盘输入两个整数，经过判断输出他们的关系
>
> 【解析】
>
> ```java
> class IntCompare
> {
> 	public static void main(String[] args){
> 		// 从键盘输入两个整数，经过判断输出他们的关系
> 		int x = 5 , y = 10;
> 		//判断x和y是否相等
> 		if(x!=y){
> 			if(x>y){
> 				System.out.println(x+"大于"+y);
> 			}else{
> 				System.out.println(x+"小于"+y);
> 			}
> 		}else{
> 			System.out.println(x+"和"+y+"相等");
> 		}
> 	}
> }
> ```

### 3.if和switch的区别

> *  if结构：
>   * 判断条件是布尔类型
>   * 判断条件是一个范围
> * switch结构：
>   * 判断条件是常量值
>
> switch结构
>
> ```java
> switch(表达式){
> 	case 常量表达式1:
> 		语句1;break;
>     case 常量表达式2:
>     	语句2;break;
>     default:
>     	语句3;
> }
> ```
>
> [注意]
>
> * 大括号不能取消
> * 关键字 case
> * 关键字 break(不是必须的)
> * default (所有条件都不满足,执行default)
>
> [案例]
>
> * 从键盘输入1-7之间的任意数字,分别输出对应信息.
>
> * 1>>>星期一
>
> * 2>>>星期二
>
> * 3>>>星期三
>
> * 4>>>星期四
>
> * 5>>>星期五
>
> * 6>>>星期六
>
> * 7>>>星期日
>
>   ```java
>   import java.util.Scanner;
>   public class InputWeek
>   {
>   	public static void main(String[] args){
>   		/** 从键盘输入1-7之间的任意数字,分别输出对应信息.
>   
>   		* 1>>>星期一
>   
>   		* 2>>>星期二
>   
>   		* 3>>>星期三
>   
>   		* 4>>>星期四
>   
>   		* 5>>>星期五
>   
>   		* 6>>>星期六
>   
>   		* 7>>>星期日  
>   		*/
>   		System.out.println("请输入数字:");
>   		Scanner sc = new Scanner(System.in);
>   		int week = sc.nextInt();
>   		switch(week){
>   			case 1:
>   				System.out.println("星期一");
>   			break;
>   			case 2:
>   				System.out.println("星期二");
>   			break;
>   			case 3:
>   				System.out.println("星期三");
>   			break;
>   			case 4:
>   				System.out.println("星期四");
>   			break;
>   			case 5:
>   				System.out.println("星期五");
>   			break;
>   			case 6:
>   				System.out.println("星期六");
>   			break;
>   			case 7:
>   				System.out.println("星期日");
>   			break;
>   			default:
>   				System.out.println("输入有误,程序终止!");
>   		}
>   	}
>   }
>   ```
>   
>   [字符串类型使用switch]
>   
>   ```java
>   import java.util.Scanner;
>   public class WeekDemo
>   {
>   	public static void main(String[] args){
>   		//以字符串形式使用switch
>   		//提示
>   		System.out.println("请输入汉字星期几:");
>   		//录入键盘
>   		Scanner sc = new Scanner(System.in);
>   		String week = sc.next();
>   		//开始switch语句
>   		switch(week){
>   			//case字符串也要加""
>   			case "星期一":
>   				System.out.println("星期一");
>   			break;//跳出循环
>   			//default 跳出
>   			default:
>   				System.out.println("输入有误!");
>   		}
>   	}
>   }
>   ```
>   
>   