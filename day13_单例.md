# 设计模式

简单来说:设计模式是软件开发人员在开发过程中面临一般问题的解决方案

* 设计模式基于场景的解决方案

* 如果某个新场景的解决方案被认可,那我们可以定义一个新的设计模式

* 目的

  * 使得类的一个对象成为该类系统中的一个实例

* 定义

  * 一个类有且仅有一个实例,并且自行实例化向整个系统提供

* 要点:

  * 1. 某个类只能有一个实例
    2. 必须自行创建实例
    3. 必须自行向整个系统提供这个实例

* 实现:

  * 1. 只提供私有的构造方法
    2. 含有一个该类的静态私有对象
    3. 提供一个静态的公有方法用于创建,获取静态私有对象

* 代码实现方案

  * 饿汉式:对象创建过程中实例化

  * ```java
    package com.hare.singleton;
    
    //饿汉式:创建对象实例的时候直接初始化
    public class SingletonOne {
    
    	//1.创建类中的私有构造
    	private SingletonOne() {
    		
    	}
    	
    	//2.创建该类型的私有静态实例
    	private static SingletonOne instance = new SingletonOne();
    	
    	//3.创建公有静态方法返回静态实例对象
    	public static SingletonOne getInstance() {
    		return instance;
    	}
    }
    ```

  * 懒汉式:静态公有方法中实例化

  * ```java
    package com.hare.singleton;
    
    //饿汉式:创建对象实例的时候直接初始化  空间换时间
    //用时间换空间
    public class SingletonOne {
    
    	//1.创建类中的私有构造
    	private SingletonOne() {
    		
    	}
    	
    	//2.创建该类型的私有静态实例
    	private static SingletonOne instance = new SingletonOne();
    	
    	//3.创建公有静态方法返回静态实例对象
    	public static SingletonOne getInstance() {
    		return instance;
    	}
    }
    ```

* 饿汉式pk懒汉式

  * 饿汉式在类加载时就创建实例,空间换时间(线程安全)
  * 饿汉式第一次使用时进行实例化,时间换空间(线程风险)
    * 1. 同步锁
      2. 双重校验锁
      3. 静态内部类
      4. 枚举

* 优点

  * 1. 在内存中只有一个对象,节省内存空间
    2. 避免频繁的创建销毁对象,提高性能
    3. 避免对共享资源的多重占用

* 缺点

  * 1. 扩展笔记困难
    2. 如果实例化后的对象长期不利于,系统将会默认为垃圾进行回收,造成状态丢失

* 使用场景

  * 1. 如果创建对象时占用资源过多,但同时又需要用到该类对象
    2. 对系统内资源要求统一读写,如读写配置信息
    3. 当多个实例存在可能引起逻辑错误,如号码生成器