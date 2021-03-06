### 综合案例

> * 需求:定义一个类,对数组中的数据进行管理.
>
> * 方法:
>
> * 插入数据:
>
>   ```java
>   public int[] insertDate(){}
>   ```
>
> * 显示所有数据:
>
>   ```java
>   public void showDate(int[] a , long leght){}
>   ```
>
> * 在指定位置处插入数据:
>
>   ```java
>   public void insertAtArray(int[] a, int n,int k){}
>   ```
>
> * 查询能被3整数的数据:
>
>   ```java
>   public void divThree(int[] a){}
>   ```
>
>   code:
>
>   ```java
>   package com.imooc.datamanage;
>   
>   import java.util.Scanner;
>   
>   /**
>    * 从键盘接收整型数据存放数组中,并对数组中的数据进行管理
>    * 
>    * @author hare
>    *
>    */
>   public class DataManage {
>   	/**
>   	 * 从键盘接收数据
>   	 * 
>   	 * @return接收数据的数组
>   	 */
>   	public int[] insertData() {
>   		int[] a = new int[10];
>   		Scanner sc = new Scanner(System.in);
>   		// 少接收一个数据,为在指定位置处插入数据作准备
>   		for (int i = 0; i < a.length - 1; i++) {
>   			System.out.println("请输入第" + (i + 1) + "个数据:");
>   			try {
>   				a[i] = sc.nextInt();
>   			} catch (java.util.InputMismatchException e) {
>   				System.out.println("输入的数据格式有误,不能有非数字");
>   				sc.next();
>   				i--;
>   			}
>   		}
>   		return a;
>   	}
>   
>   	/**
>   	 * 显示数组中元素的内容
>   	 * 
>   	 * @param a      数组
>   	 * @param length 要显示数组元素的个数
>   	 */
>   	public void showDate(int[] a, int length) {
>   		for (int i = 0; i < length; i++) {
>   			System.out.print(a[i] + ",");
>   		}
>   		System.out.println();
>   	}
>   
>   	/**
>   	 * 从键盘接收一个数据,插入到数组的指定位置处
>   	 * 
>   	 * @param a 要插入数据的数组
>   	 * @param n 要插入数组的数据
>   	 * @param k 要插入的位置,从0开始
>   	 */
>   	public void insertAtArray(int[] a, int n, int k) {
>   		// 注意从最后一个数据开始移动,避免数据覆盖
>   		for (int i = a.length - 1; i > k; i--) {
>   			a[i] = a[i - 1];
>   		}
>   		a[k] = n;
>   	}
>   
>   	/**
>   	 * 输出数组中能被3整除的元素
>   	 * 
>   	 * @param a 数组
>   	 */
>   	public void divThree(int[] a) {
>   		String str = "";// 元素存入str
>   		int count = 0;// 可以被3整除的个数
>   		for (int n : a) {
>   			if (n % 3 == 0) {
>   				str = str + n + "  ";
>   				count++;
>   			}
>   		}
>   		if (count == 0) {
>   			System.out.println("数组中没有能被3整除的元素1");
>   		} else {
>   			System.out.println("数组中能被3整除的元素为:" + str);
>   		}
>   	}
>   
>   	/**
>   	 * 提示信息
>   	 */
>   	public void notice() {
>   		System.out.println("**************************");
>   		System.out.println("      1.插入数据");
>   		System.out.println("      2.显示所以数据");
>   		System.out.println("      3.在指定位置处插入数据");
>   		System.out.println("      4.查询能被3整除的数据");
>   		System.out.println("      0.退出");
>   		System.out.println("**************************");
>   	}
>   
>   	public static void main(String[] args) {
>   		DataManage dm = new DataManage();
>   		Scanner sc = new Scanner(System.in);
>   		int input = 0;
>   		int[] a = null;
>   		int n = 0, k = 0;// n表示插入的数据,k插入位置
>   		while (true) {
>   			dm.notice();
>   			System.out.println("请输入对应的数字,进行操作:");
>   			try {
>   				input = sc.nextInt();
>   			} catch (java.util.InputMismatchException e) {
>   				System.out.println("输入的数据格式有误,不能有非数字!");
>   				sc.next();
>   				continue;
>   			}
>   			if (input == 0) {
>   				System.out.println("退出程序!");
>   				break;
>   			}
>   			switch (input) {
>   			case 1:
>   				// 插入数据
>   				a = dm.insertData();
>   				// 显示数据
>   				System.out.println("数组元素为:");
>   				dm.showDate(a, a.length - 1);
>   				break;
>   			case 2:
>   				if (a != null) {
>   					System.out.println("数组元素为:");
>   					if (a[a.length - 1] == 0) {
>   						// 如果数组的最后一个元素为0,说明还没有插入数据,因此不显示最后一个元素
>   						dm.showDate(a, a.length - 1);
>   					} else {
>   						dm.showDate(a, a.length);
>   					}
>   				} else {
>   					System.out.println("还未在数组中插入数据,请重新选择操作!");
>   				}
>   				break;
>   			case 3:
>   				// 在指定位置处插入数据
>   				if (a != null) {
>   					System.out.println("请输入要插入的数据:");
>   					try {
>   						n = sc.nextInt();
>   						System.out.println("请输入要插入数据的位置:");
>   						k = sc.nextInt();
>   					} catch (java.util.InputMismatchException e) {
>   						System.out.println("输入的数据格式有误,不能有非数字!");
>   						sc.next();
>   						break;
>   					}
>   					dm.insertAtArray(a, n, k);
>   					dm.showDate(a, a.length);
>   				} else {
>   					System.out.println("还未在数组中插入数据,请重新选择操作!");
>   				}
>   				break;
>   			case 4:
>   				//查询数组中能被3整除的元素
>   				if(a!=null) {
>   					dm.divThree(a);
>   				}else {
>   					System.out.println("还未在数组中插入数据,请重新选择操作!");
>   				}
>   				break;
>   			}
>   		}
>   	}
>   }
>   ```
>
>   

