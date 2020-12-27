---
title: Java入门基础
date: 2020-12-06 15:04:55
tags: 
categories: 
	- 基本数据类型
	- 对象
	- 方法
---

## 基本数据类型及运算符

### 基本数据类型

```java
整型
    byte<-2^8=-128,2^8-1=127>
    short<-2^15=32768,2^15-1=32767>
    int
    long
浮点型 
    float
    double
字符型
    '字符'
    
字符串型
    "字符串"
布尔型
    true/false
```

当数据类型不一样时，将发生数据类型转换。

**自动类型转换（隐式）**代码不需要进行特殊处理，自动完成

```java
// 数据范围从小到大 如int->long
long num1 = 100;

// 数据范围从小到大 如float->double
double num2 = 2.5F;

// 数据范围从小到大 如long->float
float num3 = 30L;
```

**强制类型转换（显式）**（布尔数据类型不能发生数据类型转换）
格式：范围小的类型 范围小的变量名 = （范围小的类型）原本范围大的数据;

```java
// long强制转换为int类型,这里存在发生 数值溢出
int num2 = (int) 6000000000L;

// double->int ，强制类型转换，这里存在发生精度损失，所有的小数值都会被舍弃掉
int num3 = (int) 3.4;
```

### 运算符

#### 四则运算符

```java
加：+
减：-
乘：*
除：/
取模: %
```

#### 自增自减运算符

前"变"后"不变"

```java
int num2 = 20;//混合使用，先++，变量立刻马上变成21，然后打印21
System.out.println(++num2);//21
System.out.println(num2);//21
int num3 = 30; //混合使用，后++，首先使用变量值，然后再让变量+1
System.out.println(num3++);//30
System.out.println(num3);//31
```

#### 复合赋值运算符

```java
复合赋值运算符：
+= : a += 1      ->   a = a + 1
-= : a -= 1      ->   a = a - 1
*= : a *= 2      ->   a = a * 2
/= : a /= 2      ->   a = a / 2
%= : a %= 3      ->   a = a % 3
```

#### 比较运算符

```java
比较运算符:==、>、>=、<、<=、！=
```

#### 逻辑运算符

```java
与（并且）：&&
或（或者）：||
非（取反）：！
// &&、 || 具有短路效果，根据左边已经可以判断得到最终结果，那么右边的代码将不再执行，节省性能
int a = 10;
System.out.println(3>4 && ++a<100);   //false，这里++a不执行!
System.out.println(a);//10
int b =20;
System.out.println(3<4||++b<100);    //ture ，这里++b不执行
System.out.println(b);//20
```

#### 三元运算符

**一元运算符**：只需要一个数据就可以进行操作的运算符。取反！、自增++、自减--
**二元运算符**：需要两个数据进行操作的运算符。四则运算、赋值运算、比较运算
**三元运算符**：需要三个数据

```
格式：
数据类型：变量名称 = 条件判断 ？ 表达式A : 表达式B;
流程：（二者选其一）
首先判断条件是否成立：
    如果成立，将表达式A的值赋于给左侧的变量；
    如果不成立，则将表达式B的值赋值给左侧变量。
```

```java
int  a = 30;
int  b = 20;
// 数据类型：变量名称 = 条件判断 ？ 表达式A : 表达式B;
int max = a > b ? a: b;
System.out.println("最大值为："+max);
System.out.println("a、b两者的最大值为："+(a > b ? a : b));
```



## 流程控制

### 顺序结构

```java
System.out.println("今天天气不错");
System.out.println("挺风和日丽的");
System.out.println("我们下午没事");
```

### if-else 结构

#### 单if

```java
int age = 19
if (age>=18){
    System.out.println("进入网吧，开始high!");
    System.out.println("遇到一群猪队友，开始骂街");
    System.out.println("感觉不爽，结账走人。");
}
```

#### if-else结构

```java
if ( a%2 == 0 ){
    System.out.println(a+"是偶数");
} else {
    System.out.println(a+"是奇数");
}
```

#### if-else if-else 结构

```java
int x = 10;
int y;
if ( x >= 3 ){
    y = 2 * x + 1;
} else if (x > -1 && x < 3){
    y = 2 * x;
} else{
    y = 2 * x - 1;
}
System.out.println("结果是："+ y);
```

### Switch结构

switch 后面的条件 只能是下列数据类型：
	基本数据类型： byte   short   char  int
	引用数据类型： String字符串    enum枚举

```java
switch(条件){
	case 条件1:
	语句体;
	break;
	
	...
	case 条件n:
	语句体;
	break;
	
	default:
	语句体;
	break;
}
```

### For结构

```java
for (初始化表达式1; 布尔表达式2; 步进表达式4){
	循环体3;
    }
```

### While结构

```java
标准格式：
    while(条件){
        循环体
    }
拓展格式：
    初始化语句1;
    while(条件2){
        循环体3;
        步进表达式4;
    }
```

#### Do-while结构

```java
do-while 循环标准格式：
    do{
        循环体
    } while(条件判断);

do-while 循环扩展格式：
    初始化语句1；
    do{
        循环体3；
        步进语句4；
    } while(条件判断2);
```



## 方法重载

### 方法定义

注意事项：
1.方法定义的先后顺序无所谓
2.方法必须是挨着的，不能在一个方法的内部定义另一个方法
3.方法定义之后，自己不会执行的，如果希望使用，必须调用方法。

```java
定义格式：
public static void 方法名称(){
    方法体
}

调用格式：
方法名称();
```

```java
完整的格式：
修饰符 返回值类型 方法名称(参数类型 参数名称，...){
    方法体;
    return 返回值;
}
```

**修饰符**：public / default / protected / privated 
**返回值类型**：方法产生数据的类型
**方法名称**：小驼峰式（首字母小写，后面每个单子的首字母大写）
**参数类型**：byte  short  int  long  char  float double  boolen
**参数名称**：小驼峰式
**return**：第一停止当前方法，第二讲后面的返回值还给调用处

**注意事项** ：

1.如果方法有返回值，那么必须写上“return 返回值;”。
2.return 后面的返回值数据，必须和方法返回值类型相同。
3.对于一个void没有返回值的方法，不能写return后面的返回值，只能写return自己
4.对于void方法当中最后一行的return可以省略不写。
5.一个方法当中可以有多个return语句，但是必须保证同时只有一个会被执行到，两个return自己。

### 方法重载

方法重载：Overload  多个方法名称一样，但参数列表不一样。

好处：只需要记住唯一的方法名称，就可以实现多个功能。

方法重载与下列因素相关：

```
1.参数个数不同
2.参数类型不同
3.参数的多类型顺序不同
```

方法重载与下列因素无关：

```
1.与参数名称
2.与方法的返回值
```

```java
public static int sum(int a, int b) {
        System.out.println("有两个参数的方法执行！");
        return a + b;
    }

public static int sum(double a, double b) {
    System.out.println("有两个参数的方法执行！");
    return (int) (a + b);
}

public static int sum(int a, double b) {
    System.out.println("有两个参数的方法执行！");
    return (int) (a + b);
}

public static int sum(double a, int b) {
    System.out.println("有两个参数的方法执行！");
    return (int) (a + b);
}

public static int sum(int a, int b, int c) {
    System.out.println("有三个参数的方法执行！");
    return a + b + c;
}

public static int sum(int a, int b, int c, int d) {
    System.out.println("有四个参数的方法执行！");
    return a + b + c + d;
}
```



## 数组

数组是一种**引用类型**，可存放多个数据，**数据类型必须统一**，长度**不可变**。

所有的引用常量，都可以赋值为一个null值，但代表什么也没有；数组必须进行new初始化才能使用其中元素；单独使用null赋值，将会发生空指针异常NullPointerException。

动态初始化：

```
数据类型[] 数组名称 = new 数据类型[数组长度];
```

动态初始化一个数组,其中的元素将会自动拥有一个默认值，规则如下：

*  如果是整数类型，那么默认为 0;
* 如果是浮点类型，那么默认为 0.0;
* 如果是字符类型，那么默认为‘\u0000’;

静态初始化：

```
数据类型[] 数组名称 = new 数据类型[] {元素1，元素2,......}
省略格式：
	数据类型[] 数组名称 = {元素1，元素2，....};
```

注意事项：
静态初始化的省略格式，不能拆分为两个部分，但动态可以。

```java
int[] arrayD;
arrayD = {10,20,30};
```

### 数组的遍历

* 数组的索引从0开始，最大值为数组的长度减一
* 数组长度的获取：  **数组名称.length**

**普通for遍历**

```java
数组名.fori
for (int i = 0; i < array.length; i++) {
            System.out.println(array[i]);
        }
```

**增强遍历**

```java
for(int num:array){
	System.out.println(num);
}
```

### 数组的作用

* 作为方法的参数

    当调用方法的时候，传递方法参数进去的是【数组的地址】

    ```java
    public static void main(String[] args) {
            int[] a = {10,20,30,40,50};
        	printArray(a);// [I@10f87f48
    }
    public static void printArray(int[] array){
           //System.out.println("printArray收到的参数是：");
            System.out.println(array);  //地址值
    }
    ```

* 作为方法的返回值

    一个方法可以有0、1、多个参数，但是只有0或者1个返回值。如果需要**返回多个参数**，需要将数组作为返回值，返回的也是数组的**地址值**。

    ```java
    public class Demo02ArrayReturn {
        public static void main(String[] args) {
            int[] res = cal(4, 5, 6);
            System.out.println("main函数的返回值数组是：");
            System.out.println(res);//地址值
            System.out.println("总和："+res[0]);
            System.out.println("平均值："+res[1]);
        }
    
        public static int[] cal(int a, int b, int c) {
            int sum = a + b + c;
            int avg = sum / 3;
            int[] res = {sum, avg};
            System.out.println("cal函数传出的数组是：");
            System.out.println(res);//地址值
            System.out.println("================");
            return res;
        }
    }
    ```

### 常用函数

* public static String toString(数组)  将参数数组变成字符串

    ```
     默认格式  [元素1,元素2,元素3...]
    ```

* public static void sort(数组)  按照默认升序对数组元素进行排序

    1） 如果是数值，默认按照升序从小到大

    2） 如果是字母，默认按照字母升序
    3） 如果是中文或者符号，看字符对应ASCII值
    4） 如果是自定义类型，那么该类型需要有Comparable或者Comparator接口的支持。(今后学习)

## ArrayList——长度可变

ArrayList<E> E表示泛型，只能是**引用类型**；

* 对于ArrayList集合来说，直接打印得到的不是地址值，而是内容
* 如果内容为空，得到的是空的中括号。

```java
ArrayList<String> al = new ArrayList<>();
System.out.println(al); //  []
```

如果需要往ArrayList集合中存入基本数据类型，必须使用基本类型对应的”包装类“。

| 基本类型 | 包装类型  |
| :------: | :-------: |
|   byte   |   Byte    |
|  short   |   Short   |
|   int    |  Integer  |
|   long   |   Long    |
|  float   |   Float   |
|  double  |  Double   |
|   char   | Character |
| boolean  |  Boolean  |

​      

### 常用方法

* public boolean add(E,e) ：向集合中添加元素，参数类型和泛型一致。
* public E get(int index)：从集合中获取元素
* public E remove(int index)：从集合中删除元素，参数为索引编号
* public int size()： 获取集合的大小

#### 遍历集合元素

```java
public class Demo04ArrayListEach {
    public static void main(String[] args) {
        ArrayList<String> al = new ArrayList<>();
        al.add("迪丽热巴");
        al.add("古力娜扎");
        al.add("马尔扎哈");

        // 变量集合
        for (int i = 0; i < al.size(); i++) {
            System.out.println("元素为："+al.get(i));
        }
    }
}
```

#### 题目

* 生成6个1-33之间的随机整数，添加到集合，并遍历集合。

```java
public class Demo01ArrayListRandom {
    public static void main(String[] args) {
        Random r = new Random();
        ArrayList<Integer> list = new ArrayList<>();
        for (int i = 0; i < 6; i++) {
            list.add(r.nextInt(33)+1);
        }
        //遍历集合
        for (int i = 0; i < list.size(); i++) {
            System.out.println(list.get(i));
        }
    }
}
```

* 定义以指定格式打印集合的方法（ArrayList类型作为参数），使用{}扩起集合，使用@分隔每个元素

    格式如   {元素@元素@元素@元素}

```java
public class Demo03ArrayListPrint {
    public static void main(String[] args) {
        ArrayList<Integer> al = new ArrayList<>();
        al.add(12);
        al.add(18);
        al.add(10);
        System.out.println(al); // [12, 18, 10]
        System.out.println("==============");
        System.out.println("按照格式要求输出的是");
        printArrayList(al);
    }

    public static void printArrayList(ArrayList<Integer> al) {
        System.out.print("{");
        for (int i = 0; i < al.size(); i++) {
            int num  = al.get(i);
            if (i == al.size() - 1) {
                System.out.println(num + "}");
            } else {
                System.out.print(num + "@");
            }
        }
    }
}
```



## 类与对象

类一般包括**构造方法**、**属性（成员变量）**和**方法**三部分。

```java
class 类名称
{
	// 定义属性（成员变量）
	数据类型 属性；      //零到多个属性
	// 定义构造函数
	类名称（参数，…）{   //零个到多个构造方法
	
	}
	// 定义方法
	返回值的数据类型 方法名称（参数1，参数2…） //零到多个方法
	{
    	程序语句 ;
   	 	return 表达式 ;
	}
}
```

对象是类的**实例化**体现，具体使用步骤如下：

1.**导包**：对于和当前类同属一个包的情况，可以省略导包语句

```
import 包名称.类名称
```

2.**创建**：new

```
类名称 对象名 = new 类名称();
```

3.**使用**：

```
使用成员变量：对象名.成员变量名
使用成员方法: 对象名.成员方法名(参数)
```

*  当一个对象作为方法的**传入参数**，实际上传递进去的是“ **对象的地址值**“

```java
public class Demo04PhoneParam {
    public static void main(String[] args) {
        Phone one = new Phone();
        one.brand = "苹果";
        one.color = "土豪金";
        one.price = 8388.0;
        method(one);//传递进去的是对象one的地址值
    }
    public static void method(Phone param){
        System.out.println("传入方法的是：");
        System.out.println(param); // cn.itcast.day06.demo02.Phone@b4c966a
    }
}
```

* 对象类型作为方法**返回值**时,返回的是   “  对象的地址值   ”

```java
public class Demo05PhoneReturn {
    public static void main(String[] args) {
        Phone two = getPhone();
        System.out.println("方法返回的对象是：");
        System.out.println(two); // cn.itcast.day06.demo02.Phone@b4c966a
    }
    public static Phone getPhone(){
        Phone one = new Phone();
        one.price=8388.0;
        one.color="玫瑰金";
        one.brand="苹果";
        return one;
    }
}
```

### 匿名对象

**new 类名称();**

**注意事项**：匿名对象只能使用唯一的一次，下次再用不得不再创建一个新对象

**使用建议：**如果确定有一个对象只需要使用唯一的一次，就可以使用匿名对象。

```java
public class Person {
    String name;
    public void showName(){
        System.out.println("我叫"+name);
    }
}
public class Demo01Anoymous {
    public static void main(String[] args) {
        // 匿名对象
        new Person().name = "赵又廷"; //第一个对象
        new Person().showName();    //第二个对象  我叫：null
    }
}
```



### 变量和成员变量的区别

1.定义的位置不同【重点】
局部变量：在方法内部
成员变量：在方法外部，直接写在类当中

2.作用的范围不一样【重点】
局部变量：只有在方法中才可以使用，出了方法不可用
成员变量：整个类都可以调用

3.默认值不一样【重点】
局部变量：没有默认值，如果使用必须赋值
成员变量：有默认值，规则和数组一样

4.内存的位置不一样（了解）
局部变量：位于栈heap内存
成员变量：位于堆stack内存 new产生的成员变量

5.生命周期不一样（了解）
局部变量：随着方法进栈而诞生，随着方法出栈消失
成员变量：随着对象创建而诞生，随着对象被回收而消失

### private关键字修饰成员变量

使用**private**进行修饰，那么**本类当中可以访问**，超出本类范围之外，不可以直接访问。

间接访问private成员变量，就定义一对getter和setter方法。

* getter和setter方法，方法名必须是getXxx或者setXxx
    * setter 方法  不能有返回值【void】，参数类型和成员变量对应
    * getter 方法  不能有参数，返回值类型和成员变量的数据类型对应

```java
public class Person {
	private int age;
    // 这个成员方法，专门用于向age设置数据
    public void setAge(int num) {
        if (num < 100 & num >= 0) {
            age = num;
        } else {
            System.out.println("数据不合理！");
        }
    }

    // 这个成员方法，专门用于获取age数据
    public int getAge() {
        return age;
    }
}

public class Demo03Person {
    public static void main(String[] args) {
          Person person = new Person();
        // person.age = 35; // 直接访问private方法，错误写法！
    	person.setAge(-20);
    }
}       
```

### 构造方法

**构造方法**是专门用来创建对象的方法，当我们通过关键字new创建对象时，其实就是调用构造方法。

```java
public 类名称 (参数类型 参数名称){
   方法体
}
```

**注意事项：**

1. 构造方法的名称必须和所在的类名称完全一样，就连大小写也要一样
2. 构造方法【不要写返回值类型，连**void**都不写】
3. 构造方法不能**return**一个具体的返回值
4. 如果没有编写任何构造方法，那么编译器将会默认赠送一个构造方法，
5. 一旦编写了至少一个构造方法，那么编译器便不再赠送。

### 标准类

1. 所有的成员变量都要使用private关键字修饰
2. 为每个成员变量编写setter和getter方法
3. 编写一个无参数构造方法 public 类名称(){}
4. 编写一个全参数构造方法 public 类名称(参数类型 参数名,...){}

```
 IEDA插入构造方法：
 code -> generate -> constructor/getter、setter
 IDEA快捷键：
 Alt+insert
```

## 常用函数

一般步骤：

1.导包：import 包名称.类名称

2.创建：类名称 对象名  = new 类名称();

3.使用：对象名.成员方法名(参数类型，参数名);

### Scanner类

```java
import java.util.Scanner;

Scanner sc = new Scanner(System.in);  //System.in 代表从键盘输入

int num = sc.nextInt();
```

### Random类

```java
import java.util.Random;
Random r = new Random();

int num = r.nextInt();//获取随机的int数字，范围为int所有范围，有正负之分
System.out.println("随机数为：" + num);

int num1 = r.nextInt(3);//参数代表范围，左闭右开区间 [0 3)
System.out.println("随机参数为" + num1);
```

#### 猜数字小游戏

```java
public class Demo04Random {
    public static void main(String[] args) {
        int r = new Random().nextInt(10) + 1; // [1,11)
        Scanner sc = new Scanner(System.in);

        System.out.println("请输入你猜测的数字：");
        while(true){
            int num = sc.nextInt();

            if (num < r) {
                System.out.println("数字小了,请重新输入");

            } else if (num > r) {
                System.out.println("数字大了，请重新输入");

            } else {
                System.out.println("恭喜你，你猜对了！");
                break;//如果猜中，不再重试
            }
        }
        System.out.println("游戏结束！GameOver!");
    }
}
```

## 字符串及常用字符串函数

### 字符串的特点

* 字符串的内容永不可变。【重点】
* 因为字符串不可变，所以字符串是可以共享使用。
* 字符串效果上相当于是char[]字符数组，但底层原理是byte[]字节数组。

**创建字符串的常见3+1种方式：**

```java
public class Demo01String {
    public static void main(String[] args) {
        // 使用空参构造,public String();
        String str1 = new String();;
        System.out.println("第一个字符串：" + str1);

        // 根据字符数组创建字符串，public String(char[] array);
        char[] charArray = {'A', 'B', 'C'};
        String str2 = new String(charArray);
        System.out.println("第二个字符串：" + str2);

        // 根据字节数组创建字符串，Public string(byte[] array);
        byte[] byteArray = {97, 98, 99};
        String str3 = new String(byteArray);
        System.out.println("第三个字符串：" + str3);

        // 直接创建，直接写上双引号，就是字符串对象
        String str4 = "Hello,World!";
        System.out.println("第四个字符串：" + str4);
    }
}
```

**注意：**直接创建字符串，就在**字符串常量池**【**前三种构造方法**】中；new的不在常量池中。

### 字符串常用函数

* public boolean **equals**(Object obj)

    **注意事项：**

    ​		1) 任何对象都可以用object进行接收

    ​		2) equal方法具有对称性，也就是a.equal(b)和b.euqal(a)

    ​		3) 如果比较双方一个常量一个变量，推荐把常量字符串写在前面

    **推荐：**"abc".equal(str)     **不推荐：**str.euqal("abc")

* public boolean **equalsIgnoreCase**(String str)：不区分大小写字符串进行比较

* public int **length**()：获取字符串中含有的字符个数

* public String **concat**(String str)：将当前字符串和参数字符串拼接并返回

* public char **charAt**(int index)：获取指定索引位置的单个字符（索引从0开始）

* public int **indexOf**(String str)：查找参数字符串在本字符串当中首次出现的索引位置，如果没有返回-1值

#### 字符串截取

​	public String **substring**(inr index) ：截取从参数位置一直到字符串末尾，返回新字符串

​	public String **substring**(int begin , int end) ：截取位置[begin , end)

​	public String[] **split**(String regex) 按照参数的规则，将字符串切分成为若干部分

```java
// 正常的切分规则
String str1 = "aaa,bbb,ccc";
String[] array1 = str1.split(",");
// 如果按照英文句点“.”进行切分，则需要改为“\\.”
String str3 = "XXX.YYY.ZZZ";
String[] array3 = str3.split("\\.");
```

#### 字符串转换

* public char[] toCharArray() 将当前字符串拆分为字符串数组作为返回值
* public byte[] getBytes() 获取当前字符串底层的字节数组
* public String replace(CharSequence oldString ,CharSequence newString)：将所有出现的老字符串替换成为新的字符串，返回替换之后的结果新字符串

**备注：**CharSequence 表示可以接受字符串类型

```java
public class Demo04StringConvert {
    public static void main(String[] args) {
        char[] chars = "HelloWorld".toCharArray();
        System.out.println(chars);
        //  这里注意【字符串数组】的长度用  ".length"
        // 【字符串】的长度用   ".length();"
        System.out.println(chars.length);
        System.out.println("============");

        // 转换为字节数组
        byte[] charBytes = "abc".getBytes();
        for (int i = 0; i < charBytes.length; i++) {
            System.out.println(charBytes[i]);
        }
        System.out.println("=============");

        // 替换字符串
        String str1 = "How do you do ?";
        String strNew = str1.replace("o", "*");
        System.out.println(strNew);//H*w d* y*u d* ?
        System.out.println("==============");

        String lang1 = "会不会玩呀！你大爷的！";
        String lang2 = lang1.replace("你大爷的", "****");
        System.out.println(lang2); // 会不会玩呀！****！
    }
}
```

### 题目

要求：键盘输入一个字符串，并且统计其中各种字符出现的次数

字符串种类：大写字母、小写字母、数字、其他

分析：
* 1.Scanner类读取用户输入字符串
* 2.String str = sc.next();
* 3.定义四个变量，分别代表四种字符各自的次数
* 4.需要对字符串一个字一个字进行检查 ：String -> char[]   toCharArray();
* 5.遍历char[]字符数组，对当前字符种类进行判断，并且用四个变量进行++动作
* 6.打印输出四个变量，分别代表四种字符出现的次数

```java
public class Demo07StringCount {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        System.out.println("请输入一个字符串：");
        String input = sc.next();

        int countUpper = 0;
        int countLower = 0;
        int countNumber = 0;
        int countOther = 0;

        char[] charArray = input.toCharArray();
        for (int i = 0; i < charArray.length; i++) {
            char ch = charArray[i];
            if ('A' <= ch && ch <= 'Z') {
                countUpper++;
            } else if (ch <= 'z' && ch >= 'a') {
                countLower++;
            } else if (ch >= '0' && ch <= '9') {
                countNumber++;
            } else {
                countOther++;
            }
        }
        System.out.println("大写字母有：" + countUpper);
        System.out.println("小写字母有：" + countLower);
        System.out.println("数字有：" + countNumber);
        System.out.println("其他符号有：" + countOther);
    }
}
```

## 静态关键字Static

### 修饰成员变量

使得**类中所有对象**共用该**成员变量**

* **定义学生类**

```java

public class Student {
    private int id; //学号
    private String name;//姓名
    private int age;// 年龄
    // 
    static String room;//所在教室
    private static int countId = 0; //用来统计学生数量

    public Student() {
        this.id = ++countId;
    }

    public Student(String name, int age) {
        this.name = name;
        this.age = age;
        this.id = ++countId;
    }
}
```

* 创建3个对象，学生类中**被static修饰**的【room】成员变量，共享该变量值。

```java
public class Demo01StaticField {
    public static void main(String[] args) {
        // 姓名：黄容,年龄：16,教室：1804班,学号：1
        Student one = new Student("黄容", 16);
        Student.room = "1804班";
        System.out.println("姓名：" + one.getName()
                + ",年龄：" + one.getAge() + ",教室：" + one.room
                + ",学号：" + one.getId());

        // 姓名：null,年龄：0,教室：1804班,学号：1
        Student aa = new Student();
        System.out.println("姓名：" + aa.getName()
                + ",年龄：" + aa.getAge() + ",教室：" + aa.room
                + ",学号：" + aa.getId());

        // 姓名：郭靖,年龄：18,教室：1804班,学号：3
        Student two = new Student("郭靖", 18);
        System.out.println("姓名：" + two.getName()
                + ",年龄：" + two.getAge() + ",教室：" + two.room
                + ",学号：" + two.getId());
    }
}
```

### 修饰成员方法

* 一旦使用static修饰成员方法，那么这就成为静态方法，静态方法不属于对象，而属于类。
* 如果没有static关键字修饰该方法，那么必须首先创造对象，然后通过对象才能使用它。
* 无论成员变量，还是成员方法，如果有static，都推荐使用类名称进行调用
    * 静态变量：类名称.静态变量
    *  静态方法：类名称.静态方法()

**注意事项：**

​	1.静态不能直接访问非静态——在内存中，先有静态内容，后有非静态内容

​	2.静态方法中不能使用this——this 代表当前对象，通过谁调用的方法，谁就当前对象

```java
public class MyClass {
    int num;
    static int numStatic;
    public void method() {
        System.out.println("这是一个普通的成员方法");
        // 成员方法可以访问成员变量
        System.out.println(num);
        // 成员方法可以访问静态变量
        System.out.println(numStatic);
    }
    public static void staticMethod() {
        System.out.println("这是一个静态方法");
        // 静态方法可以访问静态变量
        System.out.println(numStatic);

        //静态方法不可以直接访问成员变量
//        System.out.println(num);

        // 静态方法中不可使用this关键字
//        System.out.println(this);
    }
}
```

### 静态代码块

**格式：**

```java
 public class 类名称{
 static{
      // 静态代码块的内容
    }
 }
```

特点：当第一次用到本类时，静态代码块执行唯一的一次

* 静态内容总是优先于非静态，所以静态代码块比构造方法先执行
* 当第一次用到本类时，静态代码块执行唯一的一次
* 用来一次性地对静态成员变量进行赋值

```java
public class Person {
    static {
        int num = 10;
        System.out.println("静态代码块执行！");
    }
    public Person(int num){
        System.out.println(num);
        System.out.println("构造方法执行！");
    }
}

public class Demo04Static {
    public static void main(String[] args) {
        Person one = new Person(5);
       // 静态代码块执行！
       // 5
       // 构造方法执行！
    }
}
```

## Java三大特性之继承性

三大特性：**封装性、继承性、多态性**

定义父类的格式：（普通类定义）	

```java
public class 父类名称(){
    // ...
}
```

定义子类格式：

```java
public class 子类名称 extends 父类名称{
       // ...
}
```

无论是成员方法还是成员变量，如果没有都是**向上找父类**，绝对不会向下找子类的。

### 成员变量重名

```java
public class Fu {
    int numFu = 10;
    int num = 100;
    public void methodFu(){
        // 使用的是本类当中的num
        System.out.println(num);
    }
}

public class Zi extends Fu{
    int numZi = 20;
    int num = 200;
    public void methodZi(){
        // 使用的是本类当中的num
        System.out.println(num);
    }
}
```

在父子的继承关系中，如果**成员变量重名**，则创建子类对象时，成员变量的访问规则：

* **直接：**通过子类对象访问成员变量，等号左边是谁，就优先用谁，没有则往上找。

```java
System.out.println(zi.num);//200
```

* **间接**：通过成员方法访问成员变量，方法属于谁，就优先用谁，没有则往上找。

```java
// 这里调用的是子类方法，变量优先选用子类的变量，没有则往上找
zi.methodZi();//200
zi.methodFu();//100
```

### this、super关键字

* 局部变量、  直接写
* 本类的成员变量  this.成员变量
* 父类的成员变量  super.成员变量

```java
public class Zi extends Fu{
    int num =20;
    public void method(){
        int num = 30;
        System.out.println(num);// 30 局部变量
        System.out.println(this.num);// 20 本类的成员变量
        System.out.println(super.num);//10 父类的成员变量
    }
}
```

**super关键字的用法：**

* 1.在子类的成员方法中，访问父类的成员变量。
* 2.在子类的成员方法中，访问父类的成员方法。
* 3.在子类的构造方法中，访问父类的构造方法。

```java
public class Zi extends Fu {
    int num = 20;
    public Zi(){
        super();
    }
    
    public void methodZi() {
        System.out.println(super.num);// 父类中的num
        System.out.println(num);
    }
    
    public void method(){
        super.method(); // 访问父类中的method()方法
        System.out.println("子类成员方法");
    }
}
```

**this关键字的用法：**

* 1.在本类的成员方法中，访问本类的成员变量

* 2.在本类的成员方法中，访问本类的另一个成员方法
* 3.在本类的成员方法中，访问本类的另一个构造方法

在第三种用法当中也要注意：

this(参数)调用也必须是构造方法的**第一个语句**，且只能使用一次

```java
public class Zi extends Fu {
    int num = 20;
//   1.在本类的成员方法中，访问本类的成员变量
    public void showNum() {
        int num = 10;
        System.out.println(num);// 局部变量
        System.out.println(this.num);// 本类中的成员变量
        System.out.println(super.num);// 父类中的成员变量
    }
//  2.在本类的成员方法中，访问本类的另一个成员方法
    public void methodA() {
        System.out.println("AAA");
    }

    public void methodB() {
        this.methodA();
        System.out.println("BBB");
    }
//  3.在本类的构造方法中，访问本类的另一个构造方法
//  this(参数)调用也必须是构造方法的第一个语句，且只能使用一次
    public Zi() {
//        this(100);// 本类的无参构造，调用本类的有参构造
//        this(10,20);
    }

    public Zi(int n) {
        this(20,30);
    }
    public Zi(int n,int m) {
        this();
    }

}
```

### 方法重写 (Override)

在父子类的继承关系中，创建子类对象，访问成员方法的规则：创建的对象是谁，就优先用谁，如果没有则向上找。

**注意事项**：

1.必须保证父子类之间方法的名称相同，参数列表也相同。

**@Override** 写在方法前面，用来检测是不是有效的正确覆盖重写。

2.子类方法的返回值必须【小于】父类方法的返回值范围。

3.子类方法的权限必须【大于等于】父类方法的权限修饰符。

```java
public > protected > (default) > private
```

**重写(Override)**

*  概念：在继承关系中，方法的名称一样，参数列表**【一样】**。

**重载(OverLoad)**

* 方法的名称一样，参数列表**【不一样】**。

```java
public class Fu {
    public void methodFu(){
        System.out.println("父类方法执行！");
    }
    public void method(){
        System.out.println("父类重名方法执行！");
    }
}

public class Zi extends Fu{
    public void methodZi(){
        System.out.println("子类方法执行！");
    }
    public void method(){
        System.out.println("子类重名方法执行！");
    }
}

public class Demo01ExtendsMethod {
    public static void main(String[] args) {
        Zi zi = new Zi();

        zi.methodFu();
        zi.methodZi();
        System.out.println("==============");
		// 创建的是子类对象(new),就优先用子类方法
        zi.method(); //  子类重名方法执行！
    }
}
```

#### 继承中方法的重写

```java
public class Phone {
    public void call() {
        System.out.println("打电话");
    }

    public void send() {
        System.out.println("发短信");
    }

    public void show() {
        System.out.println("显示号码");
    }
}
    
public class NewPhone extends Phone {
    @Override
    public void show(){
//        System.out.println("显示号码");
        super.show();
        System.out.println("显示头像");
        System.out.println("显示姓名");
    }
}
```

### **构造方法**

在继承关系中，父子类构造方法的**访问特点**：

1. 子类构造方法当中有一个默认隐含的”super();"调用
2. 子类构造可以通过Super关键字来调用父类重载构造
3. super的父类构造调用，必须是子类构造方法的第一个语句。
4. 不能一个子类构造调用多次super构造，且只能是子类构造方法调用。

```java
public class Fu {
    public Fu(){
        System.out.println("父类无参构造方法");
    }
    public Fu(int num){
        System.out.println("父类有参构造方法");
    }
}

public class Zi extends Fu {

    public Zi() {
        super();//调用父类无参数构造方法
//        super(10);//调用父类有参数构造方法
        System.out.println("子类构造方法");
    }

    public void method() {
//      错误写法！只有子类构造方法才能调用父类构造方法
//        super();
    }
}
```

### Abstract关键字

**抽象方法格式：**

```java
修饰符 abstract 返回值类型 方法名称();
```

**抽象类格式：**

```java
修饰符 abstract class 类名称{
	// ... 
}
```

如何使用抽象类和抽象方法

* 1.不能直接创建new抽象对象

* 2.必须用一个子类来继承抽象父类

* 3.子类必须覆盖重写抽象父类当中所有的抽象方法

  覆盖重写（实现）：子类去掉抽象方法中abstract关键字，然后补上方法体大括号

* 4.创建子类对象进行使用

**注意事项：**一个抽象类不一定有抽象方法，抽象方法一定在抽象类中

```java
public abstract class Animal {
    // 这是一个抽象方法，代表吃东西，但是具体吃什么（大括号的内容）不确定。
    public abstract void eat();
    // 普通的成员方法
    public void normalMethod(){
        System.out.println("这是一个正常的成员方法！");
    }
}

public class Cat extends Animal {
    @Override
    public void eat(){
        System.out.println("猫吃鱼！");
    }
}

public class DemoMain {
    public static void main(String[] args) {
//        错误写法！不能直接创建抽象类对象
//        Animal animal = new Animal();
        Cat cat = new Cat();
        cat.eat();
    }
}
```



## 接口和多态

接口是多个类的公共规范，是一种引用类型，重要的是 其中的**抽象方法** 。

定义接口的格式：

public interface 接口名称(大驼峰式){

​	// 接口内容

}

**接口内容：**

如果是java7，那么接口中可以包含的内容有：
* 1. 常量
* 2. 抽象方法

如果是java8，还可以包含：

* 3. 默认方法
* 4. 静态方法

如果是java9，还包含：

* 5. 私有方法

**接口的使用步骤：**

1.接口不能直接使用，必须有一个 "实现类" 来 "实现" 该接口
格式：
	public class 实现类名称 implements 接口名称{
    	// ...
	}
2.接口的实现类必须覆盖重写（实现）接口中的所有抽象方法。
  去掉abstract 关键字，加上方法体大括号
3.创建实现类的对象，进行使用

### 接口中抽象方法

* 1.接口当中的抽象方法，修饰符必须是两个固定的关键字：public abstract
* 2.这两个关键字修饰符，可以选择性地省略。（今天新学，这里不推荐）
* 3.方法的三要素可以根据条件，进行随意定义 （参数列表、返回值类型、方法名称）

```java
public interface MyInterfaceAbstract {
    // 定义抽象方法  public abstract 返回值类型 方法名称(参数列表);
    public abstract void methodAbs1();
    // 这也是抽象方法
    abstract void methodAbs2();
    // 这也是抽象方法
    public void methodAbs3();
    // 这也是抽象方法
    void methodAbs4();
}
```

### 接口对应的实现类

```java
public class MyInterfaceAbstractImpl implements MyInterfaceAbstract{

    @Override
    public void methodAbs1() {
        System.out.println("这是第一个方法！");
    }

    @Override
    public void methodAbs2() {
        System.out.println("这是第二个方法！");
    }

    @Override
    public void methodAbs3() {
        System.out.println("这是第三个方法！");
    }

    @Override
    public void methodAbs4() {
        System.out.println("这是第四个方法！");
    }
}
```

**注意事项：**

如果【实现类】并没有覆盖重写（override）接口中的所有抽象方法，那么这个【实现类】必须是【抽象类】。

【接口的使用】

```java
public class Demo01Interface {
    public static void main(String[] args) {
        // 创建接口的实现类对象
        MyInterfaceAbstractImpl myInterface = new MyInterfaceAbstractImpl();
        myInterface.methodAbs1();
        myInterface.methodAbs2();
        myInterface.methodAbs3();
        myInterface.methodAbs4();
    }
}
```

### 接口中的默认方法

格式：

```java
public **default** 返回值类型 方法名称(参数列表){
	// 方法体
}
```

备注：接口当中的默认方法，可以解决接口升级的问题

```java
public interface MyInterfaceDefault {
    // 抽象方法
    public abstract void methodAbs();
//    // 新添加一个抽象方法，根据这个接口【MyInterfaceDefault】创建的【实现类】就会出错
//    public abstract void methodAbs2();

    // 新添加的方法，改成默认方法就可以解决问题
    public default void methodDefault(){
        System.out.println("这是新添加的默认方法！");
    }

}
```

### 接口中的静态方法

**格式**：

```java
public **static** 返回值类型 方法名称(参数列表){
	// 方法体
}
```

**使用方法**：接口名称.静态方法名

```java
public interface MyInterfaceStatic {
    public static void methodStatic(){
        System.out.println("这是接口的静态方法！");
    }
}

public class Demo03Interface {
    public static void main(String[] args) {
        // 创建实现类对象
        MyInterfaceStaticImpl impl = new MyInterfaceStaticImpl();
        // 错误写法
//        impl.methodStatic();
        // 应该通过接口名称.静态方法名 进行调用
        MyInterfaceStatic.methodStatic();
    }
}
```

### 接口中的静态私有方法

解决多个静态方法之间重复代码问题

```java
public interface MyInterfacePrivateB {
    public static void methodStatic1() {
        System.out.println("这是一个静态方法1");
        methodStaticCommon();
    }

    public static void methodStatic2() {
        System.out.println("这是一个静态方法2");
        methodStaticCommon();
    }

    private static void methodStaticCommon() {
        System.out.println("AAA");
        System.out.println("BBB");
    }
}
```

### 接口总结

在 java9+ 版本中， 接口的内容可以有：

1.成员变量 其实是**常量**，格式：
[public] [static] [final] 数据类型 常量名称 = 数据值；
注意：常量必须进行赋值，而且一旦赋值不能改变
  常量名称必须完全大写，用下划线进行分隔

2.接口中最重要的是**抽象方法**，格式：
[public] [abstract] 返回值类型 方法名称(参数列表);
注意：实现类  必须覆盖重写所有的抽象方法，除非实现类是抽象类

3.从java 8+ 开始，接口允许定义**默认方法**，格式：
[public] [default] 返回值类型 方法名称(参数列表){方法体};
注意：默认方法也可以覆盖重写

4.从java8 开始， 接口允许定义**静态方法**，格式：
[public] static 返回值类型 方法名称(参数列表){方法体};
注意：应该通过接口名称进行调用，不能通过 实现类 对象调用接口静态方法

5.从java9 开始，接口允许定义**私有方法**，格式：
**普通私有方法**：

​	 private 返回值类型 方法名称(参数列表){方法体}

**静态私有方法**：

​			private static 返回值类型 方法名称(参数列表){方法体}

**注意：** private 方法只能被接口自己使用，不能被实现类或者别人使用

### 接口（interface）和继承(extends)之间的区别

* 1.类与类之间是单继承的，直接父类只有一个
* 2.类与接口之间是多实现的，一个类可以实现多个接口  
* 3.接口与接口之间是多继承的。   

**注意事项：**

* 1.多个父接口当中的抽象方法如果重复，没关系,子接口不用对抽象方法进行覆盖重写    **见【MyInterface】的 methodCommon**
* 2.多个父接口当中的默认方法如果重复，那么子接口必须进行默认方法的覆盖重写，【而且带着default关键字】，在子接口的实现类中可以不用对重复的默认方法进行覆盖重写【@override】       **见【MyInterfaceImpl】**

```java
public interface MyInterface extends MyInterfaceA, MyInterfaceB {
    public abstract void method();
//    多个父接口当中的默认方法如果重复，那么子接口必须进行默认方法的覆盖重写，
    @Override
    default void methodDefault() {
        System.out.println("默认方法重复了");
    }
}
```

```java
public class MyInterfaceImpl implements MyInterface{
    @Override
    public void method() {
        System.out.println("子接口方法");
    }

    @Override
    public void methodA() {
        System.out.println("接口A方法");
    }

    @Override
    public void methodB() {
        System.out.println("接口B方法");
    }

    @Override
    public void methodCommon() {
        System.out.println("A、B接口公共方法");
    }
//    多个父接口当中的默认方法如果重复，那么子接口必须进行默认方法的覆盖重写，实现类中可以不用对重复的默认方法进行覆盖重写
//    @Override
//    public void methodDefault() {
//        System.out.println("默认接口重复");
//    }
}
```

### 多态性

**父类引用指向子类对象**

格式：

​		父类名称 对象名 = new 子类名称();

或者

​		接口名称 对象名 = new 实现类名称();

```java
public class Fu {
    int num = 10;
}

public class Zi extends Fu {
    int num = 20;
    @Override
    public void showNum() {
        System.out.println(num);
    }
}
```

#### 访问成员变量的两种方式

* 1.直接通过【对象名称】访问成员变量：看等号**左边是谁**，优先用谁，没有往上找

```java
Fu obj = new Zi();

System.out.println(obj.num);  //10
```

* 2.间接通过【成员方法】访问成员变量：看该方法**右侧是谁**，优先用谁，没有往上找。

```java
obj.showNum(); //20
```

**注意事项：**

子类没有覆盖重写方法，就是父类方法，有覆盖就是子类方法。

```java
public class Zi extends Fu {
    int num = 20;
	@Override
    public void showNum() {
        System.out.println(num);
    }
}

obj.showNum();//20
```

### 向上转型和向下转型

向上转型是指**父类引用指向子类对象**，是安全的，没有问题，正确的，但一旦向上转型为父类，那么就**无法调用子类原本特有的内容见【子类catchMouse方法】**。

#### 向下转型

**格式**：  子类名称 对象名 = (子类名称) 父类对象;

```java
public class Cat extends Animal{
    @Override
    public void eat() {
        System.out.println("猫吃鱼");
    }

    // 子类特有方法
    public void catchMouse(){
        System.out.println("猫抓老鼠");
    }
}

public class Demo01Main {
    public static void main(String[] args) {
        Animal animal = new Cat();
        animal.catchMouse();  // 错误写法
        // 向下转型
        Cat cat= (Cat) animal;
        cat.catchMouse(); // 猫抓老鼠
    }
}
```

#### instanceof 判断对象是否属于子类

```java
public static void giveMeAPet(Animal animal){
    if (animal instanceof Dog){
        Dog dog = (Dog) animal;
        dog.watchHouse();
    }
    // 判断animal本来是不是Cat
    if (animal instanceof Cat){
        Cat cat = (Cat) animal;
        cat.catchMouse();
    }
}
```

## 内部类

### final关键字

常见四种用法：

* 1.**可以用来修饰一个类**      不能有任何的子类，其中的所有成员方法都无法进行覆盖重写（太监类）

```java
public final class MyClass {
    public void method(){
        System.out.println("方法执行！");
    }
}
```

* 2.可以用来修饰一个方法     该方法就是最终方法，也就是不能被覆盖重写

    这里注意：abstract 和 final关键字不能同时作用于同一个方法

    ```java
    //  错误写法
    public abstract final void methodAbs();
    ```

* 3.可以用来修饰一个局部变量 ，一旦使用**final**关键字用来修饰局部变量，那么这个变量就不能进行更改

    ```java
    final int num2 = 200;
      or 
    final int num3;
    num3 = 30;
    ```

* 4.可以用来修饰一个成员变量  

    对于成员变量来说，如果使用final关键字修饰，那么这个变量也照样是不可变的。

    1.由于成员变量具有默认值，所以用了final之后必须手动赋值，不会再给默认值

    2.对于final的成员变量，要么使用直接赋值，要么通过构造方法赋值。 二者选取一。

    3.必须保证类当中的所有重载的构造方法，都最终会对final的成员变量进行赋值。

    ```java
    ublic class Person {
    	// 1. 
        private final String name;/* = "李庆梅";*/
    
        public String getName() {
            return name;
        }
    
    //    public void setName(String name) {
    //        this.name = name;
    //    }
    	// 2.
        public Person(String name) {
            this.name = name;
        }
    	// 2.
        public Person() {
            name = "李庆梅";
        }
    }
    ```

### 修饰符

Java 中四种权限修饰符：

|                      | public | protected | (default) | private |
| :------------------: | :----: | :-------: | :-------: | :-----: |
|    同一类(我自己)    |  YES   |    YES    |    YES    |   YES   |
|    同一包(我邻居)    |  YES   |    YES    |    YES    |   NO    |
|  不同包子类(我儿子)  |  YES   |    YES    |    NO     |   NO    |
| 不同包非子类(陌生人) |  YES   |    NO     |    NO     |   NO    |

### 成员内部类

成员内部类的定义格式：
			修饰符 class 外部类名称{
   				修饰符 class 内部类名称{
         				// ...
    				}
   					// ...
			}

注意：
* 内部类用外部类，随意访问；
* 外部类用内部类，需要内部类对象。

#### 使用方法

* 1.在外部类的方法当中，使用内部类，然后main只是调用外部类的方法。【间接方法】

* 2.【直接方法】

     公式：外部类名称.内部类名称 对象名 = new 外部类名称().new 内部类名称();

```java
public class Demo01InnerClass {
    public static void main(String[] args) {
        // 间接方法
        Body body = new Body();// 外部类的对象
        // 通过外部类的对象，调用外部类方法，里面间接在使用内部类的方法
        body.methodBody();
        System.out.println("=============");
        // 直接方式
        Body.Heart heart = new Body().new Heart();
        heart.beat();
    }
}
public class Body {// 外部类
	public void methodBody(){// 外部类的方法
        System.out.println("外部类的方法");
        new Heart().beat();
    }
}
```

### 局部内部类

如果一个类是定义在一个**方法内部**的，那么这个类就是**局部内部类**。

局部内部类格式：

```java
修饰符 class 外部类名称{
 	修饰符 返回值类型 外部类方法名称(参数列表){
       class 内部类名称{
               // ...
        }
    }
    // ...
}
```

定义一个类的对象，权限修饰符规则：
* 1.外部类：Public / (default)
* 2.成员内部类:public/protected/(default)/private
* 3.局部内部类:什么都不写。

### 匿名内部类

**格式：**

接口名称 对象名 = new 接口名称(){

​				// 覆盖重写所有的抽象方法

}    //匿名内部类，没有名字

**注意事项：**

1.对格式进行解析“new 接口名称(){...}”：

* new 代表创建对象的动作
* 接口名称() 就是匿名内部类需要实现哪个接口
* {...}匿名内部类的内容

2.匿名内部类，在【创建对象】时，只能使用唯一一次

3.匿名对象，再【调用方法】时，只能调用唯一一次

4.匿名内部类 是省略了【实现类/子类】，匿名对象  是省略了【对象名称】。

```java
MyInterface objA  = new MyInterface() {
    @Override
    public void method1() {
        System.out.println("匿名内部类现象了方法，111-A");
    }
    @Override
    public void method2() {
        System.out.println("匿名内部类现象了方法，222-A");
    }
};
objA.method1();
objA.method2();
```

### 红包案例

要做的事情：
*         设置一下程序的标题，通过构造方法的字符串参数
*         设置群主名称 set
*         设置分发策略；平均还是随机？

红包分发的策略：

*         普通红包（平均）：totalMoney/totalCount,余数放在最后一个红包当中。
*         手气红包（随机）：最少1分钱，最多不超过平均数的2倍。应该越发越少

**发放模式：**

```java
public interface OpenMode {
/*
* 请将totalMoney分成totalCount份，保存到ArrayList<Integer>中，返回即可。
* totalMoney   总金额为方便计算，已经转换为整数，单位为分
* totalCount   红包个数
* ArrayList<Integer>  元素为各个红包的金额值，所有元素的值得累和等于总金额。
* */
    ArrayList<Integer> divide(int totalMoney,int totalCount);
}
```

#### 平均发放

```java
public class NormalMode implements OpenMode {
    @Override
    public ArrayList<Integer> divide(final int totalMoney, final int totalCount) {
        ArrayList<Integer> list = new ArrayList<>();

        int avg = totalMoney / totalCount; //平均值
        int mod = totalMoney % totalCount;// 余数，零头

        for (int i = 0; i < totalCount; i++) {
            if (i == totalCount - 1) {
                list.add(avg + mod);//有零头，需要放在最后一个红包当中
            } else {
                list.add(avg);
            }
        }
        return list;
    }
}
```

#### 随机发放

```java
public class RandomMode implements OpenMode {
    @Override
    public ArrayList<Integer> divide(final int totalMoney, final int totalCount) {
        ArrayList<Integer> list = new ArrayList<>();
        // 随机分发
        Random r = new Random();
        // 最少一分钱，最多不超过所剩金额平均数的2倍。
        int reminder = totalMoney;
        for (int i = 0; i < totalCount - 1; i++) {
            int max = (int) 2 * (reminder / (totalCount - i));
            int num = r.nextInt(max) + 1;
            list.add(num);
            reminder -= num;// 所剩金额越来越少
        }
        list.add(reminder);
        return list;
    }
}
```

