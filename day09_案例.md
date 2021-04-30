# 案例

---

模拟场景实现:

​	专业计算机科学与应用(学科专业类)

​	专业编号为:J0001

​	学制年限:4年

三个学生(学生类)

> | 姓名 | 学号 | 姓名 | 年龄 |
> | ---- | ---- | ---- | ---- |
> | 张三 | s01  | 男   | 18岁 |
> | 李四 | s02  | 女   | 17岁 |
> | 王五 | s03  | 男   | 18岁 |

一共4个对象

* 类:
  * 专业
    * 专业名称,编号,学制年限
  * 学生
    * 姓名,学号,性别,年龄

> 学科专业类关联起来的三种方案
>
> 方案一:在方法中添加2个参数.分别表示专业名称和学制年限(好理解)
>
> 风险:描述多时,参数列表会过长
>
> ```java
> /**
> 	 * 学生自我介绍的方法
> 	 * 
> 	 * @param subjectName 所学专业名称
> 	 * @param subjectLife 学制年限
> 	 * @return 自我介绍的信息,姓名,学号,性别,年龄,所学专业,学制年限
> 	 * 方案一
> 	 */
> 	public String intoduction(String subjectName, int subjectLife) {
> 		String str = "学生信息如下:\n姓名:" + this.getStudentName() + "\n学号:" + this.getStudentNo() + "\n性别:"
> 				+ this.getStudentSex() + "\n年龄:" + this.getStudentAge() + "\n所报的专业名称:" + subjectName + "\n学制年限:"
> 				+ subjectLife;
> 		return str;
> 	}
> ```
>
> 方案2:在方法中添加1个专业对象作为参数,通过其属性获得相关信息(简单)
>
> 与方案3 的区别:专业和学生的关联强调没有那么强
>
> ```java
> /**
> 	 * 学生自我介绍的方法
> 	 * 
> 	 * @param mySubject 所选专业的对象
> 	 * @return自我介绍的信息,姓名,学号,性别,年龄,所学专业,学制年限,专业编号
> 	 * 方案二
> 	 */
> 	public String introduction(Subject mySubject) {
> 		String str = "学生信息如下:\n姓名:" + this.getStudentName() + "\n学号:" + this.getStudentNo() + "\n性别:"
> 				+ this.getStudentSex() + "\n年龄:" + this.getStudentAge() + "\n所报的专业名称:" + mySubject.getSubjectName()
> 				+ "\n学制年限:" + mySubject.getSubjectLife() + "\n专业编号:" + mySubject.getSubjectNo();
> 		return str;
> 	}
> ```
>
> 方案3:在类中添加专业对象作为属性,通过其属性获得相关信息.(关联性更强)
>
> ```java
> private Subject studentSubject;//方案三
> 
> 
> /**
> 	 * 学生自我介绍的方法
> 	 * 
> 	 * @return 自我介绍的信息,姓名,学号,性别,年龄
> 	 * 方案三
> 	 */
> 	public String introduction() {
> 		String str = "学生信息如下:\n姓名:" + this.getStudentName() + "\n学号:" + this.getStudentNo() + "\n性别:"
> 				+ this.getStudentSex() + "\n年龄:" + this.getStudentAge()+ this.getStudentAge() + "\n所报的专业名称:" + this.getStudentSubjcet().getSubjectName() + "\n学制年限:"
> 						+ this.getStudentSubjcet().getSubjectLife();
> 		return str;
> 	}
> 
> ```
>
> 当对象作为参数时,引用的是参数的地址,可以使用对象的所以信息

关于addStudent的几点疑问

* 为什么添加学生的操作不放在构造方法或者set方法中
  * 构造方法在对象构造时产生
  * set主要用于属性赋值,参数是学生类型的数组
* 为什么方法通过get方法进行数组成员赋值而不是set
  * 需要先取到数据才能装填,直接赋值不太可能
  * 且有空间位置
* 为什么要通过get方法获取数组取得长度,直接用属性不行么
  * 因为要用get所以保证添加学生没有问题,所以先进行确认不是空的