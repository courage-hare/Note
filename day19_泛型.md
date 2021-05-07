### 1. 泛型

* 泛型作为方法参数
* 自定义泛型类
* 自定义泛型方法

#### 1.1 为什么使用泛型

* 在java中增加泛型之前,泛型的程序设计使用继承来实现的

* 坏处:

  * 需要强制转换
  * 可向集合中添加任意类型的对象,存在风险

* ```java
  List<String> list = new ArrayList<String>();
  ```

* 在java SE7 以后的版本,构造构造方法可以省略泛型类型

* ```java
  List<String> list = new ArrayList<>();
  ```



#### 1.2 多态和泛型

```java
class Animal{}
class Cat extends Animal{}
List<Animal> list = new ArrayList<Cat>();//false
//变量声明的类型必须匹配传递给实际对象类型
//其他错误例子
List<Object> list = new ArrayList<String>();
List<Number> numbers = new ArrayList<Integer>();
```

### 2. 泛型作为方法参数

* 需求分析:
* 定义一个抽象类Goods,包含抽象方法sell()
* 分别定义类Book,Clothes和Shoes继承Goods,并实现sell()方法,输出一句话,如:sell books
* 定义一个商品销售类GoodsSeller,模拟销售,包括方法:
* public void sellGoods(List<Goods> goods),循环使用List对象的sell()方法
* 测试



```java
public void sellGoods(List<? extends Goods> goods)
```

如果泛型作为方法参数时,没有? extends 父类,那么使用方法时,只能是固定类的使用



### 3. 自定义泛型类

* <T> 为占位符,传什么类型它就是什么类型

```
package com.hare.generic;

public class NumGeneric<T> {
	private T num;
	
	public T getNum() {
		return num;
	}
	public void setNum(T num) {
		this.num = num;
	}
	
	//测试
	public static void main(String[] args) {
		NumGeneric<Integer> intNum = new NumGeneric<>();
		intNum.setNum(123);
		System.out.println(intNum.getNum());
		
		NumGeneric<Float> floatNum = new NumGeneric<>();
		floatNum.setNum(12.5f);
		System.out.println(floatNum.getNum());
	}
}

```

* 双参数泛型类

  ```java
  package com.hare.generic;
  
  public class TwoNumGeneric<T,X> {
  	private T num1;
  	private X num2;
  	
  	public void genNum(T num1, X num2) {
  		this.num1 = num1;
  		this.num2 = num2;
  	}
  
  	public T getNum1() {
  		return num1;
  	}
  
  	public void setNum1(T num1) {
  		this.num1 = num1;
  	}
  
  	public X getNum2() {
  		return num2;
  	}
  
  	public void setNum2(X num2) {
  		this.num2 = num2;
  	}
  	
  	//测试
  	public static void main(String[] args) {
  		TwoNumGeneric<Integer,Float> numObj = new TwoNumGeneric<>();
  		numObj.genNum(25, 2.5f);
  		System.out.println(numObj.getNum1()+"   "+numObj.getNum2());
  	}
  }
  
  ```

### 4. 泛型方法

注意书写格式<T>必须在public和void 中间

同样<T extends 父类>也是可以的

```java
package com.hare.generic;

public class GenericMethod {
	public <T> void printValue(T t) {
		System.out.println(t);
	}
	
	public static void main(String[] args) {
		GenericMethod gm = new GenericMethod();
		gm.printValue("hare");
		gm.printValue(123);
		gm.printValue(1.23);
	}
}
```

### 5. 总结

* 为什么使用泛型
  * 可以提供便利,不用在强制转换
  * 避免运行时异常的安全隐患
  * 变量声明的类型,必须和对象类型是一致的
* 泛型作为方法参数
  * <? extends 父类> 子类也可以传入
  * <? super 父类> 这样的话就是 父类的超类也可以
* 自定义泛型类
* 自定义泛型方法