# 字符串处理类

* 如何创建String 对象
* String对象的常用方法
* ==和equals方法的区别
* String的不可变性

### 创建String对象的方法

```java
String s1 = "hare";	//创建了一个字符串对象,名为s1
String s2 = new String();	//创建了一个空字符串对象,名为s2
String s3 = new String("hare");	//创建了一个字符串对象hare,名为s3
```

* 字符串charAt(),substring()

* ```java
  package com.hare.string;
  
  public class StringDemo1 {
  
  	public static void main(String[] args) {
  		//定义一个字符串"JAVA 编程 基础"
  		String str = "JAVA 编程 基础";
  		//打印字符串的长度
  		System.out.println("字符串的长度为:"+str.length());
  		
  		//取出字符'程'并输出
  		System.out.println(str.charAt(6));
  		
  		//取出子串"编程 基础"并输出
  		System.out.println(str.substring(5));
  		
  		//取出子串"编程"并输出
  		System.out.println(str.substring(5, 7));
  	}
  
  }
  
  ```

* 字符串indexOf(),lastIndexOf()

* ```java
  package com.hare.string;
  
  public class StringDemo2 {
  
  	public static void main(String[] args) {
  //		String str = "JAVA编程基础,我喜欢java编程";
  		
  		String str = new String("JAVA编程基础,我喜欢java编程");
  		
  		//查找字符A在字符串第一次出现的位置
  		System.out.println("字符A在字符串第一次出现的位置:"+str.indexOf('A'));
  
  		//查找子串"编程"在字符串第一次出现的位置
  		System.out.println("字符\"编程\"在字符串第一次出现的位置:"+str.indexOf("编程"));
  		
  		//查找字符A在字符串最后一次出现的位置
  		System.out.println("字符A在字符串最后一次出现的位置:"+str.lastIndexOf('A'));
  		
  		//查找子串"编程"在字符串最后一次出现的位置
  		System.out.println("字符\"编程\"在字符串最后一次出现的位置:"+str.lastIndexOf("编程"));
  		
  		//在字符串index值为8的位置开始,查找子串"编程"第一次出现的位置
  		System.out.println("在字符串index值为8的位置开始,查找子串\"编程\"第一次出现的位置:"+str.indexOf("编程",8));
  	}
  
  }
  
  ```

* 字符串:byte数组和字符串转换

* ```java
  package com.hare.string;
  
  import java.io.UnsupportedEncodingException;
  
  public class StringDemo3 {
  
  	public static void main(String[] args) throws UnsupportedEncodingException {
  		// 字符串和byte数组直接的转换
  		//定义一个字符串
  		String str = new String("JAVA 编程 基础");
  		//将字符串转换为byte数组,并打印输出
  		byte[] arrs = str.getBytes("UTF-8");
  		for(int i = 0 ; i < arrs.length;i++) {
  			System.out.print(arrs[i]+" , ");
  		}
  		
  		System.out.println();
  		//将byte数组转换为字符串
  		//编码问题
  		String str1 = new String(arrs,"UTF-8");
  		System.out.println(str1);
  	}
  
  }
  ```

  * 字符串可以通过String构造方法改变编码形式,但是要注意的是编码应和转换前编码保持一致,不然会中文乱码
  * 异常处理机制UnsupportedEncodingException



### == 和 equals 

```java
package com.hare.string;

public class StringDemo4 {

	public static void main(String[] args) {
		// == 和 equals 方法区别
		//定义3个字符串,内容都是hare
		String str1 = "hare";
		String str2 = "hare";
		String str3 = new String("hare");

		System.out.println("str1和str2内容相同么?"+(str1.equals(str2)));//true
		System.out.println("str1和str3内容相同么?"+(str1.equals(str3)));//true
		
		System.out.println("str1和str2地址相同么?"+(str1==str2));//true
		System.out.println("str1和str3地址相同么?"+(str1==str3));//false
	}

}

```

### String的不变性

* 只是指向变了,内容是不变的,存在常量池中

* ```java
  package com.hare.string;
  
  public class StringDemo6 {
  
  	public static void main(String[] args) {
  		// TODO Auto-generated method stub
  		//String的不变性
  		//String的对象一旦被创建,则不能修改,是不可变的
  		//所谓的修改其实是创建了新的对象,所指向的内存空间不变
  		String s1 = "hare";
  		String s2 = "hello,"+s1;
  		//s1不再指向hare所在的内存空间,而是指向了"hello,hare"
  		System.out.println("s1="+s1);
  		System.out.println("s2="+s2);
  		
  		String s3 = new String("hello,hare");
  		System.out.println("子串:"+s3.substring(0,5));
  		System.out.println("s3= "+s3);
  		
  	}
  
  }
  
  ```



### StringBuilder

* String 和 StringBuilder 的区别:
  * String具有不可变,而StringBuilder不具备
* 建议:
  * 当频繁操作字符串时,使用StringBuilder
* StringBuilder和StringBuffer
* 二者基本相似
* StringBuffer是线程安全的,StringBuilder是没有,所以性能略高





* 方法

  * StringBuilder append(String str)
  * StringBuilder delete(int start,int end)
  * StringBuilder insert(int offset,String str)
  * StringBuilder replace(int start, int end, String str)

  ```java
  package com.hare.string;
  
  public class StringBuilderDemo1 {
  
  	public static void main(String[] args) {
  		//定义一个字符串"你好"
  		StringBuilder str = new StringBuilder("你好");
  		
  		//在"你好"后面添加内容,将字符串编程"你好,hare"
  //		str.append(",");
  //		str.append("hare!");
  //		System.out.println("str="+str);
  		System.out.println("str="+str.append(",").append("hare!"));
  
  		//将字符串变成"你好,HARE!"
  		//两种方式
  		//1.使用delete方法删除hare,然后插入HARE
  //		System.out.println("替换后:"+str.delete(3, 7).insert(3, "HARE"));
  		
  		//2.使用replace方法直接替换
  		System.out.println("替换后:"+str.replace(3, 7, "HARE"));
  		
  		//在字符串"你好,hare"中提取"你好"并输出
  		System.out.println(str.substring(0,2));
  	}
  
  }
  
  ```





# 总结

* String和StringBuilder(性能好)
* 两个类的常用方法
* 在String中介绍了 == 和equals()方法的区别
  * 地址和内容
* String 和StringBuilder 区别, 主要是不可变性