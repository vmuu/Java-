###  实践题1
#### 1、下载并安装JDK，设置环境变量
历史JDK地址[：](https://note.youdao.com/)https://jdk.java.net/jmc/8/

环境变量设置：我的电脑-属性-高级系统设置-环境变量-系统变量

变量值：C:\Program Files\Java\jdk1.8.0_181

变量设置参数如下：

变量名：JAVA_HOME
变量值：C:\Program Files (x86)\Java\jdk1.8.0_91        // 要根据自己的实际路径配置
变量名：CLASSPATH
变量值：.;%JAVA_HOME%\lib\dt.jar;%JAVA_HOME%\lib\tools.jar;         //记得前面有个"."
变量名：Path
变量值：%JAVA_HOME%\bin;%JAVA_HOME%\jre\bin;


[Java，JDK安装及环境配置](https://blog.csdn.net/weixin_44893902/article/details/104296736/)
#### 2、自己手动安装完成HelloWold程序

```java
public class HellowWord {
	public static void main(String[] args){
		System.out.print("Hellow Word");
	}
}
```

#### 3、下载eclipse，完成HelloWorld程序。

下载地址：https://www.eclipse.org/downloads/

File-New-Java Project

#### 4、使用Scanner类的输入法方法来输入数据，然后将输入的数据显示在屏幕上。

```java
import java.util.Scanner;

public class MyTest {
	public static void main(String[] args) {
		int flag = 1;
		while (flag!=0) {
			Scanner input = new Scanner(System.in);
			System.out.println("请输入字符：");
			String next = input.next();
			if (next.equals("0")) {
				flag = 0;
				System.err.println("退出成功！");
			}
			System.out.println("【输入0退出】您输入的字符为："+next);
		}
	}
}

```

<br/>

###  实践题2
##### 1、输出1000以内所有的“水仙花数”。水仙花数是指一个3位数，其各位数字的立方和等于该数本身。例如，153是一个水仙花数，因为153=1^3^+1^5^+3^3^。

```java
public class MyTest {
	/*    打印1-1000的水仙花数
    水仙花数：例如  153=1*1*1+5*5*5+3*3*3     */
  public static void main(String[] args) {

    //定义一个变量，水仙花数起始值位0
    int count = 0;
    //要找出1000以内的水仙花数，先要遍历其每个数字；因为水仙花数是三位数所以从100开始
    for (int i = 100; i < 1000; i++) {
      //取出个位
      int g = i%10;
      //取出十位
      int s = i/10%10;
      //取出百位
      int b = i/100;
      //判断每个位上的立方和是否等于它自己，如果是则打印出该数字
      if (g*g*g+s*s*s+b*b*b==i){
        //如果是水仙花数，count加一
        count++;
        System.out.println(i);
      }
    }
    System.out.println("1000以内水仙花数的个数："+count);
  }
}

```



**扩展：**

> 水仙花数只是自幂数的一种，严格来说 3 位数的 3 次幂数才称为水仙花数。

>  附：其他位数的自幂数名字
>  一位自幂数：独身数
>  两位自幂数：没有
>  三位自幂数：水仙花数
>  四位自幂数：四叶玫瑰数
>  五位自幂数：五角星数
>  六位自幂数：六合数
>  七位自幂数：北斗七星数
>  八位自幂数：八仙数
>  九位自幂数：九九重阳数
>  十位自幂数：十全十美数

##### 2、猴子吃桃问题：猴子第一天摘下若干个桃子，当即吃了一半，感觉不够，又多吃了一个。第二天早上又讲剩下的桃子吃掉一半，再多吃一个。以后每天早上都吃前一天剩下的一个零半个。到第十天早上想再吃时，见剩下一个桃子。求第一天共摘了多少个桃子。

从最后一天开始倒推：
```java
public class MyTest {
	public static void main(String[] args) {
		int count = 10; //从第十天开始倒推
		int num = 1; //最后剩下1个桃子
		while (count != 1) { //如果到第一天停止循环
			count--;//每次运行-1
			num = (num + 1) * 2;  // 前一天的桃子数量等于后一天的*2+1。第10天是剩1个
		}
		System.out.println("第一天一共摘了" + tao + "个桃子");
	}
}

```
换一种循环实现：

```java
public class MyTest {
	public static void main(String[] args) {
		int num = 1; //最后剩下1个桃子
		for (int i = 1; i < 10; i++) {
			num = (num + 1) * 2;
		}
		System.out.println("猴子第一天摘了 " + num + " 个桃子");
	}
}

```



```
从第一天到第十天的桃子的减少公式是n/2-1=n;
从第十天到第一天桃子增多的公式是2*(n+1)=n;
因为最后一天的值已经提供，所以此时用倒退的方式；
```

##### 3、大马、小马和马驹共100匹，共驮100片瓦。大马一驮三，小马一驮二，马驹二驮一，一次驮完，三种吗都驮，请输出所有组合。

设大马、中马、马驹各为：
x+y+z=100
3x+2y+z/2=200

```java
public class MyTest {
	public static void main(String[] args) {
		for (int x = 1; x <= 33; x++) {
			for (int y = 1; y <= 50; y++) {
				for (int z = 0; z < 100; z+=2) {
					if (x+y+z==100 & 3*x+2*y+z/2==100) {
						System.out.println("大马："+x+"，中马："+y+"，马驹："+z);
					}
				}
			}
		}
	}
}
```

结果：

```java
大马：2，中马：30，马驹：68
大马：5，中马：25，马驹：70
大马：8，中马：20，马驹：72
大马：11，中马：15，马驹：74
大马：14，中马：10，马驹：76
大马：17，中马：5，马驹：78
```



##### 4、输出九九乘法口诀。

```java
public class MyTest {
	public static void main(String[] args) {
		for (int num1 = 1; num1 <=9; num1++) {
			for (int num2 = 1; num2 <= num1; num2++) {
				System.out.print(num2+"*"+num1+"="+(num1*num2)+" ");
			}
			System.out.println();
		}
	}
}
```

##### 5、有n个小孩围成一个圈，顺序排号。从第一个小孩开始报数（从1到3报数），凡报到3的小孩退出圈外，问最后留下的是原来第几号小孩。



<br/>

###  实践题3

##### 1、定义一个公司员工类：属性有方法、员工号、部门及当前员工对象数；有2个构造方法（一个无参构造和一个姓名、员工号及部门编号的有参构造方法）、获取和设置各属性的方法，以及获取当前员工对象数的方法。
```java
public class Employee {
    private String name; // 姓名
    private int id; // 员工号
    private int num; // 员工数
     
    public Employee() { // 无参构造器
    }
 
    public Employee(String name, int id, int num) { // 有参构造器
        this.name = name;
        this.id = id;
        this.num = num;
    }
    // 属性的get set方法
    public String getName() {
        return name;
    }
 
    public void setName(String name) {
        this.name = name;
    }
 
    public int getId() {
        return id;
    }
 
    public void setId(int id) {
        this.id = id;
    }
 
    public int getNum() {
        return num;
    }
 
    public void setNum(int num) {
        this.num = num;
    }
     
}
```

##### 2、实现一个先进先出（FIFO）队列类（MyQueue），并用测试类进行测试。



##### 3、编写一个方法，计算一个字符串中某一子串的次数并返回。字符串和子串通过方法参数传入。然后用测试类进行测试。



<br/>

###  实践题4

##### 1、定义带默认构造方法的类A和类B，在默认构造方法中分别输出”执行了类A的构造方法！”和执行了类B的构造方法！“。再定义一个类C，然他从类A继承，在类C中定义一个类B的引用属性成员并同时创建一个类B的对象让其指向，在默认构造方法中输出”执行了类C的构造方法！“。定义测试类，在main()方法中创建一个类C的对象，执行程序观察结果并分析

##### 2、定义一个USB接口，在其中定义一个start()方法和一个stop()方法，分别表示USB设备开始和结束工作。定义一个U盘类Flash和打印机类Print实现USB接口。定义一个计算机类Computer，在其中定义一个静态方法plugin()，方法的参数是一个USB接口类型的引用，在方法中调用参数对象的start()方法和stop()方法。定义一个测试类进行测试。

##### 3、定义一个水果接口Fruit，在其中定义一个表示吃水果的方法eat()方法。定义一个苹果类Apple和一个橘子类Orange实现接口Fruit。定义一个工厂类FruitFactory，在其中定一个一个带String类型的参数的静态方法getInstance()，在方法中根据参数创建相应类型的对象（列如，参数是apple，就创建Apple类的对象）并返回对象。定义测试类进行测试。


## 实验与课程设计

### 实验1 Java编程基础 实验题

1、使用循环语句输出如下图案。

```
   *
  ***
 *****
*******
```

代码：
```java
public class MyTest {
	public static void main(String[] args) {
		for (int a = 1; a <= 4; a++) {
            for (int i = 1; i <= 4 - a; i++) {
                System.out.print(" ");
            }
            for (int j = 1; j <= 2*a-1; j++) {
                System.out.print("*");
            }
            System.out.println("");
        }

	}
}
```

```java
public class MyTest {
	public static void main(String[] args) {
		Print(5);
	}

	static void Print(int n) {
		if (n > 0) {
			Print(n - 1);
			for (int i = 5 - n; i > 0; i--) {
				System.out.print(" ");
			}
			for (int j = (n * 2) - 1; j > 0; j--) {
				System.out.print('*');
			}
			System.out.println();
		}
		return;
	}
}
```





###  实践题5