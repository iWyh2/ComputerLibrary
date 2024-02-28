## day02作业

#### 一、选择题：

**1、以下对接口描述错误的有（D）**
A) 接口没有提供构造器
B) 接口中的方法默认使用public、abstract修饰
C) 接口中的成员变量默认使用public、static、final修饰
D) 接口不允许多继承



**2、以下哪个接口的定义是正确的？ D **

```java
A.interface B{ 
   void print() { }  
  } 

B.abstract interface B { void print()  }  

C.abstract interface B extends A1,A2 { abstract void   print(){ }; 

D.interface B { void print();} 
```



**3. 列选项中关于Java中super关键字的说法错误的是（ B ）**

   A. 当子父类中成员变量重名时,在子类方法中想输出父类成员变量的值,可以用super区分子父类成员变量
   B. super语句可以放在构造器的任意一行
   C. 子类可以通过super关键字调用父类的方法
   D. 子类可以通过super关键字调用父类的属性

**4.  运行如下代码：控制台输出的结果是（A）**  

```java
class COne {
  public void f() {
    System.out.println("COne.f");
  }
}
class CTwo extends COne{
  public void f() {
    System.out.println("CTwo.f");
  }  
}
class CThree {
  public void g(COne one) {
    System.out.println("g(Cone)");
    one.f();
  }
  public void g(CTwo two) {
    System.out.println("g(Ctwo)");
    two.f();
  }
}
public class Main {
  public static void main(String[] args) {
    COne one = new CTwo();
    CThree three = new CThree();
    three.g(one);
  }
}
```

 A.  
 g(Cone)  
       CTwo.f 
B.  
 g(Cone)
       COne.f 
C.  
 g(Ctwo)
       CTwo.f 
D.  
 g(Ctwo)
       COne.f 



**5. [多选题]关于Java中的多态的前提，有哪几项（ A B C  ）**

   A. 要有继承或实现
   B. 父类类型的变量引用子类对象
   C. 存在方法重写
   D. 父类必须是抽象类

**6. 编译运行如下Java代码，输出结果是（ D   ）** 

```java
class Base {
  public void method(){
  	System.out.print ("Base method");
  }
}
class Child extends Base{
  public void methodB(){
  	System.out.print ("Child methodB");
  }
}
class Sample {
  public static void main(String[] args) {
    Base base= new Child();
    base.methodB();
  }
}
```

   A. Base method
   B. Child methodB
   C. Base method
​	Child methodB
   D. 编译错误

**7.  给定如下Java程序，Test类中的四个输出语句输出结果依次是（ C  ）** 

```java
class Person {
  String name="person";
  public void shout(){
  	System.out.println(name);
  }
}
class Student extends Person{
  String name="student";
  String school="school";
}
public class Test {
  public static void main(String[ ] args) {
    Person p=new Student();
    System.out.println(p instanceof Student);
    System.out.println(p instanceof Person);
    System.out.println(p instanceof Object);
    System.out.println(p instanceof System);
    }
} 
```

   A. true,false,true,false
   B. false,true,false,false
   C. true,true,true,编译错误
   D. true,true,false,编译错误

**8.  【多选题】下面关于Java接口的说法正确的是（ABD）**

   A. Java接口中定义的是扩展功能
   B. Java接口中可以被多个子类实现,一个类也可以同时实现多个接口
   C. Java接口中可以声明私有成员
   D. Java接口不能被实例化

**9.  给定java代码，如下：**      

```java
 abstract class Shape     { 
   abstract void draw( );     
} 
```

 要创建Shape类的子类Circle，以下代码正确的是（D）

   A. class Circle extends Shape{    int draw( ){}      } 
   B. abstract class Circle extends Shape{      } 
   C. class Circle extends Shape{    void draw( );  }
   D. class Circle extends Shape{    void draw( ){} } 

**10. 下面Java代码的运行结果是（A）**

```java
class Animal{
    private String name;  // 名字
    private int health;      // 健康值
    private String sex;   // 性别
    public Animal(String name){
        this.name = name;
    }
   public void print() {
        System.out.println("企鹅的名字是" + super.name +
                "，健康值是" + health + "，性别是" + sex + "。");
    }
}
class Penguin extends Animal {
    private String name = null; // 名字
    private int health = 0;     // 健康值
    private String sex = null;  // 性别
    public Penguin() {
        super("小可爱");
        health = 10;
        sex = "雄";
        System.out.println("执行构造器。");
    }
    public void print() {
        System.out.println("企鹅的名字是" + super.name +
                "，健康值是" + health + "，性别是" + sex + "。");
    }
    public static void main(String[] args) {
        Animal pgn = new Penguin();
        pgn.print();
    }
}
```

   A. 执行构造器。
​	企鹅的名字是小可爱，健康值是10，性别是雄。
   B. 执行构造器。
       企鹅的名字是null，健康值是0，性别是null。
   C. 企鹅的名字是小可爱，健康值是0，性别是null。
   D. 执行构造器。
       企鹅的名字是null，健康值是10，性别是雄。

**11. 【多选题】 在Java中，下面关于抽象类的描述正确的是（BD）**    

   A. 抽象类可以被实例化 
   B. 如果一个类中有一个方法被声明为抽象的，那么这个类必须是抽象类 
   C. 抽象类中的方法必须都是抽象的  
   D. 声明抽象类必须带有关键字abstract 

**12.  给定如下Java程序代码，在_横线处加入（A）语句，可以使这段代码编译通过。** 

```java
interface Parent{
   public int count(int i);
}

public class Test implements Parent {
   public int count(int i){
       return i % 9;
   }
   public static void main(String[] args){
       // 此处写什么代码？
       __________
       int i = p.count(20);
   }
}
```

   A. Test p = new Test();

   B. Parent p;

   C. Parent p = new Parent();

   D. Test p = new Parent();

------

#### 二、今日单词：

1. 判断左边的对象，是否是右边的类型的关键字： instanceof
2. 调用父类成员关键字：super
3. 定义抽象类的关键字：abstract
4. 定义常量关键字：static final
5. 定义接口关键字：interface
6. 实现接口关键字：implements

------

#### 三、简答题：

1. 什么是多态？多态的好处和弊端分别是什么？如何解决弊端？

   答：指对象和行为上的多态；好处是在多态形式下，右边的代码是解耦合的，更便于扩展和维护；定义方法时，使用父类类型作为形参，可以接收一切子类对象，扩展行更强，更便利；弊端是在多态形式下，不能调用子类特有的方法；解决方法是类型转换，自动类型转换和强制类型转换；

2. abstract不能和哪些关键字共存？为什么？

   答：private：abstract 是为了用来让子类继承的，子类不能继承父类 private 方法
   static：static 是属于类的，在类加载时同时被加载了，被类的所有实例共享，而且一定存在具体的实现。但是抽象类不能创建类的实例，抽象方法也没有方法体，这两个关键字本身就存在矛盾。
   final：final 的目的是防止属性和方法被修改，不能被继承，但是抽象方法就是用来被继承的。

3. 抽象类和普通父类有何区别？为什么要定义抽象父类？

   答：区别在于需要重写的方法，抽象类只需要写方法签名即可；定义抽象父类是为了更好的支持多态

4. final关键字能修饰哪些成员？各自特点是什么？

   答：

   - final修饰类：该类称为最终类，特点是不能被继承
   - final修饰方法：该方法称之为最终方法，特点是不能被重写。
   - final修饰变量：该变量只能被赋值一次。

5. 如果调用父类构造器？调用父类构造器的目的？

   答：super(..)；利用父类构造器去完成相同的功能，简化代码

6. 接口和抽象类有何区别？

   答：抽象类可以拥有和正常类一样的所有成员（成员变量、成员方法、构造器），而接口只能有常量和抽象方法；

------

#### 四、排错题：

##### 排错题1：

```java
// 以下代码是否有问题？为什么？如何解决？
interface A{
    static void method(){
        System.out.println("A-method");
    }
    default void show(){
        System.out.println("A-show");
    }
}
interface B{
    static void method(){
        System.out.println("B-method");
    }
    default void show(){
        System.out.println("B-show");
    }
}
interface C extends A,B{
    @Override
    default void show(){
        System.out.println("C-show");
    }
}
```

##### 排错题2：

```java
// 以下代码是否有问题？为什么？如何解决？
interface  A{
   int x = 0;
}
class B{
   int x = 1;
}
class C extends B implements A {
   public void pX(){
      System.out.println(A.x);
   }
   public static void main(String[] args) {
      new C().pX();
   }
}
```

##### 排错题3：

```java
// 以下代码是否有问题？为什么？如何解决？
public class Something {
   public static void main(String[] args) {
       Other o = new Other();
       new Something().addOne(o);
   }
   public void addOne(final Other o) {
       o.i++;
   }
}
class Other {
   public int i;
} 
```

------

#### 五、代码题：

##### 第一题： 分析以下需求，并用代码实现

	1.定义动物类:
		属性:
			年龄
		行为:
			喝水,吃东西(吃什么不确定)
	2.定义游泳接口:
		行为:
			游泳方法swimming
	3.定义狗类:
		行为:
			吃饭(啃骨头)和 游泳(狗刨)
	4.定义羊类:sheep
		行为:
			吃饭(羊啃草)
	5.定义青蛙类:frog
		行为:
			吃饭(吃虫子)和 游泳(蛙泳)
	6.定义饲养员类:breeder
		行为:
			饲养动物breed:包括吃饭和喝水
	7.定义测试类:
		创建饲养员对象,饲养员调用三次饲养方法:饲养狗,饲养羊,饲养青蛙
要求: 

​	1.子类重写父类中的吃东西方法
​	2.要求给狗和青蛙添加游泳的方法(实现游泳接口)
​	3.饲养员类中定义一个方法,传入动物类对象(父类),调用吃饭方法,如果有游泳方法也需进行测试

效果展示：

 ![1](image\1.jpg)

```java
public abstract class Animal {
    private int age;
    
    public abstract void eat();
    
    public abstract void drink();
}
```

​	

```java
public interface Swimming {
    void swimming();
}
```



```java
public class Dog extends Animal implements Swimming {
    @Override
    public void eat() {
        System.out.println("狗会啃骨头");
    }
    
    @Override
    public void drink() {
        System.out.println("狗喝水");
    }
    
    @Override
    public void swimming() {
        System.out.println("狗会狗刨");
    }
}
```



```java
public class Sheep extends Animal {
    @Override
    public void eat() {
        System.out.println("羊会吃草");
    }
    
    @Override
    public void drink() {
        System.out.println("羊喝水");
    }
}
```



```java
public class Frog extends Animal implements Swimming {
    @Override
    public void eat() {
        System.out.println("蛙会吃虫子");
    }
    
    @Override
    public void drink() {
        System.out.println("蛙喝水");
    }
    
    @Override
    public void swimming() {
        System.out.println("蛙会蛙泳");
    }
}
```



```java
public class Breeder {
    public void breed(Animal a) {
        a.eat();
        a.drink();
        
        if (a instanceof Swimming) {
            Swimming s = (Swimming) a;
            s.swimming();
        }
    }
}
```



------

##### 第二题：按要求定义类,完成以下功能：	

1.定义电视类TV，要求包含：
   1)成员变量:名称 name（ String s）；
   2)构造器:空参、满参构造器；
   3)成员方法:public void play(String channel) ,方法内,打印输出 "xx电视正在播放xxx节目"（channel表示电视节目);

2.定义遥控器类RemoteControl,包含:
​    成员方法:public void  controlTV(TV tv):方法内输出"遥控器控制电视",然后提示用户键盘录入一个字符串作为电视节目信息,调用tv的play方法,将节目信息作为参数传入；


3.定义测试类Test，在main方法实现以下功能：
​	* 创建TV对象；
​	* 创建RemoteControl对象,调用其controlTV的方法

效果演示：

![](image\2.jpg)



```java
public class TV {
    private String name;
    
    public TV() {}
    
    public TV(String name) {
        this.name = name;
    }
    
    public void play(String channel) {
        System.out.println(this.name+"电视正在播放"+channel+"节目");
    }
}
```



```java
public class RemoteControl {
    public void controlTV(TV tv) {
        System.out.println("遥控器控制电视");
        Scanner sc = new Scanner(System.in);
        tv.play(sc.next());
    }
}
```



------

##### 第三题：【选做题】

**训练目标**：掌握Java中抽象类以及继承的使用，以及理解其在开发中的应用

**需求背景**：在现在的互联网系统中大部分的网站都是支持手机号码登录的，当用户输入完手机号码点击获取短信验证码此时就会访问一些短信平台，由短信平台(阿里云短信平台、腾讯云短信平台)

给用户的手机号码上发送一个短信验证码！如下图所示：

| ![image](image/image-20220128212052382.png) |
| ------------------------------------------------------------ |

发送短信验证码的大致逻辑如下所示：

1、生成一个4位的随机的数字字符串

2、访问指定的短信服务平台让其完成验证码的发送

3、将验证码数据进行存储

**需求描述**：在素材的msg项目的AliyunSendMsg类和TencentSendMsg的指定位置补全代码，并使用模板设计模式对代码进行优化。实现短信验证码发送功能！案例实现效果如下所示：

1、当在Entry类中创建AliyunSendMsg对象时，在控制台输出

| ![image](image/image-20220128212616075.png) |
| ------------------------------------------------------------ |

2、当在Entry类中创建TencentSendMsg对象时，在控制台输出

| ![image](image/image-20220128212723338.png) |
| ------------------------------------------------------------ |

**实现提示**：

1、生成一个4位随机字符串(字符来源于chs数组)

2、发送短信验证码(由于知识储备不足，此处可以通过输出语句进行模拟)

3、创建CheckCode对象，将该对象存储到arrayList集合中

4、将AliyunSendMsg和TencentSendMsg中相同的代码向上进行抽取，将其定义到一个模板类中，然后让AliyunSendMsg和TencentSendMsg继承该类



CheckCode:

```java
package com.itheima.msg.domain;

public class CheckCode {            // 记录短信验证码的类

    private String phone ;          // 手机号码
    private String checkCode ;      // 验证码

    public String getPhone() {
        return phone;
    }

    public void setPhone(String phone) {
        this.phone = phone;
    }

    public String getCheckCode() {
        return checkCode;
    }

    public void setCheckCode(String checkCode) {
        this.checkCode = checkCode;
    }
}
```



AliyunSendMsg:

```java
package com.itheima.msg.service;

public class AliyunSendMsg extends SendMsg{
    @Override
    public void send(String phone, String code) {
        System.out.println("阿里云：" + phone + "发送了验证码" + code);
    }
}
```



SendMsg:

```java
package com.itheima.msg.service;

import com.itheima.msg.domain.CheckCode;

import java.util.ArrayList;
import java.util.Random;

public abstract class SendMsg {
    // 存储短信验证码的集合
    public ArrayList<CheckCode> arrayList = new ArrayList<>() ;
    private Random random = new Random();

    // 定义发送短信验证码时可选的数字字符
    public char[] chs = {'0' , '1' , '2' , '3' , '4' , '5' , '6' , '7' , '8' , '9'} ;

    // 发送短信验证码的方法
    public void sendMsg(String phone) {
        // 补全代码
        // 1、产生随机验证码。
        String code = "";

        for (int i = 0; i < 4; i++) {
            code += chs[random.nextInt(chs.length)];
        }
        // 2、模拟发送短信
        send(phone, code);

        // 3、存储验证码
        CheckCode checkCode = new CheckCode();
        checkCode.setPhone(phone);
        checkCode.setCheckCode(code);
    }

    public abstract void send(String phone, String code);
}
```



TencentSendMsg:

```java
package com.itheima.msg.service;


public class TencentSendMsg extends SendMsg{

    @Override
    public void send(String phone, String code) {
        System.out.println("腾讯云：" + phone + "发送了验证码" + code);
    }

}
```



Entry:

```java
package com.itheima.msg.entry;

import com.itheima.msg.service.AliyunSendMsg;
import com.itheima.msg.service.TencentSendMsg;

import java.util.Scanner;

public class Entry {
    public static void main(String[] args) {

        // 请输入手机号码
        Scanner sc = new Scanner(System.in) ;
        System.out.print("请您输入登录的手机号码: ");
        String phone = sc.nextLine();

        // 调用发送短信类的方法发送短信验证码
        // SendMsg sendMsg = new AliyunSendMsg();
        SendMsg sendMsg = new TencentSendMsg();
        sendMsg.sendMsg(phone);


        System.out.print("请您输入登录的手机号码: ");
        String phone2 = sc.nextLine();
        TencentSendMsg tencentSendMsg = new TencentSendMsg() ;
        tencentSendMsg.sendMsg(phone2);

    }

}
```

