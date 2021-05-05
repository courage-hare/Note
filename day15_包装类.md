# 包装类

* 什么是包装类
* 包装类与基本数据类型之间的对应关系
* 包装类的常用方法

### java中的数据类型

* 包装类的存在就是解决基本数据类型没有属性,方法,无法对象化交互的问题

* 可以和对象一样拥有属性,方法,并且完成对象化交互

  | 基本数据类型 | 对应的包装类 |
  | ------------ | ------------ |
  | byte         | Byte         |
  | short        | Short        |
  | int          | Integer      |
  | long         | Long         |
  | float        | Float        |
  | double       | Double       |
  | char         | Character    |
  | boolean      | Boolean      |

* 装箱

  * 给基本数据类型进行转换变为包装类

* 拆箱

  * 就是装箱的逆运算

### 知识点

* 包装类对象的初始值

  * 包装类对象初始值为null

* 包装类的对象之间比较

  * 只有int 有个-128<= ---- >=127 区间有个对象池

  * ```java
    package com.hare.warp;
    
    public class WrapperTest {
    
    	public static void main(String[] args) {
    		// TODO Auto-generated method stub
    		Integer one = new Integer(100);
    		Integer two = new Integer(100);
    		System.out.println("one == two的结果为:"+(one==two));//false
    		
    		Integer three = 100;//自动装箱
    		System.out.println("three == 100的结果为:"+(three==100));//2 true 自动拆箱
    		
    		Integer four = 100;
    		//Integer four = Intger.valueOf(100);
    		System.out.println("four == three的结果为:"+(three==four));//3  true
    		
    		Integer five = 200;
    		System.out.println("five == 200 的结果:"+(five == 200));//4 true
    		
    		Integer six = 200;
    		System.out.println("six  == five 的结果:"+(five == six))	;//5 false
    		
    		Double d1 = Double.valueOf(200);
    		System.out.println("d1 == 100 的结果为:"+(d1==200));//true
    		
    		Double d2 = Double.valueOf(200);
    		System.out.println("d1 == d2 的结果为:"+(d1==d2));
            //false
    	}
    
    }
    
    ```

    

