### 集合排序

> * 集合中的基本数据类型排序
> * 集合中的字符串排序
> * Comparator接口
> * Comparable接口

#### 1.1 回顾

> * 数组的排序
>
>   ```java
>   int[] arr = {12,3,532,13,13};
>   Arrays.sort(arr)
>   ```
>
> * 使用Collections类的sort()方法
>
>   * sort(List<T> list)
>     * 根据元素的自然顺序对指定列表按升序进行排序

### 例题

> 例1:对存放在List中的整型数据进行排序
>
> ```java
> package com.hare.sort;
> 
> import java.util.ArrayList;
> import java.util.Collections;
> import java.util.List;
> 
> 
> public class IntSort {
> 
> 	public static void main(String[] args) {
> 		//对存储在List中的整型数据进行排序
> 		List<Integer> list = new ArrayList<Integer>();
> 		list.add(5);
> 		list.add(9);
> 		list.add(3);
> 		list.add(1);
> 		System.out.println("排序前:");
> 		for(int n : list) {
> 			System.out.print(n+" ");
> 		}
> 		System.out.println();
> 		//对list中的数据进行排序
> 		Collections.sort(list);
> 		System.out.println("排序后:");
> 		for(int n : list) {
> 			System.out.print(n + " ");
> 		}
> 	}
> 
> }
> 
> ```
>
> 例2:对存放在List中的字符串进行排序
>
> ```java
> package com.hare.sort;
> 
> import java.util.ArrayList;
> import java.util.Collections;
> import java.util.List;
> 
> public class StringSort {
> 
> 	public static void main(String[] args) {
> 		// 对存放在List中的字符串进行排序
> 		List<String> list = new ArrayList<String>();
> 		
> 		list.add("orange");
> 		list.add("blue");
> 		list.add("yellow");
> 		list.add("gray");
> 		System.out.println("排序前:");
> 		for(String s: list) {
> 			System.out.print(s + " ");
> 		}
> 		System.out.println();
> 		Collections.sort(list);
> 		System.out.println("排序后:");
> 		for(String s: list) {
> 			System.out.print(s + " ");
> 		}
> 	}
> 
> }
> 
> ```

### Comparator接口

* 强行对某个对象进行整体排序的比较函数.
* 可以将Comparator传递给sort方法(如Collections.sort或Array.sort)
* int compare(T o1, T o2)比较用来排序的两个参数
  * 如果o1<o2,返回负整数
  * 如果o1 == o2,返回0
  * 如果o1 > o2,返回正整数
* boolean equals(Object obj)指示某个其他对象是否"等于"次Comparator
* 此方法可以被Object类中的equals方法覆盖,不必重写

例:对宠物分别按名字升序,年龄降序进行排序

```java
package com.hare.sort;

public class Cat {
	private String name;
	private int month;
	private String species;
	
	public Cat() {
		super();
	}
	public Cat(String name, int month, String species) {
		super();
		this.name = name;
		this.month = month;
		this.species = species;
	}
	public String getName() {
		return name;
	}
	public void setName(String name) {
		this.name = name;
	}
	public int getMonth() {
		return month;
	}
	public void setMonth(int month) {
		this.month = month;
	}
	public String getSpecies() {
		return species;
	}
	public void setSpecies(String species) {
		this.species = species;
	}
	@Override
	public String toString() {
		return "[名字=" + name + ", 年龄=" + month + ", 品种=" + species + "]";
	}
	
}

```

```java
package com.hare.sort;

import java.util.Comparator;

public class NameComparator implements Comparator<Cat> {

	@Override
	public int compare(Cat o1, Cat o2) {
		// 按名字升序排序
		String name1 = o1.getName();
		String name2 = o2.getName();
		int n = name2.compareTo(name1);
		return n;
	}

}

```

```java
package com.hare.sort;

import java.util.Comparator;

public class AgeComparator implements Comparator<Cat> {

	@Override
	public int compare(Cat o1, Cat o2) {
		// 按年龄降序排序
		int age1 = o1.getMonth();
		int age2 = o2.getMonth();
		return age2-age1;
	}

}

```

```java
package com.hare.sort;

import java.util.ArrayList;
import java.util.Collections;
import java.util.List;

public class CatTest {

	public static void main(String[] args) {
		// 按名字升序排序
		Cat huahua = new Cat("huahua",5,"英国短毛猫");
		Cat fanfan = new Cat("fanfan",2,"中华田园猫");
		Cat maomao = new Cat("maomao",3,"中华田园猫");
		
		List<Cat> catList = new ArrayList<Cat>();
		catList.add(maomao);
		catList.add(fanfan);
		catList.add(huahua);
		
		//排序前
		System.out.println("按名字排序前:");
		for(Cat cat: catList ) {
			System.out.println(cat);
		}
		//按名字进行升序排序
		Collections.sort(catList, new NameComparator());
		System.out.println("按名字排序后:");
		for(Cat cat: catList ) {
			System.out.println(cat);
		}
		
		//按年龄进行降序排序
		Collections.sort(catList, new AgeComparator());
		System.out.println("按年龄降序后:");
		for(Cat cat: catList ) {
			System.out.println(cat);
		}

	}

}

```

### Comparable接口

* 此接口强行对实现它的每个类的对象进行整体排序
* 这种排序被称为类的自然排序,类的compareTo方法被称为它的自然比较方法
* 对于集合,通过调用Collections.sort方法进行排序
* 对于数组,通过调用Arrays.sort方法进行排序



* int compareTo(T o)方法

* 该对象小于,等于或大于指定对象,则分别返回负整数,零或正整数

* 例题:对商品价格进行降序排列

* ```java
  package com.hare.sort;
  
  public class Goods implements Comparable<Goods> {
  
  	@Override
  	public int compareTo(Goods o) {
  		// 按照商品价格进行降序排序
  		//取出商品价格
  		double price1 = this.getPrice();
  		double price2 = o.getPrice();
  		int n = new Double(price2 - price1).intValue();
  		return n;
  	}
  
  	private String id;
  	private String name;
  	private double price;
  	public Goods(String id, String name, double price) {
  		super();
  		this.id = id;
  		this.name = name;
  		this.price = price;
  	}
  	public String getId() {
  		return id;
  	}
  	public void setId(String id) {
  		this.id = id;
  	}
  	public String getName() {
  		return name;
  	}
  	public void setName(String name) {
  		this.name = name;
  	}
  	public double getPrice() {
  		return price;
  	}
  	public void setPrice(double price) {
  		this.price = price;
  	}
  	@Override
  	public String toString() {
  		return "Goods [商品编号=" + id + ", 商品名称=" + name + ", 商品价格=" + price + "]";
  	}
  	
  }
  
  ```

  ```java
  package com.hare.sort;
  
  import java.util.ArrayList;
  import java.util.Collections;
  import java.util.List;
  
  public class GoodsTest {
  
  	public static void main(String[] args) {
  		Goods g1 = new Goods("s0001","手机",2000);
  		Goods g2 = new Goods("s0002","冰箱",5000);
  		Goods g3 = new Goods("s0003","电视机",3000);
  		
  		List<Goods> goodsList = new ArrayList<Goods>();
  		
  		goodsList.add(g1);
  		goodsList.add(g2);
  		goodsList.add(g3);
  		
  		System.out.println("排序前的数据是:");
  		for(Goods goods : goodsList) {
  			System.out.println(goods);
  		}
  		Collections.sort(goodsList);
  		System.out.println("排序后的数据是:");
  		for(Goods goods : goodsList) {
  			System.out.println(goods);
  		}
  	}
  
  }
  
  ```



### Comparator和Comparable的区别

| Comparator                              | Comparable                        |
| --------------------------------------- | --------------------------------- |
| 位于java.util包                         | 位于java.lang包                   |
| 在要比较的类的外部实现该接口            | 在比较的类上实现该接口            |
| 调用sort方法是,要指定Comparator的实现类 | 调用sort方法时,只需指定集合名即可 |

Comparator

	1. 实现要比较的类
 	2. 实现Comparator接口
 	3. 测试

Comparable

	1. 定义要比较的类,并实现Comparable接口
 	2. 测试