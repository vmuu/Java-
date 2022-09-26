### 课本实例

#### 【实例 1-1】使用read()方法从键盘输入字符

```java
import java.io.IOException;

// 【实例 1-1】使用read()方法从键盘输入字符
public class ReadDemo {
	public static void main(String[] args) {
		char ch;
		System.out.println("请输入一个字符：");
		try {
			ch = (char) System.in.read();//使用read()方法返回int类型0~255的值
			System.out.println(ch);
		} catch (IOException e) {
			e.printStackTrace();
		}
	}
}
```

#### 【实例 1-2】使用Scanner类进行键盘输入

```java
import java.io.IOException;
import java.util.Scanner;//引入Scanner类

//【实例 1-2】使用Scanner类进行键盘输入
public class ScannerDemo {
	public static void main(String[] args) {
		Scanner reader = new Scanner(System.in);//创建Scanner类的对象
		System.out.println("请输入一个字符串：");//从键盘接收一行字符串
		String s = reader.next();
		System.out.println("请输入一个整数：");//从键盘接收一个整数
		int i = reader.nextInt();
		System.out.println("请输入一个浮点数：");//从键盘接收一个浮点数
		double d = reader.nextDouble();
		System.out.println("s="+s+" i="+i+" d="+d);
		reader.close();
	}
}
```

#### 【实例 2-1】计算光在指定的天数旅行的千米数

```java

public class LightTravel {

//【实例 2-1】计算光在指定的天数旅行的千米数
	public static void main(String[] args) {
		int lightSpeed;
		long days;
		long seconds;
		long distance;
		//光速大约每秒是30000千米
		lightSpeed = 30000;
		days = 1000;
		seconds = days * 24 * 60 * 60;
		distance = lightSpeed*seconds;
		System.out.println("在"+days+"里，光旅行了大概"+distance+"千米！");
	}
}
```

#### 【实例 2-2】char型变量的使用

```java
//【实例 2-2】char型变量的使用
public class CharDemo {

	public static void main(String[] args) {
		char ch = 'A';
		System.out.println("ch字符："+ch);
		System.out.println("ch字符的ASCII码为："+(int)ch);
	}
}
```

#### 【实例 2-3】对一个字符变量进行增量操作

```java
//【实例 2-3】对一个字符变量进行增量操作
public class CharDemo2 {

	public static void main(String[] args) {
		char ch = 'A';
		ch++;
		System.out.println("ch："+ch);
		System.out.println("ASCII："+(int)ch);
	}

}
```

#### 【实例 2-4】使用if-else-if阶梯来确定考试分数所属等级

```java
import java.util.Scanner;

public class If_else_ifDemo {
	public static void main(String[] args) {
		Scanner input = new Scanner(System.in);
		System.out.println("请输入一个成绩分数：");
		int score = input.nextInt();
		String level = null;
		if (score>=90) {
			level = "优";
		} else if(score>=80) {
			level = "良";
		}else if(score>=70){
			level = "中";
		}else if(score>=60){
			level = "及格";
		}else {
			level = "不及格";
		}
		System.out.println("成绩等级："+level);
	}
}
```

#### 【实例 2-5】输入一个星期几数字，输出星期几



