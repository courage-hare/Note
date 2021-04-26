### 面向对象

---

> 万物皆对象

#### 1.1 什么是面向对象

> * 人关注的对象
> * 人关注事物信息

#### 1.2 类和对象

> * 类是模子,确定对象将会拥有的特征(属性)和行为(方法)
>   * 概念性
> * 对象是类的实例化表现
>   * 真实的
> * 类是对象的类型
> * 对象是特定类型的数据

#### 1.3 属性和方法

> * 属性:对象具有的各种静态特征
>   * 对象有什么
> * 方法:对象具体有的各种动态行为
>   * 对象能做什么

#### 1.4 类和对象的关系

> * 类
>   * 抽象的概念
>   * 模板
> * 对象
>   * 一个看得见,摸得着的具体实体
>
> 类>>>>实例化对象

#### 2. 类的使用

> ```java
> package com.immoc.animal;
> /**
>  * 宠物猫类
>  * @author hare
>  *
>  */
> public class cat {
> 	//成员属性:昵称,年龄,体重,品种
> 	String name;//名字
> 	float month;//年龄
> 	double weight;//体重
> 	String species;//品种
> 	
> 	//成员方法:跑,吃东西
> 	//跑动的方法
> 	public void run() {
> 		System.out.println("小猫会跑");
> 	}
> 	//吃东西的方法
> 	public void eat() {
> 		System.out.println("小猫会吃鱼");
> 	}
> }
> ```
>
> 对于一个类的属性都是有默认值的

#### 3. 实例化对象

> ```java
> package com.immoc.animal;
> 
> public class CatTest {
> 	public static void main(String[] args) {
> 		//对象实例化
> 		Cat one = new Cat();
> 		//调用猫的跑动,吃饭
> 		one.eat();
> 		one.run();
> 		
> 		one.name ="花花";
> 		one.month=2.5f;
> 		one.weight=1000;
> 		one.species="英国短毛猫";
> 		System.out.println("年龄:"+one.month);
> 		System.out.println("昵称:"+one.name);
> 		System.out.println("体重:"+one.weight);
> 		System.out.println("品种:"+one.species);
> 		one.run(one.name);
> 		
> 	}
> }
> 
> ```

### 4. 单一职责原则

> 有且只有一个引起功能变化的原因.
>
> 一个类只有一个功能,只干一件事
>
> 将不同职责的类,放入不同的类
>
> 减少耦合性
>
> 
>
> 类间如何识别
>
> * 本类
>   * 本包

### 5. new关键字

> ```java
> cat one = new cat();
> ```
>
> 对象实例化
>
> * 实例化对象可以分为2部分:
>   * 声明对象 Cat one
>     * 只是在'栈'中开了一个空间,实际是空的
>   * 实例化对象 new Cat()
>     * 在'堆'里面开辟了一块空间
>
> ```java
> package com.immoc.animal;
> 
> public class CatTest {
> 	public static void main(String[] args) {
> 		//对象实例化
> 		Cat one = new Cat();
> //		Cat two = new Cat();
> 		Cat two = one;
> //		Cat one;//声明对象
> 		//调用猫的跑动,吃饭
> 		
> 		one.name ="花花";
> 		one.month=2.5f;
> 		one.weight=1000;
> 		one.species="英国短毛猫";
> 		two.month=2.5f;
> 		two.name ="凡凡";
> 		two.weight=800;
> 		two.species="中华田园猫";
> 		System.out.println("年龄:"+one.month);
> 		System.out.println("昵称:"+one.name);
> 		System.out.println("体重:"+one.weight);
> 		System.out.println("品种:"+one.species);
> 		System.out.println("===========================");
> 		System.out.println("年龄:"+two.month);
> 		System.out.println("昵称:"+two.name);
> 		System.out.println("体重:"+two.weight);
> 		System.out.println("品种:"+two.species);
> 	}
> }
> ```
>
> 几点注意事项
>
> * 需要多次访问一对象时,必须进行声明
>
>   * new Cat().ear();
>
> * 同一范围内,不能定义同名对象
>
>   * 相同范围内,不能出现
>
> * 可以同时声明多个引用,用逗号隔开;
>
>   * ```java
>     Cat one,two;
>     one = new Cat()
>     two = new Cat()
>     
>     Cat three = new Cat(),four = new Cat()
>     ```

### 6. 构造方法

> 构造函数,构造器
>
> 必须要用new ,不能被单独调用
>
> 语法结构:
>
>  * 构造方法与类名同名且没有返回值
>
>  * 构造方法的语句格式
>
>  * 只能在对象实例化的时候调用
>
>  * 当没有指定构造方法时,系统会自动添加无参的构造方法
>
>  * 当有指定构造方法,无论是有参,无参的构造方法,都不会自动添加无参的构造方法
>
>  * 一个类中可以由多个构造方法
>
>    ```java
>    public 构造方法名(){//初始化代码}
>    ```
>
>    ```java
>    public Cat() {
>    		
>    	}
>    	public Cat(String name) {
>    		System.out.println("我是有参构造方法");
>    	}
>    	public Cat(String newName,float newMonth,double newWeight,String newSpecies) {
>    		name = newName;
>    		month = newMonth;
>    		weight = newWeight;
>    		species = newSpecies;
>    	}
>    ```

### 7. this关键字

> ```java
> public Cat(String name,float month,double weight,String species) {
> 		this.name = name;
> 		this.month = month;
> 		this.weight = weight;
> 		this.species = species;
> 	}
> ```

# 总结

* 关注现实存在的事物的各方面的信息,从对象的角度出发,根据事物的特征进行程序设计

* 对象:用来描述客观事物的一个实体

* 类:具有相同属性和方法的一组对象的集合

  * 属性(成员属性)
  * 方法(成员方法)

* 定义类

  ```java
  public class 类名{
  //定义属性部分
  [访问修饰符] 数据类型 属性名;
  
  //定义方法部分
  [访问修饰符] 返回类型 方法名(参数){
  
  	}
  }
  ```

* 创建并引用对象

  ```java
  类名 对象名 = new 构造方法();
  对象名.属性
  对象名.方法名()
  ```

* 实例化对象的过程可以分成两部分

  * 声明对象	Cat one
  * 实例化对象  new Cat();
  * Cat one = new Cat();

* 构造方法

  * 构造方法与类名同名且没有返回值

    ```java
    public 构造方法名(){
    //初始化代码
    }
    ```

  * 只能在对象实例化时使用
  * 一个类可以有多个构造方法---构造方法重载
  * 当没有指定构造方法时,系统会自动添加无参的构造方法
  * 当有指定构造方法,无论有参,无参的构造方法,都不会自动添加无参构造方法

* this关键字

  * this:当前对象默认引用
  * this的使用
    * 调用成员属性,解决成员属性的局部变量同名冲突
    * 调用成员方法
    * 调用重载的构造方法(必须放在方法体的第一条)

通常先来定义类,在进行实例化对象





> 栈:局部变量
>
> 堆:动态数据





