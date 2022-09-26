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

#### 4、使用Scanner类的输入法方法来输入数据，然后将输入的数据显示在屏幕上。


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
x+y+z=100 .(1)
3x+2y+1/2z=100,即6x+4y+z=200 .(2)

(2)-(1)：5x+3y=100
3y=100-5x=5(20-x)
y必须是5的倍数,20-x必须是3的倍数

(1)*4-(2)：-2x+3z=200
z=2(x+100)/3
20-x可能等于3,6,9,12,15,18
20-x=3时x=17,y=5,z=78
20-x=6时x=14,y=10,z=76
20-x=9时x=11,y=15,z=74
20-x=12时x=8,y=20,z=72
20-x=15时x=5,y=25,z=70
20-x=18时x=2,y=30,z=68

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

##### 2、实现一个先进先出（FIFO）队列类（MyQueue），并用测试类进行测试。

##### 3、编写一个方法，计算一个字符串中某一子串的次数并返回。字符串和子串通过方法参数传入。然后用测试类进行测试。

