alt + /   智能提示+自动补全



# 一、Java基础



## day01【前言、入门程序、常量、变量】

### 1. 关键字keywords

关键字：是指在程序中，Java已经定义好的单词，具有特殊含义。

- HelloWorld案例中，出现的关键字有 public 、class 、 static 、 void 等，这些单词已经被Java定义好，全部都是小写字母，notepad++中颜色特殊。
- 关键字比较多，不能死记硬背，学到哪里记到哪里即可。

### 2. 标识符

标识符：是指在程序中，我们自己定义内容。比如**类的名字、方法的名字和变量的名字**等等，都是标识符。

- 命名规则： `硬性要求`
  标识符可以包含英文字母26个(区分大小写) 、0-9数字 、$（美元符号） 和_（下划线） 。
  标识符不能以数字开头。
  标识符不能是关键字。
- 命名规范：`软性建议`
  类名规范：首字母大写，后面每个单词首字母大写（大驼峰式）。
  方法名规范： 首字母小写，后面每个单词首字母大写（小驼峰式）。
  变量名规范：全部小写。

### 3. 常量

定义：在Java程序中固定不变的数据

| 分类   |                                                          |                             |
| ------ | :------------------------------------------------------- | --------------------------- |
| 整数   |                                                          |                             |
| 小数   |                                                          |                             |
| 字符   | 单引号，只能写一个字符，必须有内容，一个汉字也是一个字符 | a' ， ' '， '好'            |
| 字符串 | 双引号，可以写多个字符，也可以不写                       | "A" ，"Hello" ，"你好" ，"" |
| 布尔   | true false                                               |                             |
| 空     | 只有一个值                                               | null                        |

### 4. 变量

定义：在程序中可以变化的量

注意事项：

* Java中要求一个变量每次只能保存一个数据，必须要明确保存的数据类型。

- 定义的变量，不赋值不能使用

### 5. 数据类型

分类：

- 基本数据类型：整数、浮点数、字符、布尔
- 引用数据类型：类、数组、接口

**四类八种基本数据类型**：

1字节 =  8位 = 8bit

| 数据类型     | 关键字                         | 内存占用 | 取值范围                   |
| ------------ | ------------------------------ | -------- | -------------------------- |
| 字节型       | byte                           | 1个字节  | -128~127共2^8=256个数      |
| 短整型       | short                          | 2        | -32768~32767               |
| 整型         | int（默认）                    | 4        | -(2的31次方)~(2的31次方-1) |
| 长整型       | long（**建议数据后加L表示**）  | 8        |                            |
| 单精度浮点数 | float（**建议数据后加F表示**） | 4        | 1.4013E-45~3.4028E+38      |
| 双精度浮点数 | double（默认）                 | 8        | 4.9E-324~1.7977E+308       |
| 字符型       | char                           | 2        | 0-65535                    |
| 布尔类型     | boolean                        | 1        | true，false                |

**Java中的默认类型：整数类型是int 、浮点类型是double 。**

## day02 【数据类型转换、运算符】

### 1. 数据类型转换

* 自动转换

  取值范围小的类型 -> 大范围类型

  byte、short、char‐‐>int‐‐>long‐‐>float‐‐>double

  ```java
  public static void main(String[] args) {
      int i = 1;
      byte b = 2;
      // byte x = b + i; // 报错
      //int类型和byte类型运算，结果是int类型
      int j = b + i;
      System.out.println(j);
  }
  ```

  ```java
  public static void main(String[] args) {
      int i = 1;
      double d = 2.5;
      //int类型和double类型运算，结果是double类型
      //int类型会提升为double类型
      double e = d+i;
      System.out.println(e);
  }
  ```

* 强制转换

  ```java
  int i = 1.5; // 错误
  // double类型数据强制转成int类型，直接去掉小数点。
  int i = (int) 1.5;
  ```

  ```java
  public static void main(String[] args) {
      //short类型变量，内存中2个字节
      short s = 1;
      /*
      出现编译失败
      s和1做运算的时候，1是int类型，s会被提升为int类型
      s+1后的结果是int类型，将结果在赋值会short类型时发生错误
      short内存2个字节，int类型4个字节，s = s + 1会砍掉int中前面两个字节
      必须将int强制转成short才能完成赋值
      */
      s = s + 1；//编译失败
      s = (short)(s+1);//编译成功
  }
  ```

  ```java
  /*
  强制类型转换
  	1. 特点：代码需要进行特殊的格式处理，不能自动完成。
  	2. 格式：范围小的类型 范围小的变量名 = (范围小的类型) 原本范围大的数据;
  
  注意事项：
  	1. 强制类型转换一般不推荐使用，因为有可能发生精度损失、数据溢出。
  	2. byte/short/char这三种类型都可以发生数学运算，例如加法“+”.
  	3. byte/short/char这三种类型在运算的时候，都会被首先提升成为int类型，然后再计算。
  	4. boolean类型不能发生数据类型转换
  */
  public class Demo02DataType {
  	public static void main(String[] args) {
  		// 左边是int类型，右边是long类型，不一样
  		// long --> int，不是从小到大
  		// 不能发生自动类型转换！
  		// 格式：范围小的类型 范围小的变量名 = (范围小的类型) 原本范围大的数据;
  		int num = (int) 100L;
  		System.out.println(num);
  		
  		// long强制转换成为int类型
  		int num2 = (int) 6000000000L;
  		System.out.println(num2); // 1705032704
  		
  		// double --> int，强制类型转换
  		int num3 = (int) 3.99;
  		System.out.println(num3); // 3，这并不是四舍五入，所有的小数位都会被舍弃掉
  		
  		char zifu1 = 'A'; // 这是一个字符型变量，里面是大写字母A
  		System.out.println(zifu1 + 1); // 66，也就是大写字母A被当做65进行处理
  		// 计算机的底层会用一个数字（二进制）来代表字符A，就是65
  		// 一旦char类型进行了数学运算，那么字符就会按照一定的规则翻译成为一个数字
  		
  		byte num4 = 40; // 注意！右侧的数值大小不能超过左侧的类型范围
  		byte num5 = 50;
  		// byte + byte --> int + int --> int
  		int result1 = num4 + num5;
  		System.out.println(result1); // 90
  		
  		short num6 = 60;
  		// byte + short --> int + int --> int
  		// int强制转换为short：注意必须保证逻辑上真实大小本来就没有超过short范围，否则会发生数据溢出
  		short result2 = (short) (num4 + num6);
  		System.out.println(result2); // 100
  	}
  }
  ```



### 2. ASCII编码表

记住三个ASCII值：48代表0；65代表A；97代表a

```java
/*
数字和字符的对照关系表（编码表）：

ASCII码表：American Standard Code for Information Interchange，美国信息交换标准代码。
Unicode码表：万国码。也是数字和符号的对照关系，开头0-127部分和ASCII完全一样，但是从128开始包含有更多字符。

48 - '0'
65 - 'A'
97 - 'a'
*/
public class Demo03DataTypeChar {
	public static void main(String[] args) {
		char zifu1 = '1';
		System.out.println(zifu1 + 0); // 49
		
		char zifu2 = 'A'; // 其实底层保存的是65数字
		
		char zifu3 = 'c';
		// 左侧是int类型，右边是char类型，
		// char --> int，确实是从小到大
		// 发生了自动类型转换
		int num = zifu3;
		System.out.println(num); // 99
		
		char zifu4 = '中'; // 正确写法
		System.out.println(zifu4 + 0); // 20013
	}
}

```

### 3. 运算符

* 算数运算符

  前++与后++

  * 变量前++ ：变量a自己加1，将加1后的结果赋值给b，也就是说a先计算。a和b的结果都是2。

  * 变量后++ ：变量a先把自己的值1，赋值给变量b，此时变量b的值就是1，变量a自己再加1。a的结果是2，b的结果是1。

  ```java
  public static void main(String[] args) {
      int a = 1;
      int b = ++a;
      System.out.println(a);//计算结果是2
      System.out.println(b);//计算结果是2
  }
  ```

  ```java
  public static void main(String[] args) {
      int a = 1;
      int b = a++;
      System.out.println(a);//计算结果是2
      System.out.println(b);//计算结果是1
  }
  ```

  +遇到字符串表示拼接

  ```java
  public static void main(String[] args){
  	System.out.println("5+5="+5+5);//输出5+5=55
  }
  ```

  

* 赋值运算符

  +=符号：s += 1 逻辑上看作是s = s + 1 计算结果被提升为int类型，再向short类型赋值时发生错误，因为不能将取值范围大的类型赋值到取值范围小的类型。但是， s=s+1进行两次运算， += 是一个运算符，只运算一次，并带有强制转换的特点，也就是说s += 1 就是s = (short)(s + 1) ，因此程序没有问题编译通过，运行结果是2.

  ```java
  public static void main(String[] args){
      short s = 1;
      s+=1;//等价于s = (short)(s + 1)
      System.out.println(s);
  }
  ```

  

* 比较运算符

  返回boolean值

* 逻辑运算符

  | 逻辑运算符    |                                         |
  | ------------- | --------------------------------------- |
  | ``&&`` 短路与 | 短路特点：符号左边是false，右边不再运算 |
  | `||`短路或    | 短路特点： 符号左边是true，右边不再运算 |
  | `!` 取反      |                                         |

  ```java
  public static void main(String[] args) {
      System.out.println(true && true);//true
      System.out.println(true && false);//false
      System.out.println(false && true);//false，右边不计算
      System.out.println(false || false);//falase
      System.out.println(false || true);//true
      System.out.println(true || false);//true，右边不计算
      System.out.println(!false);//true
  }
  ```

  

* 三元运算符

```java
public static void main(String[] args) {
    int i = (1==2 ? 100 : 200);
    System.out.println(i);//200
    int j = (3<=4 ? 500 : 600);
    System.out.println(j);//500
}
```

### 4. JShell脚本工具

* JShell脚本工具是JDK9的新特性
* 什么时候会用到JShell 工具呢：当我们编写的代码非常少的时候，而又不愿意编写类，main方法，也不愿意去编译和运行，这个时候可以使用JShell工具。
* 使用步骤：
  * 启动JShell工具，在DOS命令行直接输入JShell命令。
  * 编写Java代码，无需写类和方法，直接写方法中的代码即可，同时无需编译和运行，直接回车即可
  * 退出指令  /exit

### 5. 常量和变量的运算

```java
public static void main(String[] args){
    byte b1=1;
    byte b2=2;
    byte b3=1 + 2;
    /*
    在编译的时候，编译器javac不确定b2+b3的结果是什么，因此会将结果以int类型进行处理，所以int类型不能赋值给byte类型，因此编译失败
    */
    byte b4=b2 + b3;//编译失败
    System.out.println(b3);
    System.out.println(b4);
}

```

## day03【 流程控制语句】

### 1. 判断语句

三种：if；if...else；if...else if...else

```java
public class ifPanDuan {
    public static void main(String[] args) {
        // x和y的关系满足如下：
        // x>=3 y = 2x + 1;
        //‐1<=x<3 y = 2x;
        // x<=‐1 y = 2x – 1;
        // 根据给定的x的值，计算出y的值并输出。
        // 定义变量
        int x = 5;
        int y;
        if (x >= 3) {
            y = 2 * x + 1;
        } else if (-1 <= x && x < 3) {
            y = 2 * x;
        } else {
            y = 2 * x - 1;
        }
        System.out.println("y的值是" + y);
    }
}
```

### 2.选择语句

* 结构

switch...case

```java
switch (表达式){
    case 常量值1:
        语句体1;
        break;
    case 常量值2:
        语句体2;
        break;
    ...
    default:
    	语句体n+1;
        break;
}        
```

实例：

```java
public class Test {
    public static void main(String[] args) {
	//定义变量，判断是星期几
        int weekday = 6;
	//switch语句实现选择
        switch (weekday) {
            case 1:
                System.out.println("星期一");
                break;
            case 2:
                System.out.println("星期二");
                break;
            case 3:
                System.out.println("星期三");
                break;
            case 4:
                System.out.println("星期四");
                break;
            case 5:
                System.out.println("星期五");
                break;
            case 6:
                System.out.println("星期六");
                break;
            case 7:
                System.out.println("星期日");
                break;
            default:
                System.out.println("你输入的数字有误");
                break;// 最后一个break语句可以省略，但是强烈推荐不要省略
        }
    }
}
```

* case的穿透性

如果case的后面不写break，将出现穿透现象，也就是 不会再判断下一个case的值，直接向后运
行，直到遇到break，或者整体switch结束。

**注意事项**：

* 多个case后面的数值不可以重复。
* switch后面小括号当中只能是下列数据类型：
  基本数据类型：byte/short/char/int
  引用数据类型：String字符串、enum枚举
* switch语句格式可以很灵活：前后顺序可以颠倒，而且break语句还可以省略。
  “匹配哪一个case就从哪一个位置向下执行，直到遇到了break或者整体结束为止。”

### 3. 循环语句

* for循环

  格式：

  ```java
  for(初始化表达式step1; 布尔表达式step2; 步进表达式step3){
      循环体step4
  }
  ```

  实例：

  ```java
  public class Test {
      public static void main(String[] args) {
          for (int i = 0; i < 5; i++) {
              System.out.println("HelloWorld" + i);
          }
      }
  }
  ```

  

* while循环

  格式：

  ```java
  初始化表达式step1
  while(布尔表达式step2){
      循环体step3
      步进表达式step4
  }
  ```

  实例：

  ```java
  public class Test {
      public static void main(String[] args) {
          int i = 0;
          while (i < 10) {
              System.out.println("HelloWorld" + i);
              i++;
          }
      }
  }
  ```

  

* do...while循环 【初学者不建议使用】

  格式：

  ```java
  初始化表达式step1
  do{
      循环体step3
      步进表达式step4
  }while(布尔表达式step2);
  ```

  实例：

  ```java
  public class Test {
      public static void main(String[] args) {
          int i = 0;
          do {
              System.out.println("HelloWrold" + i);
              i++;
          } while (i<10);
      }
  }
  ```

* 循环中的跳出语句：break与continue

  ```java
  //break
  //遇到break，跳出整个循环
  public class Test {
      public static void main(String[] args) {
          //需求:打印完两次HelloWorld之后结束循环
          for(int i = 0; i<5; i++){
              if(i == 2){
                  break;
              }
              System.out.println("HelloWorld" + i);
          }
      }
  }
  HelloWorld0
  HelloWorld1
  ```

  ```java
  //continue
  //本次循环至continue，然后进入下一轮循环
  public class Test {
      public static void main(String[] args) {
          //需求:打印完两次HelloWorld之后结束循环
          for(int i = 0; i<5; i++){
              if(i == 2){
                  continue;
              }
              System.out.println("HelloWorld" + i);
          }
      }
  }
  HelloWorld0
  HelloWorld1
  HelloWorld3
  HelloWorld4
  ```

* 死循环 while(true){}

  使用死循环的场景，例如：我们需要读取用户输入的输入，但是用户输入多少数据我们并不清楚，也只能使用死循环，当用户不想输入数据了，就可以结束循环了，如何去结束一个死循环呢，就需要使用到跳出语句了。

* 嵌套循环

  for内有for

  ```java
  public class Test {
      public static void main(String[] args) {
          //使用嵌套循环，打印5*8的矩形
          for (int i = 0; i < 5; i++) {
              for (int j = 0; j < 8; j++) {
                  System.out.print("*");
              }
              System.out.println();
          }
      }
  }
  ********
  ********
  ********
  ********
  ********
  ```





## day04【IDEA、方法】

### 1. 开发工具IntelliJ IDEA的使用

* 常用快捷键

  | 快捷键                               | 功能                                        |
  | ------------------------------------ | ------------------------------------------- |
  | Alt+Enter                            | 导入包，自动修正代码                        |
  | Ctrl+Y                               | 删除光标所在行                              |
  | Ctrl+D                               | 复制光标所在行的内容，插入光标位置下面      |
  | Ctrl+Alt+L                           | 格式化代码                                  |
  | Ctrl+/                               | 单行注释                                    |
  | Ctrl+Shift+/                         | 选中代码注释，多行注释，再按取消注释        |
  | Alt+Ins                              | 自动生成代码，toString，get，set等方法      |
  | Alt+Shift+上下箭                     | 移动当前代码行                              |
  | Alt+1  与 Alt + 4                    | 隐藏/展开左侧项目栏  与 隐藏/展开下侧运行栏 |
  | 数字/数组等.fori 与 数字/数组等.forr | for循环的正序遍历与倒叙遍历                 |
  | 选中要改的变量->Shift + F6           | 多个位置使用了某变量，改变这些变量的名字    |

### 2. 方法

* 定义：将一个功能抽取出来，把代码单独定义在一个大括号内，形成一个单独的功能。当我们需要这个功能的时候，就可以去调用。这样即实现了代码的复用性，也解决了代码冗余的现象。

```java
/*
修饰符 返回值类型 方法名 (参数列表) {
	代码...
	return ;
}
*/
//修饰符：public static 固定写法
//返回值类型：void
//方法名：methodName
public static void methodName() {
	System.out.println("这是一个方法");
}
```

* 方法调用的三种形式：

  根据有无返回值分类！！

  * 直接调用：直接写方法名调用

    ```java
    public class Test {
        public static void main(String[] args) {
            print();
        }
        public static void print(){
            System.out.println("方法被调用");
        }
    }
    ```

    

  * 赋值调用：调用方法，在方法前面定义变量，接受方法返回值

    ```java
    public class Test {
        public static void main(String[] args) {
            int sum = getSum(5,6);
            System.out.println(sum);
        }
        public static int getSum(int a,int b) {
            return a + b;
        }
    }
    ```

    

  * 输出语句调用：

    * 在输出语句中调用方法，`System.out.println(方法名())`

      ```java
      public static void main(String[] args) {
      System.out.println(getSum(5,6));
      }
      public static int getSum(int a,int b) {
      return a + b;
      }
      ```

      

    * 不能用输出语句调用`void`类型的方法。因为执行后没有结果，也就打印不出任何内容

      ```java
      public static void main(String[] args) {
      System.out.println(printHello());// 错误，不能输出语句调用void类型方法
      }
      public static void printHello() {
      System.out.println("Hello");
      }
      ```

* 方法重载

  定义：指在同一个类中，允许存在一个以上的同名方法，只要它们的参数列表不同即可，与修饰符和返回值类型无关。

  * 参数列表：个数不同，数据类型不同，顺序不同。
  * 重载方法调用：JVM通过方法的参数列表，调用不同的方法

  练习1：

  ```java
  public class Test {
      public static void main(String[] args) {
          byte a = 10;
          byte b = 20;
          short c = 20;
          short d = 20;
          int e = 10;
          int f = 10;
          long g = 10;
          long h = 20;
          System.out.println(compare(a, b));
          System.out.println("=================");
  
          System.out.println(compare(c, d));
          System.out.println("=================");
  
          System.out.println(compare(e, f));
          System.out.println("=================");
  
          System.out.println(compare(g, h));
          System.out.println("=================");
      }
      public static boolean compare(byte a, byte b){
          System.out.println("byte");
          return a == b;
  
      }
      public static boolean compare(short a, short b){
          System.out.println("short");
          return a == b;
      }
      public static boolean compare(int a, int b){
          System.out.println("long");
          return a == b;
      }
      public static boolean compare(long a, long b){
          System.out.println("long");
          return a == b;
      }
  }
  ```

  练习2：

  判断哪些方法是重载关系。

  ```java
  public static void open(){} //正确重载
  public static void open(int a){}//正确重载
  static void open(int a,int b){}//代码错误：和第8行冲突
  public static void open(double a,int b){}//正确重载
  public static void open(int a,double b){}//代码错误：和第6行冲突
  public void open(int i,double d){}//代码错误：和第5行冲突
  public static void OPEN(){}//代码正确不会报错，但是并不是有效重载
  public static void open(int i,int j){}//代码错误：和第3行冲突
  ```

  练习3：

  模拟输出语句中的`println` 方法效果，传递什么类型的数据就输出什么类型的数据，只允许定义一个方法名`println `。

* **注意事项**：一个方法不能定义在另一个方法内部

```java
public class Demo {
	public static void main(String[] args){
	//错误写法，一个方法不能定义在另一方法内部
		public static void method(){}
	}
}
```

* 方法中的可变参数

```java
/*
    可变参数:是JDK1.5之后出现的新特性
    使用前提:
        当方法的参数列表数据类型已经确定,但是参数的个数不确定,就可以使用可变参数.
    使用格式:定义方法时使用
        修饰符 返回值类型 方法名(数据类型...变量名){}
    可变参数的原理:
        可变参数底层就是一个数组,根据传递参数个数不同,会创建不同长度的数组,来存储这些参数
        传递的参数个数,可以是0个(不传递),1,2...多个

 */
public class Demo01VarArgs {
    public static void main(String[] args) {
        //int i = add();
        //int i = add(10);
        int i = add(10,20);
        //int i = add(10,20,30,40,50,60,70,80,90,100);
        System.out.println(i);

        method("abc",5.5,10,1,2,3,4);
    }

    /*
        可变参数的注意事项
            1.一个方法的参数列表,只能有一个可变参数
            2.如果方法的参数有多个,那么可变参数必须写在参数列表的末尾
     */
    /*public static void method(int...a,String...b){

    }*/

    /*public static void method(String b,double c,int d,int...a){
    }*/

    //可变参数的特殊(终极)写法
    public static void method(Object...obj){

    }

    /*
        定义计算(0-n)整数和的方法
        已知:计算整数的和,数据类型已经确定int
        但是参数的个数不确定,不知道要计算几个整数的和,就可以使用可变参数
        add(); 就会创建一个长度为0的数组, new int[0]
        add(10); 就会创建一个长度为1的数组,存储传递来过的参数 new int[]{10};
        add(10,20); 就会创建一个长度为2的数组,存储传递来过的参数 new int[]{10,20};
        add(10,20,30,40,50,60,70,80,90,100); 就会创建一个长度为2的数组,存储传递来过的参数 new int[]{10,20,30,40,50,60,70,80,90,100};
     */
    public static int add(int...arr){
        //System.out.println(arr);//[I@2ac1fdc4 底层是一个数组
        //System.out.println(arr.length);//0,1,2,10
        //定义一个初始化的变量,记录累加求和
        int sum = 0;
        //遍历数组,获取数组中的每一个元素
        for (int i : arr) {
            //累加求和
            sum += i;
        }
        //把求和结果返回
        return sum;
    }

    //定义一个方法,计算三个int类型整数的和
    /*public static int add(int a,int b,int c){
        return a+b+c;
    }*/

    //定义一个方法,计算两个int类型整数的和
    /*public static int add(int a,int b){
        return a+b;
    }*/
}

```





## day05【数组】

概念：存储数据长度固定的容器，保证多个数据的数据类型要一致。

### 1. 数组的定义

* 格式一

  ```java
  数据存储的数据类型[] 数组名字 = new 数组存储的数据类型[长度];
  ```

  * 数组存储的数据类型： 创建的数组容器可以存储什么数据类型。
  * [] : 表示数组。
  * 数组名字：为定义的数组起个变量名，满足标识符规范，可以使用名字操作数组。
  * new：关键字，创建数组使用的关键字。
  * 数组存储的数据类型： 创建的数组容器可以存储什么数据类型。
  * [长度]：数组的长度，表示数组容器中可以存储多少个元素。
  * 注意：数组有定长特性，长度一旦指定，不可更改。
    * 和水杯道理相同，买了一个2升的水杯，总容量就是2升，不能多也不能少。

  举例：

  ```java
  // 定义可以存储3个整数的数据容器
  int[] arr = new int[3];
  ```

  

* 格式二

  ```java
  数据类型[] 数组名 = new 数据类型[]{元素1,元素2,元素3,...};
  举例：定义存储1,2,3,4,5整数的数组容器
  int[] arr = new int[]{1,2,3,4,5};
  ```

  

* 格式三

  ```java
  int[] arr = {1,2,3,4,5};
  ```

  

### 2. 数组的访问

```java
public class Test {
    public static void main(String[] args) {
        //定义存储int类型数组，赋值元素1，2，3，4，5
        int[] arr = {1,2,3,4,5};
        //为0索引元素赋值为6
        arr[0] = 6;
        //获取数组0索引上的元素
        int i = arr[0];
        System.out.println(i);
        //直接输出数组0索引元素
        System.out.println(arr[0]);
    }
}
```



### 3. Java中的内存划分

分成5个部分：

（1）栈（stack）：存放的都是方法中的局部变量。方法的运行一定要在栈当中运行。

​				局部变量：方法的参数，或者是方法{}内部的变量。

​				作用域：一旦超出作用域，立刻从栈内存当中消失。

（2）堆（Heap）：凡是new出来的东西，都在栈当中。

​				堆内存里面的东西都有一个地址值：16进制

​				堆内存里面的数据都有默认值。规则：

​							如果是整数					默认0

​							如果是浮点数				默认0.0

​							如果是字符					默认'\u0000'

​							如果是布尔					默认false

​							如果是引用类型			默认null

（3）方法区（Method Area）：存储.class相关信息，包含方法的信息。



（4）本地方法栈（Native Method Stack）：与操作系统相关。

（5）寄存器（pc Register）：与CPU相关

### 4. 数组在内存中的存储

* 一个数组内存图

  ```java
   class Test {
      public static void main(String[] args) {
          int[] arr = new int[3];
          System.out.println(arr);//[I@50cbc42f
          System.out.println(arr[0]);//0，输出数组 索引是0 位置处的值
      }
  }
  ```

  [I@50cbc42f是数组在内存中的地址，new出来的内容，都是在堆内存中存储的，而方法中的变量arr保存的是数组的地址。

  ![image-20210223175648876](Java%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0.assets/一个数组的内存图.png)

* 两个相互独立的数组 的内存图

  ![image-20210223180029879](Java%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0.assets/两个相互独立的数组的内存图.png)

* 两个引用指向同一个数组的内存图

  ![两个引用指向同一个数组的内存图](Java%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0.assets/%E4%B8%A4%E4%B8%AA%E5%BC%95%E7%94%A8%E6%8C%87%E5%90%91%E5%90%8C%E4%B8%80%E4%B8%AA%E6%95%B0%E7%BB%84%E7%9A%84%E5%86%85%E5%AD%98%E5%9B%BE.png)

  

### 5.数组常见操作 

#### 5.1 数组越界异常

```java
public class Test {
    public static void main(String[] args) {
        int[] arr = {1,2,3};
        System.out.println(arr[3]);
    }
}
Exception in thread "main" java.lang.ArrayIndexOutOfBoundsException: 3
	at Test.main(Test.java:4)
```

* 创建数组，赋值3个元素，数组的索引就是0，1，2，没有3索引，因此我们不能访问数组中不存在的索引，程序运行后，将会抛出 `ArrayIndexOutOfBoundsException `数组越界异常。

* 在开发中，数组的越界异常是不能出现的，一旦出现了，就必须要修改我们编写的代码。

#### 5.2 数组空指针异常

```java
public class Test {
    public static void main(String[] args) {
        int[] arr = {1,2,3};
        arr = null;//不保存数组地址
        System.out.println(arr[0]);
    }
}
Exception in thread "main" java.lang.NullPointerException
	at Test.main(Test.java:5)
```

* `arr = null` 这行代码，意味着变量arr将不会在保存数组的内存地址，也就不允许再操作数组了，因此运行的时候会抛出`NullPointerException` 空指针异常。

* 在开发中，数组的空指针异常是不能出现的，一旦出现了，就必须要修改我们编写的代码。

#### 5.3 数组遍历【重点】

```java
public class Test {
    public static void main(String[] args) {
        int[] arr = {1, 2, 3, 4, 5};
        for (int i = 0; i < arr.length; i++) {
            System.out.println(arr[i]);
        }
    }
}
```

#### 5.4 数组获取最大值元素

```java
public class Test {
    public static void main(String[] args) {
        int[] arr = {5, 15, 2000, 10000, 100, 4000};
        int max = arr[0];
        for (int i = 0; i < arr.length; i++) {
            if (arr[i] > max) {
                max = arr[i];
            }
        }
        System.out.println("数组最大值是：" + max);
    }
}
```

#### 5.5 数组反转

```java
public class Test {
    public static void main(String[] args) {
        int[] arr = {1, 2, 3, 4, 5};
        int left = 0;
        int right = arr.length - 1;
        while (left < right){
            int tmp = arr[left];
            arr[left] = arr[right];
            arr[right] = tmp;
            left++;
            right--;
        }
        for (int i = 0; i < arr.length; i++) {
            System.out.println(arr[i]);
        }
    }
}
```



### 6.数组作为方法的参数和返回值

* 数组作为方法的参数

  ```java
  public class Test {
      public static void main(String[] args) {
          int[] arr = {1, 3, 5, 7, 9};
          printArray(arr);
      }
      public static void printArray(int[] arr){
          for (int i = 0; i < arr.length; i++) {
              System.out.println(arr[i]);
          }
      }
  }
  ```

  数组作为方法的参数传递，传递的参数是数组内存的地址

* 数组作为方法返回值

  ```java
  public class Test {
      public static void main(String[] args) {
          int[] arr = getArray();
          for (int i = 0; i < arr.length; i++) {
              System.out.println(arr[i]);
          }
      }
      public static int[] getArray() {
          int[] arr = {1, 3, 5, 7, 9};
          return arr;
      }
  }
  ```

  数组作为方法的返回值，返回的是数组的内存地址

* 方法的参数类型区别

  方法的参数为基本类型时,传递的是数据值. 方法的参数为引用类型时,传递的是地址值.

## day06【类与对象、封装、构造方法】

### 1. 面向对象思想概述

* 对象：泛指现实中一切事物，每种事物都具备自己的**属性**和**行为**。

* 面向对象：区别于面向过程思想，强调的是**通过调用对象的行为来实现功能**，而不是自己一步一步的去操作实现。

* 三大基本特征：**封装、继承、多态**

### 2. 类和对象

* 类：是一组相关**属性和行为**的集合。可以看成是一类事物的模板，使用事物的属性特征和行为特征来描述该类事物。

* 属性：该事物的状态信息。

* 行为：该事物能够做什么。
* 对象：是一类事物的具体体现。对象是类的一个实例（对象并不是找个女朋友），必然具备该类事物的属性和行为。
* 类是对象的模板，对象是类的实体

### 3. 类的定义

Java中用class描述事物：

* **成员变量**：对应事物的属性。

* **成员方法**：对应事物的行为。

```java
public class ClassName{
    //成员变量：在类中，方法外。
    //成员方法：和以前定义方法几乎是一样的；只不过把static去掉。
}
```

实例：

```java
public class Student {
    String name;
    int age;
    public void study(){
        System.out.println("好好学习，天天向上");
    }
    public void eat(){
        System.out.println("学习饿了要吃饭");
    }
}
```

### 4. 对象的使用

创建对象：

```java
类名 对象名 = new 类名();
```

使用对象访问类中的成员：

```java
对象名.成员变量;
对象.成员方法();
```

对象的使用格式举例：

```java
public class Test {
    public static void main(String[] args) {
        Student s = new Student();
        System.out.println("s:"+s);

        System.out.println("姓名："+s.name);
        System.out.println("年龄："+s.age);
        System.out.println("------");

        s.name = "赵丽颖";
        s.age = 18;

        System.out.println("姓名："+s.name);
        System.out.println("年龄："+s.age);
        System.out.println("------");

        s.study();
        s.eat();
    }
}
```

**成员变量的默认值：**

|          | 数据类型                       | 默认值   |
| -------- | ------------------------------ | -------- |
| 基本类型 | 整数（byte, short, int, long） | 0        |
|          | 浮点数（float, double）        | 0.0      |
|          | 字符（char）                   | '\u0000' |
|          | 布尔（boolean）                | false    |
| 引用类型 | 数组，类，接口                 | null     |

### 5. 对象内存图

class放到方法区，方法在栈中运行，new出来的在堆中。

* 一个对象，调用一个方法内存图

  ![image-20210223210152019](Java%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0.assets/一个对象调用方法的内存图.png)

* 两个对象，调用同一方法内存图

  ![image-20210223210430233](Java%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0.assets/两个对象调用同一方法的内存图.png)

* 两个引用指向同一对象的内存图

  ![image-20210223210755317](Java%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0.assets/两个引用指向同一对象的内存图.png)

* 使用对象类型作为方法的参数

  ![image-20210223211041418](Java%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0.assets/使用对象类型作为方法的参数的内存图.png)

* 使用对象类型作为方法的返回值

  ![image-20210223211422024](Java%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0.assets/使用对象类型作为方法的返回值的内存图.png)

### 6. 成员变量和局部变量的区别

```java
public class Car{
    String color;//成员变量，默认有初始值
    public void drive(){
        int speed = 80;//局部变量
        System.out.pintln("时速："+speed);
    }
    
}
```

**两种变量的不同：**

* 初始化值的不同

  成员变量有默认值；局部变量没有默认值，必须先定义、赋值，才能使用

* 在内存中位置不同

  成员变量在堆内存中；局部变量在栈内存中

* 生命周期不同

  成员变量随着对象的创建而存在，随其消失而消失；

  局部变量随方法的调用而存在，随方法的调用完毕而消失。

### 7. 封装概述

面向对象编程语言是对客观世界的模拟，客观世界里**成员变量都是隐藏在对象内部的**，外界无法直接操作和修改。封装可以被认为是一个保护屏障，**防止该类的代码和数据被其他类随意访问**。要访问该类的数据，必须通过指定的方式。适当的封装可以让代码更容易理解与维护，也加强了代码的安全性。

**将属性隐藏起来，若需要访问某个属性，提供公共方法对其访问。**

其后章节还有”接口的私有方法“

### 8. 封装的操作

* 操作步骤

  * 使用 private 关键字来修饰成员变量。

  * 对需要访问的成员变量，提供对应的一对 getXxx 方法 、setXxx 方法。

* private的含义

  * private是一个权限修饰符，代表最小权限。

  * 可以修饰成员变量和成员方法。

  * 被private修饰后的成员变量和成员方法，**只在本类中才能访问**。

实例：

```java
public class Student {
    private String name;
    private int age;

    public void setName(String n) {
        name = n;
    }

    public String getName() {
        return name;
    }

    public void setAge(int a) {
        age = a;
    }

    public int getAge() {
        return age;
    }

    public void study() {
        System.out.println("好好学习，天天向上");
    }

    public void eat() {
        System.out.println("学习饿了要吃饭");
    }
}
```



### 9. 封装的优化1——this关键字

我们发现 setXxx 方法中的形参名字并**不符合见名知意的规定**，那么如果修改与成员变量名一致，是否就见名知意了呢？代码如下：

```java
public class Student {
    private String name;
    private int age;
    public void setName(String name) {
    	name = name;
	}
    public void setAge(int age) {
    	age = age;
    }
}
```

以上代码给成员变量赋值失败！

原因：形参变量名与成员变量名重名，导致成员变量名被隐藏，方法中的变量名，无法访问到成员变量。

解决方法：使用this关键字，**注意：通过谁调用的方法，谁就是this**

```java
public class Student {
    private String name;
    private int age;

    public void setName(String name) {
        //name = name;
        this.name = name;
    }

    public String getName() {
        return name;
    }

    public void setAge(int age) {
        //age = age;
        this.age = age;
    }

    public int getAge() {
        return age;
    }

    public void study() {
        System.out.println("好好学习，天天向上");
    }

    public void eat() {
        System.out.println("学习饿了要吃饭");
    }
}
```

### 10. 封装的优化2——构造方法

* 当一个对象被创建的时候，构造方法用来初始化该对象，给对象的成员变量赋初始值。
* 创建对象**new那步就是在调用构造方法**。
* 无论是否自定义构造方法，所有类都有构造方法，因为Java自动提供了一个无参数的构造方法。
* 一旦自己定义了构造方法，Java自动提供的 无参数的 构造方法就会失效。
* 构造方法的方法名 与 它所在的 类名 完全相同（就连大小写也相同），没有返回值，**不需要void**。

实例：

```java
public class Student {
    private String name;
    private int age;
	// 无参数构造方法
    public Student(){}
    // 有参数构造方法
    public Student(String name, int age){
        this.name = name;
        this.age = age;
    }
}
```

**注意事项：**

* 如果你不提供构造方法，系统会给出无参数构造方法。

* 如果你提供了构造方法，系统将**不再提供无参数构造方法**。

  上述代码中，如果注释掉无参数的构造方法，使用类构造对象时，必须传递参数，不传参数就会报错。

* 构造方法是可以重载的，既可以定义参数，也可以不定义参数。

### 11. 标准代码——JavaBean

`JavaBean`是Java语言编写类的一种标准规范。符合`JavaBean` 的类，要求类必须是具体的和公共的，并且**具有无参数的构造方法**，提供用来操作成员变量的`set` 和`get `方法。

**intellij idea快捷键生成：alt + ins**

```java
public class ClassName{
    //成员变量
    //构造方法
    //无参构造方法【必须】
    //有参构造方法【建议】
    //成员方法
    //getXxx()
    //setXxx()
}
```

实例：

```java
public class Student{
    private String name;
    private int age;

    public void setName(String name) {
        this.name = name;
    }

    public void setAge(int age) {
        this.age = age;
    }

    public String getName() {

        return name;
    }

    public int getAge() {
        return age;
    }

    public Student(String name, int age) {

        this.name = name;
        this.age = age;
    }

    public Student() {
    }
}
```

测试类的代码如下：

```java
public class Test {
    public static void main(String[] args) {
        Student s = new Student();
        s.setName("柳岩");
        s.setAge(18);

        System.out.println(s.getName()+"---"+s.getAge());
        System.out.println("------");

        Student s2 = new Student("赵丽颖",18);
        System.out.println(s2.getName() + "---" + s2.getAge());
    }
}
```

## day07【Scanner类、Random类、ArrayList类】

### 1. API

API(Application Programming Interface)，应用程序编程接口。

* 不需要关心这些类是如何实现的，只需要学习这些类如何使用即可。

* java.lang下的类不需要导包，其他需要。
* JDK API 1.6.0中文版

### 2. Scanner类

可以解析基本类型和字符串的简单文本扫描器。

使用步骤如下：

* 查看类

  `java.util.Scanner `：该类需要import导入后使用。IDE会自动导入。

* 查看构造方法

  `public Scanner(InputStream source)` : 构造一个新的` Scanner` ，它生成的值是从指定的输入流扫描的。

* 查看成员方法

  `public int nextInt() `：将输入信息的下一个标记扫描为一个` int `值。

  `public String next() `：将输入信息的下一个标记扫描为一个字符串。

```java
import java.util.Scanner;

public class Test {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        System.out.println("请输入一个整数：");
        //System.in 系统输入指的是通过键盘录入数据。
        int i = sc.nextInt();
        System.out.println("i:" + i);
    }
}
```

### 3. Random类

此类的实例用于生成伪随机数。

使用步骤如下：

* 查看类

  `java.util.Random `：该类需要import导入后使用。IDE会自动导入。

* 查看构造方法

  `public Random()` : 创建一个新的随机数生成器。

* 查看成员方法

  `public int nextInt(int n) `：返回一个伪随机数，范围在` 0 `（包括）和`指定值 n `（不包括）之间的`int` 值，[0, n)。

练习：

* 使用Random类，完成生成3个10以内的随机整数的操作，代码如下：

```java
import java.util.Random;

public class Test {
    public static void main(String[] args) {
        Random r = new Random();

        for (int i = 0; i < 3; i++) {
            int number = r.nextInt(10);
            System.out.println("number:" + number);
        }
    }
}

```

* 获取1-n之间的随机数，包含n，代码如下：

```java
import java.util.Random;

public class Test {
    public static void main(String[] args) {
        int n = 50;
        Random r = new Random();
        int number = r.nextInt(n) + 1;
        System.out.println("number:" + number);
    }
}
```

* 综合案例：猜数字小游戏
  游戏开始时，会随机生成一个1-100之间的整数number 。玩家猜测一个数字guessNumber ，会与number 作比较，系统提示大了或者小了，直到玩家猜中，游戏结束。

  ```java
  import java.util.Random;
  import java.util.Scanner;
  
  public class Test {
      public static void main(String[] args) {
          /*游戏开始时，会随机生成一个1-100之间的整数number 。
          玩家猜测一个数字guessNumber ，会与number 作比较，系统提示大了或者小了，
          直到玩家猜中，游戏结束。*/
          Random r = new Random();
          int number = r.nextInt(100) + 1;
          while (true){
              Scanner sc = new Scanner(System.in);
              System.out.println("请输入你要猜的数字（1-100）：");
              int guessNumber = sc.nextInt();
              if (guessNumber > number){
                  System.out.println("你猜是数据" + guessNumber + "大了");
              }else if(guessNumber<number){
                  System.out.println("你猜是数据" + guessNumber + "小了");
              }else{
                  System.out.println("恭喜你猜中了");
                  break;
              }
          }
      }
  }
  ```

  

### 4. ArrayList类

#### 4.1 引入——对象数组

```java
public class Test {
    public static void main(String[] args) {
        Person[] array = new Person[3];

        Person one = new Person("迪丽热巴",18);
        Person two = new Person("古力娜扎",28);
        Person three = new Person("马尔扎哈",38);

        array[0] = one;
        array[1] = two;
        array[2] = three;

        System.out.println(array[0]);//将地址值放到数组中
        System.out.println(array[1]);
        System.out.println(array[2]);

        System.out.println(array[1].getName());
    }
}
public class Person {
    private String name;
    private int age;

    public Person() {
    }

    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }
}
```

* 到目前为止，我们想存储对象数据，选择的容器，只有对象数组，而**数组的长度是固定的，无法适应数据变化的需求**。
* 为了解决这个问题，Java提供了另一个容器`java.util.ArrayList `集合类,让我们可以更便捷的存储和操作对象数据。

#### 4.2 ArrayList类

概念：`java.util.ArrayList `是大小**可变的数组**的实现。

此类的实例用于生成伪随机数。ArrayList对象**不能存储基本类型**，**只能存储引用类型数据。**

使用步骤如下：

* 查看类

  `java.util.ArrayList <E> `：该类需要import导入后使用。IDE会自动导入。

  `<E>` ，表示一种指定的数据类型，叫做**泛型**。`E` ，取自Element（元素）的首字母。在出现`E `的地方，我们使用一种引用数据类型将其替换即可，表示我们将存储哪种引用类型的元素。代码如下：

  ```java
  ArrayList<String>, ArrayList<Student>
  ```

  

* 查看构造方法

  `public ArrayList()` : 构造一个内容为空的集合。

  基本格式：

  ```java
  ArrayList<String> list = new ArrayList<String>();
  ```

  在JDK 7后,右侧泛型的尖括号之内可以留空，但是<>仍然要写。简化格式：

  ```java
  ArrayList<String> list = new ArrayList<>();
  ```

  

* 查看成员方法

  `public boolean add(E e) `：将指定的元素添加到此集合的尾部。

  参数` E e` ，在构造ArrayList对象时， `<E> `指定了什么数据类型，那么`add(E e) `方法中，只能添加什么数据类型的对象。

使用ArrayList类，存储三个字符串元素，代码如下：

```java
import java.util.ArrayList;

public class Test {
    public static void main(String[] args) {
        ArrayList<String> list = new ArrayList<>();

        String s1 = "曹操";
        String s2 = "刘备";
        String s3 = "孙权";

        System.out.println(list);

        list.add(s1);
        list.add(s2);
        list.add(s3);

        System.out.println(list);
    }
}
```

* 常用方法和遍历

  * `public boolean add(E e) `：将指定的元素添加到此集合的尾部。

  * `public E remove(int index) `：移除此集合中指定位置上的元素。返回被删除的元素。
  * `public E get(int index) `：返回此集合中指定位置上的元素。返回获取的元素。
  * `public int size() `：返回此集合中的元素数。遍历集合时，可以控制索引范围，防止越界。

```java
import java.util.ArrayList;

public class Test {
    public static void main(String[] args) {
        ArrayList<String> list = new ArrayList<>();

        list.add("hello");
        list.add("world");
        list.add("java");
		
        //public E get(int index):返回指定索引处的元素
        System.out.println("get:" + list.get(0));
        System.out.println("get:" + list.get(1));
        System.out.println("get:" + list.get(2));
		//public int size():返回集合中的元素的个数
        System.out.println("size:" + list.size());
		//public E remove(int index):删除指定索引处的元素，返回被删除的元素
        System.out.println("remove:" + list.remove(0));

        for (int i = 0; i < list.size(); i++) {
            System.out.println(list.get(i));
        }
    }
}
```

* 如何存储基本数据类型？

ArrayList对象**不能存储基本类型**，**只能存储引用类型数据。**类似`<int>`不能写，但是存储基本数据类型对应的**包装类型**是可以的。

| 基本类型 | 基本类型的包装类 |
| -------- | ---------------- |
| byte     | Byte             |
| short    | Short            |
| int      | **Integer**      |
| long     | Long             |
| float    | Float            |
| double   | Double           |
| char     | **Character**    |
| boolean  | Boolean          |

```java
import java.util.ArrayList;

public class Test {
    public static void main(String[] args) {
        ArrayList<Integer> list = new ArrayList<>();
        list.add(1);
        list.add(2);
        list.add(3);
        list.add(4);

        System.out.println(list);
    }
}
[1, 2, 3, 4]
```

#### 4.3 ArrayList练习

* 数值添加到集合

生成6个1~33之间的随机整数，添加到集合，并遍历

```java
import java.util.ArrayList;
import java.util.Random;

public class Test {
    public static void main(String[] args) {
        Random random = new Random();
        ArrayList<Integer> list = new ArrayList<>();
        for (int i = 0; i < 6; i++) {
            int r = random.nextInt(33) + 1;
            list.add(r);
        }
        for (int i = 0; i < list.size(); i++) {
            System.out.println(list.get(i));
        }
    }
}
```

* 对象添加到集合中

自定义4个学生对象，添加到集合，并遍历

```java
import java.util.ArrayList;

public class Test {
    public static void main(String[] args) {
        ArrayList<Student> list = new ArrayList<>();
        Student s1 = new Student("赵丽颖",18);
        Student s2 = new Student("唐嫣",20);
        Student s3 = new Student("景甜",25);
        Student s4 = new Student("柳岩",19);

        list.add(s1);
        list.add(s2);
        list.add(s3);
        list.add(s4);

        for (int i = 0; i < list.size(); i++) {
            Student s = list.get(i);
            System.out.println(s.getName()+"---"+s.getAge());
        }
    }
}
```

* 打印集合方法

定义以指定格式打印集合的方法(ArrayList类型作为参数)，使用{}扩起集合，使用@分隔每个元素。格式参照 {元素@元素@元素}。

```java
import java.util.ArrayList;

public class Test {
    public static void main(String[] args) {
        ArrayList<String> list = new ArrayList<>();
        list.add("张三丰");
        list.add("宋远桥");
        list.add("张无忌");
        list.add("殷梨亭");
        printArrayList(list);
    }
    public static void printArrayList(ArrayList<String> list) {
        System.out.print("{");
        for (int i = 0; i < list.size(); i++) {
            String s = list.get(i);
            if (i != list.size() - 1) {
                System.out.print(s + "@");
            } else {
                System.out.println(s + "}");
            }
        }
    }
}
```

* 获取集合方法

定义获取所有偶数元素集合的方法(ArrayList类型作为返回值)

```java
import java.util.ArrayList;
import java.util.Random;

public class Test {
    public static void main(String[] args) {
        Random random = new Random();
        ArrayList<Integer> list = new ArrayList<>();
        for (int i = 0; i < 20; i++) {
            int r = random.nextInt(1000) + 1;
            list.add(r);
        }
        ArrayList<Integer> arrayList = getArrayList(list);
        System.out.println(arrayList);
    }

    public static ArrayList<Integer> getArrayList(ArrayList<Integer> list) {
        ArrayList<Integer> smallList = new ArrayList<>();
        for (int i = 0; i < list.size(); i++) {
            Integer num = list.get(i);
            if (num % 2 == 0) {
                smallList.add(num);
            }
        }
        return smallList;
    }
}
```

## day08【String类、static、Arrays类、Math类】

### 1. String类

概念：`java.lang.String` 类代表字符串。Java程序中所有的字符串文字（例如`"abc"` ）都可以被看作是实现此类的实例。

* 特点：

  * 字符串的值在创建后不能被更改

  * String对象不可变，所以它们可以被共享。

  ```java
  String s1 = "abc";
  String s2 = "abc";
  // 内存中只有一个"abc"对象被创建，同时被s1和s2共享。
  System.out.println(s1==s2);//true
  ```

  - `"abc"`等效于`char[] data = {'a', 'b', 'c'}`。

    ```java
    String str = "abc";
    相当于：
    char[] data = {'a', 'b', 'c'};
    String str = new String(data);
    // String底层是靠字符数组实现的。
    ```

* 使用步骤：

  * 查看类

    `java.util.String `：该类在lang包中，不需要导入后。

  * 查看构造方法

    * `public String()` : 初始化新创建的 String对象，以使其表示空字符序列。

    * `public String(char[] value)`：通过当前参数中的字符数组来构造新的String。

    * `public String(byte[] bytes)`：通过使用平台的默认字符集解码当前参数中的字节数组来构造新的String。

  实例：

  ```java
  public class Test {
      public static void main(String[] args) {
          // 使用空参构造
          String str1 = new String();
          System.out.println("第1个字符串：" + str1);
  
          // 根据字符数组创建字符串
          char[] charArray = {'A', 'B', 'C'};
          String str2 = new String(charArray);
          System.out.println("第2个字符串：" + str2);
  
          // 根据字节数组创建字符串
          byte[] byteArray = {97, 98, 99};
          String str3 = new String(byteArray);
          System.out.println("第3个字符串：" + str3);
      }
  }
  
  ```

* 常用方法

  * 判断功能的方法

    `public boolean equals (Object anObject)`：将此字符串与指定对象进行比较。

    `public boolean equalsIgnoreCase (String anotherString)`：将此字符串与指定对象进行比较，忽略大小写。

    ```java
    /*
    ==是进行对象的地址值比较，如果确实需要字符串的内容比较，可以使用两个方法：
    
    public boolean equals(Object obj)：参数可以是任何对象，只有参数是一个字符串并且内容相同的才会给true；否则返回false。
    注意事项：
    1. 任何对象都能用Object进行接收。
    2. equals方法具有对称性，也就是a.equals(b)和b.equals(a)效果一样。
    3. 如果比较双方一个常量一个变量，推荐把常量字符串写在前面。
    推荐："abc".equals(str)    不推荐：str.equals("abc")
    
    public boolean equalsIgnoreCase(String str)：忽略大小写，进行内容比较。
     */
    public class Demo01StringEquals {
    
        public static void main(String[] args) {
            String str1 = "Hello";
            String str2 = "Hello";
            char[] charArray = {'H', 'e', 'l', 'l', 'o'};
            String str3 = new String(charArray);
    
            System.out.println(str1.equals(str2)); // true
            System.out.println(str2.equals(str3)); // true
            System.out.println(str3.equals("Hello")); // true
            System.out.println("Hello".equals(str1)); // true
    
            String str4 = "hello";
            System.out.println(str1.equals(str4)); // false
            System.out.println("=================");
    
            String str5 = null;
            System.out.println("abc".equals(str5)); // 推荐：false
    //        System.out.println(str5.equals("abc")); // 不推荐：报错，空指针异常NullPointerException
            System.out.println("=================");
    
            String strA = "Java";
            String strB = "java";
            System.out.println(strA.equals(strB)); // false，严格区分大小写
            System.out.println(strA.equalsIgnoreCase(strB)); // true，忽略大小写
    
            // 注意，只有英文字母区分大小写，其他都不区分大小写
            System.out.println("abc一123".equalsIgnoreCase("abc壹123")); // false
        }
    }
    ```

    

  * 获取功能的方法

    `public int length () `：返回此字符串的长度。
    `public String concat (String str) `：将指定的字符串连接到该字符串的末尾。
    `public char charAt (int index) `：返回指定索引处的 char值。
    `public int indexOf (String str) `：返回指定子字符串第一次出现在该字符串内的索引。
    `public String substring (int beginIndex) `：返回一个子字符串，从beginIndex开始截取字符串到字符串结尾。
    `public String substring (int beginIndex, int endIndex)` ：返回一个子字符串，beginIndex到endIndex截取字符串。含beginIndex，不含endIndex。

    ```java
    /*
    String当中与获取相关的常用方法有：
    
    public int length()：获取字符串当中含有的字符个数，拿到字符串长度。
    public String concat(String str)：将当前字符串和参数字符串拼接成为返回值新的字符串。
    public char charAt(int index)：获取指定索引位置的单个字符。（索引从0开始。）
    public int indexOf(String str)：查找参数字符串在本字符串当中首次出现的索引位置，如果没有返回-1值。
     */
    public class Demo02StringGet {
    
        public static void main(String[] args) {
            // 获取字符串的长度
            int length = "asdasfeutrvauevbueyvb".length();
            System.out.println("字符串的长度是：" + length);
    
            // 拼接字符串
            String str1 = "Hello";
            String str2 = "World";
            String str3 = str1.concat(str2);
            System.out.println(str1); // Hello，原封不动
            System.out.println(str2); // World，原封不动
            System.out.println(str3); // HelloWorld，新的字符串
            System.out.println("==============");
    
            // 获取指定索引位置的单个字符
            char ch = "Hello".charAt(1);
            System.out.println("在1号索引位置的字符是：" + ch);
            System.out.println("==============");
    
            // 查找参数字符串在本来字符串当中出现的第一次索引位置
            // 如果根本没有，返回-1值
            String original = "HelloWorldHelloWorld";
            int index = original.indexOf("llo");
            System.out.println("第一次索引值是：" + index); // 2
    
            System.out.println("HelloWorld".indexOf("abc")); // -1
        }
    }
    ```

    ```java
    /*
    字符串的截取方法：
    
    public String substring(int index)：截取从参数位置一直到字符串末尾，返回新字符串。
    public String substring(int begin, int end)：截取从begin开始，一直到end结束，中间的字符串。
    备注：[begin,end)，包含左边，不包含右边。
     */
    public class Demo03Substring {
        public static void main(String[] args) {
            String str1 = "HelloWorld";
            String str2 = str1.substring(5);
            System.out.println(str1); // HelloWorld，原封不动
            System.out.println(str2); // World，新字符串
            System.out.println("================");
    
            String str3 = str1.substring(4, 7);
            System.out.println(str3); // oWo
            System.out.println("================");
    
            // 下面这种写法，字符串的内容仍然是没有改变的
            // 下面有两个字符串："Hello"，"Java"
            // strA当中保存的是地址值。
            // 本来地址值是Hello的0x666，
            // 后来地址值变成了Java的0x999
            String strA = "Hello";
            System.out.println(strA); // Hello
            strA = "Java";
            System.out.println(strA); // Java
        }
    }
    ```

  

  * 转换功能的方法

    ```java
    /*
    String当中与转换相关的常用方法有：
    
    public char[] toCharArray()：将当前字符串拆分成为字符数组作为返回值。
    public byte[] getBytes()：获得当前字符串底层的字节数组。
    public String replace(CharSequence oldString, CharSequence newString)：
    将所有出现的老字符串替换成为新的字符串，返回替换之后的结果新字符串。
    备注：CharSequence意思就是说可以接受字符串类型。
     */
    public class Demo04StringConvert {
    
        public static void main(String[] args) {
            // 转换成为字符数组
            char[] chars = "Hello".toCharArray();
            System.out.println(chars[0]); // H
            System.out.println(chars.length); // 5
            System.out.println("==============");
    
            // 转换成为字节数组
            byte[] bytes = "abc".getBytes();
            for (int i = 0; i < bytes.length; i++) {
                System.out.println(bytes[i]);
            }
            System.out.println("==============");
    
            // 字符串的内容替换
            String str1 = "How do you do?";
            String str2 = str1.replace("o", "*");
            System.out.println(str1); // How do you do?
            System.out.println(str2); // H*w d* y*u d*?
            System.out.println("==============");
    
            String lang1 = "会不会玩儿呀！你大爷的！你大爷的！你大爷的！！！";
            String lang2 = lang1.replace("你大爷的", "****");
            System.out.println(lang2); // 会不会玩儿呀！****！****！****！！！
        }
    	
    }
    ```

  * 分割截取功能

    ```java
    /*
    分割字符串的方法：
    public String[] split(String regex)：按照参数的规则，将字符串切分成为若干部分。
    
    注意事项：
    split方法的参数其实是一个“正则表达式”，今后学习。
    今天要注意：如果按照英文句点“.”进行切分，必须写"\\."（两个反斜杠）
     */
    public class Demo05StringSplit {
    
        public static void main(String[] args) {
            String str1 = "aaa,bbb,ccc";
            String[] array1 = str1.split(",");
            for (int i = 0; i < array1.length; i++) {
                System.out.println(array1[i]);
            }
            System.out.println("===============");
    
            String str2 = "aaa bbb ccc";
            String[] array2 = str2.split(" ");
            for (int i = 0; i < array2.length; i++) {
                System.out.println(array2[i]);
            }
            System.out.println("===============");
    
            String str3 = "XXX.YYY.ZZZ";
            String[] array3 = str3.split("\\.");
            System.out.println(array3.length); // 0
            for (int i = 0; i < array3.length; i++) {
                System.out.println(array3[i]);
            }
        }
    
    }
    ```

* String类的练习

  * 拼接字符串

    ```java
    /*
    题目：
    定义一个方法，把数组{1,2,3}按照指定格式拼接成一个字符串。格式参照如下：[word1#word2#word3]。
    
    分析：
    1. 首先准备一个int[]数组，内容是：1、2、3
    2. 定义一个方法，用来将数组变成字符串
    三要素
    返回值类型：String
    方法名称：fromArrayToString
    参数列表：int[]
    3. 格式：[word1#word2#word3]
    用到：for循环、字符串拼接、每个数组元素之前都有一个word字样、分隔使用的是#、区分一下是不是最后一个
    4. 调用方法，得到返回值，并打印结果字符串
     */
    public class Demo06StringPractise {
    
        public static void main(String[] args) {
            int[] array = {1, 2, 3, 4};
    
            String result = fromArrayToString(array);
            System.out.println(result);
        }
    
        public static String fromArrayToString(int[] array) {
            String str = "[";
            for (int i = 0; i < array.length; i++) {
                if (i == array.length - 1) {
                    str += "word" + array[i] + "]";
                } else {
                    str += "word" + array[i] + "#";
                }
            }
            return str;
        }
    
    }
    ```

  * 统计字符个数

    ```java
    import java.util.Scanner;
    
    /*
    题目：
    键盘输入一个字符串，并且统计其中各种字符出现的次数。
    种类有：大写字母、小写字母、数字、其他
    
    思路：
    1. 既然用到键盘输入，肯定是Scanner
    2. 键盘输入的是字符串，那么：String str = sc.next();
    3. 定义四个变量，分别代表四种字符各自的出现次数。
    4. 需要对字符串一个字、一个字检查，String-->char[]，方法就是toCharArray()
    5. 遍历char[]字符数组，对当前字符的种类进行判断，并且用四个变量进行++动作。
    6. 打印输出四个变量，分别代表四种字符出现次数。
     */
    public class Demo07StringCount {
    
        public static void main(String[] args) {
            Scanner sc = new Scanner(System.in);
            System.out.println("请输入一个字符串：");
            String input = sc.next(); // 获取键盘输入的一个字符串
    
            int countUpper = 0; // 大写字母
            int countLower = 0; // 小写字母
            int countNumber = 0; // 数字
            int countOther = 0; // 其他字符
    
            char[] charArray = input.toCharArray();
            for (int i = 0; i < charArray.length; i++) {
                char ch = charArray[i]; // 当前单个字符
                if ('A' <= ch && ch <= 'Z') {
                    countUpper++;
                } else if ('a' <= ch && ch <= 'z') {
                    countLower++;
                } else if ('0' <= ch && ch <= '9') {
                    countNumber++;
                } else {
                    countOther++;
                }
            }
    
            System.out.println("大写字母有：" + countUpper);
            System.out.println("小写字母有：" + countLower);
            System.out.println("数字有：" + countNumber);
            System.out.println("其他字符有：" + countOther);
        }
    
    }
    ```

    



### 2. static关键字

如果一个成员变量使用了static关键字，那么这个变量不再属于对象自己，而是属于所在的类。多个对象共享同一份数据。

![image-20210224150816153](Java%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0.assets/静态static关键字概述.png)

* static用于成员变量，即类属性

```java
public class Demo01StaticField {

    public static void main(String[] args) {

        Student two = new Student("黄蓉", 16);
        two.room = "101教室";
        System.out.println("姓名：" + two.getName()
                + "，年龄：" + two.getAge() + "，教室：" + two.room
                + "，学号：" + two.getId());

        Student one = new Student("郭靖", 19);
        System.out.println("姓名：" + one.getName()
                + "，年龄：" + one.getAge() + "，教室：" + one.room
                + "，学号：" + one.getId());
    }
//1. 只给对象two给定了教室，one也就随之而有同一个教室了
//2. 自动生成学号    
}



public class Student {

    private int id; // 学号
    private String name; // 姓名
    private int age; // 年龄
    static String room; // 所在教室
    private static int idCounter = 0; // 学号计数器，每当new了一个新对象的时候，计数器++

    public Student() {
        this.id = ++idCounter;
    }

    public Student(String name, int age) {
        this.name = name;
        this.age = age;
        this.id = ++idCounter;
    }

    public int getId() {
        return id;
    }

    public void setId(int id) {
        this.id = id;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }
}
```

* static用于成员方法->静态方法

```java
/*
一旦使用static修饰成员方法，那么这就成为了静态方法。静态方法不属于对象，而是属于类的。

如果没有static关键字，那么必须首先创建对象，然后通过对象才能使用它。
如果有了static关键字，那么不需要创建对象，直接就能通过类名称来使用它。

无论是成员变量，还是成员方法。如果有了static，都推荐使用类名称进行调用。
静态变量：类名称.静态变量
静态方法：类名称.静态方法()

注意事项：
1. 静态不能直接访问非静态。//我的笔记：静态方法不能直接访问非静态变量
原因：因为在内存当中是【先】有的静态内容，【后】有的非静态内容。
“先人不知道后人，但是后人知道先人。”
2. 静态方法当中不能用this。
原因：this代表当前对象，通过谁调用的方法，谁就是当前对象。
 */
public class Demo02StaticMethod {

    public static void main(String[] args) {
        MyClass obj = new MyClass(); // 首先创建对象
        // 然后才能使用没有static关键字的内容
        obj.method();

        // 对于静态方法来说，可以通过对象名进行调用，也可以直接通过类名称来调用。
        obj.methodStatic(); // 正确，不推荐，这种写法在编译之后也会被javac翻译成为“类名称.静态方法名”
        MyClass.methodStatic(); // 正确，推荐

        // 对于本来当中的静态方法，可以省略类名称
        myMethod();
        Demo02StaticMethod.myMethod(); // 完全等效
    }

    public static void myMethod() {
        System.out.println("自己的方法！");
    }

}


public class MyClass {

    int num; // 成员变量
    static int numStatic; // 静态变量

    // 成员方法
    public void method() {
        System.out.println("这是一个成员方法。");
        // 成员方法可以访问成员变量
        System.out.println(num);
        // 成员方法可以访问静态变量
        System.out.println(numStatic);
    }

    // 静态方法
    public static void methodStatic() {
        System.out.println("这是一个静态方法。");
        // 静态方法可以访问静态变量
        System.out.println(numStatic);
        // 静态不能直接访问非静态【重点】
//        System.out.println(num); // 错误写法！

        // 静态方法中不能使用this关键字。
//        System.out.println(this); // 错误写法！
    }

}
```

* 静态的内存图

![image-20210224153142976](Java%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0.assets/静态的内存图.png)

* 静态代码块

  jdbc时有用！

  ```java
  /*
  静态代码块的格式是：
  
  public class 类名称 {
      static {
          // 静态代码块的内容
      }
  }
  
  特点：当第一次用到本类时，静态代码块执行唯一的一次。
  静态内容总是优先于非静态，所以静态代码块比构造方法先执行。
  
  静态代码块的典型用途：
  用来一次性地对静态成员变量进行赋值。
   */
  public class Demo04Static {
  
      public static void main(String[] args) {
          Person one = new Person();
          Person two = new Person();
      }
  
  }
  运行结果：
  静态代码块执行！
  构造方法执行！
  构造方法执行！    
  
  public class Person {
  
      static {
          System.out.println("静态代码块执行！");
      }
  
      public Person() {
          System.out.println("构造方法执行！");
      }
  
  }
  ```

### 3. Arrays类

概念：操作数组的各种方法。其所有方法都是静态方法，调用起来非常简单

```java
/*
java.util.Arrays是一个与数组相关的工具类，里面提供了大量静态方法，用来实现数组常见的操作。

public static String toString(数组)：将参数数组变成字符串（按照默认格式：[元素1, 元素2, 元素3...]）
public static void sort(数组)：按照默认升序（从小到大）对数组的元素进行排序。

备注：
1. 如果是数值，sort默认按照升序从小到大
2. 如果是字符串，sort默认按照字母升序
3. 如果是自定义的类型，那么这个自定义的类需要有Comparable或者Comparator接口的支持。（今后学习）
 */
public class Demo01Arrays {

    public static void main(String[] args) {
        int[] intArray = {10, 20, 30};
        // 将int[]数组按照默认格式变成字符串
        String intStr = Arrays.toString(intArray);
        System.out.println(intStr); // [10, 20, 30]

        int[] array1 = {2, 1, 3, 10, 6};
        Arrays.sort(array1);
        System.out.println(Arrays.toString(array1)); // [1, 2, 3, 6, 10]

        String[] array2 = {"bbb", "aaa", "ccc"};
        Arrays.sort(array2);
        System.out.println(Arrays.toString(array2)); // [aaa, bbb, ccc]
    }

}
```

练习：

```java
import java.util.Arrays;
/*
题目：
请使用Arrays相关的API，将一个随机字符串中的所有字符升序排列，并倒序打印。
 */
public class Test {
    public static void main(String[] args) {
        String str = "asv76agfqwdfvasdfvjh";
		
        // 如何进行升序排列：sort
        // 必须是一个数组，才能用Arrays.sort方法
        // String --> 数组，用toCharArray
        char[] chars = str.toCharArray();
        Arrays.sort(chars);// 对字符数组进行升序排列
        System.out.print(chars);

        System.out.println();

        for (int i = chars.length - 1; i >= 0; i--) {
            System.out.print(chars[i]);
        }

    }
}
运行结果：
67aaaddfffghjqssvvvw
wvvvssqjhgfffddaaa76    
```

### 4. Math类

概念：`java.lang.Math `类包含用于执行基本数学运算的方法，如初等指数、对数、平方根和三角函数。类似这样的工具类，其**所有方法均为静态方法**，并且**不会创建对象，调用起来非常简单**。

```java
/*
java.util.Math类是数学相关的工具类，里面提供了大量的静态方法，完成与数学运算相关的操作。

public static double abs(double num)：获取绝对值。有多种重载。
public static double ceil(double num)：向上取整。
public static double floor(double num)：向下取整。
public static long round(double num)：四舍五入。

Math.PI代表近似的圆周率常量（double）。
 */
public class Demo03Math {

    public static void main(String[] args) {
        // 获取绝对值
        System.out.println(Math.abs(3.14)); // 3.14
        System.out.println(Math.abs(0)); // 0
        System.out.println(Math.abs(-2.5)); // 2.5
        System.out.println("================");

        // 向上取整
        System.out.println(Math.ceil(3.9)); // 4.0
        System.out.println(Math.ceil(3.1)); // 4.0
        System.out.println(Math.ceil(3.0)); // 3.0
        System.out.println("================");

        // 向下取整，抹零
        System.out.println(Math.floor(30.1)); // 30.0
        System.out.println(Math.floor(30.9)); // 30.0
        System.out.println(Math.floor(31.0)); // 31.0
        System.out.println("================");

        System.out.println(Math.round(20.4)); // 20
        System.out.println(Math.round(10.5)); // 11
    }

}


```

练习：

```java
/*
题目：
计算在-10.8到5.9之间，绝对值大于6或者小于2.1的整数有多少个？

分析：
1. 既然已经确定了范围，for循环
2. 起点位置-10.8应该转换成为-10，两种办法：
    2.1 可以使用Math.ceil方法，向上（向正方向）取整
    2.2 强转成为int，自动舍弃所有小数位
3. 每一个数字都是整数，所以步进表达式应该是num++，这样每次都是+1的。
4. 如何拿到绝对值：Math.abs方法。
5. 一旦发现了一个数字，需要让计数器++进行统计。

备注：如果使用Math.ceil方法，-10.8可以变成-10.0。注意double也是可以进行++的。
 */
public class Demo04MathPractise {

    public static void main(String[] args) {
        int count = 0; // 符合要求的数量

        double min = -10.8;
        double max = 5.9;
        // 这样处理，变量i就是区间之内所有的整数
        for (int i = (int) min; i <= max; i++) {
            int abs = Math.abs(i); // 绝对值
            if (abs > 6 || abs < 2.1) {
                System.out.println(i);
                count++;
            }
        }

        System.out.println("总共有：" + count); // 9
    }

}
```





## day09【继承、super、this、抽象类】

### 1. 继承的概念

* 多个类中存在相同属性和行为时，将这些内容抽取到单独一个类中，那么多个类无需再定义这些属性和行为，只要继承那一个类即可。如图所示：

![image-20210224163351346](Java%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0.assets/继承的实例.png)

* 子类——父类，继承描述的是is-a的关系
* 子类继承父类的**属性**和**行为**，使得子类对象具有与父类相同的属性、相同的行为。子类可以直接访问父类中的**非私有的属性和行为**。
* 提高代码的复用性
* 类与类之间产生了关系，是多态的前提。

### 2. 继承的格式

```java
class 父类{
    ...
}
class 子类 extends 父类{
    ...
}
```

继承演示，代码如下：

```java
public class Employee {

    public void method() {
        System.out.println("方法执行！");
    }

}

public class Teacher extends Employee {

}

public class Demo01Extends {

    public static void main(String[] args) {
        // 创建了一个子类对象
        Teacher teacher = new Teacher();
        // Teacher类当中虽然什么都没写，但是会继承来自父类的method方法。
        teacher.method();

        // 创建另一个子类助教的对象
        Assistant assistant = new Assistant();
        assistant.method();
    }

}
```

### 3. 继承后父子类成员变量重名

* 在父子类的继承关系当中，如果成员变量重名，则创建子类对象时的访问方式

```java
public class Fu {
    int numFu = 10;
    int num = 100;
    public void methodFu() {
        // 使用的是本类当中的，不会向下找子类的
        System.out.println(num);
    }
}

public class Zi extends Fu {
    int numZi = 20;
    int num = 200;
    public void methodZi() {
        // 因为本类当中有num，所以这里用的是本类的num
        System.out.println(num);
    }
}

/*
在父子类的继承关系当中，如果成员变量重名，则创建子类对象时，访问有两种方式：

直接通过子类对象访问成员变量：
    等号左边是谁，就优先用谁，没有则向上找。
间接通过成员方法访问成员变量：
    该方法属于谁，就优先用谁，没有则向上找。
 */
public class Demo01ExtendsField {

    public static void main(String[] args) {
        Fu fu = new Fu(); // 创建父类对象
        System.out.println(fu.numFu); // 只能使用父类的东西，没有任何子类内容
        System.out.println("===========");
        Zi zi = new Zi();
        System.out.println(zi.numFu); // 10
        System.out.println(zi.numZi); // 20
        System.out.println("===========");
        // Zi zi = new Zi(),等号左边是谁，就优先用谁
        System.out.println(zi.num); // 优先子类，200
//        System.out.println(zi.abc); // 到处都没有，编译报错！
        System.out.println("===========");
        // 这个方法是子类的，优先用子类的，没有再向上找
        zi.methodZi(); // 200
        // 这个方法是在父类当中定义的，
        zi.methodFu(); // 100
    }
}
```

* 某类中**同时使用重名的**局部变量、该类成员变量、父类成员变量

```java
public class Fu {
    int num = 10;
}

public class Zi extends Fu {
    int num = 20;
    public void method() {
        int num = 30;
        System.out.println(num); // 30，局部变量
        System.out.println(this.num); // 20，本类的成员变量
        System.out.println(super.num); // 10，父类的成员变量
    }
}

/*
局部变量：         直接写成员变量名
本类的成员变量：    this.成员变量名
父类的成员变量：    super.成员变量名
 */
public class Demo01ExtendsField {
    public static void main(String[] args) {
        Zi zi = new Zi();
        zi.method();
    }
}

```

### 4. 继承后父子类成员方法重名

```java
public class Fu {
    public void methodFu() {
        System.out.println("父类方法执行！");
    }
    public void method() {
        System.out.println("父类重名方法执行！");
    }
}

public class Zi extends Fu {
    public void methodZi() {
        System.out.println("子类方法执行！");
    }
    public void method() {
        System.out.println("子类重名方法执行！");
    }
}

/*
在父子类的继承关系当中，创建子类对象，访问成员方法的规则：
    创建的对象是谁，就优先用谁，如果没有则向上找。

注意事项：
无论是成员方法还是成员变量，如果没有都是向上找父类，绝对不会向下找子类的。
*/
public class Demo01ExtendsMethod {
    public static void main(String[] args) {
        Zi zi = new Zi();
        zi.methodFu();
        zi.methodZi();
        // 创建的是new了子类对象，所以优先用子类方法
        zi.method();
    }
}
```

* 成员方法覆盖重写（Override）
  概念：在继承关系当中，方法的名称一样，参数列表也一样。

  覆盖重写（Override）：**方法的名称一样，参数列表【也一样】**。覆盖、覆写。
  重载（Overload）：方法的名称一样，参数列表【不一样】。

  方法的覆盖重写特点：**创建的是子类对象，则优先用子类方法**。

  ```java
  public class Fu {
      public String method() {
          return null;
      }
  }
  
  public class Zi extends Fu {
      @Override//！！！！！！！覆盖重写标记
      public String method() {
          return null;
      }
  }
  
  /*
  方法覆盖重写的注意事项：
  
  1. 必须保证父子类之间方法的名称相同，参数列表也相同。
  @Override：写在方法前面，用来检测是不是有效的正确覆盖重写。
  这个注解就算不写，只要满足要求，也是正确的方法覆盖重写。
  
  //以下两条了解即可
  2. 子类方法的返回值必须【小于等于】父类方法的返回值范围。
  小扩展提示：java.lang.Object类是所有类的公共最高父类（祖宗类），java.lang.String就是Object的子类。
  
  3. 子类方法的权限必须【大于等于】父类方法的权限修饰符。
  小扩展提示：public > protected > (default) > private
  备注：(default)不是关键字default，而是什么都不写，留空。
   */
  public class Demo01Override {
  
  }
  ```

  **方法覆盖重写的应用场景**

  ![image-20210224182829657](Java%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0.assets/方法覆盖重写的应用场景.png)

  ```java
  // 本来的老款手机
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
  
  // 定义一个新手机，使用老手机作为父类
  public class NewPhone extends Phone {
  
      @Override
      public void show() {
          super.show(); // 把父类的show方法拿过来重复利用
          // 自己子类再来添加更多内容
          System.out.println("显示姓名");
          System.out.println("显示头像");
      }
  }
  
  public class Demo01Phone {
  
      public static void main(String[] args) {
          Phone phone = new Phone();
          phone.call();
          phone.send();
          phone.show();
          System.out.println("==========");
  
          NewPhone newPhone = new NewPhone();
          newPhone.call();
          newPhone.send();
          newPhone.show();
      }
  
  }
  ```

  

### 5. 继承中构造方法的访问特点

```java
public class Fu {

    public Fu() {
        System.out.println("父类无参构造");
    }

    public Fu(int num) {
        System.out.println("父类有参构造！");
    }

}

public class Zi extends Fu {

    public Zi() {
        super(); // 在调用父类无参构造方法
//        super(20); // 在调用父类重载的构造方法
        System.out.println("子类构造方法！");
    }

    public void method() {
//        super(); // 错误写法！只有子类构造方法，才能调用父类构造方法。
    }

}

/*
继承关系中，父子类构造方法的访问特点：

1. 子类构造方法当中有一个默认隐含的“super()”调用，所以一定是先调用的父类构造，后执行的子类构造。
2. 子类构造可以通过super关键字来调用父类重载构造。
3. super的父类构造调用，必须是子类构造方法的第一个语句。不能一个子类构造调用多次super构造。
总结：
子类必须调用父类构造方法，不写则赠送super()；写了则用写的指定的super调用，super只能有一个，还必须是第一个。
 */
public class Demo01Constructor {

    public static void main(String[] args) {
        Zi zi = new Zi();
    }

}
```



### 6. super关键字的三种用法

用于访问父类内容

```java
/*
1. 在子类的成员方法中，访问父类的成员变量。
2. 在子类的成员方法中，访问父类的成员方法。
3. 在子类的构造方法中，访问父类的构造方法。
*/
public class Zi extends Fu {

    int num = 20;

    public Zi() {
        super();
    }

    public void methodZi() {
        System.out.println(super.num); // 父类中的num
    }

    public void method() {
        super.method(); // 访问父类中的method
        System.out.println("子类方法");
    }

}


public class Fu {

    int num = 10;

    public void method() {
        System.out.println("父类方法");
    }

}

```

### 7. this关键字的三种用法

```java
/*
super关键字用来访问父类内容，而this关键字用来访问本类内容。用法也有三种：

1. 在本类的成员方法中，访问本类的成员变量。
2. 在本类的成员方法中，访问本类的另一个成员方法。
3. 在本类的构造方法中，访问本类的另一个构造方法。
在第三种用法当中要注意：
A. this(...)调用也必须是构造方法的第一个语句，唯一一个。
B. super和this两种构造调用，不能同时使用。
 */

public class Zi extends Fu {

    int num = 20;

    public Zi() {
//        super(); // 这一行不再赠送
        this(123); // 本类的无参构造，调用本类的有参构造
//        this(1, 2); // 错误写法！
    }

    public Zi(int n) {
        this(1, 2);
    }

    public Zi(int n, int m) {
    }

    public void showNum() {
        int num = 10;
        System.out.println(num); // 局部变量
        System.out.println(this.num); // 本类中的成员变量
        System.out.println(super.num); // 父类中的成员变量
    }

    public void methodA() {
        System.out.println("AAA");
    }

    public void methodB() {
        this.methodA();//2. 在本类的成员方法中，访问本类的另一个成员方法。
        System.out.println("BBB");
    }

}

public class Fu {

    int num = 30;

}
```

### 8. super与this的内存图

![image-20210224200929307](Java%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0.assets/super与this的内存图.png)

### 9. Java继承的三个特点

* Java只支持单继承，不支持多继承。后面讲到的接口支持多继承

  ```java
  //一个类只能有一个父类，不可以有多个父类。
  class C extends A{} //ok
  class C extends A，B... //error
  ```

* Java支持多级继承(继承体系)。顶层父类是Object类。所有的类默认继承Object，作为父类。

  ```java
  //C->B->A是祖先
  class A{}
  class B extends A{}
  class C extends B{}
  ```

  

* 子类和父类是一种相对的概念。

### 10. 抽象类

* 概念：
  * 父类中的方法，被它的子类们重写，子类各自的实现都不尽相同。那么**父类的方法声明和方法主体，只有声明还有意义，而方法主体则没有存在的意义了**。我们把**没有方法主体的方法称为抽象方法**。
  * Java语法规定，**包含抽象方法的类就是抽象类**。
  * 使用`abstract`关键字

* 抽象方法

  注意：**抽象方法没有方法体**

  定义格式：

  ```java
  修饰符 abstract 返回值 方法名 (参数列表);
  //举例
  public abstract void run();
  ```

  

* 抽象类

  ```java
  public abstract class Animal {
  	public abstract void run()；
  }
  ```

  

* 抽象的使用

  ```java
  /*
  抽象方法：就是加上abstract关键字，然后去掉大括号，直接分号结束。
  抽象类：抽象方法所在的类，必须是抽象类才行。在class之前写上abstract即可。
  
  如何使用抽象类和抽象方法：
  1. 不能直接创建new抽象类对象。
  2. 必须用一个子类来继承抽象父类。
  3. 子类必须覆盖重写抽象父类当中所有的抽象方法。
  覆盖重写（实现）：子类去掉抽象方法的abstract关键字，然后补上方法体大括号。
  4. 创建子类对象进行使用。
   */
  public abstract class Animal {
  
      // 这是一个抽象方法，代表吃东西，但是具体吃什么（大括号的内容）不确定。
      public abstract void eat();
  
      // 这是普通的成员方法
  //    public void normalMethod() {
  //
  //    }
  
  }
  
  public class Cat extends Animal {
  
      @Override
      public void eat() {
          System.out.println("猫吃鱼");
      }
  
  }
  
  public class DemoMain {
  
      public static void main(String[] args) {
  //        Animal animal = new Animal(); // 错误写法！不能直接创建抽象类对象
  
          Cat cat = new Cat();
          cat.eat();
      }
  
  }
  
  ```

* 注意事项

  关于抽象类的使用，以下为语法上要注意的细节，虽然条目较多，但若理解了抽象的本质，无需死记硬背。
  * **抽象类不能创建对象**，如果创建，编译无法通过而报错。只能创建其非抽象子类的对象。
    **理解**：假设创建了抽象类的对象，调用抽象的方法，而抽象方法没有具体的方法体，没有意义。

  * 抽象类中，可以有构造方法，是供子类创建对象时，初始化父类成员使用的。
    **理解**：子类的构造方法中，有默认的super()，需要访问父类构造方法。

  * 抽象类中，**不一定包含抽象方法**，但是有抽象方法的类必定是抽象类。

    **理解**：未包含抽象方法的抽象类，目的就是不想让调用者创建该类对象，通常用于某些特殊的类结构设
    计。

  * 抽象类的子类，必须**重写抽象父类中所有的抽象方法**，否则，编译无法通过而报错。**除非该子类也是抽象类**。
    **理解**：假设不重写所有抽象方法，则类中可能包含抽象方法。那么创建对象后，调用抽象的方法，没有
    意义。

  实例：

  DemoMain主类

  Animal抽象类->Dog抽象类->DogGolden与Dog2Ha两个非抽象类

  ```java
  //运行的主类
  public class DemoMain {
      public static void main(String[] args) {
  //        Animal animal = new Animal(); // 错误！
  //        Dog dog = new Dog(); // 错误，这也是抽象类
          Dog2Ha ha = new Dog2Ha(); // 这是普通类，可以直接new对象。
          ha.eat();
          ha.sleep();
          System.out.println("==========");
  
          DogGolden golden = new DogGolden();
          golden.eat();
          golden.sleep();
      }
  }
  
  
  // 最高的抽象父类
  public abstract class Animal {
      public abstract void eat();
      public abstract void sleep();
  }
  // Animal的子类也是一个抽象类
  public abstract class Dog extends Animal {
      @Override
      public void eat() {
          System.out.println("狗吃骨头");
      }
      // public abstract void sleep();
  }
  //金毛狗是Dog抽象类的一个子类，是非抽象类
  public class DogGolden extends Dog {
      @Override
      public void sleep() {
          System.out.println("呼呼呼……");
      }
  }
  //二哈狗是Dog抽象类的一个子类，是非抽象类
  public class Dog2Ha extends Dog {
      @Override
      public void sleep() {
          System.out.println("嘿嘿嘿……");
      }
  }
  ```

  

## day10【接口、多态】

### 1.接口

#### 1.1 接口概念

* Java语言中的一种引用类型，是方法的集合。
* 类的内部封装了成员变量、构造方法和成员方法；**接口的内部主要就是封装了方法**。封装的方法包括：**抽象方法**（JDK 7及以前）、**默认方法**和**静态方法**（JDK 8），**私有方法**（JDK 9）。
* 使用`interface`关键字
* 也会被编译成.class文件
* 接口的使用，它**不能创建对象**，但是可以被**实现（` implements `，**类似于被继承）。一个**实现接口的类**（可以**看做是接口的子类**），需要**实现接口中所有的抽象方法**，创建该类对象，就可以调用方法了，否则它必须是一个抽象类。

#### 1.2 接口的定义

```java
public interface 接口名称 {
    // 抽象方法
    // 默认方法
    // 静态方法
    // 私有方法
}
```

#### 1.3 接口中的方法

* 含有抽象方法

  * 接口当中的抽象方法，修饰符必须是两个固定的关键字：public abstract
  * 这两个关键字修饰符，可以选择性地省略。（今天刚学，所以不推荐。）
  * 方法的三要素，可以随意定义。

  ```java
  public interface MyInterfaceAbstract {
  
      // 这是一个抽象方法
      public abstract void methodAbs1();
  
      // 这也是抽象方法
      abstract void methodAbs2();
  
      // 这也是抽象方法
      public void methodAbs3();
  
      // 这也是抽象方法
      void methodAbs4();
  
  }
  ```

* 含有默认方法和静态方法

  * 某个接口MyInterface应用到项目中，被项目中的两个类MyInterfaceA、MyInterfaceB实现，如果有天增加了接口MyInterface的**抽象方法**，那两个实现类将会报错，因此必须想办法，既能增加接口的**抽象方法**又不会让实现类报错。——>引入**默认方法**

  ```java
  /*
  1. 接口的默认方法，可以通过 接口实现类 对象，直接调用。
  2. 接口的默认方法，也可以被接口实现类进行覆盖重写。
   */
  //运行main
  public class Demo02Interface {
      public static void main(String[] args) {
          // 创建了实现类对象
          MyInterfaceDefaultA a = new MyInterfaceDefaultA();
          a.methodAbs(); // 调用抽象方法，实际运行的是右侧实现类。
          // 调用默认方法，如果实现类当中没有，会向上找接口
          a.methodDefault(); // 这是新添加的默认方法
          System.out.println("==========");
          MyInterfaceDefaultB b = new MyInterfaceDefaultB();
          b.methodAbs();
          b.methodDefault(); // 实现类B覆盖重写了接口的默认方法
      }
  }
  
  // 接口实现类A
  public class MyInterfaceDefaultA implements MyInterfaceDefault {
      @Override
      public void methodAbs() {
          System.out.println("实现了抽象方法，AAA");
      }
  }
  // 接口实现类B
  public class MyInterfaceDefaultB implements MyInterfaceDefault {
      @Override
      public void methodAbs() {
          System.out.println("实现了抽象方法，BBB");
      }
      @Override
      public void methodDefault() {
          System.out.println("实现类B覆盖重写了接口的默认方法");
      }
  }
  
  
  // 接口
  public interface MyInterfaceDefault {
      // 抽象方法
      public abstract void methodAbs();
      // 新添加了一个抽象方法
  //    public abstract void methodAbs2();
      // 新添加的方法，改成默认方法
      public default void methodDefault() {
          System.out.println("这是新添加的默认方法");
      }
  }
  
  ```

  * 静态方法

    如前类中静态方法一样，**接口静态方法与对象无关**

  ```java
  /*
  注意事项：不能通过 接口实现类的对象 来调用接口当中的静态方法。
  正确用法：通过接口名称，直接调用其中的静态方法。
  格式：
  接口名称.静态方法名(参数);
   */
  //运行main
  public class Demo03Interface {
      public static void main(String[] args) {
          // 创建了实现类对象
          MyInterfaceStaticImpl impl = new MyInterfaceStaticImpl();
          // 错误写法！
  //        impl.methodStatic();
          // 直接通过接口名称调用静态方法
          MyInterfaceStatic.methodStatic();
      }
  }
  
  //接口实现类
  public class MyInterfaceStaticImpl implements MyInterfaceStatic {
  }
  //接口
  public interface MyInterfaceStatic {
      public static void methodStatic() {
          System.out.println("这是接口的静态方法！");
      }
  }
  ```

  

  

* 含有私有方法和私有静态方法

  【**问题描述**】：
  在接口中，我们需要抽取一个共有方法，用来解决两个默认方法之间重复代码的问题。
  但是这个共有方法不应该让实现类使用，应该是接口私有化的。

  【**解决方案**】：
  从Java 9开始，接口当中允许定义私有方法。

  ​	**普通私有方法**，解决多个默认方法之间重复代码问题。格式：

  ```java
  private 返回值类型 方法名称(参数列表) {
  	方法体
  }
  ```

  ​	**静态私有方法**，解决多个静态方法之间重复代码问题。格式：

  ```java
  private static 返回值类型 方法名称(参数列表) {
  	方法体
  }
  ```

  **实例：**

  * 普通私有方法

    ```java
    //接口的实现类
    public class MyInterfacePrivateAImpl implements MyInterfacePrivateA {
        public void methodAnother() {
            // 如果不将接口的中的methodCommon方法改成private，那么就直接访问到了接口中的默认方法，这样是错误的！
    //        methodCommon();
        }
    }
    
    //接口
    public interface MyInterfacePrivateA {
        public default void methodDefault1() {
            System.out.println("默认方法1");
            methodCommon();
        }
        public default void methodDefault2() {
            System.out.println("默认方法2");
            methodCommon();
        }
        private void methodCommon() {
            System.out.println("AAA");
            System.out.println("BBB");
            System.out.println("CCC");
        }
    }
    ```

    

  * 静态私有方法

    回顾：静态方法不属于对象，而是属于类的

    ```java
    // 接口的实现类
    public class Demo04Interface {
        public static void main(String[] args) {
            MyInterfacePrivateB.methodStatic1();
            MyInterfacePrivateB.methodStatic2();
            // 错误写法！
    //        MyInterfacePrivateB.methodStaticCommon();
        }
    }
    
    // 接口
    public interface MyInterfacePrivateB {
        public static void methodStatic1() {
            System.out.println("静态方法1");
            methodStaticCommon();
        }
        public static void methodStatic2() {
            System.out.println("静态方法2");
            methodStaticCommon();
        }
        private static void methodStaticCommon() {
            System.out.println("AAA");
            System.out.println("BBB");
            System.out.println("CCC");
        }
    }
    ```

    

#### 1.4 接口中的常量定义和使用

```java
/*
接口当中也可以定义“成员变量”，但是必须使用public static final三个关键字进行修饰。
从效果上看，这其实就是接口的【常量】。
格式：
public static final 数据类型 常量名称 = 数据值;
备注：
一旦使用final关键字进行修饰，说明不可改变。

注意事项：
1. 接口当中的常量，可以省略public static final，注意：不写也照样是这样。
2. 接口当中的常量，必须进行赋值；不能不赋值。
3. 接口中常量的名称，使用完全大写的字母，用下划线进行分隔。（推荐命名规则）
 */
// 接口实现类
public class Demo05Interface {
    public static void main(String[] args) {
        // 访问接口当中的常量
        System.out.println(MyInterfaceConst.NUM_OF_MY_CLASS);
    }
}

// 接口
public interface MyInterfaceConst {
    // 这其实就是一个常量，一旦赋值，不可以修改
    public static final int NUM_OF_MY_CLASS = 12;
}
```

#### 1.5 继承父类并实现多个接口

```java
/*
使用接口的时候，需要注意：

1. 接口是没有静态代码块或者构造方法的。
2. 一个类的直接父类是唯一的，但是一个类可以同时实现多个接口。
格式：
public class MyInterfaceImpl implements MyInterfaceA, MyInterfaceB {
    // 覆盖重写所有抽象方法
}
3. 如果实现类所实现的多个接口当中，存在重复的抽象方法，那么只需要覆盖重写一次即可。
4. 如果实现类没有覆盖重写所有接口当中的所有抽象方法，那么实现类就必须是一个抽象类。
5. 如果实现类锁实现的多个接口当中，存在重复的默认方法，那么实现类一定要对冲突的默认方法进行覆盖重写。
6. 一个类如果直接父类当中的方法，和接口当中的默认方法产生了冲突，优先用父类当中的方法。
 */
```

#### 1.6 接口之间的多继承

```java
/*
1. 类与类之间是单继承的。直接父类只有一个。
2. 类与接口之间是多实现的。一个类可以实现多个接口。
3. 接口与接口之间是多继承的。

注意事项：
1. 多个父接口当中的抽象方法如果重复，没关系。
2. 多个父接口当中的默认方法如果重复，那么子接口必须进行默认方法的覆盖重写，【而且带着default关键字】。
 */

```

```java
/*
接口 MyInterface extends MyInterfaceA, MyInterfaceB
实现类MyInterfaceImpl implements MyInterface
*/
//实现类
public class MyInterfaceImpl implements MyInterface {
    @Override
    public void method() {
    }
    @Override
    public void methodA() {
    }
    @Override
    public void methodB() {
    }
    @Override
    public void methodCommon() {
    }
}

//子接口
/*
这个子接口当中有几个方法？答：4个。
methodA 来源于接口A
methodB 来源于接口B
methodCommon 同时来源于接口A和B
method 来源于我自己
 */
public interface MyInterface extends MyInterfaceA, MyInterfaceB {
    public abstract void method();
    @Override
    public default void methodDefault() {
    }
}

//两个父接口
public interface MyInterfaceA {
    public abstract void methodA();
    public abstract void methodCommon();
    public default void methodDefault() {
        System.out.println("AAA");
    }
}

public interface MyInterfaceB {
    public abstract void methodB();
    public abstract void methodCommon();
    public default void methodDefault() {
        System.out.println("BBB");
    }
}
```

#### 1.7 接口的其他特点

* 接口中，无法定义成员变量，但是可以定义常量，其值不可以改变，默认使用public static final修饰。
* 接口中，没有构造方法，不能创建对象。
* 接口中，没有静态代码块。



### 2. 多态

#### 2.1 多态的概念

* 多态是继封装、继承之后，面向对象的第三大特性。

* 比如跑的动作，小猫、小狗和大象，跑起来是不一样的。可见，同一行为，通过不同的事物，可以体现出来的不同的形态。多态，描述的就是这样的状态。

* 因此多态的定义是：同一行为，具有多个不同表现形式。

* 多态体现的格式：

  ```java
  父类类型 变量名 = new 子类对象;
  变量名.方法名();
  //代码如下:
  Fu f = New Zi();
  f.method();
  ```

  

#### 2.2 多态中成员变量的使用特点

```java
/*
访问成员变量的两种方式：
1. 直接通过对象名称访问成员变量：看等号左边是谁，优先用谁，没有则向上找。
2. 间接通过成员方法访问成员变量：看该方法属于谁，优先用谁，没有则向上找。
 */
public class Demo01MultiField {
    public static void main(String[] args) {
        // 使用多态的写法，父类引用指向子类对象
        Fu obj = new Zi();
        System.out.println(obj.num); // 父：10
//        System.out.println(obj.age); // 错误写法！
        System.out.println("=============");
        // 子类没有覆盖重写，就是父：10
        // 子类如果覆盖重写，就是子：20
        obj.showNum();
    }
}

public class Zi extends Fu {
    int num = 20;
    int age = 16;
    @Override
    public void showNum() {
        System.out.println(num);
    }
    @Override
    public void method() {
        System.out.println("子类方法");
    }
    public void methodZi() {
        System.out.println("子类特有方法");
    }
}

public class Fu /*extends Object*/ {
    int num = 10;
    public void showNum() {
        System.out.println(num);
    }
    public void method() {
        System.out.println("父类方法");
    }
    public void methodFu() {
        System.out.println("父类特有方法");
    }
}
```

#### 2.3 多态中成员方法的使用特点

```java
/*
在多态的代码当中，成员方法的访问规则是：
    看new的是谁，就优先用谁，没有则向上找。

口诀：编译看左边，运行看右边。

对比一下：
成员变量：编译看左边，运行还看左边。
成员方法：编译看左边，运行看右边。
 */
public class Demo02MultiMethod {
    public static void main(String[] args) {
        Fu obj = new Zi(); // 多态
        obj.method(); // 父子都有，优先用子
        obj.methodFu(); // 子类没有，父类有，向上找到父类
        // 编译看左边，左边是Fu，Fu当中没有methodZi方法，所以编译报错。
//        obj.methodZi(); // 错误写法！
    }
}


```

#### 2.4 使用多态的好处

![image-20210225132237523](Java%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0.assets/使用多态的好处.png)

#### 2.5 对象的向上转型和向下转型

![image-20210225134007706](Java%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0.assets/对象的上下转型.png)

```java
// 对象的向上转型，就是：父类引用指向之类对象。

/*
向上转型一定是安全的，没有问题的，正确的。但是也有一个弊端：
对象一旦向上转型为父类，那么就无法调用子类原本特有的内容。

解决方案：用对象的向下转型【还原】。
 */
public class Demo01Main {
    public static void main(String[] args) {
        // 对象的向上转型，就是：父类引用指向之类对象。
        Animal animal = new Cat(); // 本来创建的时候是一只猫
        animal.eat(); // 猫吃鱼
//        animal.catchMouse(); // 错误写法！
        // 向下转型，进行“还原”动作
        Cat cat = (Cat) animal;
        cat.catchMouse(); // 猫抓老鼠
        // 下面是错误的向下转型
        // 本来new的时候是一只猫，现在非要当做狗
        // 错误写法！编译不会报错，但是运行会出现异常：
        // java.lang.ClassCastException，类转换异常
        Dog dog = (Dog) animal;
    }
}

// 两个子类
public class Cat extends Animal {
    @Override
    public void eat() {
        System.out.println("猫吃鱼");
    }
    // 子类特有方法
    public void catchMouse() {
        System.out.println("猫抓老鼠");
    }
}
public class Dog extends Animal {
    @Override
    public void eat() {
        System.out.println("狗吃SHIT");
    }
    public void watchHouse() {
        System.out.println("狗看家");
    }
}
//父类
public abstract class Animal {
    public abstract void eat();
}

```

#### 2.6 对象的向下转型要进行instanceof判断

```java
/*
如何才能知道一个父类引用的对象，本来是什么子类？
格式：
对象 instanceof 类名称
这将会得到一个boolean值结果，也就是判断前面的对象能不能当做后面类型的实例。
 */
public class Demo02Instanceof {
    public static void main(String[] args) {
        Animal animal = new Dog(); // 本来是一只狗
        animal.eat(); // 狗吃SHIT
        // 如果希望掉用子类特有方法，需要向下转型
        // 判断一下父类引用animal本来是不是Dog
        if (animal instanceof Dog) {
            Dog dog = (Dog) animal;
            dog.watchHouse();
        }
        // 判断一下animal本来是不是Cat
        if (animal instanceof Cat) {
            Cat cat = (Cat) animal;
            cat.catchMouse();
        }
        giveMeAPet(new Dog());
    }
    public static void giveMeAPet(Animal animal) {
        if (animal instanceof Dog) {
            Dog dog = (Dog) animal;
            dog.watchHouse();
        }
        if (animal instanceof Cat) {
            Cat cat = (Cat) animal;
            cat.catchMouse();
        }
    }
}
```

## day11【final、权限、内部类】

### 1. final关键字概述

修饰不可改变的内容，用于修饰类、方法和变量

* 类：被修饰的类，不能被继承。

  ```java
  final class 类名{}
  ```

  API：`public final class String`，`public final class Math`，`public final class Scanner` 目的是供我们使用，而不是让我们可以改变其内容。

* 方法：被修饰发方法，不能被重写。

  ```java
  修饰符 final 返回值类型 方法名(参数列表){
      //方法体
  }
  ```

  

* 变量：被修饰的变量，不能被重新赋值。

  * 局部变量——基本类型

    以下两种写法，哪种可以编译？

    ```java
    // 写法1
    final int c = 0;
    for (int i = 0; i < 10; i++) {
        c = i;
        System.out.println(c);
    }
    
    //写法2
    for (int i = 0; i < 10; i++) {
        final int c = i;
        System.out.println(c);
    }
    ```

    写法1报错！写法2，为什么通过编译呢？因为**每次循环，都是一次新的变量c**。

  * 局部变量——引用类型

    引用类型的局部变量，被final修饰后，只能指向一个对象，地址不能再更改。但是不影响对象内部的成员变量值的修改，代码如下：

    ```java
    public class FinalDemo2 {
        public static void main(String[] args) {
            // 创建 User 对象
            final User u = new User();
            // 创建 另一个 User对象
            u = new User(); // 报错，指向了新的对象，地址值改变。
            // 调用setName方法
            u.setName("张三"); // 可以修改
        }
    }
    ```

    

  * 成员变量

    被final修饰的常量名称，一般都有书写规范，**所有字母都大写**。

    * 显示初始化

      ```java
      public class User{
          final String USERNAME = "张三";
          private int age;
      }
      ```

      

    * 构造方法初始化

      ```java
      public class User{
          final String USERNAME;
          private int age;
          public User(String username, int age){
              this.USERNAME = username;
              this.age = age;
          }
      }
      ```

      

### 2. 权限修饰符

在Java中提供了四种访问权限，使用不同的访问权限修饰符修饰时，被修饰的内容会有不同的访问权限。

|                        | public | protected | default  (空的) | private |
| ---------------------- | ------ | --------- | --------------- | ------- |
| 同一类中               | y      | y         | y               | y       |
| 同一包中(子类与无关类) | y      | y         | y               |         |
| 不同包的子类           | y      | y         |                 |         |
| 不同包中的无关类       | y      |           |                 |         |

备注：不加权限修饰符，其访问能力与default修饰符相同

### 3. 内部类

#### 3.1 内部类的概念

将一个类A定义在另一个类B里面，里面的那个类A就称为内部类，B则称为外部类。

内部类仍然是一个独立的类，在编译之后会内部类会被编译成独立的.class文件，但是前面冠以外部类的类名
和dollar符号 。比如，Person$Heart.class

#### 3.2 成员内部类：定义在类中、方法外的类

```java
修饰符 class 外部类名称 {
    修饰符 class 内部类名称 {
        // ...
    }
    // ...
}
注意：内用外，随意访问；外用内，需要内部类对象。
```

访问特点

```java
外部类名.内部类名 对象名 = new 外部类型().new 内部类型();
```

```java
/*
如何使用成员内部类？有两种方式：
1. 间接方式：在外部类的方法当中，使用内部类；然后main只是调用外部类的方法。
2. 直接方式，公式：
类名称 对象名 = new 类名称();
【外部类名称.内部类名称 对象名 = new 外部类名称().new 内部类名称();】
 */
public class Demo01InnerClass {
    public static void main(String[] args) {
        Body body = new Body(); // 外部类的对象
        // 通过外部类的对象，调用外部类的方法，里面间接在使用内部类Heart
        body.methodBody();
        System.out.println("=====================");
        // 按照公式写：
        Body.Heart heart = new Body().new Heart();
        heart.beat();
    }
}

public class Body { // 外部类
    public class Heart { // 成员内部类
        // 内部类的方法
        public void beat() {
            System.out.println("心脏跳动：蹦蹦蹦！");
            System.out.println("我叫：" + name); // 正确写法！
        }
    }
    // 外部类的成员变量
    private String name;
    // 外部类的方法
    public void methodBody() {
        System.out.println("外部类的方法");
        new Heart().beat();
    }
    public String getName() {
        return name;
    }
    public void setName(String name) {
        this.name = name;
    }
}
```

#### 3.3 成员内部类的同名变量访问

```java
// 如果出现了重名现象，那么格式是：外部类名称.this.外部类成员变量名
public class Outer {
    int num = 10; // 外部类的成员变量
    public class Inner /*extends Object*/ {
        int num = 20; // 内部类的成员变量
        public void methodInner() {
            int num = 30; // 内部类方法的局部变量
            System.out.println(num); // 局部变量，就近原则
            System.out.println(this.num); // 内部类的成员变量
            System.out.println(Outer.this.num); // 外部类的成员变量
        }
    }
}

public class Demo02InnerClass {
    public static void main(String[] args) {
        // 外部类名称.内部类名称 对象名 = new 外部类名称().new 内部类名称();
        Outer.Inner obj = new Outer().new Inner();
        obj.methodInner();
    }
}

```

#### 3.4 局部内部类——方法内的类

```java
/*
如果一个类是定义在一个方法内部的，那么这就是一个局部内部类。
“局部”：只有当前所属的方法才能使用它，出了这个方法外面就不能用了。

定义格式：
修饰符 class 外部类名称 {
    修饰符 返回值类型 外部类方法名称(参数列表) {
        class 局部内部类名称 {
            // ...
        }
    }
}

小节一下类的权限修饰符：
public > protected > (default) > private
定义一个类的时候，权限修饰符规则：
1. 外部类：public / (default)
2. 成员内部类：public / protected / (default) / private
3. 局部内部类：什么都不能写
 */
class Outer {
    public void methodOuter() {
        class Inner { // 局部内部类
            int num = 10;
            public void methodInner() {
                System.out.println(num); // 10
            }
        }
        Inner inner = new Inner();
        inner.methodInner();
    }
}

public class DemoMain {
    public static void main(String[] args) {
        Outer obj = new Outer();
        obj.methodOuter();
    }
}

```

#### 3.5 局部内部类的final问题——方法中的局部变量与方法内的类

```java
/*
局部内部类，如果希望访问所在方法的局部变量，那么这个局部变量必须是【有效final的】。

备注：从Java 8+开始，只要局部变量事实不变，那么final关键字可以省略。

原因：
1. new出来的对象在堆内存当中。
2. 局部变量是跟着方法走的，在栈内存当中。
3. 方法运行结束之后，立刻出栈，局部变量就会立刻消失。
4. 但是new出来的对象会在堆当中持续存在，直到垃圾回收消失。
 */
public class MyOuter {
    public void methodOuter() {
        int num = 10; // 所在方法的局部变量
        class MyInner {
            public void methodInner() {
                System.out.println(num);
            }
        }
    }
}
```

#### 3.6 匿名内部类（是局部内部类其中的）【重点】与匿名内部对象

* 概念
  * 内部类的简化写法。开发中，**最常用到的内部类就是匿名内部类**。
  * 以接口举例，当你使用一个接口时，似乎得做如下几步操作：
    * 定义该接口的子类
    * 重写接口中的方法
    * 创建子类对象
    * 调用重写后的方法
  * 我们的目的，最终只是为了调用方法，那么能不能简化一下，把以上四步合成一步呢？**匿名内部类就是做这样的快捷方式**。
* 前提：匿名内部类必须**继承一个父类**或者**实现一个父接口**。

```java
/*
如果接口的实现类（或者是父类的子类）只需要使用唯一的一次，
那么这种情况下就可以省略掉该类的定义，而改为使用【匿名内部类】。

匿名内部类的定义格式：
接口名称 对象名 = new 接口名称() {
    // 覆盖重写所有抽象方法
};

对格式“new 接口名称() {...}”进行解析：
1. new代表创建对象的动作
2. 接口名称就是匿名内部类需要实现哪个接口
3. {...}这才是匿名内部类的内容

另外还要注意几点问题：
1. 匿名内部类，在【创建对象】的时候，只能使用唯一一次。
如果希望多次创建对象，而且类的内容一样的话，那么就需要使用单独定义的实现类了。
2. 匿名对象，在【调用方法】的时候，只能调用唯一一次。
如果希望同一个对象，调用多次方法，那么必须给对象起个名字。
3. 匿名内部类是省略了【实现类/子类名称】，但是匿名对象是省略了【对象名称】
强调：匿名内部类和匿名对象不是一回事！！！
 */
public class DemoMain {
    public static void main(String[] args) {
//        MyInterface obj = new MyInterfaceImpl();
//        obj.method();
//        MyInterface some = new MyInterface(); // 错误写法！
        // 使用匿名内部类，但不是匿名对象，对象名称就叫objA
        MyInterface objA = new MyInterface() {
            @Override
            public void method1() {
                System.out.println("匿名内部类实现了方法！111-A");
            }
            @Override
            public void method2() {
                System.out.println("匿名内部类实现了方法！222-A");
            }
        };
        objA.method1();
        objA.method2();
        System.out.println("=================");
        // 使用了匿名内部类，而且省略了对象名称，也是匿名对象
        new MyInterface() {
            @Override
            public void method1() {
                System.out.println("匿名内部类实现了方法！111-B");
            }
            @Override
            public void method2() {
                System.out.println("匿名内部类实现了方法！222-B");
            }
        }.method1();
        // 因为匿名对象无法调用第二次方法，所以需要再创建一个匿名内部类的匿名对象
        new MyInterface() {
            @Override
            public void method1() {
                System.out.println("匿名内部类实现了方法！111-B");
            }
            @Override
            public void method2() {
                System.out.println("匿名内部类实现了方法！222-B");
            }
        }.method2();
    }
}

// 接口
public interface MyInterface {
    void method1(); // 抽象方法
    void method2();
}
```

### 4. 引用类型方法总结

#### 4.1 类作为成员变量

类作为成员变量时，对它进行赋值的操作，实际上，是赋给它该类的一个对象。

```java
public class DemoMain {
    public static void main(String[] args) {
        // 创建一个英雄角色
        Hero hero = new Hero();
        // 为英雄起一个名字，并且设置年龄
        hero.setName("盖伦");
        hero.setAge(20);
        // 创建一个武器对象
        Weapon weapon = new Weapon("AK-47");
        // 为英雄配备武器
        hero.setWeapon(weapon);
        // 年龄为20的盖伦用多兰剑攻击敌方。
        hero.attack();
    }
}

// 游戏当中的英雄角色类
public class Hero {
    private String name; // 英雄的名字
    private int age; // 英雄的年龄
    private Weapon weapon; // 英雄的武器
    public Hero() {
    }
    public Hero(String name, int age, Weapon weapon) {
        this.name = name;
        this.age = age;
        this.weapon = weapon;
    }
    public void attack() {
        System.out.println("年龄为" + age + "的" + name + "用" + weapon.getCode() + "攻击敌方。");
    }
    public String getName() {
        return name;
    }
    public void setName(String name) {
        this.name = name;
    }
    public int getAge() {
        return age;
    }
    public void setAge(int age) {
        this.age = age;
    }
    public Weapon getWeapon() {
        return weapon;
    }
    public void setWeapon(Weapon weapon) {
        this.weapon = weapon;
    }
}

public class Weapon {
    private String code; // 武器的代号
    public Weapon() {
    }
    public Weapon(String code) {
        this.code = code;
    }
    public String getCode() {
        return code;
    }
    public void setCode(String code) {
        this.code = code;
    }
}
```

#### 4.2 接口作为成员变量

```java
// 运行main
public class DemoGame {

    public static void main(String[] args) {
        Hero hero = new Hero();
        hero.setName("艾希"); // 设置英雄的名称

        // 设置英雄技能
//        hero.setSkill(new SkillImpl()); // 使用单独定义的实现类

        // 还可以改成使用匿名内部类
//        Skill skill = new Skill() {
//            @Override
//            public void use() {
//                System.out.println("Pia~pia~pia~");
//            }
//        };
//        hero.setSkill(skill);

        // 进一步简化，同时使用匿名内部类和匿名对象
        hero.setSkill(new Skill() {
            @Override
            public void use() {
                System.out.println("Biu~Pia~Biu~Pia~");
            }
        });
        hero.attack();
    }
}

// Hero类
package cn.itcast.day11.demo07;
public class Hero {
    private String name; // 英雄的名称
    private Skill skill; // 英雄的技能
    public Hero() {
    }
    public Hero(String name, Skill skill) {
        this.name = name;
        this.skill = skill;
    }
    public void attack() {
        System.out.println("我叫" + name + "，开始施放技能：");
        skill.use(); // 调用接口中的抽象方法
        System.out.println("施放技能完成。");
    }
    public String getName() {
        return name;
    }
    public void setName(String name) {
        this.name = name;
    }
    public Skill getSkill() {
        return skill;
    }
    public void setSkill(Skill skill) {
        this.skill = skill;
    }
}
// 接口Skill的实现类
public class SkillImpl implements Skill {
    @Override
    public void use() {
        System.out.println("Biu~biu~biu~");
    }
}
// 接口Skill
public interface Skill {
    void use(); // 释放技能的抽象方法
}
```

#### 4.3 接口作为 方法的参数和返回值类型

```java
import java.util.ArrayList;
import java.util.List;

/*
java.util.List正是ArrayList所实现的接口。
 */
public class DemoInterface {

    public static void main(String[] args) {
        // 左边是接口名称，右边是实现类名称，这就是多态写法
        List<String> list = new ArrayList<>();

        List<String> result = addNames(list);
        for (int i = 0; i < result.size(); i++) {
            System.out.println(result.get(i));
        }
    }
	
    // 传进方法的参数是接口类型，返回的是接口类型
    public static List<String> addNames(List<String> list) {
        list.add("迪丽热巴");
        list.add("古力娜扎");
        list.add("玛尔扎哈");
        list.add("沙扬娜拉");
        return list;
    }

}
```



# 二、 Java进阶



## day01【Object类、常用API】

### 1. Object类

#### 1.1 概念

* `java.lang.Object `类是Java语言中的根类，即所有类的父类。它中描述的所有方法子类都可以使用。
* 不同于`Objects`类。下面会讲到此类。
* 在对象实例化的时候，最终找的父类就是Object。
* 如果一个类没有特别指定父类， 那么默认则继承自Object类。
* 包含11个方法

#### 1.2 toString方法

* `public String toString() `：返回该对象的字符串表示。
* 该字符串内容就是对象的类型+@+内存地址值。
* 直接使用输出语句 输出对象名的时候，其实是通过该对象调用了其toString()方法。
* 返回的结果是内存地址，而在开发中，经常需要按照对象的属性得到相应的字符串表现形式，因此也需要重写它。

**覆盖重写**：

```java
public class Person {

    private String name;
    private int age;

    @Override
    public String toString() {
        return "Person{" +
                "name='" + name + '\'' +
                ", age=" + age +
                '}';
    }
}
// 测试类
public class Test {
    public static void main(String[] args) {
        Person person = new Person();
        System.out.println(person);
    }
}
```

在IntelliJ IDEA中，可以点击`Code `菜单中的`Generate... `，也可以使用快捷键`alt+insert` ，点击`toString()` 选项。选择需要包含的成员变量并确定。

#### 1.3 equals方法

* `public boolean equals(Object obj) `：指示其他某个对象是否与此对象“相等”。
* 这里的“相同”有 **默认地址**和**自定义** 两种方式：如果没有覆盖重写equals方法，那么Object类中默认进行`== `运算符的**对象地址**比较，只要不是同一个对象，结果必然为false；如果希望进行对象的内容比较，即所有或指定的部分成员变量相同就判定两个对象相同，则可以覆盖重写equals方法。

```java
/*
可以使用Code 菜单中的Generate… 选项，也可以使用快捷键alt+insert ，并选择equals() and hashCode() 进行自动代码生成
*/
import java.util.Objects;

public class Person {

    private String name;
    private int age;

    @Override
    public boolean equals(Object o) {
        // 如果对象地址一样，则认为相同
        if (this == o) return true;
        // 如果参数为空，或者类型信息不一样，则认为不同
        if (o == null || getClass() != o.getClass()) return false;
        // 转换为当前类型
        Person person = (Person) o;
        // 要求基本类型相等，并且将引用类型交给java.util.Objects类的equals静态方法取用结果
        return age == person.age &&
                Objects.equals(name, person.name);
    }

    @Override
    public int hashCode() {

        return Objects.hash(name, age);
    }
}
```

#### Objects类

在JDK7添加了一个Objects工具类，它提供了一些方法来操作对象，它由一些**静态的实用方法**组成，这些方法是
null-save（空指针安全的）或null-tolerant（容忍空指针的），用于计算对象的hashcode、返回对象的字符串表示形式、比较两个对象。

`public static boolean equals(Object a, Object b)` ：判断两个对象是否相等。其源码如下：

```java
public static boolean equals(Object a, Object b) {
	return (a == b) || (a != null && a.equals(b));
}
```



### 2. 日期时间类

* 西方星期的开始为周日，中国为周一。
* 在Calendar类中，月份的表示是以0-11代表1-12月。
* 日期是有大小关系的，时间靠后，时间越大。

#### 2.1 Date类

`java.util.Date` 类 表示特定的瞬间，精确到毫秒

* 构造方法

  * `public Date()`：分配Date对象并初始化此对象，以表示分配它的时间（精确到毫秒）。
  * `public Date(long date)`：分配Date对象并初始化此对象，以表示自从标准基准时间（称为“历元
    （epoch）”，即1970年1月1日00:00:00 GMT）以来的指定毫秒数。

  ```java
  public class Test {
      public static void main(String[] args) {
          // 创建日期对象，把当前的时间
          System.out.println(new Date());//Thu Feb 25 21:56:09 CST 2021
          // 创建日期对象，把当前的毫秒值转成日期对象
          System.out.println(new Date(0L));//Thu Jan 01 08:00:00 CST 1970
      }
  }
  ```

  **tips**:在使用println方法时，会自动调用Date类中的toString方法。**Date类对Object类中的toString方法进行了覆盖重写**，所以结果为指定格式的字符串。

* 常用方法

  `public long getTime()`把日期对象转成对应的时间毫秒值。

  ```java
  public class Test {
      public static void main(String[] args) {
          Date s = new Date();
          System.out.println("起始时刻s：" + s.getTime() + "ms");
  
          for (int i = 0; i < 10000; i++) {
              continue;
          }
  
          Date e = new Date();
          System.out.println("结束时刻e：" + e.getTime() + "ms");
          System.out.println("运行时间：" + (e.getTime() - s.getTime()) + "ms");
  
      }
  }
  起始时刻s：1614262227855ms
  结束时刻e：1614262227886ms
  运行时间：31ms
  ```

#### 2.2 DateFormat类

* `java.text.DateFormat` 是日期/时间格式化子类的抽象类，我们通过这个类可以帮我们完成**日期和文本之间的转换**,也就是可以在**Date对象**与**String对象**之间进行来回转换。

* 格式化：按照指定的格式，从Date对象转换为String对象。解析：按照指定的格式，从String对象转换为Date对象。

* 构造方法

  `DateFormat`为抽象类，不能直接使用，所以需要常用的子类`java.text.SimpleDateFormat `。

  `public SimpleDateFormat(String pattern)` ：用给定的模式和默认语言环境的日期格式符号构造
  SimpleDateFormat。参数pattern是一个字符串，代表日期时间的自定义格式。

  ```java
  import java.text.DateFormat;
  import java.text.SimpleDateFormat;
  
  
  public class Test {
      public static void main(String[] args) {
          // 对应的日期格式如：2018‐01‐16 15:06:38
          DateFormat df = new SimpleDateFormat("yyyy-MM-dd HH:mm:ss");
          System.out.println(df);//java.text.SimpleDateFormat@4f76f1a0
      }
  }
  ```

  常用格式规则：

  | 标识字母（区分大小写） | 含义 |
  | ---------------------- | ---- |
  | y                      | 年   |
  | M                      | 月   |
  | d                      | 日   |
  | H                      | 时   |
  | m                      | 分   |
  | s                      | 秒   |

* 常用方法

  `public String format(Date date) `：将Date对象格式化为字符串。
  `public Date parse(String source)` ：将字符串解析为Date对象。

  * format方法

    ```java
    public class Test {
        public static void main(String[] args) {
            Date date = new Date();
    
            DateFormat df1 = new SimpleDateFormat("yyyy-MM-dd HH:mm:ss");
            String str1 = df1.format(date);
            System.out.println(str1);
    
            DateFormat df2 = new SimpleDateFormat("y年MM月d日");
            String str2 = df2.format(date);
            System.out.println(str2);
        }
    }
    2021-02-25 22:39:47
    2021年02月25日
    ```

    

  * parse方法

    ```java
    public class Test {
        public static void main(String[] args) throws ParseException {
            DateFormat df = new SimpleDateFormat("y年M月d日");
            String str = "2018年12月11日";
            Date date = df.parse(str);
            System.out.println(date);// Tue Dec 11 00:00:00 CST 2018
        }
    }
    ```

    

#### 2.4 Calendar类

`java.util.Calendar `是日历类，在Date后出现，替换掉了许多Date的方法。该类将所有可能用到的时间信息封装为**静态成员变量**，方便获取。日历类就是方便获取各个时间属性的。

* 对象创建——通过静态方法，返回子类对象

  Calendar为抽象类，由于语言敏感性，Calendar类在**创建对象时并非直接创建，而是通过静态方法创建**，**返回子类对象**。

  `public static Calendar getInstance()`：使用默认时区和语言环境获得一个日历

```java
public class Test {
    public static void main(String[] args) throws ParseException {
        Calendar cal = Calendar.getInstance();
    }
}
```

* 常用方法

  `public int get(int field)` ：返回给定日历字段的值。
  `public void set(int field, int value)` ：将给定的日历字段设置为给定值。
  `public abstract void add(int field, int amount)` ：根据日历的规则，为给定的日历字段添加或减去指定的时间量。
  `public Date getTime()` ：返回一个表示此Calendar时间值（从历元到现在的毫秒偏移量）的Date对象。

  ```java
  // get/set方法
  public class Test {
      public static void main(String[] args) throws ParseException {
  
          Calendar cal = Calendar.getInstance();
          int year = cal.get(Calendar.YEAR);
          int month = cal.get(Calendar.MONTH)+1;
          int dayOfMonth = cal.get(Calendar.DAY_OF_MONTH);
          System.out.println(year + "年" + month + "月" + dayOfMonth + "日");
          // 2021年2月25日
      }
  }
  
  
  public class Test {
      public static void main(String[] args) throws ParseException {
          Calendar cal = Calendar.getInstance();
          cal.set(Calendar.YEAR, 2020);
          int year = cal.get(Calendar.YEAR);
          int month = cal.get(Calendar.MONTH)+1;
          int dayOfMonth = cal.get(Calendar.DAY_OF_MONTH);
          System.out.println(year + "年" + month + "月" + dayOfMonth + "日");
          // 2020年2月25日
      }
  }
  ```

  ```java
  // add
  public class Test {
      public static void main(String[] args) throws ParseException {
          Calendar cal = Calendar.getInstance();
          cal.add(Calendar.DAY_OF_MONTH,2);// 使用add方法
          cal.add(Calendar.YEAR,-3);// 减3年
          int year = cal.get(Calendar.YEAR);
          int month = cal.get(Calendar.MONTH) + 1;
          int dayOfMonth = cal.get(Calendar.DAY_OF_MONTH);
          System.out.println(year + "年" + month + "月" + dayOfMonth + "日");
      }
  }
  2018年2月28日
  ```
  
  ```java
  // getTime 并不是获取毫秒时刻，而是拿到对应的Date对象。
  public class Test {
      public static void main(String[] args) throws ParseException {
          Calendar cal = Calendar.getInstance();
          Date date = cal.getTime();
          System.out.println(date);// Tue Jan 16 16:03:09 CST 2018
      }
  }
  ```
  
  

### 3. System类

`java.lang.System `类中提供了大量的静态方法，可以获取与系统相关的信息或系统级操作。

常用方法：

* `public static long currentTimeMillis() `：返回以毫秒为单位的当前时间。获取当前系统时间与1970年01月01日00:00点之间的毫秒差值

* `public static void arraycopy(Object src, int srcPos, Object dest, int destPos, int length) `：将数组中指定的数据拷贝到另一个数组中。

  | 参数序号 | 参数名称 | 参数类型 | 参数含义             |
  | -------- | -------- | -------- | -------------------- |
  | 1        | src      | Object   | 源数组               |
  | 2        | srcPos   | int      | 源数组索引起始位置   |
  | 3        | dest     | Object   | 目标数组             |
  | 4        | destPos  | int      | 目标数组索引起始位置 |
  | 5        | length   | int      | 复制元素个数         |

  

```java
public class Test {
    public static void main(String[] args) throws ParseException {

        long start = System.currentTimeMillis();
        for (int i = 0; i < 100000; i++) {
            System.out.println(i);
        }
        long end = System.currentTimeMillis();
        System.out.println("共耗时毫秒：" + (end - start));

    }
}
```

```java
public class Test {
    public static void main(String[] args) throws ParseException {

        int[] src = {1, 2, 3, 4, 5};
        int[] dest = {6, 7, 8, 9, 10};
        System.arraycopy(src, 0, dest, 0, 3);
        for (int i = 0; i < src.length; i++) {
            System.out.print(src[i]);
        }
        System.out.println();
        for (int i = 0; i < dest.length; i++) {
            System.out.print(dest[i]);
        }

    }
}
```



### 4. StringBuilder类——可变字符序列

#### 4.1 由字符串拼接问题引出该类

* 由于String类的对象内容不可改变，所以每当进行字符串拼接时，总是会在内存中创建一个新的对象。
* 对字符串进行拼接操作，每次拼接，都会构建一个新的String对象，既耗时，又浪费空间。为了解决这一问题，可以使用`java.lang.StringBuilder `类。

#### 4.2 StringBuilder概述

* 一个类似于 String 的**字符串缓冲区**，通过某些方法调用可以改变该序列的长度和内容。
* 它的内部拥有一个数组用来存放字符串内容，进行字符串拼接时，直接在数组中加入新内容。StringBuilder会自动维护数组的扩容。

#### 4.3 构造方法

* `public StringBuilder()`：构造一个空的StringBuilder容器。
* `public StringBuilder(String str)`：构造一个StringBuilder容器，并将字符串添加进去。

```java
public class Test {
    public static void main(String[] args) throws ParseException {

        StringBuilder str1 = new StringBuilder();
        System.out.println(str1);//(空白)

        StringBuilder str2 = new StringBuilder("itcast");
        System.out.println(str2);//itcast
		// 覆盖重写了toString方法
    }
}
```



#### 4.4 常用方法

* `public StringBuilder append(...)`：添加任意类型数据的字符串形式，并返回当前对象自身。
* `public String toString() `：将当前StringBuilder对象转换成String对象。

**append方法：**

append方法具有多种重载形式，可以**接收任意类型的参数**。任何数据作为参数都会将对应的字符串内容添加到StringBuilder中。

```java
public class Test {
    public static void main(String[] args) throws ParseException {

        StringBuilder b1 = new StringBuilder();
        StringBuilder b2 = b1.append("hello");

        System.out.println("b1:" + b1);
        System.out.println("b2:" + b2);
        System.out.println(b1 == b2);//==比较对象地址
		
        // 链式编程
        b1.append("hello").append("world").append(true).append(100);
        System.out.println("b1:" + b1);

    }
}
```

**toString()方法：**

```java
public class Test {
    public static void main(String[] args) {

        StringBuilder sb = new StringBuilder("Hello").append("World").append("java");
        String str = sb.toString();
        System.out.println(str);

    }
}
```







### 5. 包装类

#### 5.1 概述

Java提供了两个类型系统，**基本类型与引用类型**，使用基本类型在于效率，然而很多情况，会创建对象使用，因为对象可以做更多的功能，**如果想要我们的基本类型像对象一样操作，就可以使用基本类型对应的包装类。**

| 基本类型 | 对应的包装类（位于java.lang包中） |
| -------- | --------------------------------- |
| byte     | Byte                              |
| short    | Short                             |
| int      | **Integer**                       |
| long     | Long                              |
| float    | Float                             |
| double   | Bouble                            |
| char     | **Character**                     |
| boolean  | Boolean                           |

#### 5.2 装箱与拆箱（看懂代码即可）

基本类型 <=> 对应的包装类对象：

* 装箱：从基本类型转换为对应的包装类对象。
* 拆箱：从包装类对象转换为对应的基本类型。

```java
// 数值--->包装对象
Integer i = new Integer(4);
Integer iii = Integer.valueOf(4);
// 包装对象--->基本数值
int num = i.intValue();
```

#### 5.3 自动装箱与自动拆箱

从Java 5（JDK 1.5）开始，基本类型与包装类的装箱、拆箱动作可以自动完成。

```java
Integer i = 4; //自动装箱。相当于Integer i = Integer.valueOf(4);
i = i + 5; //等号右边：将i对象转成基本数值(自动拆箱) i.intValue() + 5;
//加法运算完成后，再次装箱，把基本数值转成对象。
```



#### 5.4 基本类型与字符串之间的转换

* 基本类型 -> String

  基本类型转换String总共有三种方式，查看课后资料可以得知，这里只讲最简单的一种方式：

```java
// 基本类型直接与""相连接即可
34 + "";
```

* 字符串 -> 基本类型

  除了Character类之外，其他所有包装类都具有parseXxx静态方法可以将字符串参数转换为对应的基本类型：

  * `public static byte parseByte(String s) `：将字符串参数转换为对应的byte基本类型。
  * `public static short parseShort(String s)` ：将字符串参数转换为对应的short基本类型。
  * `public static int parseInt(String s)` ：将字符串参数转换为对应的int基本类型。
  * `public static long parseLong(String s) `：将字符串参数转换为对应的long基本类型。
  * `public static float parseFloat(String s) `：将字符串参数转换为对应的float基本类型。
  * `public static double parseDouble(String s)` ：将字符串参数转换为对应的double基本类型。
  * `public static boolean parseBoolean(String s) `：将字符串参数转换为对应的boolean基本类型。

  如果字符串参数的内容无法正确转换为对应的基本类型，则会抛出`java.lang.NumberFormatException`异常。

  ```java
  public class Test {
      public static void main(String[] args) {
          int num = Integer.parseInt("100");
          System.out.println(num);
      }
  }
  ```

  

## day02【Collection、泛型】

### 1. Collection集合——单列集合

单列集合`java.util.Collection `

双列集合`java.util.Map`，后面讲

#### 1.1 集合概念

* 集合是java中提供的一种容器，可以用来存储多个数据
* 数组的长度是固定的；集合的长度是可变的
* 数组中存储的是同一类型的元素，可以存储基本数据类型值；。集合存储的都是对象。而且对象的类型可以不一致。
* 在开发中一般当对象多的时候，使用集合进行存储。



#### 1.2 Collection集合框架

![image-20210226162119722](Java%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0.assets/Collection集合类的继承体系.png)

**橙色是接口类型，蓝色是具体的实现类**。

在Collection 接口定义着单列集合框架中**最最共性的内容**。

* `java.util.List`：元素有序且可重复。其主要实现类有：
  * `java.util.ArrayList`
  * `java.util.LinkedList`
* `java.utill.Set`：元素无序且不可重复。
  * `java.util.HashSet`
  * `java.util.TreeSet`

#### 1.3 Collection 常用功能

在Collection中定义了单列集合(List和Set)通用的一些方法，这些方法可用于操作所有的单列集合。

* `public boolean add(E e)` ： 把给定的对象添加到当前集合中 。
* `public void clear() `:清空集合中所有的元素。
* `public boolean remove(E e)` : 把给定的对象在当前集合中删除。
* `public boolean contains(E e)` : 判断当前集合中是否包含给定的对象。
* `public boolean isEmpty() `: 判断当前集合是否为空。
* `public int size() `: 返回集合中元素的个数。
* `public Object[] toArray()` : 把集合中的元素，存储到数组中。

```java
public class Test {
    public static void main(String[] args) {
        // 创建集合对象
        // 使用多态形式
        Collection<String> coll = new ArrayList<String>();
        // 使用方法
        // 添加功能 boolean add(String s)
        coll.add("小李广");
        coll.add("扫地僧");
        coll.add("石破天");
        System.out.println(coll);
        // boolean contains(E e) 判断o是否在集合中存在
        System.out.println("判断 扫地僧 是否在集合中" + coll.contains("扫地僧"));
        //boolean remove(E e) 删除在集合中的o元素
        System.out.println("删除石破天：" + coll.remove("石破天"));
        System.out.println("操作之后集合中元素:" + coll);
        // size() 集合中有几个元素
        System.out.println("集合中有" + coll.size() + "个元素");
        // Object[] toArray()转换成一个Object数组
        Object[] objects = coll.toArray();
        // 遍历数组
        for (int i = 0; i < objects.length; i++) {
            System.out.println(objects[i]);
        }
        // void clear() 清空集合
        coll.clear();
        System.out.println("集合中内容为：" + coll);
        // boolean isEmpty() 判断是否为空
        System.out.println(coll.isEmpty());
    }
}
[小李广, 扫地僧, 石破天]
判断 扫地僧 是否在集合中true
删除石破天：true
操作之后集合中元素:[小李广, 扫地僧]
集合中有2个元素
小李广
扫地僧
集合中内容为：[]
true
```

### 2. Iterator迭代器

#### 2.1 Iterator接口

Java集合包括`Iterator`、`Collection`、`Map`等。

* `Iterator `主要用于迭代访问（即**遍历**） Collection 中的元素，因此Iterator 对象也被称为**迭代器**
* `Collection `接口与`Map` 接口主要用于存储元素。

**迭代器的获取**：

`public Iterator iterator()`：获取集合对应的迭代器，用来遍历集合中的元素。

**常用方法**：

* `public E next()`：返回迭代的下一个元素。

* `public boolean hashNext()`：如果仍有元素可以迭代，就返回true。

  ```java
  public class Test {
      public static void main(String[] args) {
  		// 使用多态方式 创建对象
          Collection<String> coll = new ArrayList<>();
  
          coll.add("串串星人");
          coll.add("吐槽星人");
          coll.add("汪星人");
  		//使用迭代器 遍历 每个集合对象都有自己的迭代器
          Iterator<String> it = coll.iterator();
          // 泛型指的是 迭代出 元素的数据类型
          while (it.hasNext()){ //判断是否有迭代元素
              String s = it.next(); //获取迭代出的元素
              System.out.println(s);
          }
      }
  }
  ```

  在进行集合元素取出时，如果集合中已经没有元素了，还继续使用迭代器的next方法，将会发生
  java.util.NoSuchElementException没有集合元素的错误。

#### 2.2 增强for——内部原理是Iterator迭代器

* 专门用来遍历数组和集合的。
* 内部原理是Iterator迭代器，因此，在遍历过程中，不能增删集合中的元素。
* 新for循环必须有被遍历的目标，目标只能是Collection或者是数组。

格式：

```java
for(元素的数据类型 变量：Collection集合or数组){
    // 写操作代码
}
```

```java
// 例1
public class Test {
    public static void main(String[] args) {
        int[] arr = {3, 5, 6, 87};
        for (int a:arr){
            System.out.println(i);
        }
    }
}
// 例2
public class Test {
    public static void main(String[] args) {
        Collection<String> coll = new ArrayList<>();
        coll.add("小河神");
        coll.add("老河神");
        coll.add("神婆");
        for (String s:coll){
            System.out.println(s);
        }
    }
}
```

### 3. 泛型

#### 3.1 为什么引入泛型

Collection集合可以存放任意对象，只要把对象存储到集合后，它们**都会被提升为Object类型**。取对象并进行相应的操作时，就**必须采用类型转换**。观察下面的代码：

```java
public class Test {
    public static void main(String[] args) {
        Collection coll = new ArrayList();
        coll.add("abc");
        coll.add("itcast");
        coll.add(5);
        Iterator it = coll.iterator();
        while(it.hasNext()){
            /*java.lang.ClassCastException:
            java.base/java.lang.Integer cannot be cast to java.base/java.lang.String*/
            String str = (String) it.next();
            System.out.println(str.length());
        }
    }
}
// 报错啦！！！
```



Collection虽然可以存储各种对象，但实际上通常Collection只存储同一类型对象。在JDK5之后，新增了泛型(Generic)语法，让你在设计API时可以指定类或方法支持泛型，这样我们使用API的时候也变得更为简洁，并**得到了编译时期的语法检查**。

#### 3.2 泛型的概念

* 可以在类或方法中预支地使用未知的类型。
* 一般在创建对象时，将未知的类型确定具体的类型。
* 当没有指定泛型时，默认类型为Object类型。

#### 3.3 引入泛型的好处

* 将运行时期的ClassCastException，转移到了编译时期变成了编译失败。
* 避免了类型强转的麻烦。

```java
public class Test {
    public static void main(String[] args) {
        Collection<String> list = new ArrayList<>();
        list.add("abc");
        list.add("itcast");
        // list.add(5);//当集合明确类型后，存放类型不一致就会编译报错
        // 集合已经明确具体存放的元素类型，那么在使用迭代器的时候，迭代器也同样会知道具体遍历元素类型
        Iterator<String> it = list.iterator();
        while (it.hasNext()){
            String str = it.next();
            //当使用Iterator<String>控制元素类型后，就不需要强转了。获取到的元素直接就是String类型
            System.out.println(str.length());
        }
    }
}
```

#### 3.3 泛型的定义和使用

* 定义和使用含有泛型的类

  定义格式：

```java
修饰符 class 类名<代表泛型的变量>{ }
```

​		举例：

```java
class ArrayList<E> {
    public boolean add(E e){ }
    public E get(int index){ }
    ...
}
```

​		何时确定泛型？——**创建对象时**

```java
ArrayList<String> list = new ArrayList();
```

​		自定义泛型类

```java
public class MyGenericClass<MVP> {
//没有MVP类型，在这里代表 未知的一种数据类型 未来传递什么就是什么类型
    private MVP mvp;
    public void setMVP(MVP mvp) {
    	this.mvp = mvp;
    }
    public MVP getMVP() {
    	return mvp;
    }
}

public class GenericClassDemo {
	public static void main(String[] args) {
        // 创建一个泛型为String的类
        MyGenericClass<String> my = new MyGenericClass<String>();
        // 调用setMVP
        my.setMVP("大胡子登登");
        // 调用getMVP
        String mvp = my.getMVP();
        System.out.println(mvp);
        //创建一个泛型为Integer的类
        MyGenericClass<Integer> my2 = new MyGenericClass<Integer>();
        my2.setMVP(123);
        Integer mvp2 = my2.getMVP();
    }
}
```

*  含有泛型的方法

  格式：

  ```java
  修饰符 <代表泛型的变量> 返回值类型 方法名(参数){ }
  ```

  举例：

  ```java
  // 无论第一行 该类是否是泛型
  public class MyGenericMethod {
      public <MVP> void show(MVP mvp) {
      	System.out.println(mvp.getClass());
      }
      public <MVP> MVP show2(MVP mvp) {
      	return mvp;
      }
  }
  ```

  创建对象时不是泛型，调用方法时，确定泛型的类型

  ```java
  public class Test {
      public static void main(String[] args) {
          // 创建对象时不是泛型
          MyGenericMethod mm = new MyGenericMethod();
          mm.show("aa");
          mm.show(123);
          mm.show(12.45);
      }
  }
  ```

  

  

* 含有泛型的接口

  ```java
  修饰符 interface接口名<代表泛型的变量> { }
  ```

  举例：

  ```java
  public interface MyGenericInterface<E>{
  	public abstract void add(E e);
  	public abstract E getE();
  }
  ```

  ```java
  public class MyImp1 implements MyGenericInterface<String> {
      @Override
      public void add(String e) {
          // 省略...
      }
      @Override
      public String getE() {
          return null;
      }
  }
  ```

  ```java
  public class MyImp2<E> implements MyGenericInterface<E> {
      @Override
      public void add(E e) {
          // 省略...
      }
      @Override
      public E getE() {
          return null;
      }
  }
  
  public class GenericInterface {
      public static void main(String[] args) {
          MyImp2<String> my = new MyImp2<String>();
          my.add("aa");
      }
  }
  ```

  



#### 3.4 泛型通配符

```java
/*
    泛型的通配符:
        ?:代表任意的数据类型
    使用方式:
        不能创建对象使用
        只能作为方法的参数使用
 */
public class Demo05Generic {
    public static void main(String[] args) {
        ArrayList<Integer> list01 = new ArrayList<>();
        list01.add(1);
        list01.add(2);

        ArrayList<String> list02 = new ArrayList<>();
        list02.add("a");
        list02.add("b");

        printArray(list01);
        printArray(list02);

        //ArrayList<?> list03 = new ArrayList<?>();//不能创建对象使用
    }

    /*
        定义一个方法,能遍历所有类型的ArrayList集合
        这时候我们不知道ArrayList集合使用什么数据类型,可以泛型的通配符?来接收数据类型
        注意:
            泛型没有继承概念的
     */
    // 若使用Integer则，上面String类型的报错；反之，...
    public static void printArray(ArrayList<?> list){
        //使用迭代器遍历集合
        Iterator<?> it = list.iterator();
        while(it.hasNext()){
            //it.next()方法,取出的元素是Object,可以接收任意的数据类型
            Object o = it.next();
            System.out.println(o);
        }
    }
}
```

* 高级使用

  【看源码内看就行，平时工作用到很少】

  ```java
  /*
      泛型的上限限定: ? extends E  代表使用的泛型只能是E类型的子类/本身
      泛型的下限限定: ? super E    代表使用的泛型只能是E类型的父类/本身
   */
  public class Demo06Generic {
      public static void main(String[] args) {
          Collection<Integer> list1 = new ArrayList<Integer>();
          Collection<String> list2 = new ArrayList<String>();
          Collection<Number> list3 = new ArrayList<Number>();
          Collection<Object> list4 = new ArrayList<Object>();
  
          getElement1(list1);
          //getElement1(list2);//报错
          getElement1(list3);
          //getElement1(list4);//报错
  
          //getElement2(list1);//报错
          //getElement2(list2);//报错
          getElement2(list3);
          getElement2(list4);
  
          /*
              类与类之间的继承关系
              Integer extends Number extends Object
              String extends Object
           */
  
      }
      // 泛型的上限：此时的泛型?，必须是Number类型或者Number类型的子类
      public static void getElement1(Collection<? extends Number> coll){}
      // 泛型的下限：此时的泛型?，必须是Number类型或者Number类型的父类
      public static void getElement2(Collection<? super Number> coll){}
  }
  
  
  ```

  

## day03【数据结构、List、Set、Collections】

List：Collection的一个子类`java.util.List`接口

Set：Collection的一个子类`java.util.Set`集合

### 1. 数据结构

#### 1.1 红黑树

* 二叉查找树
* 根节点是黑色的
3. 叶子节点(特指空节点)是黑色的
4. 每个红色节点的子节点都是黑色的
5. 任何一个节点到其每一个叶子节点的所有路径上黑色节点数相同

**红黑树的特点**：速度特别快,趋近平衡树,查找叶子元素最少和最多次数不多于二倍

### 2. List接口

![](Java%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0.assets/Collection%E9%9B%86%E5%90%88%E7%B1%BB%E7%9A%84%E7%BB%A7%E6%89%BF%E4%BD%93%E7%B3%BB.png)

单列集合Collection（是一个接口）的一个子类`java.util.List`接口

**特点**：

* 存储有序，
* 带有索引
* 元素可重复，通过元素的equals方法，来比较是否为重复的元素。
* `java.util.ArrayList`类是List接口的实现类，该类中的方法都是来自List中定义。

#### 2.1 List接口中的常用方法

* `public void add(int index, E element) `: 将指定的元素，添加到该集合中的指定位置上。
* `public E get(int index) `:返回集合中指定位置的元素。
* `public E remove(int index)` : 移除列表中指定位置的元素, 返回的是被移除的元素。
* `public E set(int index, E element)` :用指定元素替换集合中指定位置的元素,返回值的更新前的元素。

```java
public class Test {
    public static void main(String[] args) {
        List<String> list = new ArrayList<>();

        // 往 尾部添加 指定元素
        list.add("图图");
        list.add("小美");
        list.add("不高兴");
        System.out.println(list);
        // add(int index,String s) 往指定位置添加
        list.add(1,"没头脑");

        System.out.println(list);
        // String remove(int index) 删除指定位置元素 返回被删除元素
        // 删除索引位置为2的元素
        System.out.println("删除索引位置为2的元素");
        System.out.println(list.remove(2));

        System.out.println(list);
        // 在指定位置 进行 元素替代（改）
        list.set(0,"三毛");
        System.out.println(list);
		
        // 跟size() 方法一起用 来 遍历的
        for (int i = 0; i < list.size(); i++) {
            System.out.println(list.get(i));
        }
		
        // 还可以使用增强for
        for (String str:list){
            System.out.println(str);
        }
        
    }
}
```

### 3. List接口的实现类

#### 3.1 ArrayList集合

增删慢，随机访问快

具体见  基础——day07——ArrayList类

#### 3.2 LinkedList集合

`java.util.LinkedList`链表，增删快。

* `public void addFirst(E e)` :将指定元素插入此列表的开头。
* `public void addLast(E e) `:将指定元素添加到此列表的结尾。
* `public E getFirst() `:返回此列表的第一个元素。
* `public E getLast()` :返回此列表的最后一个元素。
* `public E removeFirst() `:移除并返回此列表的第一个元素。
* `public E removeLast()` :移除并返回此列表的最后一个元素。
* `public E pop()` :从此列表所表示的堆栈处弹出一个元素。
* `public void push(E e) `:将元素推入此列表所表示的堆栈。
* `public boolean isEmpty() `：如果列表不包含元素，则返回true。

LinkedList是List的子类，List中的方法LinkedList都是可以使用。

```java
public class Test {
    public static void main(String[] args) {
        LinkedList<String> link = new LinkedList<>();
        link.addFirst("abc1");
        link.addFirst("abc2");
        link.addFirst("abc3");
        System.out.println(link);

        System.out.println(link.getFirst());
        System.out.println(link.getLast());
        while (!link.isEmpty()){
            System.out.println(link.pop());
        }

        System.out.println(link);

    }
}
```



### 4. Set接口

* 存储的元素是不可重复的，并且元素都是无序的(即存取顺序不一致)。
* Set集合取出元素的方式可以采用：迭代器、增强for。

#### 4.1 HashSet

* `java.util.HashSet `底层的实现其实是一个`java.util.HashMap` 支持，由于我们暂时还未学习，先做了解。

* `HashSet `是根据对象的哈希值来确定元素在集合中的存储位置，因此具有良好的存取和查找性能。
* 保证元素唯一性的方式依赖于： `hashCode` 与`equals `方法。

#### 4.2 HashSet集合存储数据的结构（哈希表）

在JDK1.8之前，哈希表底层采用**数组+链表**实现，即使用链表处理冲突，**同一hash值的链表都存储在一个链表里**。但是当位于一个桶中的元素较多，即hash值相等的元素较多时，通过key值依次查找的效率较低。而JDK1.8中，哈希表存储采用**数组+链表+红黑树**实现，当**链表长度超过阈值（8）时，将链表转换为红黑树**，这样大大减少了查找时间。

![image-20210227095505198](Java%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0.assets/HashSet底层.png)

#### 4.3 HashSet存储自定义类型元素

需要重写对象中的hashCode和equals方法，建立自己的比较方式，才能保证HashSet集合中的对象唯一

举例说明：

```java
// 如果不重写
public class Person {
    private String name;
    private int age;

    public Person() {
    }

    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }
	//这两段注掉表示不重写
/*    @Override
    public boolean equals(Object o) {
        if (this == o) return true;
        if (o == null || getClass() != o.getClass()) return false;
        Person person = (Person) o;
        return age == person.age &&
                Objects.equals(name, person.name);
    }

    @Override
    public int hashCode() {

        return Objects.hash(name, age);
    }
*/
    @Override
    public String toString() {
        return "Person{" +
                "name='" + name + '\'' +
                ", age=" + age +
                '}';
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }
}

// 测试类
// == 比较的是地址值；equals默认比较地址值
public class Demo03HashSetSavePerson {
    public static void main(String[] args) {
        //创建HashSet集合存储Person
        HashSet<Person> set = new HashSet<>();
        Person p1 = new Person("小美女",18);
        Person p2 = new Person("小美女",18);
        Person p3 = new Person("小美女",19);
        System.out.println(p1.hashCode());//1967205423
        System.out.println(p2.hashCode());//42121758

        System.out.println(p1==p2);//false
        System.out.println(p1.equals(p2));//false
        set.add(p1);
        set.add(p2);
        set.add(p3);
        System.out.println(set);
    }

}
// 运行结构发现 小美女 18岁存储了两个——》如何避免？
[Person{name='小美女', age=19}, Person{name='小美女', age=18}, Person{name='小美女', age=18}]
```

重写后：

```java
// 如果不重写
public class Person {
    private String name;
    private int age;

    public Person() {
    }

    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }
	// 重写
    @Override
    public boolean equals(Object o) {
        if (this == o) return true;
        if (o == null || getClass() != o.getClass()) return false;
        Person person = (Person) o;
        return age == person.age &&
                Objects.equals(name, person.name);
    }

    @Override
    public int hashCode() {

        return Objects.hash(name, age);
    }

    @Override
    public String toString() {
        return "Person{" +
                "name='" + name + '\'' +
                ", age=" + age +
                '}';
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }
}

// 测试类
// == 比较的是地址值；equals默认比较地址值
public class Demo03HashSetSavePerson {
    public static void main(String[] args) {
        //创建HashSet集合存储Person
        HashSet<Person> set = new HashSet<>();
        Person p1 = new Person("小美女",18);
        Person p2 = new Person("小美女",18);
        Person p3 = new Person("小美女",19);
        System.out.println(p1.hashCode());//相同
        System.out.println(p2.hashCode());//相同

        System.out.println(p1==p2);//仍然false
        System.out.println(p1.equals(p2));//but这项是True
        set.add(p1);
        set.add(p2);
        set.add(p3);
        System.out.println(set);
    }

}
// 运行结构发现 小美女 18岁存储了一个
// 两个元素的hashCode、equals相同，对set来说，就代表是一个元素
[Person{name='小美女', age=19},  Person{name='小美女', age=18}]
```

#### 4.4 LinkedhashSet

我们知道HashSet保证元素唯一，可是元素存放进去是没有顺序的，那么我们要保证有序，怎么办呢？
在HashSet下面有一个子类`java.util.LinkedHashSet` ，它是链表和哈希表组合的一个数据存储结构。

```java
public class Test {
    public static void main(String[] args) {
        Set<String> set = new LinkedHashSet<>();
        set.add("bbb");
        set.add("aaa");
        set.add("abc");
        set.add("bbc");
        Iterator<String> it = set.iterator();
        while (it.hasNext()){
            System.out.println(it.next());
        }
    }
}
```

### 5. Collections

#### 5.1 常用功能

`java.utils.Collections` 是集合工具类，用来对集合进行操作。部分方法如下：

* `public static <T> boolean addAll(Collection<T> c, T... elements) `:往集合中添加一些元素。
* `public static void shuffle(List<?> list) `打乱顺序:打乱集合顺序。
* `public static <T> void sort(List<T> list)` :将集合中元素按照默认规则排序。
* `public static <T> void sort(List<T> list，Comparator<? super T> ) `:将集合中元素按照指定规则排序。

```java
public class Test {
    public static void main(String[] args) {
        ArrayList<Integer> list = new ArrayList<>();
        //原来写法
        //list.add(12);
        //list.add(14);
        //list.add(15);
        //list.add(1000);
        //采用工具类 完成 往集合中添加元素
        Collections.addAll(list,5,222,1,2);
        System.out.println(list);

        Collections.sort(list);
        System.out.println(list);
    }
}
[5, 222, 1, 2]
[1, 2, 5, 222]
```

sort排序采用默认的顺序，如果想要指定顺序那该怎么办呢？

* 重写对象所属的类中的`compareTo`方法。`public static <T> void sort(List<T> list)` 这个方法完成的排序，实际上要求了被排序的类型需要实现Comparable接口完成比较的功能，而`java.lang.Comparable `接口实现死板，举例说明：

  ```java
  /*
      - java.utils.Collections是集合工具类，用来对集合进行操作。部分方法如下：
          public static <T> void sort(List<T> list):将集合中元素按照默认规则排序。
  
      注意:
           sort(List<T> list)使用前提
           被排序的集合里边存储的元素,必须实现Comparable,重写接口中的方法compareTo定义排序的规则
  
      Comparable接口的排序规则:
          自己(this)-参数:升序
   */
  // 实现类
  public class Test {
      public static void main(String[] args) {
          ArrayList<Integer> list01 = new ArrayList<>();
          list01.add(1);
          list01.add(3);
          list01.add(2);
          System.out.println(list01);//[1, 3, 2]
  
          //public static <T> void sort(List<T> list):将集合中元素按照默认规则排序。
          Collections.sort(list01);//默认是升序
  
          System.out.println(list01);//[1, 2, 3]
  
          ArrayList<String> list02 = new ArrayList<>();
          list02.add("a");
          list02.add("c");
          list02.add("b");
          System.out.println(list02);//[a, c, b]
  
          Collections.sort(list02);
          System.out.println(list02);//[a, b, c]
  
          ArrayList<Person> list03 = new ArrayList<>();
          list03.add(new Person("张三",18));
          list03.add(new Person("李四",20));
          list03.add(new Person("王五",15));
          System.out.println(list03);//[Person{name='张三', age=18}, Person{name='李四', age=20}, Person{name='王五', age=15}]
  
          Collections.sort(list03);//如果不重写Person中的compareTo()方法，此处编译就会报错！！
          System.out.println(list03);
      }
  }
  
  // Person类
  public class Person implements Comparable<Person>{
      private String name;
      private int age;
  
      public Person() {
      }
  
      public Person(String name, int age) {
          this.name = name;
          this.age = age;
      }
  
      @Override
      public String toString() {
          return "Person{" +
                  "name='" + name + '\'' +
                  ", age=" + age +
                  '}';
      }
  
      public String getName() {
          return name;
      }
  
      public void setName(String name) {
          this.name = name;
      }
  
      public int getAge() {
          return age;
      }
  
      public void setAge(int age) {
          this.age = age;
      }
  
      //重写排序的规则
      @Override
      public int compareTo(Person o) {
          //return 0;//认为元素都是相同的
          //自定义比较的规则,比较两个人的年龄(this,参数Person)
          //return this.getAge() - o.getAge();//年龄升序排序
          return o.getAge() - this.getAge();//年龄降序排序
      }
  }
  
  ```

  

* 使用`public static <T> void sort(List<T> list, Comparator<? super T> ) `，`java.util.Comparator `接口实现**灵活**。

`public static <T> void sort(List<T> list, Comparator<? super T> ) `:将集合中元素按照指定规则排序。接下来讲解一下指定规则的排列。

#### 5.2 Comparator比较器

其内有方法`public int compare(String o1, String o2)` ：比较其两个参数的顺序。
两个对象比较的结果有三种：大于，等于，小于。
如果要按照升序排序， 则o1 小于o2，返回（负数），相等返回0，01大于02返回（正数） 如果要按照降序排序 则o1 小于o2，返回（正数），相等返回0，01大于02返回（负数）。

```java
/*
    - java.utils.Collections是集合工具类，用来对集合进行操作。部分方法如下：
        public static <T> void sort(List<T> list，Comparator<? super T> ):将集合中元素按照指定规则排序。

     Comparator和Comparable的区别
        Comparable:自己(this)和别人(参数)比较,自己需要实现Comparable接口,重写比较的规则compareTo方法
        Comparator:相当于找一个第三方的裁判,比较两个

    Comparator的排序规则:
        o1-o2:升序
 */
public class Test {
    public static void main(String[] args) {
        ArrayList<Integer> list01 = new ArrayList<>();
        list01.add(1);
        list01.add(3);
        list01.add(2);
        System.out.println(list01);//[1, 3, 2]

        Collections.sort(list01, new Comparator<Integer>() {
            //重写比较的规则
            @Override
            public int compare(Integer o1, Integer o2) {
                //return o1-o2;//升序
                return o2-o1;//降序
            }
        });

        System.out.println(list01);

        ArrayList<Student> list02 = new ArrayList<>();
        list02.add(new Student("a迪丽热巴",18));
        list02.add(new Student("古力娜扎",20));
        list02.add(new Student("杨幂",17));
        list02.add(new Student("b杨幂",18));
        System.out.println(list02);

        /*Collections.sort(list02, new Comparator<Student>() {
            @Override
            public int compare(Student o1, Student o2) {
                //按照年龄升序排序
                return o1.getAge()-o2.getAge();
            }
        });*/

        //扩展:了解
        Collections.sort(list02, new Comparator<Student>() {
            @Override
            public int compare(Student o1, Student o2) {
                //按照年龄升序排序
                int result =  o1.getAge()-o2.getAge();
                //如果两个人年龄相同,再使用姓名的第一个字比较
                if(result==0){
                    result =  o1.getName().charAt(0)-o2.getName().charAt(0);
                }
                return  result;
            }

        });

        System.out.println(list02);
    }
}
```

## day04 【Map、java9的of()方法】

### 1. Map接口

#### 1.1 Map双列集合与Collection单列集合的对比

* Collection 中的集合称为单列集合， Map 中的集合称为双列集合。
* 需要注意的是， Map 中的集合**不能包含重复的键**，值可以重复；每个键只能对应一个值

#### 1.2 Map的实现类

* `HashMap`：存储数据采用的哈希表结构，元素的**存取顺序不能保证一致**。由于要保证键的唯一、不重复，需要重写键的hashCode()方法、equals()方法。
* `LinkedHashMap`：HashMap下有个子类LinkedHashMap，存储数据采用的哈希表结构+链表结构。通过链表结构可以**保证元素的存取顺序一致**；通过哈希表结构可以保证的键的唯一、不重复，需要重写键的hashCode()方法、equals()方法。

Map接口中的集合**都有两个泛型变量**,在使用时，要为两个泛型变量赋予数据类型。**两个泛型变量的数**
**据类型可以相同，也可以不同**。

#### 1.3 Map接口中的常用方法

* `public V put(K key, V value) `: 把指定的键与指定的值添加到Map集合中。
  * 若指定的键(key)在集合中没有，则没有这个键对应的值，返回null，并把指定的键值添加到集合中；
  * 若指定的键(key)在集合中存在，则返回值为集合中键对应的值（该值为替换前的值），并把指定键所对应的值，替换成指定的新值。
* `public V remove(Object key) `: 把指定的键 所对应的键值对元素 在Map集合中删除，返回被删除元素的值。
* `public V get(Object key) `根据指定的键，在Map集合中获取对应的值。
* `public Set<K> keySet()` : 获取Map集合中所有的键，存储到Set集合中。
* `public Set<Map.Entry<K,V>> entrySet()` : 获取到Map集合中所有的**键值对对象**的集合(Set集合)。

```java
public class Test {
    public static void main(String[] args) {
        HashMap<String, String> map = new HashMap<>();
        map.put("黄晓明", "杨颖");
        map.put("文章", "马伊利");
        map.put("邓超", "孙俪");
        System.out.println(map);

        System.out.println(map.remove("邓超"));
        System.out.println(map);
        System.out.println(map.remove("邓超"));

        System.out.println(map.get("黄晓明"));
        System.out.println(map.get("邓超"));
    }
}
```

#### 1.4 Map集合遍历键找值的方式

```java
public class Test {
    public static void main(String[] args) {
        HashMap<String, String> map = new HashMap<>();
        map.put("胡歌", "霍建华");
        map.put("郭德纲", "于谦");
        map.put("薛之谦", "大张伟");

        Set<String> keys = map.keySet();
        for (String key:keys){
            String val = map.get(key);
            System.out.println(key+"："+val);
        }
    }
}
```

#### 1.5 Entry键值对对象

key:value这一对对象称作`Map`的一个`Entry`。`Entry` 将键值对的对应关系封装成了对象，即键值对对象。

* `public K getKey() `：获取Entry对象中的键。
* `public V getValue() `：获取Entry对象中的值。

```java
public class Test {
    public static void main(String[] args) {
        HashMap<String, String> map = new HashMap<>();
        map.put("胡歌", "霍建华");
        map.put("郭德纲", "于谦");
        map.put("薛之谦", "大张伟");

        Set<Map.Entry<String,String>> entryset = map.entrySet();
        for (Map.Entry<String,String> entry: entryset){
            String key = entry.getKey();
            String val = entry.getValue();
            System.out.println(key+":"+val);
        }
    }
}
```

#### 1.6 LinkedHashMap

`java.util.LinkedHashMap`可保证map中存放的key和取出的顺序一致。

LinkedHashMap是HashMap下面的一个子类，它是链表和哈希表组合的一个数据存储结构。

```java
public class Test {
    public static void main(String[] args) {
        LinkedHashMap<String, String> map = new LinkedHashMap<>();
        map.put("邓超", "孙俪");
        map.put("李晨", "范冰冰");
        map.put("刘德华", "朱丽倩");

        Set<Map.Entry<String, String>> entryset = map.entrySet();
        for (Map.Entry<String, String> entry: entryset){
            System.out.println(entry.getKey()+":"+entry.getValue());
        }
    }
}
```

### 2. java9的of()方法

* `of()`方法**只是Map，List，Set这三个接口的静态方法**，其父类接口和子类实现并没有这类方法，比如HashSet，ArrayList等待；
* 返回的集合是不可变的；

```java
public class Test {
    public static void main(String[] args) {
        Set<String> str1 = Set.of("a","b","c");
        //str1.add("c");//这里编译的时候不会错，但是执行的时候会报错，因为是不可变的集合
        System.out.println(str1);

        Map<String, Integer> str2 = Map.of("a",1,"b",2);
        System.out.println(str2);

        List<String> str3 = List.of("a","b");
        System.out.println(str3);
    }
}
[a, c, b]
{a=1, b=2}
[a, b]
```

## day05 【异常、线程】

### 1. 异常——Exception

#### 1.1 异常的概念

* 指的是程序在执行过程中，出现的非正常的情况，最终会导致JVM（Java虚拟机）的非正常停止。

* 在Java等面向对象的编程语言中，异常本身是一个类，产生异常就是**创建异常对象并抛出了一个异常对象**。
* 异常指的并**不是语法错误**。语法错了,编译不通过,不会产生字节码文件,根本不能运行.
* 帮助我们找到程序中的问题

#### 1.2 异常体系

异常的根类：`java.lang.Throwable`

其下有两个子类：`java.lang.Error `与`java.lang.Exception`

**平时说的异常指`java.lang.Exception`**

Throwable中常用方法：

* `public void printStackTrace()`：JVM打印异常对象,默认此方法,打印的异常信息是最全面的.

  包含了异常的类型,异常的原因,还包括异常出现的位置,在开发和调试阶段,都得使用printStackTrace。

* `public String getMessage()` :返回此 throwable 的简短描述。

  提示给用户的时候,就提示错误原因。

* `public String toString()` :返回此 throwable 的详细消息字符串。(不用)。

#### 1.3 异常分类

* 编译时期异常:checked异常。在编译时期,就会检查,如果没有处理异常,则编译失败。(如日期格式化异常)
* 运行时期异常:runtime异常。在运行时期,检查异常.在编译时期,运行异常不会编译器检测(不报错)。(如数学异常)



![image-20210227163811775](Java%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0.assets/异常的体系与分类.png)

#### 1.4 异常的产生过程解析

```java
public class ArrayTools {
    public static int getElement(int[] arr, int index){
        int element = arr[index];
        return element;
    }
}

public class Test {
    public static void main(String[] args) {
        int[] arr = {34, 12, 67};
        int num = ArrayTools.getElement(arr,4);
        System.out.println("num="+num);
        System.out.println("over");
    }
}
```



![image-20210227164334358](Java%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0.assets/异常产生过程.png)

### 2. 异常的处理

Java异常处理的五个关键字：try、catch、finally、throw、throws

#### 2.1 抛出异常throw

throw用在方法内，用来抛出一个异常对象，将这个异常对象传递到调用者处，并结束当前方法的执行。

如果产生了问题，我们就会throw将问题描述类即异常进行抛出，也就是将问题返回给该方法的调用者。
那么对于调用者来说，该怎么处理呢？一种是进行捕获处理，另一种就是继续将问题声明出去，使用throws声明处理。**抛出来异常就必须处理！！！**

```java
throw new 异常类名(参数);
throw new NullPointerException("要访问的arr数组不存在");
throw new ArrayIndexOutOfBoundsException("该索引在数组中不存在，已超出范围");
```



```java
/*
    throw关键字
    作用:
        可以使用throw关键字在指定的方法中抛出指定的异常
    使用格式:
        throw new xxxException("异常产生的原因");
    注意:
        1.throw关键字必须写在方法的内部
        2.throw关键字后边new的对象必须是Exception或者Exception的子类对象
        3.throw关键字抛出指定的异常对象,我们就必须处理这个异常对象
            throw关键字后边创建的是RuntimeException或者是 RuntimeException的子类对象,我们可以不处理,默认交给JVM处理(打印异常对象,中断程序)
            throw关键字后边创建的是编译异常(写代码的时候报错),我们就必须处理这个异常,要么throws,要么try...catch
 */
public class Demo03Throw {
    public static void main(String[] args) {
        //int[] arr = null;
        int[] arr = new int[3];
        int e = getElement(arr,3);
        System.out.println(e);
    }
    /*
        定义一个方法,获取数组指定索引处的元素
        参数:
            int[] arr
            int index
        以后(工作中)我们首先必须对方法传递过来的参数进行合法性校验
        如果参数不合法,那么我们就必须使用抛出异常的方式,告知方法的调用者,传递的参数有问题
        注意:
            NullPointerException是一个运行期异常,我们不用处理,默认交给JVM处理
            ArrayIndexOutOfBoundsException是一个运行期异常,我们不用处理,默认交给JVM处理
     */
    public static int getElement(int[] arr,int index){
        /*
            我们可以对传递过来的参数数组,进行合法性校验
            如果数组arr的值是null
            那么我们就抛出空指针异常,告知方法的调用者"传递的数组的值是null"
         */
        if(arr == null){
            throw new NullPointerException("传递的数组的值是null");
        }

        /*
            我们可以对传递过来的参数index进行合法性校验
            如果index的范围不在数组的索引范围内
            那么我们就抛出数组索引越界异常,告知方法的调用者"传递的索引超出了数组的使用范围"
         */
        if(index<0 || index>arr.length-1){
            throw new ArrayIndexOutOfBoundsException("传递的索引超出了数组的使用范围");
        }

        int ele = arr[index];
        return ele;
    }
}


```



* ArrayIndexOutOfBoundsException

```java
public class Test {
    public static void main(String[] args) {
        int[] arr = {34, 12, 67};
        int num = getElement(arr,4);
        System.out.println("num="+num);
        System.out.println("over");
    }
    public static int getElement(int[] arr, int index){

        if (index <0||index>arr.length-1){
            throw new ArrayIndexOutOfBoundsException("哥们，角标越界了~~~~");
        }
        int element = arr[index];
        return element;
    }
}
```

​		

* NullPointerException

  还记得我们学习过一个类Objects吗，曾经提到过它由一些静态的实用方法组成，这些方法是null-save（空指针安全的）或null-tolerant（容忍空指针的），那么在它的源码中，对对象为null的值进行了抛出异常操作。

  `public static <T> T requireNonNull(T obj) `:查看指定引用对象不是null。

  ```java
  public static <T> T requireNonNull(T obj) {
      if (obj == null)
          throw new NullPointerException();
      return obj;
  }
  ```

#### 2.2 声明异常throws——处理异常的第一种方式

```java
import java.io.FileNotFoundException;
import java.io.IOException;

/*
    throws关键字:异常处理的第一种方式,交给别人处理
    作用:
        当方法内部抛出异常对象的时候,那么我们就必须处理这个异常对象
        可以使用throws关键字处理异常对象,会把异常对象声明抛出给方法的调用者处理(自己不处理,给别人处理),最终交给JVM处理-->中断处理
    使用格式:在方法声明时使用
        修饰符 返回值类型 方法名(参数列表) throws AAAExcepiton,BBBExcepiton...{
            throw new AAAExcepiton("产生原因");
            throw new BBBExcepiton("产生原因");
            ...
        }
     注意:
        1.throws关键字必须写在方法声明处
        2.throws关键字后边声明的异常必须是Exception或者是Exception的子类
        3.方法内部如果抛出了多个异常对象,那么throws后边必须也声明多个异常
            如果抛出的多个异常对象有子父类关系,那么直接声明父类异常即可
        4.调用了一个声明抛出异常的方法,我们就必须的处理声明的异常
            要么继续使用throws声明抛出,交给方法的调用者处理,最终交给JVM
            要么try...catch自己处理异常
 */
public class Demo05Throws {
    /*
        FileNotFoundException extends IOException extends Excepiton
        如果抛出的多个异常对象有子父类关系,那么直接声明父类异常即可
     */
    //public static void main(String[] args) throws FileNotFoundException,IOException {
    //public static void main(String[] args) throws IOException {
    public static void main(String[] args) throws Exception {
        readFile("c:\\a.tx");

        System.out.println("后续代码");
    }

    /*
        定义一个方法,对传递的文件路径进行合法性判断
        如果路径不是"c:\\a.txt",那么我们就抛出文件找不到异常对象,告知方法的调用者
        注意:
            FileNotFoundException是编译异常,抛出了编译异常,就必须处理这个异常
            可以使用throws继续声明抛出FileNotFoundException这个异常对象,让方法的调用者处理
     */
    public static void readFile(String fileName) throws FileNotFoundException,IOException{
        if(!fileName.equals("c:\\a.txt")){
            throw new FileNotFoundException("传递的文件路径不是c:\\a.txt");
        }

        /*
            如果传递的路径,不是.txt结尾
            那么我们就抛出IO异常对象,告知方法的调用者,文件的后缀名不对

         */
        if(!fileName.endsWith(".txt")){
            throw new IOException("文件的后缀名不对");
        }

        System.out.println("路径没有问题,读取文件");
    }
}


```

#### 2.3 try... catch——处理异常的第二种方式

```java
import java.io.IOException;

/*
    try...catch:异常处理的第二种方式,自己处理异常
    格式:
        try{
            可能产生异常的代码
        }catch(定义一个异常的变量,用来接收try中抛出的异常对象){
            异常的处理逻辑,异常异常对象之后,怎么处理异常对象
            一般在工作中,会把异常的信息记录到一个日志中
        }
        ...
        catch(异常类名 变量名){

        }
    注意:
        1.try中可能会抛出多个异常对象,那么就可以使用多个catch来处理这些异常对象
        2.如果try中产生了异常,那么就会执行catch中的异常处理逻辑,执行完毕catch中的处理逻辑,继续执行try...catch之后的代码
          如果try中没有产生异常,那么就不会执行catch中异常的处理逻辑,执行完try中的代码,继续执行try...catch之后的代码
 */
public class Demo01TryCatch {
    public static void main(String[] args) {
        try{
            //可能产生异常的代码
            readFile("d:\\a.tx");
            System.out.println("资源释放");
        }catch (IOException e){//try中抛出什么异常对象,catch就定义什么异常变量,用来接收这个异常对象
            //异常的处理逻辑,异常异常对象之后,怎么处理异常对象
            //System.out.println("catch - 传递的文件后缀不是.txt");

            /*
                Throwable类中定义了3个异常处理的方法
                 String getMessage() 返回此 throwable 的简短描述。
                 String toString() 返回此 throwable 的详细消息字符串。
                 void printStackTrace()  JVM打印异常对象,默认此方法,打印的异常信息是最全面的
             */
            //System.out.println(e.getMessage());//文件的后缀名不对
            //System.out.println(e.toString());//重写Object类的toString java.io.IOException: 文件的后缀名不对
            //System.out.println(e);//java.io.IOException: 文件的后缀名不对

            /*
                java.io.IOException: 文件的后缀名不对
                    at com.itheima.demo02.Exception.Demo01TryCatch.readFile(Demo01TryCatch.java:55)
                    at com.itheima.demo02.Exception.Demo01TryCatch.main(Demo01TryCatch.java:27)
             */
            e.printStackTrace();
        }
        System.out.println("后续代码");
    }

    /*
       如果传递的路径,不是.txt结尾
       那么我们就抛出IO异常对象,告知方法的调用者,文件的后缀名不对

    */
    public static void readFile(String fileName) throws IOException {

        if(!fileName.endsWith(".txt")){
            throw new IOException("文件的后缀名不对");
        }

        System.out.println("路径没有问题,读取文件");
    }
}

```



#### 2.4 try...catch...finally

```java
import java.io.IOException;

/*
    finally代码块
     格式:
        try{
            可能产生异常的代码
        }catch(定义一个异常的变量,用来接收try中抛出的异常对象){
            异常的处理逻辑,异常异常对象之后,怎么处理异常对象
            一般在工作中,会把异常的信息记录到一个日志中
        }
        ...
        catch(异常类名 变量名){

        }finally{
            无论是否出现异常都会执行
        }
     注意:
        1.finally不能单独使用,必须和try一起使用
        2.finally一般用于资源释放(资源回收),无论程序是否出现异常,最后都要资源释放(IO)
 */
public class Demo02TryCatchFinally {
    public static void main(String[] args) {
        try {
            //可能会产生异常的代码
            readFile("c:\\a.tx");
        } catch (IOException e) {
            //异常的处理逻辑
            e.printStackTrace();
        } finally {
            //无论是否出现异常,都会执行
            System.out.println("资源释放");
        }
    }

    /*
       如果传递的路径,不是.txt结尾
       那么我们就抛出IO异常对象,告知方法的调用者,文件的后缀名不对

    */
    public static void readFile(String fileName) throws IOException {

        if(!fileName.endsWith(".txt")){
            throw new IOException("文件的后缀名不对");
        }

        System.out.println("路径没有问题,读取文件");
    }
}


```

#### 2.5 注意事项

```java
package com.itheima.demo03.Exception;

import java.util.List;

/*
    异常的注意事项
 */
public class Demo01Exception {
    public static void main(String[] args) {
        /*
            多个异常使用捕获又该如何处理呢？
            1. 多个异常分别处理。
            2. 多个异常一次捕获，多次处理。
            3. 多个异常一次捕获一次处理。
         */

        //1. 多个异常分别处理。
       /* try {
            int[] arr = {1,2,3};
            System.out.println(arr[3]);//ArrayIndexOutOfBoundsException: 3
        }catch (ArrayIndexOutOfBoundsException e){
            System.out.println(e);
        }

        try{
            List<Integer> list = List.of(1, 2, 3);
            System.out.println(list.get(3));//IndexOutOfBoundsException: Index 3 out-of-bounds for length 3
        }catch (IndexOutOfBoundsException e){
            System.out.println(e);
        }*/

        //2. 多个异常一次捕获，多次处理。
        /*try {
            int[] arr = {1,2,3};
            //System.out.println(arr[3]);//ArrayIndexOutOfBoundsException: 3
            List<Integer> list = List.of(1, 2, 3);
            System.out.println(list.get(3));//IndexOutOfBoundsException: Index 3 out-of-bounds for length 3
        }catch (ArrayIndexOutOfBoundsException e){
            System.out.println(e);
        }catch (IndexOutOfBoundsException e){
            System.out.println(e);
        }*/

        /*
            一个try多个catch注意事项:
                catch里边定义的异常变量,如果有子父类关系,那么子类的异常变量必须写在上边,否则就会报错
                ArrayIndexOutOfBoundsException extends IndexOutOfBoundsException
         */
        /*try {
            int[] arr = {1,2,3};
            //System.out.println(arr[3]);//ArrayIndexOutOfBoundsException: 3
            List<Integer> list = List.of(1, 2, 3);
            System.out.println(list.get(3));//IndexOutOfBoundsException: Index 3 out-of-bounds for length 3
        }catch (IndexOutOfBoundsException e){
            System.out.println(e);
        }catch (ArrayIndexOutOfBoundsException e){
            System.out.println(e);
        }*/

        //3. 多个异常一次捕获一次处理。
        /*try {
            int[] arr = {1,2,3};
            //System.out.println(arr[3]);//ArrayIndexOutOfBoundsException: 3
            List<Integer> list = List.of(1, 2, 3);
            System.out.println(list.get(3));//IndexOutOfBoundsException: Index 3 out-of-bounds for length 3
        }catch (Exception e){
            System.out.println(e);
        }*/

        //运行时异常（RuntimeException，和我们现在重点关注的编译器异常（用Exception表示）包含与被包含的关系）被抛出可以不处理。即不捕获也不声明抛出。
        //默认给虚拟机处理,终止程序,什么时候不抛出运行时异常了,在来继续执行程序
        int[] arr = {1,2,3};
        System.out.println(arr[3]);//ArrayIndexOutOfBoundsException: 3
        List<Integer> list = List.of(1, 2, 3);
        System.out.println(list.get(3));//IndexOutOfBoundsException: Index 3 out-of-bounds for length 3

        System.out.println("后续代码!");
    }
}

```



```java
/*
    如果finally有return语句,永远返回finally中的结果,避免该情况.
 */
public class Demo02Exception {
    public static void main(String[] args) {
        int a = getA();
        System.out.println(a);
    }

    //定义一个方法,返回变量a的值
    public static int getA(){
        int a = 10;
        try{
            return a;
        }catch (Exception e){
            System.out.println(e);
        }finally {
            //一定会执行的代码
            // 以后不要在finally中写return
            a = 100;
            return a;
        }

    }
}

```



```java
/*
    子父类的异常:
        - 如果父类抛出了多个异常,子类重写父类方法时,抛出和父类相同的异常或者是父类异常的子类或者不抛出异常。
        - 父类方法没有抛出异常，子类重写父类该方法时也不可抛出异常。此时子类产生该异常，只能捕获处理，不能声明抛出
    注意:
        父类异常时什么样,子类异常就什么样
 */
public class Fu {
    public void show01() throws NullPointerException,ClassCastException{}
    public void show02() throws IndexOutOfBoundsException{}
    public void show03() throws IndexOutOfBoundsException{}
    public void show04() throws Exception {}
}

class Zi extends Fu{
    //子类重写父类方法时,抛出和父类相同的异常
    public void show01() throws NullPointerException,ClassCastException{}
    //子类重写父类方法时,抛出父类异常的子类
    public void show02() throws ArrayIndexOutOfBoundsException{}
    //子类重写父类方法时,不抛出异常
    public void show03() {}

    /*
        父类方法没有抛出异常，子类重写父类该方法时也不可抛出异常。

     */
    //public void show04() throws Exception{}

    //此时子类产生该异常，只能捕获处理，不能声明抛出
    public void show04()  {
        try {
            throw  new Exception("编译期异常");
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}

```





### 3. 自定义异常类

```java
/*
    自定义异常类:
        java提供的异常类,不够我们使用,需要自己定义一些异常类
    格式:
        public class XXXExcepiton extends Exception | RuntimeException{
            添加一个空参数的构造方法
            添加一个带异常信息的构造方法
        }
     注意:
        1.自定义异常类一般都是以Exception结尾,说明该类是一个异常类
        2.自定义异常类,必须的继承Exception或者RuntimeException
            继承Exception:那么自定义的异常类就是一个编译期异常,如果方法内部抛出了编译期异常,就必须处理这个异常,要么throws,要么try...catch
            继承RuntimeException:那么自定义的异常类就是一个运行期异常,无需处理,交给虚拟机处理(中断处理)
 */
public class RegisterException extends /*Exception*/ RuntimeException{
    //添加一个空参数的构造方法
    public RegisterException(){
        super();
    }
    /*
        添加一个带异常信息的构造方法
        查看源码发现,所有的异常类都会有一个带异常信息的构造方法,
        方法内部会调用父类带异常信息的构造方法,
        让父类来处理这个异常信息
     */
    public RegisterException(String message){
        super(message);
    }
}
```





### 4. 多线程

#### 4.1 并发与并行

* 并发：指两个或多个事件在同一个时间段内发生。大概率是交替进行。
* 并行：指两个或多个事件在同一时刻发生（同时发生）。

#### 4.2 线程与进程

![image-20210227182716719](Java%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0.assets/进程与线程实例图解.png)

* 进程：是指一个**内存中运行**的应用程序，每个进程都有一个独立的内存空间，一个应用程序可以同时运行多个进程；进程也是**程序的一次执行过程**，是系统运行程序的基本单位；**系统运行一个程序即是一个进程从创建、运行到消亡的过程**。

* 线程：线程是**进程中的一个执行单元**，负责当前进程中程序的执行，一个进程中至少有一个线程。一个进程中是可以有多个线程的，这个应用程序也可以称之为多线程程序。

  简而言之：一个程序运行后至少有一个进程，一个进程中可以包含多个线程

**线程调度**:

* 分时调度

  所有线程轮流使用 CPU 的使用权，平均分配每个线程占用 CPU 的时间。

* 抢占式调度

  优先让**优先级高**的线程使用 CPU，如果线程的优先级相同，那么会随机选择一个(线程随机性)，**Java使用的为抢占式调度**。电脑可以设置线程的优先级。

其实，多线程程序并不能提高程序的运行速度，但能够提高程序运行效率，让CPU的使用率更高。

#### 4.3 创建线程方式一

![image-20210227183808071](Java%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0.assets/主线程.png)

```java
/*
    主线程:执行主(main)方法的线程

    单线程程序:java程序中只有一个线程
    执行从main方法开始,从上到下依次执行

    JVM执行main方法,main方法会进入到栈内存
    JVM会找操作系统开辟一条main方法通向cpu的执行路径
    cpu就可以通过这个路径来执行main方法
    而这个路径有一个名字,叫main(主)线程
 */
public class Demo01MainThread {
    public static void main(String[] args) {
        Person p1 = new Person("小强");
        p1.run();
        System.out.println(0/0);//ArithmeticException: / by zero
        // 上行代码报异常，导致主线程结束，下面的代码不能运行，这就是单线程的弊端
        Person p2 = new Person("旺财");
        p2.run();
    }
}

public class Person {
    private String name;

    public void run(){
        //定义循环,执行20次
        for(int i=0; i<20; i++){
            System.out.println(name+"-->"+i);
        }
    }

    public Person() {
    }

    public Person(String name) {
        this.name = name;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }
}

```

Java使用`java.lang.Thread `类代表线程，所有的线程对象都必须是Thread类或其子类的实例。

```java
/*
    创建多线程程序的第一种方式:创建Thread类的子类
    java.lang.Thread类:是描述线程的类,我们想要实现多线程程序,就必须继承Thread类

    实现步骤:
        1.创建一个Thread类的子类
        2.在Thread类的子类中重写Thread类中的run方法,设置线程任务(开启线程要做什么?)
        3.创建Thread类的子类对象
        4.调用Thread类中的方法start方法,开启新的线程,执行run方法
             void start() 使该线程开始执行；Java 虚拟机调用该线程的 run 方法。
             结果是两个线程并发地运行；当前线程（main线程）和另一个线程（创建的新线程,执行其 run 方法）。
             多次启动一个线程是非法的。特别是当线程已经结束执行后，不能再重新启动。
    java程序属于抢占式调度,那个线程的优先级高,那个线程优先执行;同一个优先级,随机选择一个执行
 */
public class Demo01Thread {
    public static void main(String[] args) {
        //3.创建Thread类的子类对象
        MyThread mt = new MyThread();
        //4.调用Thread类中的方法start方法,开启新的线程,执行run方法
        mt.start();

        for (int i = 0; i <20 ; i++) {
            System.out.println("main:"+i);
        }
    }
}

//1.创建一个Thread类的子类
public class MyThread extends Thread{
    //2.在Thread类的子类中重写Thread类中的run方法,设置线程任务(开启线程要做什么?)
    @Override
    public void run() {
        for (int i = 0; i <20 ; i++) {
            System.out.println("run:"+i);
        }
    }
}
```

## day06 【线程、同步】

### 1. 多线程

#### 1.1 多线程的原理

对应的流程图：

![image-20210227210338730](Java%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0.assets/多线程随机性打印.png)

对应的内存图：

![image-20210227210917297](Java%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0.assets/多线程内存图解.png)

```java
/*
    线程的名称:
        主线程: main
        新线程: Thread-0,Thread-1,Thread-2
 */
public class Demo01GetThreadName {
    public static void main(String[] args) {
        //创建Thread类的子类对象
        MyThread mt = new MyThread();
        //调用start方法,开启新线程,执行run方法
        mt.start();

        new MyThread().start();
        new MyThread().start();

        //链式编程
        System.out.println(Thread.currentThread().getName());
    }
}

/*
    获取线程的名称:
        1.使用Thread类中的方法getName()
            String getName() 返回该线程的名称。
        2.可以先获取到当前正在执行的线程,使用线程中的方法getName()获取线程的名称
            static Thread currentThread() 返回对当前正在执行的线程对象的引用。
 */
// 定义一个Thread类的子类
public class MyThread extends Thread{
    //重写Thread类中的run方法,设置线程任务
    @Override
    public void run() {
        //获取线程名称
        //String name = getName();
        //System.out.println(name);

        //Thread t = Thread.currentThread();
        //System.out.println(t);//Thread[Thread-0,5,main]
        //String name = t.getName();
        //System.out.println(name);

        //链式编程
        System.out.println(Thread.currentThread().getName());
    }
}
```



#### 1. 2 Thread类

**构造方法：**

* `public Thread() `:分配一个新的线程对象。
* `public Thread(String name) `:分配一个指定名字的新的线程对象。
* `public Thread(Runnable target)` :分配一个带有指定目标新的线程对象。
* `public Thread(Runnable target,String name)` :分配一个带有指定目标新的线程对象并指定名字。

**常用方法：**

* `public String getName()` :获取当前线程名称。
* `public void start() `:导致此线程开始执行; Java虚拟机调用此线程的run方法。
* `public void run() `:此线程要执行的任务在此处定义代码。
* `public static void sleep(long millis) `:使当前正在执行的线程以指定的毫秒数暂停（暂时停止执行）。
* `public static Thread currentThread()` :返回对当前正在执行的线程对象的引用。

创建线程的方式总共有两种，一种是**继承Thread类方式**，一种是**实现Runnable接口方式【尽量使用该方式】**，方式一我们上一天已经完成，接下来讲解方式二实现的方式。

#### 1.3 创建线程方式二

`java.lang.Runnable`也是很常见的一种方式，只需要重写run方法。

```java
/*
    创建多线程程序的第二种方式:实现Runnable接口
    java.lang.Runnable
        Runnable 接口应该由那些打算通过某一线程执行其实例的类来实现。类必须定义一个称为 run 的无参数方法。
    java.lang.Thread类的构造方法
        Thread(Runnable target) 分配新的 Thread 对象。
        Thread(Runnable target, String name) 分配新的 Thread 对象。

    实现步骤:
        1.创建一个Runnable接口的实现类
        2.在实现类中重写Runnable接口的run方法,设置线程任务
        3.创建一个Runnable接口的实现类对象
        4.创建Thread类对象,构造方法中传递Runnable接口的实现类对象
        5.调用Thread类中的start方法,开启新的线程执行run方法

    实现Runnable接口创建多线程程序的好处:
        1.避免了单继承的局限性
            一个类只能继承一个类(一个人只能有一个亲爹),类继承了Thread类就不能继承其他的类
            实现了Runnable接口,还可以继承其他的类,实现其他的接口
        2.增强了程序的扩展性,降低了程序的耦合性(解耦)
            实现Runnable接口的方式,把设置线程任务和开启新线程进行了分离(解耦)
            实现类中,重写了run方法:用来设置线程任务
            创建Thread类对象,调用start方法:用来开启新线程
 */
public class Demo01Runnable {
    public static void main(String[] args) {
        //3.创建一个Runnable接口的实现类对象
        RunnableImpl run = new RunnableImpl();
        //4.创建Thread类对象,构造方法中传递Runnable接口的实现类对象
        //Thread t = new Thread(run);//打印线程名称
        Thread t = new Thread(new RunnableImpl2());//打印HelloWorld
        //5.调用Thread类中的start方法,开启新的线程执行run方法
        t.start();

        for (int i = 0; i <20 ; i++) {
            System.out.println(Thread.currentThread().getName()+"-->"+i);
        }
    }
}


//1.创建一个Runnable接口的实现类
public class RunnableImpl implements Runnable{
    //2.在实现类中重写Runnable接口的run方法,设置线程任务
    @Override
    public void run() {
        for (int i = 0; i <20 ; i++) {
            System.out.println(Thread.currentThread().getName()+"-->"+i);
        }
    }
}

//1.创建一个Runnable接口的实现类
public class RunnableImpl2 implements Runnable{
    //2.在实现类中重写Runnable接口的run方法,设置线程任务
    @Override
    public void run() {
        for (int i = 0; i <20 ; i++) {
            System.out.println("HelloWorld"+i);
        }
    }
}
```

#### 1.4 Thread和Runnable的区别

见上面代码内的说明

#### 1.5 匿名内部类实现多线程

```java
/*
    匿名内部类方式实现线程的创建

    匿名:没有名字
    内部类:写在其他类内部的类

    匿名内部类作用:简化代码
        把子类继承父类,重写父类的方法,创建子类对象合一步完成
        把实现类实现类接口,重写接口中的方法,创建实现类对象合成一步完成
    匿名内部类的最终产物:子类/实现类对象,而这个类没有名字

    格式:
        new 父类/接口(){
            重复父类/接口中的方法
        };
 */
public class Demo01InnerClassThread {
    public static void main(String[] args) {
        //线程的父类是Thread
        // new MyThread().start();
        new Thread(){
            //重写run方法,设置线程任务
            @Override
            public void run() {
                for (int i = 0; i <20 ; i++) {
                    System.out.println(Thread.currentThread().getName()+"-->"+"黑马");
                }
            }
        }.start();

        //线程的接口Runnable
        //Runnable r = new RunnableImpl();//多态
        Runnable r = new Runnable(){
            //重写run方法,设置线程任务
            @Override
            public void run() {
                for (int i = 0; i <20 ; i++) {
                    System.out.println(Thread.currentThread().getName()+"-->"+"程序员");
                }
            }
        };
        new Thread(r).start();

        //简化接口的方式
        new Thread(new Runnable(){
            //重写run方法,设置线程任务
            @Override
            public void run() {
                for (int i = 0; i <20 ; i++) {
                    System.out.println(Thread.currentThread().getName()+"-->"+"传智播客");
                }
            }
        }).start();
    }
}
```

### 2. 线程安全

举例：

```java
/*
    模拟卖票案例
    创建3个线程,同时开启,对共享的票进行出售
 */
public class Demo01Ticket {
    public static void main(String[] args) {
        //创建Runnable接口的实现类对象
        RunnableImpl run = new RunnableImpl();
        //创建Thread类对象,构造方法中传递Runnable接口的实现类对象
        Thread t0 = new Thread(run);
        Thread t1 = new Thread(run);
        Thread t2 = new Thread(run);
        //调用start方法开启多线程
        t0.start();
        t1.start();
        t2.start();
    }
}

/*
    实现卖票案例
 */
public class RunnableImpl implements Runnable{
    //定义一个多个线程共享的票源
    private  int ticket = 100;


    //设置线程任务:卖票
    @Override
    public void run() {
        //使用死循环,让卖票操作重复执行
        while(true){
            //先判断票是否存在
            if(ticket>0){
                //提高安全问题出现的概率,让程序睡眠
                try {
                    Thread.sleep(10);
                } catch (InterruptedException e) {
                    e.printStackTrace();
                }

                //票存在,卖票 ticket--
                System.out.println(Thread.currentThread().getName()+"-->正在卖第"+ticket+"张票");
                ticket--;
            }
        }
    }
}
```

上述代码的运行结果、线程安全问题产生的原理以及解决思路：

![image-20210227224033983](Java%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0.assets/线程安全问题产生的原理.png)

* 当我们使用多个线程访问同一资源的时候，且多个线程中对资源有写的操作，就容易出现线程安全问题。
* 要解决上述多线程并发访问一个资源的安全性问题:也就是解决重复票与不存在票问题，Java中提供了同步机制(synchronized)来解决。

* 有三种方式完成同步操作：
  * 同步代码块。
  * 同步方法。
  * 锁机制。

#### 2.1 线程同步的方式一：同步代码块

```java
/*
    卖票案例出现了线程安全问题
    卖出了不存在的票和重复的票

    解决线程安全问题的一种方案:使用同步代码块
    格式:
        synchronized(锁对象){
            可能会出现线程安全问题的代码(访问了共享数据的代码)
        }

    注意:
        1.通过代码块中的锁对象,可以使用任意的对象
        2.但是必须保证多个线程使用的锁对象是同一个
        3.锁对象作用:
            把同步代码块锁住,只让一个线程在同步代码块中执行
 */
public class RunnableImpl implements Runnable{
    //定义一个多个线程共享的票源
    private  int ticket = 100;

    //创建一个锁对象
    Object obj = new Object();

    //设置线程任务:卖票
    @Override
    public void run() {
        //使用死循环,让卖票操作重复执行
        while(true){
           //同步代码块
            synchronized (obj){
                //先判断票是否存在
                if(ticket>0){
                    //提高安全问题出现的概率,让程序睡眠
                    try {
                        Thread.sleep(10);
                    } catch (InterruptedException e) {
                        e.printStackTrace();
                    }

                    //票存在,卖票 ticket--
                    System.out.println(Thread.currentThread().getName()+"-->正在卖第"+ticket+"张票");
                    ticket--;
                }
            }
        }
    }
}

/*
    模拟卖票案例
    创建3个线程,同时开启,对共享的票进行出售
 */
public class Demo01Ticket {
    public static void main(String[] args) {
        //创建Runnable接口的实现类对象
        RunnableImpl run = new RunnableImpl();
        //创建Thread类对象,构造方法中传递Runnable接口的实现类对象
        Thread t0 = new Thread(run);
        Thread t1 = new Thread(run);
        Thread t2 = new Thread(run);
        //调用start方法开启多线程
        t0.start();
        t1.start();
        t2.start();
    }
}
```

同步的原理：

![image-20210227225003741](Java%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0.assets/同步的原理.png)



#### 2.2 线程同步的方式二：使用定义的同步方法

普通方法 和 静态的同步方法【了解】

```java
/*
    卖票案例出现了线程安全问题
    卖出了不存在的票和重复的票

    解决线程安全问题的二种方案:使用同步方法
    使用步骤:
        1.把访问了共享数据的代码抽取出来,放到一个方法中
        2.在方法上添加synchronized修饰符

    格式:定义方法的格式
    修饰符 synchronized 返回值类型 方法名(参数列表){
        可能会出现线程安全问题的代码(访问了共享数据的代码)
    }
 */
public class RunnableImpl implements Runnable{
    //定义一个多个线程共享的票源
    private static int ticket = 100;


    //设置线程任务:卖票
    @Override
    public void run() {
        System.out.println("this:"+this);//this:com.itheima.demo08.Synchronized.RunnableImpl@58ceff1
        //使用死循环,让卖票操作重复执行
        while(true){
            payTicketStatic();
        }
    }

    /*
        静态的同步方法
        锁对象是谁?
        不能是this
        this是创建对象之后产生的,静态方法优先于对象
        静态方法的锁对象是本类的class属性-->class文件对象(反射)
     */
    public static /*synchronized*/ void payTicketStatic(){
        synchronized (RunnableImpl.class){
            //先判断票是否存在
            if(ticket>0){
                //提高安全问题出现的概率,让程序睡眠
                try {
                    Thread.sleep(10);
                } catch (InterruptedException e) {
                    e.printStackTrace();
                }

                //票存在,卖票 ticket--
                System.out.println(Thread.currentThread().getName()+"-->正在卖第"+ticket+"张票");
                ticket--;
            }
        }

    }

    /*
        定义一个同步方法
        同步方法也会把方法内部的代码锁住
        只让一个线程执行
        同步方法的锁对象是谁?
        就是实现类对象 new RunnableImpl()
        也是就是this
     */
    public /*synchronized*/ void payTicket(){
        synchronized (this){
            //先判断票是否存在
            if(ticket>0){
                //提高安全问题出现的概率,让程序睡眠
                try {
                    Thread.sleep(10);
                } catch (InterruptedException e) {
                    e.printStackTrace();
                }

                //票存在,卖票 ticket--
                System.out.println(Thread.currentThread().getName()+"-->正在卖第"+ticket+"张票");
                ticket--;
            }
        }

    }
}

/*
    模拟卖票案例
    创建3个线程,同时开启,对共享的票进行出售
 */
public class Demo01Ticket {
    public static void main(String[] args) {
        //创建Runnable接口的实现类对象
        RunnableImpl run = new RunnableImpl();
        System.out.println("run:"+run);//run:com.itheima.demo08.Synchronized.RunnableImpl@58ceff1
        //创建Thread类对象,构造方法中传递Runnable接口的实现类对象
        Thread t0 = new Thread(run);
        Thread t1 = new Thread(run);
        Thread t2 = new Thread(run);
        //调用start方法开启多线程
        t0.start();
        t1.start();
        t2.start();
    }
}
```



#### 2.3 线程同步的方式三：锁机制

```java
/*
    卖票案例出现了线程安全问题
    卖出了不存在的票和重复的票

    解决线程安全问题的三种方案:使用Lock锁
    java.util.concurrent.locks.Lock接口
    Lock 实现提供了比使用 synchronized 方法和语句可获得的更广泛的锁定操作。
    Lock接口中的方法:
        void lock()获取锁。
        void unlock()  释放锁。
    java.util.concurrent.locks.ReentrantLock implements Lock接口


    使用步骤:
        1.在成员位置创建一个ReentrantLock对象
        2.在可能会出现安全问题的代码前调用Lock接口中的方法lock获取锁
        3.在可能会出现安全问题的代码后调用Lock接口中的方法unlock释放锁
 */
public class RunnableImpl implements Runnable{
    //定义一个多个线程共享的票源
    private  int ticket = 100;

    //1.在成员位置创建一个ReentrantLock对象
    Lock l = new ReentrantLock();

    //设置线程任务:卖票
    @Override
    public void run() {
        //使用死循环,让卖票操作重复执行
        while(true){
            //2.在可能会出现安全问题的代码前调用Lock接口中的方法lock获取锁
            l.lock();

            //先判断票是否存在
            if(ticket>0){
                //提高安全问题出现的概率,让程序睡眠
                try {
                    Thread.sleep(10);
                    //票存在,卖票 ticket--
                    System.out.println(Thread.currentThread().getName()+"-->正在卖第"+ticket+"张票");
                    ticket--;
                } catch (InterruptedException e) {
                    e.printStackTrace();
                }finally {
                    //3.在可能会出现安全问题的代码后调用Lock接口中的方法unlock释放锁
                    l.unlock();//无论程序是否异常,都会把锁释放
                }
            }
        }
    }

    /*//设置线程任务:卖票
    @Override
    public void run() {
        //使用死循环,让卖票操作重复执行
        while(true){
           //2.在可能会出现安全问题的代码前调用Lock接口中的方法lock获取锁
           l.lock();

            //先判断票是否存在
            if(ticket>0){
                //提高安全问题出现的概率,让程序睡眠
                try {
                    Thread.sleep(10);
                } catch (InterruptedException e) {
                    e.printStackTrace();
                }

                //票存在,卖票 ticket--
                System.out.println(Thread.currentThread().getName()+"-->正在卖第"+ticket+"张票");
                ticket--;
            }

            //3.在可能会出现安全问题的代码后调用Lock接口中的方法unlock释放锁
            l.unlock();
        }
    }*/
}


/*
    模拟卖票案例
    创建3个线程,同时开启,对共享的票进行出售
 */
public class Demo01Ticket {
    public static void main(String[] args) {
        //创建Runnable接口的实现类对象
        RunnableImpl run = new RunnableImpl();
        //创建Thread类对象,构造方法中传递Runnable接口的实现类对象
        Thread t0 = new Thread(run);
        Thread t1 = new Thread(run);
        Thread t2 = new Thread(run);
        //调用start方法开启多线程
        t0.start();
        t1.start();
        t2.start();
    }
}

```





### 3. 线程状态

#### 3.1 线程状态的概念

![image-20210228094911426](Java%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0.assets/线程的六种状态图.png)

#### 3.2 timed waiting（计时等待状态）

#### 3.3 blocked（锁阻塞状态）

#### 3.4 Wating（无限等待）

![image-20210228095415545](Java%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0.assets/等待唤醒案例图解分析.png)

当多个线程协作时，比如A，B线程，如果A线程在Runnable（可运行）状态中调用了wait()方法那么A线程就进入了Waiting（无限等待）状态，同时失去了同步锁。假如这个时候B线程获取到了同步锁，在运行状态中调用了notify()方法，那么就会将无限等待的A线程唤醒。注意是唤醒，如果获取到锁对象，那么A线程唤醒后就进入Runnable（可运行）状态；如果没有获取锁对象，那么就进入到Blocked（锁阻塞状态）。

```java
/*
    等待唤醒案例:线程之间的通信
        创建一个顾客线程(消费者):告知老板要的包子的种类和数量,调用wait方法,放弃cpu的执行,进入到WAITING状态(无限等待)
        创建一个老板线程(生产者):花了5秒做包子,做好包子之后,调用notify方法,唤醒顾客吃包子

    注意:
        顾客和老板线程必须使用同步代码块包裹起来,保证等待和唤醒只能有一个在执行
        同步使用的锁对象必须保证唯一
        只有锁对象才能调用wait和notify方法

    Obejct类中的方法
    void wait()
          在其他线程调用此对象的 notify() 方法或 notifyAll() 方法前，导致当前线程等待。
    void notify()
          唤醒在此对象监视器上等待的单个线程。
          会继续执行wait方法之后的代码
 */
public class Demo01WaitAndNotify {
    public static void main(String[] args) {
        //创建锁对象,保证唯一
        Object obj = new Object();
        // 创建一个顾客线程(消费者)
        new Thread(){
            @Override
            public void run() {
               //一直等着买包子
               while(true){
                   //保证等待和唤醒的线程只能有一个执行,需要使用同步技术
                   synchronized (obj){
                       System.out.println("告知老板要的包子的种类和数量");
                       //调用wait方法,放弃cpu的执行,进入到WAITING状态(无限等待)
                       try {
                           obj.wait();
                       } catch (InterruptedException e) {
                           e.printStackTrace();
                       }
                       //唤醒之后执行的代码
                       System.out.println("包子已经做好了,开吃!");
                       System.out.println("---------------------------------------");
                   }
               }
            }
        }.start();

        //创建一个老板线程(生产者)
        new Thread(){
            @Override
            public void run() {
                //一直做包子
                while (true){
                    //花了5秒做包子
                    try {
                        Thread.sleep(5000);//花5秒钟做包子
                    } catch (InterruptedException e) {
                        e.printStackTrace();
                    }

                    //保证等待和唤醒的线程只能有一个执行,需要使用同步技术
                    synchronized (obj){
                        System.out.println("老板5秒钟之后做好包子,告知顾客,可以吃包子了");
                        //做好包子之后,调用notify方法,唤醒顾客吃包子
                        obj.notify();
                    }
                }
            }
        }.start();
    }
}

```

增加 计时等待和唤醒多个线程notifyAll()

```java
/*
    进入到TimeWaiting(计时等待)有两种方式
    1.使用sleep(long m)方法,在毫秒值结束之后,线程睡醒进入到Runnable/Blocked状态
    2.使用wait(long m)方法,wait方法如果在毫秒值结束之后,还没有被notify唤醒,就会自动醒来,线程睡醒进入到Runnable/Blocked状态

    唤醒的方法:
         void notify() 唤醒在此对象监视器上等待的单个线程。如果有多个线程等待，那么随机唤醒一个线程。
         void notifyAll() 唤醒在此对象监视器上等待的所有线程。
 */
public class Demo02WaitAndNotify {
    public static void main(String[] args) {
        //创建锁对象,保证唯一
        Object obj = new Object();
        // 创建一个顾客线程(消费者)
        new Thread(){
            @Override
            public void run() {
                //一直等着买包子
                while(true){
                    //保证等待和唤醒的线程只能有一个执行,需要使用同步技术
                    synchronized (obj){
                        System.out.println("顾客1告知老板要的包子的种类和数量");
                        //调用wait方法,放弃cpu的执行,进入到WAITING状态(无限等待)
                        try {
                            obj.wait();
                        } catch (InterruptedException e) {
                            e.printStackTrace();
                        }
                        //唤醒之后执行的代码
                        System.out.println("包子已经做好了,顾客1开吃!");
                        System.out.println("---------------------------------------");
                    }
                }
            }
        }.start();

        // 创建一个顾客线程(消费者)
        new Thread(){
            @Override
            public void run() {
                //一直等着买包子
                while(true){
                    //保证等待和唤醒的线程只能有一个执行,需要使用同步技术
                    synchronized (obj){
                        System.out.println("顾客2告知老板要的包子的种类和数量");
                        //调用wait方法,放弃cpu的执行,进入到WAITING状态(无限等待)
                        try {
                            obj.wait();
                        } catch (InterruptedException e) {
                            e.printStackTrace();
                        }
                        //唤醒之后执行的代码
                        System.out.println("包子已经做好了,顾客2开吃!");
                        System.out.println("---------------------------------------");
                    }
                }
            }
        }.start();

        //创建一个老板线程(生产者)
        new Thread(){
            @Override
            public void run() {
                //一直做包子
                while (true){
                    //花了5秒做包子
                    try {
                        Thread.sleep(5000);//花5秒钟做包子
                    } catch (InterruptedException e) {
                        e.printStackTrace();
                    }

                    //保证等待和唤醒的线程只能有一个执行,需要使用同步技术
                    synchronized (obj){
                        System.out.println("老板5秒钟之后做好包子,告知顾客,可以吃包子了");
                        //做好包子之后,调用notify方法,唤醒顾客吃包子
                        //obj.notify();//如果有多个等待线程,随机唤醒一个
                        obj.notifyAll();//唤醒所有等待的线程
                    }
                }
            }
        }.start();
    }
}
```

#### 3.5 等待唤醒机制

就是在一个线程进行了规定操作后，就进入等待状态（wait()）， 等待其他线程执行完他们的指定代码过后 再将其唤醒（notify()）;在有多个线程进行等待时， 如果需要，可以使用 notifyAll()来唤醒所有的等待线程。wait/notify 就是线程间的一种协作机制。

如果能获取锁，线程就从 WAITING 状态变成 RUNNABLE 状态；
否则，从 wait set 出来，又进入 entry set，线程就从 WAITING 状态又变成 BLOCKED 状态

调用wait和notify方法需要注意的细节：
* wait方法与notify方法必须要由同一个锁对象调用。因为：对应的锁对象可以通过notify唤醒使用同一个锁对象调用的wait方法后的线程。

* wait方法与notify方法是属于Object类的方法的。因为：锁对象可以是任意对象，而任意对象的所属类都是继承了Object类的。

* wait方法与notify方法必须要在同步代码块或者是同步函数中使用。因为：必须要通过锁对象调用这2个方法。

 实例用上代码即可

## day07【线程池、Lambda表达式】

### 1. 线程池

#### 1.1 线程池的概念

频繁创建线程和销毁线程需要时间，有没有一种办法使得线程可以复用，就是执行完一个任务，并不被销毁，而是可以继续执行其他的任务？

线程池：其实就是一个容纳多个线程的容器，其中的线程可以反复使用，省去了频繁创建线程对象的操作，无需反复创建线程而消耗过多资源。

![image-20210228110755832](Java%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0.assets/线程池.png)

合理利用线程池能够带来三个好处：
* 降低资源消耗。减少了创建和销毁线程的次数，每个工作线程都可以被重复利用，可执行多个任务。

* 提高响应速度。当任务到达时，任务可以不需要的等到线程创建就能立即执行。

* 提高线程的可管理性。可以根据系统的承受能力，调整线程池中工作线线程的数目，防止因为消耗过多的内存，而把服务器累趴下(每个线程需要大约1MB内存，线程开的越多，消耗的内存也就越大，最后死机)。

#### 1.2 线程池的使用

Java里面线程池的顶级接口是`java.util.concurrent.Executor` ，但是严格意义上讲Executor 并不是一个线程池，而只是一个执行线程的工具。真正的线程池接口是`java.util.concurrent.ExecutorService `。



```java
/*
    线程池:JDK1.5之后提供的
    java.util.concurrent.Executors:线程池的工厂类,用来生成线程池
    Executors类中的静态方法:
        static ExecutorService newFixedThreadPool(int nThreads) 创建一个可重用固定线程数的线程池
        参数:
            int nThreads:创建线程池中包含的线程数量
        返回值:
            ExecutorService接口,返回的是ExecutorService接口的实现类对象,我们可以使用ExecutorService接口接收(面向接口编程)
    java.util.concurrent.ExecutorService:线程池接口
        用来从线程池中获取线程,调用start方法,执行线程任务
            submit(Runnable task) 提交一个 Runnable 任务用于执行
        关闭/销毁线程池的方法
            void shutdown()
    线程池的使用步骤:
        1.使用线程池的工厂类Executors里边提供的静态方法newFixedThreadPool生产一个指定线程数量的线程池
        2.创建一个类,实现Runnable接口,重写run方法,设置线程任务
        3.调用ExecutorService中的方法submit,传递线程任务(实现类),开启线程,执行run方法
        4.调用ExecutorService中的方法shutdown销毁线程池(不建议执行)
 */
public class Demo01ThreadPool {
    public static void main(String[] args) {
        //1.使用线程池的工厂类Executors里边提供的静态方法newFixedThreadPool生产一个指定线程数量的线程池
        ExecutorService es = Executors.newFixedThreadPool(2);
        //3.调用ExecutorService中的方法submit,传递线程任务(实现类),开启线程,执行run方法
        es.submit(new RunnableImpl());//pool-1-thread-1创建了一个新的线程执行
        //线程池会一直开启,使用完了线程,会自动把线程归还给线程池,线程可以继续使用
        es.submit(new RunnableImpl());//pool-1-thread-1创建了一个新的线程执行
        es.submit(new RunnableImpl());//pool-1-thread-2创建了一个新的线程执行

        //4.调用ExecutorService中的方法shutdown销毁线程池(不建议执行)
        es.shutdown();

        es.submit(new RunnableImpl());//抛异常,线程池都没有了,就不能获取线程了
    }

}
/*
    2.创建一个类,实现Runnable接口,重写run方法,设置线程任务
 */
public class RunnableImpl implements Runnable{
    @Override
    public void run() {
        System.out.println(Thread.currentThread().getName()+"创建了一个新的线程执行");
    }
}
```

### 2. Lambda表达式

使用前提：

* 使用Lambda必须具有接口，且要求接口中有且仅有一个抽象方法。
  无论是JDK内置的Runnable 、Comparator 接口还是自定义的接口，只有当接口中的抽象方法存在且唯一
  时，才可以使用Lambda。

* 使用Lambda必须具有上下文推断。
  也就是方法的参数或局部变量类型必须为Lambda对应的接口类型，才能使用Lambda作为该接口的实例。

  备注：有且仅有一个抽象方法的接口，称为“函数式接口”。



```java
/*
    Lambda表达式的标准格式:
        由三部分组成:
            a.一些参数
            b.一个箭头
            c.一段代码
        格式:
            (参数列表) -> {一些重写方法的代码};
        解释说明格式:
            ():接口中抽象方法的参数列表,没有参数,就空着;有参数就写出参数,多个参数使用逗号分隔
            ->:传递的意思,把参数传递给方法体{}
            {}:重写接口的抽象方法的方法体
 */
public class Demo02Lambda {
    public static void main(String[] args) {
        //使用匿名内部类的方式,实现多线程
        new Thread(new Runnable(){
            @Override
            public void run() {
                System.out.println(Thread.currentThread().getName()+" 新线程创建了");
            }
        }).start();

        //使用Lambda表达式,实现多线程
        new Thread(()->{
                System.out.println(Thread.currentThread().getName()+" 新线程创建了");
            }
        ).start();

        //优化省略Lambda
        new Thread(()->System.out.println(Thread.currentThread().getName()+" 新线程创建了")).start();
    }
}


```

**案例：**

* 无参无返回

  ```java
  /*
      需求:
          给定一个厨子Cook接口，内含唯一的抽象方法makeFood，且无参数、无返回值。
          使用Lambda的标准格式调用invokeCook方法，打印输出“吃饭啦！”字样
   */
  public class Demo01Cook {
      public static void main(String[] args) {
          //调用invokeCook方法,参数是Cook接口,传递Cook接口的匿名内部类对象
          invokeCook(new Cook() {
              @Override
              public void makeFood() {
                  System.out.println("吃饭了");
              }
          });
  
          //使用Lambda表达式,简化匿名内部类的书写
          invokeCook(()->{
              System.out.println("吃饭了");
          });
  
          //优化省略Lambda
          invokeCook(()-> System.out.println("吃饭了"));
      }
  
      //定义一个方法,参数传递Cook接口,方法内部调用Cook接口中的方法makeFood
      public static void invokeCook(Cook cook){
          cook.makeFood();
      }
  }
  
  /*
      定一个厨子Cook接口，内含唯一的抽象方法makeFood
   */
  public interface Cook {
      //定义无参数无返回值的方法makeFood
      public abstract void makeFood();
  }
  ```

  

* 有参有返回

  ```java
  /*
      Lambda表达式有参数有返回值的练习
      需求:
          使用数组存储多个Person对象
          对数组中的Person对象使用Arrays的sort方法通过年龄进行升序排序
   */
  public class Demo01Arrays {
      public static void main(String[] args) {
          //使用数组存储多个Person对象
          Person[] arr = {
                  new Person("柳岩",38),
                  new Person("迪丽热巴",18),
                  new Person("古力娜扎",19)
          };
  
          //对数组中的Person对象使用Arrays的sort方法通过年龄进行升序(前边-后边)排序
          /*Arrays.sort(arr, new Comparator<Person>() {
              @Override
              public int compare(Person o1, Person o2) {
                  return o1.getAge()-o2.getAge();
              }
          });*/
  
          //使用Lambda表达式,简化匿名内部类
          Arrays.sort(arr,(Person o1, Person o2)->{
              return o1.getAge()-o2.getAge();
          });
  
          //优化省略Lambda
          Arrays.sort(arr,(o1, o2)->o1.getAge()-o2.getAge());
  
          //遍历数组
          for (Person p : arr) {
              System.out.println(p);
          }
      }
  }
  
  public class Person {
      private String name;
      private int age;
  
      public Person() {
      }
  
      public Person(String name, int age) {
          this.name = name;
          this.age = age;
      }
  
      @Override
      public String toString() {
          return "Person{" +
                  "name='" + name + '\'' +
                  ", age=" + age +
                  '}';
      }
  
      public String getName() {
          return name;
      }
  
      public void setName(String name) {
          this.name = name;
      }
  
      public int getAge() {
          return age;
      }
  
      public void setAge(int age) {
          this.age = age;
      }
  }
  
  ```

  

lamda表达式是如何省略的：

```java
/*
    Lambda表达式:是可推导,可以省略
    凡是根据上下文推导出来的内容,都可以省略书写
    可以省略的内容:
        1.(参数列表):括号中参数列表的数据类型,可以省略不写
        2.(参数列表):括号中的参数如果只有一个,那么类型和()都可以省略
        3.{一些代码}:如果{}中的代码只有一行,无论是否有返回值,都可以省略({},return,分号)
            注意:要省略{},return,分号必须一起省略
 */
public class Demo01ArrayList {
    public static void main(String[] args) {
        //JDK1.7版本之前,创建集合对象必须把前后的泛型都写上
        ArrayList<String> list01 = new ArrayList<String>();

        //JDK1.7版本之后,=号后边的泛型可以省略,后边的泛型可以根据前边的泛型推导出来
        ArrayList<String> list02 = new ArrayList<>();
    }
}
```

## day08【File类、递归】

### 1. File类

#### 1.1 概述

`java.io.File` 类是文件和目录路径名的抽象表示，主要用于文件和目录的创建、查找和删除等操作。

#### 1.2 构造方法

* `public File(String pathname) `：通过将给定的路径名字符串转换为**抽象路径名**来创建新的 File实例。
* `public File(String parent, String child) `：从父路径名字符串和子路径名字符串创建新的 File实例。
* `public File(File parent, String child) `：从父抽象路径名和子路径名字符串创建新的 File实例。

```java
/*
    java.io.File类
    文件和目录路径名的抽象表示形式。
    java把电脑中的文件和文件夹(目录)封装为了一个File类,我们可以使用File类对文件和文件夹进行操作
    我们可以使用File类的方法
        创建一个文件/文件夹
        删除文件/文件夹
        获取文件/文件夹
        判断文件/文件夹是否存在
        对文件夹进行遍历
        获取文件的大小
    File类是一个与系统无关的类,任何的操作系统都可以使用这个类中的方法

    重点:记住这三个单词
        file:文件
        directory:文件夹/目录
        path:路径
 */
public class Demo01File {
    public static void main(String[] args) {
        /*
            static String pathSeparator 与系统有关的路径分隔符，为了方便，它被表示为一个字符串。
            static char pathSeparatorChar 与系统有关的路径分隔符。

            static String separator 与系统有关的默认名称分隔符，为了方便，它被表示为一个字符串。
            static char separatorChar 与系统有关的默认名称分隔符。

            操作路径:路径不能写死了
            C:\develop\a\a.txt  windows
            C:/develop/a/a.txt  linux
            "C:"+File.separator+"develop"+File.separator+"a"+File.separator+"a.txt"
         */
        String pathSeparator = File.pathSeparator;
        System.out.println(pathSeparator);//路径分隔符 windows:分号;  linux:冒号:

        String separator = File.separator;
        System.out.println(separator);// 文件名称分隔符 windows:反斜杠\  linux:正斜杠/
    }

}
;
\
```

构造方法的使用：

```java
public class Test {
    public static void main(String[] args) {
       /*
            File类的构造方法
         */
        //show02("c:\\","a.txt");//c:\a.txt
//        show02("d:\\","a.txt");//d:\a.txt
        show03();

        File f = new File("F:\\java\\学习笔记\\tmp\\tmpproject");
        long length = f.length();
        System.out.println(length);
    }

    /*
        File(File parent, String child) 根据 parent 抽象路径名和 child 路径名字符串创建一个新 File 实例。
        参数:把路径分成了两部分
            File parent:父路径
            String child:子路径
        好处:
             父路径和子路径,可以单独书写,使用起来非常灵活;父路径和子路径都可以变化
             父路径是File类型,可以使用File的方法对路径进行一些操作,再使用路径创建对象
     */
    private static void show03() {
        File parent = new File("d:\\");
        File file = new File(parent,"hello.java");
        System.out.println(file);//d:\hello.java
    }

    /*
        File(String parent, String child) 根据 parent 路径名字符串和 child 路径名字符串创建一个新 File 实例。
        参数:把路径分成了两部分
            String parent:父路径
            String child:子路径
        好处:
            父路径和子路径,可以单独书写,使用起来非常灵活;父路径和子路径都可以变化
     */
    private static void show02(String parent, String child) {
        File file = new File(parent,child);
        System.out.println(file);//c:\a.txt
    }

    /*
        File(String pathname) 通过将给定路径名字符串转换为抽象路径名来创建一个新 File 实例。
        参数:
            String pathname:字符串的路径名称
            路径可以是以文件结尾,也可以是以文件夹结尾
            路径可以是相对路径,也可以是绝对路径
            路径可以是存在,也可以是不存在
            创建File对象,只是把字符串路径封装为File对象,不考虑路径的真假情况
     */
    private static void show01() {
        File f1 = new File("F:\\java\\学习笔记\\tmp\\tmpproject\\a.txt");
        System.out.println(f1);//重写了Object类的toString方法 F:\java\学习笔记\tmp\tmpproject\a.txt

        File f2 = new File("F:\\java\\学习笔记\\tmp\\tmpproject");
        System.out.println(f2);//F:\java\学习笔记\tmp\tmpproject

        File f3 = new File("b.txt");
        System.out.println(f3);//b.txt
    }
}

```

#### 1.3 常用方法

* 获取功能的方法

  `public String getAbsolutePath() `：返回此File的绝对路径名字符串。
  `public String getPath() `：将此File转换为路径名字符串。
  `public String getName()` ：返回由此File表示的文件或目录的名称。
  `public long length() `：返回由此File表示的文件的长度。

  ```java
  /*
      File类获取功能的方法
          - public String getAbsolutePath() ：返回此File的绝对路径名字符串。
          - public String getPath() ：将此File转换为路径名字符串。
          - public String getName()  ：返回由此File表示的文件或目录的名称。
          - public long length()  ：返回由此File表示的文件的长度。
   */
  public class Demo03File {
      public static void main(String[] args) {
          show04();
      }
  
      /*
          public long length()  ：返回由此File表示的文件的长度。
          获取的是构造方法指定的文件的大小,以字节为单位
          注意:
              文件夹是没有大小概念的,不能获取文件夹的大小
              如果构造方法中给出的路径不存在,那么length方法返回0
       */
      private static void show04() {
          File f1 = new File("C:\\develop\\a\\1.jpg");
          long l1 = f1.length();
          System.out.println(l1);//780831字节
  
          File f2 = new File("C:\\develop\\a\\2.jpg");
          System.out.println(f2.length());//0
  
          File f3 = new File("C:\\develop\\a");
          System.out.println(f3.length());//0 文件夹没有大小概念的
      }
  
      /*
          public String getName()  ：返回由此File表示的文件或目录的名称。
          获取的就是构造方法传递路径的结尾部分(文件/文件夹)
       */
      private static void show03() {
          File f1 = new File("C:\\Users\\itcast\\IdeaProjects\\shungyuan\\a.txt");
          String name1 = f1.getName();
          System.out.println(name1);//a.txt
  
          File f2 = new File("C:\\Users\\itcast\\IdeaProjects\\shungyuan");
          String name2 = f2.getName();
          System.out.println(name2);//shungyuan
      }
  
      /*
          public String getPath() ：将此File转换为路径名字符串。
          获取的构造方法中传递的路径
  
          toString方法调用的就是getPath方法
          源码:
              public String toString() {
                  return getPath();
              }
       */
      private static void show02() {
          File f1 = new File("C:\\Users\\itcast\\IdeaProjects\\shungyuan\\a.txt");
          File f2 = new File("a.txt");
          String path1 = f1.getPath();
          System.out.println(path1);//C:\Users\itcast\IdeaProjects\shungyuan\a.txt
          String path2 = f2.getPath();
          System.out.println(path2);//a.txt
  
          System.out.println(f1);//C:\Users\itcast\IdeaProjects\shungyuan\a.txt
          System.out.println(f1.toString());//C:\Users\itcast\IdeaProjects\shungyuan\a.txt
      }
  
      /*
          public String getAbsolutePath() ：返回此File的绝对路径名字符串。
          获取的构造方法中传递的路径
          无论路径是绝对的还是相对的,getAbsolutePath方法返回的都是绝对路径
       */
      private static void show01() {
          File f1 = new File("C:\\Users\\itcast\\IdeaProjects\\shungyuan\\a.txt");
          String absolutePath1 = f1.getAbsolutePath();
          System.out.println(absolutePath1);//C:\Users\itcast\IdeaProjects\shungyuan\a.txt
  
          File f2 = new File("a.txt");
          String absolutePath2 = f2.getAbsolutePath();
          System.out.println(absolutePath2);//C:\Users\itcast\IdeaProjects\shungyuan\a.txt
      }
  }
  ```

  

* 判断功能的方法

  `public boolean exists() `：此File表示的文件或目录是否实际存在。
  `public boolean isDirectory() `：此File表示的是否为目录。
  `public boolean isFile()` ：此File表示的是否为文件。

  ```java
  /*
      File类判断功能的方法
          - public boolean exists() ：此File表示的文件或目录是否实际存在。
          - public boolean isDirectory() ：此File表示的是否为目录。
          - public boolean isFile() ：此File表示的是否为文件。
   */
  public class Demo04File {
      public static void main(String[] args) {
          show02();
      }
  
      /*
          public boolean isDirectory() ：此File表示的是否为目录。
              用于判断构造方法中给定的路径是否以文件夹结尾
                  是:true
                  否:false
          public boolean isFile() ：此File表示的是否为文件。
              用于判断构造方法中给定的路径是否以文件结尾
                  是:true
                  否:false
          注意:
              电脑的硬盘中只有文件/文件夹,两个方法是互斥
              这两个方法使用前提,路径必须是存在的,否则都返回false
       */
      private static void show02() {
          File f1 = new File("C:\\Users\\itcast\\IdeaProjects\\shung");
  
          //不存在,就没有必要获取
          if(f1.exists()){
              System.out.println(f1.isDirectory());
              System.out.println(f1.isFile());
          }
  
          File f2 = new File("C:\\Users\\itcast\\IdeaProjects\\shungyuan");
          if(f2.exists()){
              System.out.println(f2.isDirectory());//true
              System.out.println(f2.isFile());//false
          }
  
          File f3 = new File("C:\\Users\\itcast\\IdeaProjects\\shungyuan\\shungyuan.iml");
          if(f3.exists()){
              System.out.println(f3.isDirectory());//false
              System.out.println(f3.isFile());//true
          }
      }
  
      /*
          public boolean exists() ：此File表示的文件或目录是否实际存在。
          用于判断构造方法中的路径是否存在
              存在:true
              不存在:false
       */
      private static void show01() {
          File f1 = new File("C:\\Users\\itcast\\IdeaProjects\\shungyuan");
          System.out.println(f1.exists());//true
  
          File f2 = new File("C:\\Users\\itcast\\IdeaProjects\\shung");
          System.out.println(f2.exists());//false
  
          File f3 = new File("shungyuan.iml");//相对路径 C:\Users\itcast\IdeaProjects\shungyuan\shungyuan.iml
          System.out.println(f3.exists());//true
  
          File f4 = new File("a.txt");
          System.out.println(f4.exists());//false
      }
  }
  ```

  

* 创建与删除功能的方法

  `public boolean createNewFile() `：当且仅当具有该名称的文件尚不存在时，创建一个新的空文件。
  `public boolean delete() `：删除由此File表示的文件或目录。
  `public boolean mkdir() `：创建由此File表示的目录。
  `public boolean mkdirs() `：创建由此File表示的目录，包括任何必需但不存在的父目录。

  ```java
  *
      File类创建删除功能的方法
          - public boolean createNewFile() ：当且仅当具有该名称的文件尚不存在时，创建一个新的空文件。
          - public boolean delete() ：删除由此File表示的文件或目录。
          - public boolean mkdir() ：创建由此File表示的目录。
          - public boolean mkdirs() ：创建由此File表示的目录，包括任何必需但不存在的父目录。
   */
  
  public class Test {
      public static void main(String[] args) throws IOException {
          show03();
      }
  
      /*
          public boolean delete() ：删除由此File表示的文件或目录。
          此方法,可以删除构造方法路径中给出的文件/文件夹
          返回值:布尔值
              true:文件/文件夹删除成功,返回true
              false:文件夹中有内容,不会删除返回false;构造方法中路径不存在false
          注意:
              delete方法是直接在硬盘删除文件/文件夹,不走回收站,删除要谨慎
       */
      private static void show03() {
          File f1 = new File("08_FileAndRecursion\\新建文件夹");
          boolean b1 = f1.delete();
          System.out.println("b1:"+b1);
  
          File f2 = new File("08_FileAndRecursion\\abc.txt");
          System.out.println(f2.delete());
  
          File f3 = new File("08_F\\ccc");
          System.out.println(f3.delete());
  
          File f4 = new File("08_F");
          System.out.println(f4.delete());
      }
  
      /*
         public boolean mkdir() ：创建单级空文件夹
         public boolean mkdirs() ：既可以创建单级空文件夹,也可以创建多级文件夹
         创建文件夹的路径和名称在构造方法中给出(构造方法的参数)
          返回值:布尔值
              true:文件夹不存在,创建文件夹,返回true
              false:文件夹存在,不会创建,返回false;构造方法中给出的路径不存在返回false
          注意:
              1.此方法只能创建文件夹,不能创建文件
       */
      private static void show02() {
          File f1 = new File("08_FileAndRecursion\\aaa");
          boolean b1 = f1.mkdir();
          System.out.println("b1:"+b1);
  
          File f2 = new File("08_FileAndRecursion\\111\\222\\333\\444");
          boolean b2 = f2.mkdirs();
          System.out.println("b2:"+b2);
  
          File f3 = new File("08_FileAndRecursion\\abc.txt");
          boolean b3 = f3.mkdirs();//看类型,是一个文件
          System.out.println("b3:"+b3);
  
          File f4 = new File("08_F\\ccc");
          boolean b4 = f4.mkdirs();//不会抛出异常,路径不存在,在项目根目录下创建08_F\ccc
          System.out.println("b4:"+b4);
      }
  
      /*
          public boolean createNewFile() ：当且仅当具有该名称的文件尚不存在时，创建一个新的空文件。
          创建文件的路径和名称在构造方法中给出(构造方法的参数)
          返回值:布尔值
              true:文件不存在,创建文件,返回true
              false:文件存在,不会创建,返回false
          注意:
              1.此方法只能创建文件,不能创建文件夹
              2.创建文件的路径必须存在,否则会抛出异常
  
          public boolean createNewFile() throws IOException
          createNewFile声明抛出了IOException,我们调用这个方法,就必须的处理这个异常,要么throws,要么trycatch
       */
      private static void show01() throws IOException {
          File f1 = new File("F:\\java\\学习笔记\\tmp\\tmpproject\\08_FileAndRecursion\\1.txt");
          boolean b1 = f1.createNewFile();
          System.out.println("b1:"+b1);
  
          File f2 = new File("08_FileAndRecursion\\2.txt");
          System.out.println(f2.createNewFile());
  
          File f3 = new File("08_FileAndRecursion\\新建文件夹");
          System.out.println(f3.createNewFile());//还是创建一个文件，不要被名称迷糊,要看类型
  
          File f4 = new File("08_FileAndRecursi\\3.txt");
          System.out.println(f4.createNewFile());//路径不存在,抛出IOException
      }
  }
  ```



#### 1.4 遍历目录

```java
/*
    File类遍历(文件夹)目录功能
        - public String[] list() ：返回一个String数组，表示该File目录中的所有子文件或目录。
        - public File[] listFiles() ：返回一个File数组，表示该File目录中的所有的子文件或目录。

    注意:
        隐藏的文件和文件夹也可以遍历出来
        list方法和listFiles方法遍历的是构造方法中给出的目录
        如果构造方法中给出的目录的路径不存在,会抛出空指针异常
        如果构造方法中给出的路径不是一个目录,也会抛出空指针异常
 */

public class Test {
    public static void main(String[] args) {
        show02();
    }

    /*
        public File[] listFiles() ：返回一个File数组，表示该File目录中的所有的子文件或目录。
        遍历构造方法中给出的目录,会获取目录中所有的文件/文件夹,把文件/文件夹封装为File对象,多个File对象存储到File数组中
     */
    private static void show02() {
        File file = new File("F:\\java\\学习笔记\\tmp\\tmpproject\\08_FileAndRecursion");
        File[] files = file.listFiles();
        for (File f : files) {
            System.out.println(f);
        }
    }

    /*
        public String[] list() ：返回一个String数组，表示该File目录中的所有子文件或目录。
        遍历构造方法中给出的目录,会获取目录中所有文件/文件夹的名称,把获取到的多个名称存储到一个String类型的数组中
     */
    private static void show01() {
        //File file = new File("F:\java\学习笔记\tmp\tmpproject\\08_FileAndRecursion\\1.txt");//NullPointerException
        //File file = new File("F:\java\学习笔记\tmp\tmpproject\\08_Fi");//NullPointerException
        File file = new File("F:\\java\\学习笔记\\tmp\\tmpproject\\08_FileAndRecursion");
        String[] arr = file.list();
        for (String fileName : arr) {
            System.out.println(fileName);
        }
    }
}
```



### 2. 递归

* 递归：指在当前方法内调用自己的这种现象。
* 递归的分类:
  * 递归分为两种，直接递归和间接递归。
  * 直接递归称为方法自身调用自己。
  * 间接递归可以A方法调用B方法，B方法调用C方法，C方法调用A方法。

* 注意事项：
  * 递归一定要有条件限定，保证递归能够停止下来，否则会发生栈内存溢出。
  * 在递归中虽然有限定条件，但是递归次数不能太多。否则也会发生栈内存溢出。
  * 构造方法,禁止递归

```java
/*
    递归:方法自己调用自己
    - 递归的分类:
      - 递归分为两种，直接递归和间接递归。
      - 直接递归称为方法自身调用自己。
      - 间接递归可以A方法调用B方法，B方法调用C方法，C方法调用A方法。
    - 注意事项：
      - 递归一定要有条件限定，保证递归能够停止下来，否则会发生栈内存溢出。
      - 在递归中虽然有限定条件，但是递归次数不能太多。否则也会发生栈内存溢出。
      - 构造方法,禁止递归
    递归的使用前提:
        当调用方法的时候,方法的主体不变,每次调用方法的参数不同,可以使用递归
 */
public class Demo01Recurison {
    public static void main(String[] args) {
        //a();
        b(1);
    }

    /*
        构造方法,禁止递归
            编译报错:构造方法是创建对象使用的,一直递归会导致内存中有无数多个对象,直接编译报错
     */
    public Demo01Recurison() {
        //Demo01Recurison();
    }

    /*
            在递归中虽然有限定条件，但是递归次数不能太多。否则也会发生栈内存溢出。
            11157
                Exception in thread "main" java.lang.StackOverflowError
         */
    private static void b(int i) {
        System.out.println(i);
        if(i==20000){
            return; //结束方法
        }
        b(++i);
    }

    /*
        递归一定要有条件限定，保证递归能够停止下来，否则会发生栈内存溢出。
        Exception in thread "main" java.lang.StackOverflowError
     */
    private static void a() {
        System.out.println("a方法!");
        a();
    }
}

```

### 3. 综合案例：FileFilter过滤器+递归

```java
/*
    需求:
        遍历c:\\abc文件夹,及abc文件夹的子文件夹
        只要.java结尾的文件
        c:\\abc
        c:\\abc\\abc.txt
        c:\\abc\\abc.java
        c:\\abc\\a
        c:\\abc\\a\\a.jpg
        c:\\abc\\a\\a.java
        c:\\abc\\b
        c:\\abc\\b\\b.java
        c:\\abc\\b\\b.txt
    我们可以使用过滤器来实现
    在File类中有两个和ListFiles重载的方法,方法的参数传递的就是过滤器
    File[] listFiles(FileFilter filter)
    java.io.FileFilter接口:用于抽象路径名(File对象)的过滤器。
        作用:用来过滤文件(File对象)
        抽象方法:用来过滤文件的方法
            boolean accept(File pathname) 测试指定抽象路径名是否应该包含在某个路径名列表中。
            参数:
                File pathname:使用ListFiles方法遍历目录,得到的每一个文件对象
    File[] listFiles(FilenameFilter filter)
    java.io.FilenameFilter接口:实现此接口的类实例可用于过滤器文件名。
        作用:用于过滤文件名称
        抽象方法:用来过滤文件的方法
            boolean accept(File dir, String name) 测试指定文件是否应该包含在某一文件列表中。
            参数:
                File dir:构造方法中传递的被遍历的目录
                String name:使用ListFiles方法遍历目录,获取的每一个文件/文件夹的名称
    注意:
        两个过滤器接口是没有实现类的,需要我们自己写实现类,重写过滤的方法accept,在方法中自己定义过滤的规则
 */
public class Demo01Filter {
    public static void main(String[] args) {
        File file = new File("c:\\abc");
        getAllFile(file);
    }

    /*
        定义一个方法,参数传递File类型的目录
        方法中对目录进行遍历
     */
    public static void getAllFile(File dir){
        File[] files = dir.listFiles(new FileFilterImpl());//传递过滤器对象
        for (File f : files) {
            //对遍历得到的File对象f进行判断,判断是否是文件夹
            if(f.isDirectory()){
                //f是一个文件夹,则继续遍历这个文件夹
                //我们发现getAllFile方法就是传递文件夹,遍历文件夹的方法
                //所以直接调用getAllFile方法即可:递归(自己调用自己)
                getAllFile(f);
            }else{
                //f是一个文件,直接打印即可
                System.out.println(f);
            }
        }
    }
}

/*
    创建过滤器FileFilter的实现类,重写过滤方法accept,定义过滤规则
 */
public class FileFilterImpl implements FileFilter{
    @Override
    public boolean accept(File pathname) {
        /*
            过滤的规则:
            在accept方法中,判断File对象是否是以.java结尾
            是就返回true
            不是就返回false
         */
        //如果pathname是一个文件夹,返回true,继续遍历这个文件夹
        if(pathname.isDirectory()){
            return true;
        }

        return pathname.getName().toLowerCase().endsWith(".java");
    }
}
```

对应的匿名内部类代码为：

```java
public class Test {
    public static void main(String[] args) {
        File file = new File("c:\\abc");
        getAllFile(file);
    }

    /*
        定义一个方法,参数传递File类型的目录
        方法中对目录进行遍历
     */
    public static void getAllFile(File dir){
        //传递过滤器对象 使用匿名内部类
        File[] files = dir.listFiles(new FileFilter() {
            @Override
            public boolean accept(File pathname) {
                //过滤规则,pathname是文件夹或者是.java结尾的文件返回true
                return pathname.isDirectory() || pathname.getName().toLowerCase().endsWith(".java");
            }
        });

        //使用Lambda表达式优化匿名内部类(接口中只有一个抽象方法)
        /*File[] files = dir.listFiles((File pathname)->{
            return pathname.isDirectory() || pathname.getName().toLowerCase().endsWith(".java");
        });*/

//        File[] files = dir.listFiles(pathname->pathname.isDirectory() || pathname.getName().toLowerCase().endsWith(".java"));

        /*File[] files = dir.listFiles(new FilenameFilter() {
            @Override
            public boolean accept(File dir, String name) {
                //过滤规则,pathname是文件夹或者是.java结尾的文件返回true
                return new File(dir,name).isDirectory() || name.toLowerCase().endsWith(".java");
            }
        });*/

        //使用Lambda表达式优化匿名内部类(接口中只有一个抽象方法)
        /*File[] files = dir.listFiles((File d, String name)->{
            //过滤规则,pathname是文件夹或者是.java结尾的文件返回true
            return new File(d,name).isDirectory() || name.toLowerCase().endsWith(".java");
        });*/

        //File[] files = dir.listFiles((d,name)->new File(d,name).isDirectory() || name.toLowerCase().endsWith(".java"));

        for (File f : files) {
            //对遍历得到的File对象f进行判断,判断是否是文件夹
            if(f.isDirectory()){
                //f是一个文件夹,则继续遍历这个文件夹
                //我们发现getAllFile方法就是传递文件夹,遍历文件夹的方法
                //所以直接调用getAllFile方法即可:递归(自己调用自己)
                getAllFile(f);
            }else{
                //f是一个文件,直接打印即可
                System.out.println(f);
            }
        }
    }
}
```

## day09【字节流、字符流】

### 1. 什么是IO ？

输入输出流，**以内存为基准**：流向内存是输入流，流出内存的输出流。输入也叫做读取数据，输出也叫做作写出数据。

格局数据的类型分为：**字节流**和**字符流**。

* 字节流 ：以字节为单位，读写数据的流。
* 字符流 ：以字符为单位，读写数据的流。

顶级父类们：

|        | 输入流                 | 输出流                  |
| ------ | ---------------------- | ----------------------- |
| 字节流 | 字节输入流 InputStream | 字节输出流 OutputStream |
| 字符流 | 字符输入流 Reader      | 字符输出流 Writer       |

### 2. 字节流的概念

一切皆为字节，字节流可以传输任意文件数据，无论使用什么样的流对象，底层传输的始终为二进制数据。

硬盘存储的数据都是字节。

### 3. 字节输出流【OutputStream】

`java.io.OutputStream` 抽象类是表示字节输出流的所有类的超类，将指定的、内存中的字节信息写出到目的地。

* `public void close() `：关闭此输出流并释放与此流相关联的任何系统资源。
* `public void flush() `：刷新此输出流并强制任何缓冲的输出字节被写出。
* `public void write(byte[] b) `：将 b.length字节从指定的字节数组写入此输出流。
* `public void write(byte[] b, int off, int len) `：从指定的字节数组写入 len字节，从偏移量 off开始输出到此输出流。
* `public abstract void write(int b) `：将指定的字节输出流。

close方法，当完成流的操作时，必须调用此方法，释放系统资源。

### 4. FileOutputStream类 是 OutputStream的子类

`java.io.FileOutputStream `类是文件输出流，用于将数据从内存中写出到**文件**。

#### 4.1 构造方法

* `public FileOutputStream(File file)` ：创建文件输出流以写入由指定的 File对象表示的文件。
* `public FileOutputStream(String name) `： 创建文件输出流以指定的名称写入文件。

当你创建一个流对象时，必须传入一个文件路径。该路径下，如果没有这个文件，会创建该文件。如果有这个文件，会清空这个文件的数据。

#### 4.2 常用方法

* 写出字节数据

  ```java
  /*
  写入数据的原理(内存-->硬盘)
          java程序-->JVM(java虚拟机)-->OS(操作系统)-->OS调用写数据的方法-->把数据写入到文件中
  
      字节输出流的使用步骤(重点):
          1.创建一个FileOutputStream对象,构造方法中传递写入数据的目的地
          2.调用FileOutputStream对象中的方法write,把数据写入到文件中
          3.释放资源(流使用会占用一定的内存,使用完毕要把内存清空,提供程序的效率)
   */
  public class Demo01OutputStream {
      public static void main(String[] args) throws IOException {
          //1.创建一个FileOutputStream对象,构造方法中传递写入数据的目的地
          FileOutputStream fos = new FileOutputStream("09_IOAndProperties\\a.txt");
          //2.调用FileOutputStream对象中的方法write,把数据写入到文件中
          //public abstract void write(int b) ：将指定的字节输出流。
          fos.write(97);// 记事本打开文件显示为"a"
          //3.释放资源(流使用会占用一定的内存,使用完毕要把内存清空,提供程序的效率)
          //fos.close();
      }
  }
  
  ```

  

  ![image-20210228162526548](Java%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0.assets/文件存储的原理和记事本打开文件的原理.png)

  ```java
  /*
      一次写多个字节的方法:
          - public void write(byte[] b)：将 b.length字节从指定的字节数组写入此输出流。
          - public void write(byte[] b, int off, int len) ：从指定的字节数组写入 len字节，从偏移量 off开始输出到此输出流。
   */
  public class Demo02OutputStream {
      public static void main(String[] args) throws IOException {
          //创建FileOutputStream对象,构造方法中绑定要写入数据的目的地
          FileOutputStream fos = new FileOutputStream(new File("09_IOAndProperties\\b.txt"));
          //调用FileOutputStream对象中的方法write,把数据写入到文件中
          //在文件中显示100,写个字节
          fos.write(49);
          fos.write(48);
          fos.write(48);
  
          /*
              public void write(byte[] b)：将 b.length字节从指定的字节数组写入此输出流。
              一次写多个字节:
                  如果写的第一个字节是正数(0-127),那么显示的时候会查询ASCII表
                  如果写的第一个字节是负数,那第一个字节会和第二个字节,两个字节组成一个中文显示,查询系统默认码表(GBK)
           */
          byte[] bytes = {65,66,67,68,69};//ABCDE
          //byte[] bytes = {-65,-66,-67,68,69};//烤紻E
          fos.write(bytes);
  
          /*
              public void write(byte[] b, int off, int len) ：把字节数组的一部分写入到文件中
                  int off:数组的开始索引
                  int len:写几个字节
           */
          fos.write(bytes,1,2);//BC
  
          /*
              写入字符的方法:可以使用String类中的方法把字符串,转换为字节数组
                  byte[] getBytes()  把字符串转换为字节数组
           */
          byte[] bytes2 = "你好".getBytes();
          System.out.println(Arrays.toString(bytes2));//[-28, -67, -96, -27, -91, -67]
          fos.write(bytes2);
  
          //释放资源
          fos.close();
      }
  }
  ```

  

* 数据追加续写 + 写出换行

  ```java
  /*
      追加写/续写:使用两个参数的构造方法
          FileOutputStream(String name, boolean append)创建一个向具有指定 name 的文件中写入数据的输出文件流。
          FileOutputStream(File file, boolean append) 创建一个向指定 File 对象表示的文件中写入数据的文件输出流。
          参数:
             String name,File file:写入数据的目的地
             boolean append:追加写开关
              true:创建对象不会覆盖源文件,继续在文件的末尾追加写数据
              false:创建一个新文件,覆盖源文件
      写换行:写换行符号
          windows:\r\n
          linux:/n
          mac:/r
   */
  public class Test {
      public static void main(String[] args) throws IOException {
          FileOutputStream fos = new FileOutputStream("c.txt",true);
          for (int i = 1; i <=10 ; i++) {
              fos.write("你好".getBytes());
              fos.write("\r\n".getBytes());
          }
          fos.close();
      }
  }
  ```

  

### 5. 字节输入流【InputStream】

`java.io.InputStream `抽象类是表示字节输入流的所有类的超类，可以读取字节信息到内存中。它定义了字节输入流的基本共性功能方法。

* `public void close()` ：关闭此输入流并释放与此流相关联的任何系统资源。
* `public abstract int read() `： 从输入流读取数据的下一个字节。
* `public int read(byte[] b) `： 从输入流中读取一些字节数，并将它们存储到字节数组 b中 。

### 6. FileInputStream类 是 InputStream的子类

`java.io.FileInputStream` 类是文件输入流，从文件中读取字节。

#### 6.1 构造方法

* `FileInputStream(File file) `： 通过打开与实际文件的连接来创建一个 FileInputStream ，该文件由文件系统中的 File对象 file命名。
* `FileInputStream(String name)` ： 通过打开与实际文件的连接来创建一个 FileInputStream ，该文件由文件系统中的路径名 name命名。

当你创建一个流对象时，必须传入一个文件路径。该路径下，如果没有该文件,会抛出`FileNotFoundException`。

#### 6.2 常用方法的使用

```java
/*
    java.io.InputStream:字节输入流
    此抽象类是表示字节输入流的所有类的超类。

    定义了所有子类共性的方法:
         int read()从输入流中读取数据的下一个字节。
         int read(byte[] b) 从输入流中读取一定数量的字节，并将其存储在缓冲区数组 b 中。
         void close() 关闭此输入流并释放与该流关联的所有系统资源。

    java.io.FileInputStream extends InputStream
    FileInputStream:文件字节输入流
    作用:把硬盘文件中的数据,读取到内存中使用

    构造方法:
        FileInputStream(String name)
        FileInputStream(File file)
        参数:读取文件的数据源
            String name:文件的路径
            File file:文件
        构造方法的作用:
            1.会创建一个FileInputStream对象
            2.会把FileInputStream对象指定构造方法中要读取的文件

    读取数据的原理(硬盘-->内存)
        java程序-->JVM-->OS-->OS读取数据的方法-->读取文件

    字节输入流的使用步骤(重点):
        1.创建FileInputStream对象,构造方法中绑定要读取的数据源
        2.使用FileInputStream对象中的方法read,读取文件
        3.释放资源
 */
public class Demo01InputStream {
    public static void main(String[] args) throws IOException {
        //1.创建FileInputStream对象,构造方法中绑定要读取的数据源
        FileInputStream fis = new FileInputStream("a.txt");
        //2.使用FileInputStream对象中的方法read,读取文件
        //int read()读取文件中的一个字节并返回,读取到文件的末尾返回-1
        /*int len = fis.read();
        System.out.println(len);//97 a

        len = fis.read();
        System.out.println(len);// 98 b

        len = fis.read();
        System.out.println(len);//99 c

        len = fis.read();
        System.out.println(len);//-1

        len = fis.read();
        System.out.println(len);//-1*/

        /*
            发现以上读取文件是一个重复的过程,所以可以使用循环优化
            不知道文件中有多少字节,使用while循环
            while循环结束条件,读取到-1的时候结束

            布尔表达式(len = fis.read())!=-1
                1.fis.read():读取一个字节
                2.len = fis.read():把读取到的字节赋值给变量len
                3.(len = fis.read())!=-1:判断变量len是否不等于-1
         */
        int len = 0; //记录读取到的字节
        while((len = fis.read())!=-1){
            System.out.print(len);//abc
        }

        //3.释放资源
        fis.close();
    }
}

```

一次读多个字节：

**注意最后读出的是CD、ED、ED，思考为什么？**

```java
/*
    字节输入流一次读取多个字节的方法:
        int read(byte[] b) 从输入流中读取一定数量的字节，并将其存储在缓冲区数组 b 中。
    明确两件事情:
        1.方法的参数byte[]的作用?
            起到缓冲作用,存储每次读取到的多个字节
            数组的长度一把定义为1024(1kb)或者1024的整数倍
        2.方法的返回值int是什么?
            每次读取的有效字节个数

    String类的构造方法
        String(byte[] bytes) :把字节数组转换为字符串
        String(byte[] bytes, int offset, int length) 把字节数组的一部分转换为字符串 offset:数组的开始索引 length:转换的字节个数
 */
public class Demo02InputStream {
    public static void main(String[] args) throws IOException {
        //创建FileInputStream对象,构造方法中绑定要读取的数据源
        FileInputStream fis = new FileInputStream("b.txt");
        //使用FileInputStream对象中的方法read读取文件
        //int read(byte[] b) 从输入流中读取一定数量的字节，并将其存储在缓冲区数组 b 中。
        /*byte[] bytes = new byte[2];
        int len = fis.read(bytes);
        System.out.println(len);//2
        //System.out.println(Arrays.toString(bytes));//[65, 66]
        System.out.println(new String(bytes));//AB

        len = fis.read(bytes);
        System.out.println(len);//2
        System.out.println(new String(bytes));//CD

        len = fis.read(bytes);
        System.out.println(len);//1
        System.out.println(new String(bytes));//ED

        len = fis.read(bytes);
        System.out.println(len);//-1
        System.out.println(new String(bytes));//ED*/

        /*
            发现以上读取时一个重复的过程,可以使用循环优化
            不知道文件中有多少字节,所以使用while循环
            while循环结束的条件,读取到-1结束
         */
        byte[] bytes = new byte[1024];//存储读取到的多个字节
        int len = 0; //记录每次读取的有效字节个数
        while((len = fis.read(bytes))!=-1){
            //String(byte[] bytes, int offset, int length) 把字节数组的一部分转换为字符串 offset:数组的开始索引 length:转换的字节个数
            System.out.println(new String(bytes,0,len));
        }

        //释放资源
        fis.close();
    }
}

```

原因：

![image-20210228171638873](Java%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0.assets/文件输入流一次读书多个字节的运行图.png)

### 7. 字符流的概念

当使用字节流读取文本文件时，可能会有一个小问题。就是**遇到中文字符时，可能不会显示完整的字符，那是因为一个中文字符可能占用多个字节存储**。所以Java提供一些字符流类，**以字符为单位**读写数据，专门用于处理**文本文件**。

### 8. 字符输入流【Reader】

`java.io.Reader` 抽象类是表示用于读取字符流的所有类的超类，可以读取字符信息到内存中。它定义了字符输入流的基本共性功能方法。

* `public void close() `：关闭此流并释放与此流相关联的任何系统资源。
* `public int read() `： 从输入流读取一个字符。
* `public int read(char[] cbuf) `： 从输入流中读取一些字符，并将它们存储到字符数组 cbuf中 。

### 9. FileReader类

`java.io.FileReader `类是读取字符文件的便利类。构造时使用系统**默认的字符编码**和**默认字节缓冲区**。

**字符编码**：字节与字符的对应规则。Windows系统的中文编码默认是**GBK编码表**。idea中**UTF-8**

**字节缓冲区**：一个字节数组，用来临时存储字节数据。

#### 9.1 构造方法

`FileReader(File file)` ： 创建一个新的 FileReader ，给定要读取的File对象。
`FileReader(String fileName) `： 创建一个新的 FileReader ，给定要读取的文件的名称。
当你创建一个流对象时，必须传入一个文件路径。类似`FileInputStream `。

#### 9.2 常用方法应用

```java
/*
    使用字节流读取中文文件
    1个中文
        GBK:占用两个字节
        UTF-8:占用3个字节
 */
public class Demo01InputStream {
    public static void main(String[] args) throws IOException {
        FileInputStream fis = new FileInputStream("c.txt");
        int len = 0;
        while((len = fis.read())!=-1){
            System.out.println((char)len);
        }
        fis.close();
    }
}
```



```java
/*
字符输入流的使用步骤:
        1.创建FileReader对象,构造方法中绑定要读取的数据源
        2.使用FileReader对象中的方法read读取文件
        3.释放资源
 */
public class Demo02Reader {
    public static void main(String[] args) throws IOException {
        //1.创建FileReader对象,构造方法中绑定要读取的数据源
        FileReader fr = new FileReader("c.txt");
        //2.使用FileReader对象中的方法read读取文件
        //int read() 读取单个字符并返回。
        /*int len = 0;
        while((len = fr.read())!=-1){
            System.out.print((char)len);
        }*/

        //int read(char[] cbuf)一次读取多个字符,将字符读入数组。
        char[] cs = new char[1024];//存储读取到的多个字符
        int len = 0;//记录的是每次读取的有效字符个数
        while((len = fr.read(cs))!=-1){
            /*
                String类的构造方法
                String(char[] value) 把字符数组转换为字符串
                String(char[] value, int offset, int count) 把字符数组的一部分转换为字符串 offset数组的开始索引 count转换的个数
             */
            System.out.println(new String(cs,0,len));
        }

        //3.释放资源
        fr.close();
    }
}
```

### 10. 字符输出流【Writer】

### 11. FileWriter类

字节直接写到文件中，字符不是，字符先写到内存缓冲区中，再刷新到文件中。

```java
/*
    java.io.Writer:字符输出流,是所有字符输出流的最顶层的父类,是一个抽象类

    共性的成员方法:
        - void write(int c) 写入单个字符。
        - void write(char[] cbuf)写入字符数组。
        - abstract  void write(char[] cbuf, int off, int len)写入字符数组的某一部分,off数组的开始索引,len写的字符个数。
        - void write(String str)写入字符串。
        - void write(String str, int off, int len) 写入字符串的某一部分,off字符串的开始索引,len写的字符个数。
        - void flush()刷新该流的缓冲。
        - void close() 关闭此流，但要先刷新它。

    java.io.FileWriter extends OutputStreamWriter extends Writer
    FileWriter:文件字符输出流
    作用:把内存中字符数据写入到文件中

    构造方法:
        FileWriter(File file)根据给定的 File 对象构造一个 FileWriter 对象。
        FileWriter(String fileName) 根据给定的文件名构造一个 FileWriter 对象。
        参数:写入数据的目的地
            String fileName:文件的路径
            File file:是一个文件
        构造方法的作用:
            1.会创建一个FileWriter对象
            2.会根据构造方法中传递的文件/文件的路径,创建文件
            3.会把FileWriter对象指向创建好的文件

    字符输出流的使用步骤(重点):
        1.创建FileWriter对象,构造方法中绑定要写入数据的目的地
        2.使用FileWriter中的方法write,把数据写入到内存缓冲区中(字符转换为字节的过程)
        3.使用FileWriter中的方法flush,把内存缓冲区中的数据,刷新到文件中
        4.释放资源(会先把内存缓冲区中的数据刷新到文件中)
 */
public class Demo01Writer {
    public static void main(String[] args) throws IOException {
        //1.创建FileWriter对象,构造方法中绑定要写入数据的目的地
        FileWriter fw = new FileWriter("d.txt");
        //2.使用FileWriter中的方法write,把数据写入到内存缓冲区中(字符转换为字节的过程)
        //void write(int c) 写入单个字符。
        fw.write(97);
        //3.使用FileWriter中的方法flush,把内存缓冲区中的数据,刷新到文件中
        //fw.flush();
        //4.释放资源(会先把内存缓冲区中的数据刷新到文件中)
        fw.close();
    }
}

```



flush方法和close方法的区别：

```java
/*
    flush方法和close方法的区别
        - flush ：刷新缓冲区，流对象可以继续使用。
        - close:  先刷新缓冲区，然后通知系统释放资源。流对象不可以再被使用了。
 */
public class Demo02CloseAndFlush {
    public static void main(String[] args) throws IOException {
        //1.创建FileWriter对象,构造方法中绑定要写入数据的目的地
        FileWriter fw = new FileWriter("e.txt");
        //2.使用FileWriter中的方法write,把数据写入到内存缓冲区中(字符转换为字节的过程)
        //void write(int c) 写入单个字符。
        fw.write(97);
        //3.使用FileWriter中的方法flush,把内存缓冲区中的数据,刷新到文件中
        fw.flush();
        //刷新之后流可以继续使用
        fw.write(98);

        //4.释放资源(会先把内存缓冲区中的数据刷新到文件中)
        fw.close();

        //close方法之后流已经关闭了,已经从内存中消失了,流就不能再使用了
        fw.write(99);//IOException: Stream closed
    }
}

```

其他方法：

```java
/*
    字符输出流写数据的其他方法
        - void write(char[] cbuf)写入字符数组。
        - abstract  void write(char[] cbuf, int off, int len)写入字符数组的某一部分,off数组的开始索引,len写的字符个数。
        - void write(String str)写入字符串。
        - void write(String str, int off, int len) 写入字符串的某一部分,off字符串的开始索引,len写的字符个数。
 */
public class Demo03Writer {
    public static void main(String[] args) throws IOException {
        FileWriter fw = new FileWriter("f.txt");
        char[] cs = {'a','b','c','d','e'};
        //void write(char[] cbuf)写入字符数组。
        fw.write(cs);//abcde

        //void write(char[] cbuf, int off, int len)写入字符数组的某一部分,off数组的开始索引,len写的字符个数。
        fw.write(cs,1,3);//bcd

        //void write(String str)写入字符串。
        fw.write("传智播客");//传智播客

        //void write(String str, int off, int len) 写入字符串的某一部分,off字符串的开始索引,len写的字符个数。
        fw.write("黑马程序员",2,3);//程序员

        fw.close();
    }
}

```

续写与换行：

```java
/*
    续写和换行
    续写,追加写:使用两个参数的构造方法
        FileWriter(String fileName, boolean append)
        FileWriter(File file, boolean append)
        参数:
            String fileName,File file:写入数据的目的地
            boolean append:续写开关 true:不会创建新的文件覆盖源文件,可以续写; false:创建新的文件覆盖源文件
     换行:换行符号
        windows:\r\n
        linux:/n
        mac:/r
 */
public class Demo04Writer {
    public static void main(String[] args) throws IOException {
        FileWriter fw = new FileWriter("g.txt",true);
        for (int i = 0; i <10 ; i++) {
            fw.write("HelloWorld"+i+"\r\n");
        }

        fw.close();
    }
}
```

### 12. IO异常的处理

JDK7前，我们一直把异常抛出，而**实际开发中并不能这样处理，建议使用try...catch...finally 代码块，处理异常部分**。

JDK7优化后，使用try-with-resource 语句，该语句确保了每个资源在语句结束时关闭。所谓的资源（resource）是指在程序完成后，必须关闭的对象。

```java
/*
    JDK7的新特性
    在try的后边可以增加一个(),在括号中可以定义流对象
    那么这个流对象的作用域就在try中有效
    try中的代码执行完毕,会自动把流对象释放,不用写finally
    格式:
        try(定义流对象;定义流对象....){
            可能会产出异常的代码
        }catch(异常类变量 变量名){
            异常的处理逻辑
        }
 */
public class Demo02JDK7 {
    public static void main(String[] args) {
        try(//1.创建一个字节输入流对象,构造方法中绑定要读取的数据源
            FileInputStream fis = new FileInputStream("c:\\1.jpg");
            //2.创建一个字节输出流对象,构造方法中绑定要写入的目的地
            FileOutputStream fos = new FileOutputStream("d:\\1.jpg");){

            //可能会产出异常的代码
            //一次读取一个字节写入一个字节的方式
            //3.使用字节输入流对象中的方法read读取文件
            int len = 0;
            while((len = fis.read())!=-1){
                //4.使用字节输出流中的方法write,把读取到的字节写入到目的地的文件中
                fos.write(len);
            }

        }catch (IOException e){
            //异常的处理逻辑
            System.out.println(e);
        }


    }
}
```

### 13. 属性集

`java.util.Properties `继承于`Hashtable` ，来表示一个持久的属性集。它使用**键值结构存储数据**，每个键及其对应值都是一个**字符串**。该类也被许多Java类使用，比如获取系统属性时， `System.getProperties` 方法就是返回一个`Properties `对象。

Properties集合是一个**唯一和IO流相结合的集合**。

#### 13.1 构造方法

`public Properties() `:创建一个空的属性列表。

#### 13.2 基本的存储方法

`public Object setProperty(String key, String value) `： 保存一对属性。
`public String getProperty(String key)` ：使用此属性列表中指定的键搜索属性值。
`public Set<String> stringPropertyNames() `：所有键的名称的集合

```java
/*
    java.util.Properties集合 extends Hashtable<k,v> implements Map<k,v>
    Properties 类表示了一个持久的属性集。Properties 可保存在流中或从流中加载。
    Properties集合是一个唯一和IO流相结合的集合
        可以使用Properties集合中的方法store,把集合中的临时数据,持久化写入到硬盘中存储
        可以使用Properties集合中的方法load,把硬盘中保存的文件(键值对),读取到集合中使用

    属性列表中每个键及其对应值都是一个字符串。
        Properties集合是一个双列集合,key和value默认都是字符串
 */
public class Demo01Properties {
    public static void main(String[] args) throws IOException {
        show03();
    }

    /*
        可以使用Properties集合中的方法load,把硬盘中保存的文件(键值对),读取到集合中使用
        void load(InputStream inStream)
        void load(Reader reader)
        参数:
            InputStream inStream:字节输入流,不能读取含有中文的键值对
            Reader reader:字符输入流,能读取含有中文的键值对
        使用步骤:
            1.创建Properties集合对象
            2.使用Properties集合对象中的方法load读取保存键值对的文件
            3.遍历Properties集合
        注意:
            1.存储键值对的文件中,键与值默认的连接符号可以使用=,空格(其他符号)
            2.存储键值对的文件中,可以使用#进行注释,被注释的键值对不会再被读取
            3.存储键值对的文件中,键与值默认都是字符串,不用再加引号
     */
    private static void show03() throws IOException {
        //1.创建Properties集合对象
        Properties prop = new Properties();
        //2.使用Properties集合对象中的方法load读取保存键值对的文件
        prop.load(new FileReader("09_IOAndProperties\\prop.txt"));
        //prop.load(new FileInputStream("09_IOAndProperties\\prop.txt"));
        //3.遍历Properties集合
        Set<String> set = prop.stringPropertyNames();
        for (String key : set) {
            String value = prop.getProperty(key);
            System.out.println(key+"="+value);
        }
    }

    /*
        可以使用Properties集合中的方法store,把集合中的临时数据,持久化写入到硬盘中存储
        void store(OutputStream out, String comments)
        void store(Writer writer, String comments)
        参数:
            OutputStream out:字节输出流,不能写入中文
            Writer writer:字符输出流,可以写中文
            String comments:注释,用来解释说明保存的文件是做什么用的
                    不能使用中文,会产生乱码,默认是Unicode编码
                    一般使用""空字符串

        使用步骤:
            1.创建Properties集合对象,添加数据
            2.创建字节输出流/字符输出流对象,构造方法中绑定要输出的目的地
            3.使用Properties集合中的方法store,把集合中的临时数据,持久化写入到硬盘中存储
            4.释放资源
     */
    private static void show02() throws IOException {
        //1.创建Properties集合对象,添加数据
        Properties prop = new Properties();
        prop.setProperty("赵丽颖","168");
        prop.setProperty("迪丽热巴","165");
        prop.setProperty("古力娜扎","160");

        //2.创建字节输出流/字符输出流对象,构造方法中绑定要输出的目的地
        //FileWriter fw = new FileWriter("09_IOAndProperties\\prop.txt");

        //3.使用Properties集合中的方法store,把集合中的临时数据,持久化写入到硬盘中存储
        //prop.store(fw,"save data");

        //4.释放资源
        //fw.close();

        prop.store(new FileOutputStream("prop2.txt"),"");
    }

    /*
        使用Properties集合存储数据,遍历取出Properties集合中的数据
        Properties集合是一个双列集合,key和value默认都是字符串
        Properties集合有一些操作字符串的特有方法
            Object setProperty(String key, String value) 调用 Hashtable 的方法 put。
            String getProperty(String key) 通过key找到value值,此方法相当于Map集合中的get(key)方法
            Set<String> stringPropertyNames() 返回此属性列表中的键集，其中该键及其对应值是字符串,此方法相当于Map集合中的keySet方法
     */
    private static void show01() {
        //创建Properties集合对象
        Properties prop = new Properties();
        //使用setProperty往集合中添加数据
        prop.setProperty("赵丽颖","168");
        prop.setProperty("迪丽热巴","165");
        prop.setProperty("古力娜扎","160");//都是字符串
        //prop.put(1,true);

        //使用stringPropertyNames把Properties集合中的键取出,存储到一个Set集合中
        Set<String> set = prop.stringPropertyNames();

        //遍历Set集合,取出Properties集合的每一个键
        for (String key : set) {
            //使用getProperty方法通过key获取value
            String value = prop.getProperty(key);
            System.out.println(key+"="+value);
        }
    }
}
```

## day10【缓冲流、转换流、序列化流、打印流】

### 1. 缓冲流

缓冲流,也叫高效流，是对4个基本的`FileXxx` 流的增强，所以也是4个流，按照数据类型分类：
**字节缓冲流**： `BufferedInputStream` ， `BufferedOutputStream`
**字符缓冲流**：` BufferedReader` ， `BufferedWriter`
缓冲流的基本原理，是在创建流对象时，会**创建一个内置的默认大小的缓冲区数组，通过缓冲区读写，减少系统IO次数**，从而提高读写的效率。

#### 1.1 字节缓冲流【BufferedOutputStream、BufferedInputStream】

输出流：

```java
/*
    java.io.BufferedOutputStream extends OutputStream
    BufferedOutputStream:字节缓冲输出流

    继承自父类的共性成员方法:
        - public void close() ：关闭此输出流并释放与此流相关联的任何系统资源。
        - public void flush() ：刷新此输出流并强制任何缓冲的输出字节被写出。
        - public void write(byte[] b)：将 b.length字节从指定的字节数组写入此输出流。
        - public void write(byte[] b, int off, int len) ：从指定的字节数组写入 len字节，从偏移量 off开始输出到此输出流。
        - public abstract void write(int b) ：将指定的字节输出流。

     构造方法:
        BufferedOutputStream(OutputStream out)  创建一个新的缓冲输出流，以将数据写入指定的底层输出流。
        BufferedOutputStream(OutputStream out, int size)  创建一个新的缓冲输出流，以将具有指定缓冲区大小的数据写入指定的底层输出流。
        参数:
           OutputStream out:字节输出流
                我们可以传递FileOutputStream,缓冲流会给FileOutputStream增加一个缓冲区,提高FileOutputStream的写入效率
           int size:指定缓冲流内部缓冲区的大小,不指定默认
     使用步骤(重点)
        1.创建FileOutputStream对象,构造方法中绑定要输出的目的地
        2.创建BufferedOutputStream对象,构造方法中传递FileOutputStream对象对象,提高FileOutputStream对象效率
        3.使用BufferedOutputStream对象中的方法write,把数据写入到内部缓冲区中
        4.使用BufferedOutputStream对象中的方法flush,把内部缓冲区中的数据,刷新到文件中
        5.释放资源(会先调用flush方法刷新数据,第4部可以省略)
 */
public class Demo01BufferedOutputStream {
    public static void main(String[] args) throws IOException {
        //1.创建FileOutputStream对象,构造方法中绑定要输出的目的地
        FileOutputStream fos = new FileOutputStream("10_IO\\a.txt");
        //2.创建BufferedOutputStream对象,构造方法中传递FileOutputStream对象对象,提高FileOutputStream对象效率
        BufferedOutputStream bos = new BufferedOutputStream(fos);
        //3.使用BufferedOutputStream对象中的方法write,把数据写入到内部缓冲区中
        bos.write("我把数据写入到内部缓冲区中".getBytes());
        //4.使用BufferedOutputStream对象中的方法flush,把内部缓冲区中的数据,刷新到文件中
        bos.flush();
        //5.释放资源(会先调用flush方法刷新数据,第4部可以省略)
        bos.close();
    }

}

```

输入流：

```java
/*
    java.io.BufferedInputStream extends InputStream
    BufferedInputStream:字节缓冲输入流

    继承自父类的成员方法:
        int read()从输入流中读取数据的下一个字节。
        int read(byte[] b) 从输入流中读取一定数量的字节，并将其存储在缓冲区数组 b 中。
        void close() 关闭此输入流并释放与该流关联的所有系统资源。

    构造方法:
        BufferedInputStream(InputStream in) 创建一个 BufferedInputStream 并保存其参数，即输入流 in，以便将来使用。
        BufferedInputStream(InputStream in, int size) 创建具有指定缓冲区大小的 BufferedInputStream 并保存其参数，即输入流 in，以便将来使用。
        参数:
            InputStream in:字节输入流
                我们可以传递FileInputStream,缓冲流会给FileInputStream增加一个缓冲区,提高FileInputStream的读取效率
            int size:指定缓冲流内部缓冲区的大小,不指定默认

    使用步骤(重点):
        1.创建FileInputStream对象,构造方法中绑定要读取的数据源
        2.创建BufferedInputStream对象,构造方法中传递FileInputStream对象,提高FileInputStream对象的读取效率
        3.使用BufferedInputStream对象中的方法read,读取文件
        4.释放资源
 */
public class Demo02BufferedInputStream {
    public static void main(String[] args) throws IOException {
        //1.创建FileInputStream对象,构造方法中绑定要读取的数据源
        FileInputStream fis = new FileInputStream("10_IO\\a.txt");
        //2.创建BufferedInputStream对象,构造方法中传递FileInputStream对象,提高FileInputStream对象的读取效率
        BufferedInputStream bis = new BufferedInputStream(fis);
        //3.使用BufferedInputStream对象中的方法read,读取文件
        //int read()从输入流中读取数据的下一个字节。
        /*int len = 0;//记录每次读取到的字节
        while((len = bis.read())!=-1){
            System.out.println(len);
        }*/

        //int read(byte[] b) 从输入流中读取一定数量的字节，并将其存储在缓冲区数组 b 中。
        byte[] bytes =new byte[1024];//存储每次读取的数据
        int len = 0; //记录每次读取的有效字节个数
        while((len = bis.read(bytes))!=-1){
            System.out.println(new String(bytes,0,len));
        }

        //4.释放资源
        bis.close();
    }
}

```

#### 1.2 字符缓冲流【BufferedWriter、BufferedReader】

输出的——写到——字符缓冲输出流：

```java
/*
    java.io.BufferedWriter extends Writer
    BufferedWriter:字符缓冲输出流

    继承自父类的共性成员方法:
        - void write(int c) 写入单个字符。
        - void write(char[] cbuf)写入字符数组。
        - abstract  void write(char[] cbuf, int off, int len)写入字符数组的某一部分,off数组的开始索引,len写的字符个数。
        - void write(String str)写入字符串。
        - void write(String str, int off, int len) 写入字符串的某一部分,off字符串的开始索引,len写的字符个数。
        - void flush()刷新该流的缓冲。
        - void close() 关闭此流，但要先刷新它。

    构造方法:
        BufferedWriter(Writer out) 创建一个使用默认大小输出缓冲区的缓冲字符输出流。
        BufferedWriter(Writer out, int sz) 创建一个使用给定大小输出缓冲区的新缓冲字符输出流。
        参数:
            Writer out:字符输出流
                我们可以传递FileWriter,缓冲流会给FileWriter增加一个缓冲区,提高FileWriter的写入效率
            int sz:指定缓冲区的大小,不写默认大小

    特有的成员方法:
        void newLine() 写入一个行分隔符。会根据不同的操作系统,获取不同的行分隔符
        换行:换行符号
        windows:\r\n
        linux:/n
        mac:/r
     使用步骤:
        1.创建字符缓冲输出流对象,构造方法中传递字符输出流
        2.调用字符缓冲输出流中的方法write,把数据写入到内存缓冲区中
        3.调用字符缓冲输出流中的方法flush,把内存缓冲区中的数据,刷新到文件中
        4.释放资源
 */
public class Demo03BufferedWriter {
    public static void main(String[] args) throws IOException {
        //System.out.println();//println调用了newLine()
        //1.创建字符缓冲输出流对象,构造方法中传递字符输出流
        BufferedWriter bw = new BufferedWriter(new FileWriter("10_IO\\c.txt"));
        //2.调用字符缓冲输出流中的方法write,把数据写入到内存缓冲区中
        for (int i = 0; i <10 ; i++) {
            bw.write("传智播客");
            //bw.write("\r\n");
            bw.newLine();
        }
        //3.调用字符缓冲输出流中的方法flush,把内存缓冲区中的数据,刷新到文件中
        bw.flush();
        //4.释放资源
        bw.close();
    }
}


```

字符缓冲输入流：

```java
/*
    java.io.BufferedReader extends Reader
    BufferedReader:字符缓冲输入流

    继承自父类的共性成员方法:
        int read() 读取单个字符并返回。
        int read(char[] cbuf)一次读取多个字符,将字符读入数组。
        void close() 关闭该流并释放与之关联的所有资源。

     构造方法:
        BufferedReader(Reader in)  创建一个使用默认大小输入缓冲区的缓冲字符输入流。
        BufferedReader(Reader in, int sz)     创建一个使用指定大小输入缓冲区的缓冲字符输入流。
        参数:
            Reader in:字符输入流
                我们可以传递FileReader,缓冲流会给FileReader增加一个缓冲区,提高FileReader的读取效率
     特有的成员方法:
        String readLine() 读取一个文本行。读取一行数据
            行的终止符号:通过下列字符之一即可认为某行已终止：换行 ('\n')、回车 ('\r') 或回车后直接跟着换行(\r\n)。
        返回值:
            包含该行内容的字符串，不包含任何行终止符，如果已到达流末尾，则返回 null

     使用步骤:
        1.创建字符缓冲输入流对象,构造方法中传递字符输入流
        2.使用字符缓冲输入流对象中的方法read/readLine读取文本
        3.释放资源
 */
public class Demo04BufferedReader {
    public static void main(String[] args) throws IOException {
        //1.创建字符缓冲输入流对象,构造方法中传递字符输入流
        BufferedReader br = new BufferedReader(new FileReader("10_IO\\c.txt"));

        //2.使用字符缓冲输入流对象中的方法read/readLine读取文本
        /*String line = br.readLine();
        System.out.println(line);

        line = br.readLine();
        System.out.println(line);

        line = br.readLine();
        System.out.println(line);

        line = br.readLine();
        System.out.println(line);*/

        /*
            发下以上读取是一个重复的过程,所以可以使用循环优化
            不知道文件中有多少行数据,所以使用while循环
            while的结束条件,读取到null结束
         */
        String line;
        while((line = br.readLine())!=null){
            System.out.println(line);
        }

        //3.释放资源
        br.close();
    }
}


```





### 2. 转换流

#### 2.1 字符编码和字符集

GBK两个字节存储一个汉字；UTF-8三个字节存储一个汉字。

#### 2.2 编码引出的问题

window中ANSI就是GBK编码，也是win系统默认编码

```java
/*
    FileReader可以读取IDE默认编码格式(UTF-8)的文件
    FileReader读取系统默认编码(中文GBK)会产生乱码���
 */
public class Demo01FileReader {
    public static void main(String[] args) throws IOException {
        FileReader fr = new FileReader("10_IO\\我是GBK格式的文本.txt");
        int len = 0;
        while((len = fr.read())!=-1){
            System.out.print((char)len);
        }
        fr.close();
    }
}
```

#### 2.4 OutputStreamWriter类

```java
/*
    java.io.OutputStreamWriter extends Writer
    OutputStreamWriter: 是字符流通向字节流的桥梁：可使用指定的 charset 将要写入流中的字符编码成字节。(编码:把能看懂的变成看不懂)

    继续自父类的共性成员方法:
        - void write(int c) 写入单个字符。
        - void write(char[] cbuf)写入字符数组。
        - abstract  void write(char[] cbuf, int off, int len)写入字符数组的某一部分,off数组的开始索引,len写的字符个数。
        - void write(String str)写入字符串。
        - void write(String str, int off, int len) 写入字符串的某一部分,off字符串的开始索引,len写的字符个数。
        - void flush()刷新该流的缓冲。
        - void close() 关闭此流，但要先刷新它。
    构造方法:
        OutputStreamWriter(OutputStream out)创建使用默认字符编码的 OutputStreamWriter。
        OutputStreamWriter(OutputStream out, String charsetName) 创建使用指定字符集的 OutputStreamWriter。
        参数:
            OutputStream out:字节输出流,可以用来写转换之后的字节到文件中
            String charsetName:指定的编码表名称,不区分大小写,可以是utf-8/UTF-8,gbk/GBK,...不指定默认使用UTF-8
    使用步骤:
        1.创建OutputStreamWriter对象,构造方法中传递字节输出流和指定的编码表名称
        2.使用OutputStreamWriter对象中的方法write,把字符转换为字节存储缓冲区中(编码)
        3.使用OutputStreamWriter对象中的方法flush,把内存缓冲区中的字节刷新到文件中(使用字节流写字节的过程)
        4.释放资源
 */
public class Demo02OutputStreamWriter {
    public static void main(String[] args) throws IOException {
        //write_utf_8();
        write_gbk();
    }

    /*
       使用转换流OutputStreamWriter写GBK格式的文件
    */
    private static void write_gbk() throws IOException {
        //1.创建OutputStreamWriter对象,构造方法中传递字节输出流和指定的编码表名称
        OutputStreamWriter osw = new OutputStreamWriter(new FileOutputStream("10_IO\\gbk.txt"),"GBK");
        //2.使用OutputStreamWriter对象中的方法write,把字符转换为字节存储缓冲区中(编码)
        osw.write("你好");
        //3.使用OutputStreamWriter对象中的方法flush,把内存缓冲区中的字节刷新到文件中(使用字节流写字节的过程)
        osw.flush();
        //4.释放资源
        osw.close();
    }

    /*
        使用转换流OutputStreamWriter写UTF-8格式的文件
     */
    private static void write_utf_8() throws IOException {
        //1.创建OutputStreamWriter对象,构造方法中传递字节输出流和指定的编码表名称
        //OutputStreamWriter osw = new OutputStreamWriter(new FileOutputStream("10_IO\\utf_8.txt"),"utf-8");
        OutputStreamWriter osw = new OutputStreamWriter(new FileOutputStream("10_IO\\utf_8.txt"));//不指定默认使用UTF-8
        //2.使用OutputStreamWriter对象中的方法write,把字符转换为字节存储缓冲区中(编码)
        osw.write("你好");
        //3.使用OutputStreamWriter对象中的方法flush,把内存缓冲区中的字节刷新到文件中(使用字节流写字节的过程)
        osw.flush();
        //4.释放资源
        osw.close();
    }
}



```

#### 2.4 InputStreamReader类

```java
/*
    java.io.InputStreamReader extends Reader
    InputStreamReader:是字节流通向字符流的桥梁：它使用指定的 charset 读取字节并将其解码为字符。(解码:把看不懂的变成能看懂的)

    继承自父类的共性成员方法:
        int read() 读取单个字符并返回。
        int read(char[] cbuf)一次读取多个字符,将字符读入数组。
        void close() 关闭该流并释放与之关联的所有资源。
    构造方法:
        InputStreamReader(InputStream in) 创建一个使用默认字符集的 InputStreamReader。
        InputStreamReader(InputStream in, String charsetName) 创建使用指定字符集的 InputStreamReader。
        参数:
            InputStream in:字节输入流,用来读取文件中保存的字节
            String charsetName:指定的编码表名称,不区分大小写,可以是utf-8/UTF-8,gbk/GBK,...不指定默认使用UTF-8
     使用步骤:
        1.创建InputStreamReader对象,构造方法中传递字节输入流和指定的编码表名称
        2.使用InputStreamReader对象中的方法read读取文件
        3.释放资源
     注意事项:
        构造方法中指定的编码表名称要和文件的编码相同,否则会发生乱码
 */
public class Demo03InputStreamReader {
    public static void main(String[] args) throws IOException {
        //read_utf_8();
        read_gbk();
    }


    /*
        使用InputStreamReader读取GBK格式的文件
     */
    private static void read_gbk() throws IOException {
        //1.创建InputStreamReader对象,构造方法中传递字节输入流和指定的编码表名称
        //InputStreamReader isr = new InputStreamReader(new FileInputStream("10_IO\\gbk.txt"),"UTF-8");//???
        InputStreamReader isr = new InputStreamReader(new FileInputStream("10_IO\\gbk.txt"),"GBK");//你好

        //2.使用InputStreamReader对象中的方法read读取文件
        int len = 0;
        while((len = isr.read())!=-1){
            System.out.println((char)len);
        }
        //3.释放资源
        isr.close();
    }

    /*
        使用InputStreamReader读取UTF-8格式的文件
     */
    private static void read_utf_8() throws IOException {
        //1.创建InputStreamReader对象,构造方法中传递字节输入流和指定的编码表名称
        //InputStreamReader isr = new InputStreamReader(new FileInputStream("10_IO\\utf_8.txt"),"UTF-8");
        InputStreamReader isr = new InputStreamReader(new FileInputStream("10_IO\\utf_8.txt"));//不指定默认使用UTF-8
        //2.使用InputStreamReader对象中的方法read读取文件
        int len = 0;
        while((len = isr.read())!=-1){
            System.out.println((char)len);
        }
        //3.释放资源
        isr.close();
    }
}

```

![image-20210228223340501](Java%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0.assets/转换流图解.png)





### 3. 【未重点看】 对象序列化与反序列化

用一个字节序列可以表示一个对象，该字节序列包含该`对象的数据`、`对象的类型`和`对象中存储的属性`等信息。字节序列写出到文件之后，相当于文件中持久保存了一个对象的信息。

反之，该字节序列还可以从文件中读取回来，重构对象，对它进行反序列化。`对象的数据`、`对象的类型`和`对象中存储的数据信息`，都可以用来在内存中创建对象。看图理解序列化：



![image-20210228223648844](Java%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0.assets/对象与字节的转换.png)





#### 3.1 ObjectOutputStream类

将Java对象的原始数据类型写出到文件,实现对象的持久存储。

构造方法：

`public ObjectOutputStream(OutputStream out) `： 创建一个指定OutputStream的ObjectOutputStream。

#### 3.2 ObjectInputStream类



### 4. 打印流

平时我们在控制台打印输出，是调用print 方法和println 方法完成的，这两个方法都来自于`java.io.PrintStream` 类，该类能够方便地打印各种数据类型的值，是一种便捷的输出方式。

```java
/*
    java.io.PrintStream:打印流
        PrintStream 为其他输出流添加了功能，使它们能够方便地打印各种数据值表示形式。
    PrintStream特点:
        1.只负责数据的输出,不负责数据的读取
        2.与其他输出流不同，PrintStream 永远不会抛出 IOException
        3.有特有的方法,print,println
            void print(任意类型的值)
            void println(任意类型的值并换行)
    构造方法:
        PrintStream(File file):输出的目的地是一个文件
        PrintStream(OutputStream out):输出的目的地是一个字节输出流
        PrintStream(String fileName) :输出的目的地是一个文件路径
    PrintStream extends OutputStream
    继承自父类的成员方法:
        - public void close() ：关闭此输出流并释放与此流相关联的任何系统资源。
        - public void flush() ：刷新此输出流并强制任何缓冲的输出字节被写出。
        - public void write(byte[] b)：将 b.length字节从指定的字节数组写入此输出流。
        - public void write(byte[] b, int off, int len) ：从指定的字节数组写入 len字节，从偏移量 off开始输出到此输出流。
        - public abstract void write(int b) ：将指定的字节输出流。
    注意:
        如果使用继承自父类的write方法写数据,那么查看数据的时候会查询编码表 97->a
        如果使用自己特有的方法print/println方法写数据,写的数据原样输出 97->97
 */
public class Demo01PrintStream {
    public static void main(String[] args) throws FileNotFoundException {
        //System.out.println("HelloWorld");

        //创建打印流PrintStream对象,构造方法中绑定要输出的目的地
        PrintStream ps = new PrintStream("10_IO\\print.txt");
        //如果使用继承自父类的write方法写数据,那么查看数据的时候会查询编码表 97->a
        ps.write(97);
        //如果使用自己特有的方法print/println方法写数据,写的数据原样输出 97->97
        ps.println(97);
        ps.println(8.8);
        ps.println('a');
        ps.println("HelloWorld");
        ps.println(true);

        //释放资源
        ps.close();
    }
}
```

**改变打印流向**:
`System.out `就是`PrintStream `类型的，只不过它的流向是系统规定的，打印在控制台上。不过，既然是流对象，我们就可以玩一个"小把戏"，改变它的流向。

```java
/*
    可以改变输出语句的目的地(打印流的流向)
    输出语句,默认在控制台输出
    使用System.setOut方法改变输出语句的目的地改为参数中传递的打印流的目的地
        static void setOut(PrintStream out)
          重新分配“标准”输出流。
 */
public class Demo02PrintStream {
    public static void main(String[] args) throws FileNotFoundException {
        System.out.println("我是在控制台输出");

        PrintStream ps = new PrintStream("10_IO\\目的地是打印流.txt");
        System.setOut(ps);//把输出语句的目的地改变为打印流的目的地
        System.out.println("我在打印流的目的地中输出");

        ps.close();
    }
}



```

## day11【网络编程】

### 1. 网络编程入门

#### 1.1 软件结构

* C/S结构：Client/Server结构，是指**客户端和服务器**结构。常见程序有ＱＱ、迅雷等软件。
* B/S结构：Browser/Server结构，是指**浏览器和服务器**结构。常见浏览器有谷歌、火狐等。

两种架构各有优势，但是无论哪种架构，都离不开网络的支持。网络编程，就是在一定的协议下，实现两台计算机的通信的程序。

#### 1.2 网络通信协议

TCP/IP协议： 传输控制协议/因特网互联协议( Transmission Control Protocol/Internet Protocol)，是Internet最基本、最广泛的协议。包含4层的分层模型。

![image-20210301125443513](Java%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0.assets/TCPIP协议的四层模型.png)

### 2. TCP通信程序

`java.net`类下

* 客户端Client 和 服务端Server，服务端不能主动连接客户端
* Java中两个类用于实现TCP通信程序：
  * 客户端：`java.net.Socket`类，创建`Socket`对象，向服务端发出连接请求，服务端响应请求，两者建立连接开始通信。
  * 服务端：`java.net.ServerSocket`类，创建`ServerSocket`对象，开启一个服务，等待客户端的连接请求。

#### 2.1 Socket类

* 实现客户端套接字。

* 套接字指的是两台设备之间通讯的端点，是包含了IP地址和端口号的网络单位。

**构造方法**：

`public Socket(String host, int port)`：创建套接字对象，并将其连接到 **指定主机**上的**指定端口号**。如果host是null，则指定地址是回送地址。**回送地址**(127.x.x.x) 是本机回送地址（Loopback Address），主要用于网络软件测试以及本地机进程间通信，无论什么程序，一旦使用回送地址发送数据，立即返回，不进行任何网络传输。

```java
Socket client = new Socket("127.0.0.1", 6666);
```

**成员方法**：

* `public InputStream getInputStream() `： 返回此套接字的输入流。
  * 如果此Scoket具有相关联的通道，则生成的InputStream 的所有操作也关联该通道。
  * 关闭生成的InputStream也将关闭相关的Socket。

* `public OutputStream getOutputStream() `： 返回此套接字的输出流。
  * 如果此Scoket具有相关联的通道，则生成的OutputStream 的所有操作也关联该通道。
  * 关闭生成的OutputStream也将关闭相关的Socket。
* `public void close()` ：关闭此套接字。
  * 一旦一个socket被关闭，它不可再使用。
  * 关闭此socket也将关闭相关的InputStream和OutputStream 。
* `public void shutdownOutput() `： 禁用此套接字的输出流。
  * 任何先前写出的数据将被发送，随后终止输出流。

#### 2.2 ServerSocket类

实现了服务器套接字，该对象等待通过网络的请求。

**构造方法**：

`public ServerSocket(int port)`：使用该构造方法在创建ServerSocket对象时，就可以将其绑定到一个指定的端口号上，参数port就是端口号。

```java
ServerSocket server = new ServerSocket(6666);
```

**成员方法**：

`public Socket accept`：侦听并接受连接，返回一个新的Socket对象，用于和客户端实现通信。该方法会阻塞直到建立连接。

#### 2.3 简单的TCP网络程序

TCP通信分析图解

1. 【服务端】启动,创建ServerSocket对象，等待连接。

2. 【客户端】启动,创建Socket对象，请求连接。

3. 【服务端】接收连接,调用accept方法，并返回一个Socket对象。

4. 【客户端】Socket对象，获取OutputStream，向服务端写出数据。

5. 【服务端】Scoket对象，获取InputStream，读取客户端发送的数据。
    **到此，客户端向服务端发送数据成功。**

  **自此，服务端向客户端回写数据。**

6. 【服务端】Socket对象，获取OutputStream，向客户端回写数据。

7. 【客户端】Scoket对象，获取InputStream，解析回写数据。

8. 【客户端】释放资源，断开连接。

   ![image-20210301135409560](Java%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0.assets/TCP通信分析图解.png)

代码：

```java
/*
    TCP通信的客户端:向服务器发送连接请求,给服务器发送数据,读取服务器回写的数据
    表示客户端的类:
        java.net.Socket:此类实现客户端套接字（也可以就叫“套接字”）。套接字是两台机器间通信的端点。
        套接字:包含了IP地址和端口号的网络单位

    构造方法:
        Socket(String host, int port) 创建一个流套接字并将其连接到指定主机上的指定端口号。
        参数:
            String host:服务器主机的名称/服务器的IP地址
            int port:服务器的端口号

    成员方法:
        OutputStream getOutputStream() 返回此套接字的输出流。
        InputStream getInputStream() 返回此套接字的输入流。
        void close() 关闭此套接字。

    实现步骤:
        1.创建一个客户端对象Socket,构造方法绑定服务器的IP地址和端口号
        2.使用Socket对象中的方法getOutputStream()获取网络字节输出流OutputStream对象
        3.使用网络字节输出流OutputStream对象中的方法write,给服务器发送数据
        4.使用Socket对象中的方法getInputStream()获取网络字节输入流InputStream对象
        5.使用网络字节输入流InputStream对象中的方法read,读取服务器回写的数据
        6.释放资源(Socket)
     注意:
        1.客户端和服务器端进行交互,必须使用Socket中提供的网络流,不能使用自己创建的流对象
        2.当我们创建客户端对象Socket的时候,就会去请求服务器和服务器经过3次握手建立连接通路
            这时如果服务器没有启动,那么就会抛出异常ConnectException: Connection refused: connect
            如果服务器已经启动,那么就可以进行交互了
 */
public class TCPClient {
    public static void main(String[] args) throws IOException {
        //1.创建一个客户端对象Socket,构造方法绑定服务器的IP地址和端口号
        Socket socket = new Socket("127.0.0.1",8888);
        //2.使用Socket对象中的方法getOutputStream()获取网络字节输出流OutputStream对象
        OutputStream os = socket.getOutputStream();
        //3.使用网络字节输出流OutputStream对象中的方法write,给服务器发送数据
        os.write("你好服务器".getBytes());

        //4.使用Socket对象中的方法getInputStream()获取网络字节输入流InputStream对象
        InputStream is = socket.getInputStream();

        //5.使用网络字节输入流InputStream对象中的方法read,读取服务器回写的数据
        byte[] bytes = new byte[1024];
        int len = is.read(bytes);
        System.out.println(new String(bytes,0,len));

        //6.释放资源(Socket)
        socket.close();

    }

}


```

```java
/*
    TCP通信的服务器端:接收客户端的请求,读取客户端发送的数据,给客户端回写数据
    表示服务器的类:
        java.net.ServerSocket:此类实现服务器套接字。

    构造方法:
        ServerSocket(int port) 创建绑定到特定端口的服务器套接字。

    服务器端必须明确一件事情,必须的知道是哪个客户端请求的服务器
    所以可以使用accept方法获取到请求的客户端对象Socket
    成员方法:
        Socket accept() 侦听并接受到此套接字的连接。

    服务器的实现步骤:
        1.创建服务器ServerSocket对象和系统要指定的端口号
        2.使用ServerSocket对象中的方法accept,获取到请求的客户端对象Socket
        3.使用Socket对象中的方法getInputStream()获取网络字节输入流InputStream对象
        4.使用网络字节输入流InputStream对象中的方法read,读取客户端发送的数据
        5.使用Socket对象中的方法getOutputStream()获取网络字节输出流OutputStream对象
        6.使用网络字节输出流OutputStream对象中的方法write,给客户端回写数据
        7.释放资源(Socket,ServerSocket)
 */
public class TCPServer {
    public static void main(String[] args) throws IOException {
        //1.创建服务器ServerSocket对象和系统要指定的端口号
        ServerSocket server = new ServerSocket(8888);
        //2.使用ServerSocket对象中的方法accept,获取到请求的客户端对象Socket
        Socket socket = server.accept();
        //3.使用Socket对象中的方法getInputStream()获取网络字节输入流InputStream对象
        InputStream is = socket.getInputStream();
        //4.使用网络字节输入流InputStream对象中的方法read,读取客户端发送的数据
        byte[] bytes = new byte[1024];
        int len = is.read(bytes);
        System.out.println(new String(bytes,0,len));
        //5.使用Socket对象中的方法getOutputStream()获取网络字节输出流OutputStream对象
        OutputStream os = socket.getOutputStream();
        //6.使用网络字节输出流OutputStream对象中的方法write,给客户端回写数据
        os.write("收到谢谢".getBytes());
        //7.释放资源(Socket,ServerSocket)
        socket.close();
        server.close();
    }
}

```

#### 2.4 记住常用端口

本地ip:   127.0.0.1   端口： 8888

网络端口 80端口

数据库  mysql:3306  

oracle:1521

tomcat:  8080

redis: 6379

## day12【函数式接口】

### 1. 函数式接口

* 在Java中是指：**有且仅有一个抽象方法的接口**。

* Java中的函数式编程体现就是Lambda
* 使用@FunctionalInterface注解。一旦使用该注解来定义接口，编译器将会强制检查该接口是否确实有且仅有一个抽象方法，否则将会报错。需要注意的是，即使不使用该注解，只要满足函数式接口的定义，这仍然是一个函数式接口，使用起来都一样。

```java
/*
    函数式接口:有且只有一个抽象方法的接口,称之为函数式接口
    当然接口中可以包含其他的方法(默认,静态,私有)

    @FunctionalInterface注解
    作用:可以检测接口是否是一个函数式接口
        是:编译成功
        否:编译失败(接口中没有抽象方法抽象方法的个数多余1个)
 */
@FunctionalInterface
public interface MyFunctionalInterface {
    //定义一个抽象方法
    public abstract void method();
}
```

函数式接口的使用：

```java
/*
    函数式接口的使用:一般可以作为方法的参数和返回值类型
 */
public class Demo {
    //定义一个方法,参数使用函数式接口MyFunctionalInterface
    public static void show(MyFunctionalInterface myInter){
        myInter.method();
    }

    public static void main(String[] args) {
        //调用show方法,方法的参数是一个接口,所以可以传递接口的实现类对象
        show(new MyFunctionalInterfaceImpl());

        //调用show方法,方法的参数是一个接口,所以我们可以传递接口的匿名内部类
        show(new MyFunctionalInterface() {
            @Override
            public void method() {
                System.out.println("使用匿名内部类重写接口中的抽象方法");
            }
        });

        //调用show方法,方法的参数是一个函数式接口,所以我们可以Lambda表达式
        show(()->{
            System.out.println("使用Lambda表达式重写接口中的抽象方法");
        });

        //简化Lambda表达式
        show(()-> System.out.println("使用Lambda表达式重写接口中的抽象方法"));
    }
}

// 接口的实现类
/*
    @Override注解
    检查方法是否为重写的方法
        是:编译成功
        否:编译失败
 */
public class MyFunctionalInterfaceImpl implements MyFunctionalInterface{
    @Override
    public void method() {

    }

    /*@Override
    public void method2() {

    }*/

    /*@Override
    public void method3() {

    }*/
}
// 接口
/*
    函数式接口:有且只有一个抽象方法的接口,称之为函数式接口
    当然接口中可以包含其他的方法(默认,静态,私有)

    @FunctionalInterface注解
    作用:可以检测接口是否是一个函数式接口
        是:编译成功
        否:编译失败(接口中没有抽象方法抽象方法的个数多余1个)
 */
@FunctionalInterface
public interface MyFunctionalInterface {
    //定义一个抽象方法
    public abstract void method();
}
```





### 2. 函数式编程

#### 2.1 代码的性能浪费案例

```java
/*
    日志案例

    发现以下代码存在的一些性能浪费的问题
    调用showLog方法,传递的第二个参数是一个拼接后的字符串
    先把字符串拼接好,然后在调用showLog方法
    showLog方法中如果传递的日志等级不是1级
    那么就不会是如此拼接后的字符串
    所以感觉字符串就白拼接了,存在了浪费
 */
public class Demo01Logger {
    //定义一个根据日志的级别,显示日志信息的方法
    public static void showLog(int level, String message){
        //对日志的等级进行判断,如果是1级别,那么输出日志信息
        if(level==1){
            System.out.println(message);
        }
    }

    public static void main(String[] args) {
        //定义三个日志信息
        String msg1 = "Hello";
        String msg2 = "World";
        String msg3 = "Java";

        //调用showLog方法,传递日志级别和日志信息
        showLog(2,msg1+msg2+msg3);

    }
}
```



#### 2.2 体验Lambda的更优写法

```java
/*
    使用Lambda优化日志案例
    Lambda的特点:延迟加载
    Lambda的使用前提,必须存在函数式接口
 */
public class Demo02Lambda {
    //定义一个显示日志的方法,方法的参数传递日志的等级和MessageBuilder接口
    public static void showLog(int level, MessageBuilder mb){
        //对日志的等级进行判断,如果是1级,则调用MessageBuilder接口中的builderMessage方法
        if(level==1){
            System.out.println(mb.builderMessage());
        }
    }

    public static void main(String[] args) {
        //定义三个日志信息
        String msg1 = "Hello";
        String msg2 = "World";
        String msg3 = "Java";

        //调用showLog方法,参数MessageBuilder是一个函数式接口,所以可以传递Lambda表达式
        /*showLog(2,()->{
            //返回一个拼接好的字符串
            return  msg1+msg2+msg3;
        });*/

        /*
            使用Lambda表达式作为参数传递,仅仅是把参数传递到showLog方法中
            只有满足条件,日志的等级是1级
                才会调用接口MessageBuilder中的方法builderMessage
                才会进行字符串的拼接
            如果条件不满足,日志的等级不是1级
                那么MessageBuilder接口中的方法builderMessage也不会执行
                所以拼接字符串的代码也不会执行
            所以不会存在性能的浪费
         */
        showLog(1,()->{
            System.out.println("不满足条件不执行");
            //返回一个拼接好的字符串
            return  msg1+msg2+msg3;
        });
    }
}

@FunctionalInterface
public interface MessageBuilder {
    //定义一个拼接消息的抽象方法,返回被拼接的消息
    public abstract String builderMessage();
}
```



#### 2.3 使用Lambda作为参数和返回值

* 使用函数式接口作为函数的参数：

```java
/*
    例如java.lang.Runnable接口就是一个函数式接口，
    假设有一个startThread方法使用该接口作为参数，那么就可以使用Lambda进行传参。
    这种情况其实和Thread类的构造方法参数为Runnable没有本质区别。
 */
public class Demo01Runnable {
    //定义一个方法startThread,方法的参数使用函数式接口Runnable
    public static void startThread(Runnable run){
        //开启多线程
        new Thread(run).start();
    }

    public static void main(String[] args) {
        //调用startThread方法,方法的参数是一个接口,那么我们可以传递这个接口的匿名内部类
        startThread(new Runnable() {
            @Override
            public void run() {
                System.out.println(Thread.currentThread().getName()+"-->"+"线程启动了");
            }
        });

        //调用startThread方法,方法的参数是一个函数式接口,所以可以传递Lambda表达式
        startThread(()->{
            System.out.println(Thread.currentThread().getName()+"-->"+"线程启动了");
        });

        //优化Lambda表达式
        // run方法没有参数
        startThread(()->System.out.println(Thread.currentThread().getName()+"-->"+"线程启动了"));
    }
}
```

* 使用函数式接口作为函数的返回值：

```java
/*
    如果一个方法的返回值类型是一个函数式接口，那么就可以直接返回一个Lambda表达式。
    当需要通过一个方法来获取一个java.util.Comparator接口类型的对象作为排序器时,就可以调该方法获取。
 */
public class Demo02Comparator {
    //定义一个方法,方法的返回值类型使用函数式接口Comparator
    public static Comparator<String> getComparator(){
        //方法的返回值类型是一个接口,那么我们可以返回这个接口的匿名内部类
        /*return new Comparator<String>() {
            @Override
            public int compare(String o1, String o2) {
                //按照字符串的降序排序
                return o2.length()-o1.length();
            }
        };*/

        //方法的返回值类型是一个函数式接口,所有我们可以返回一个Lambda表达式
        /*return (String o1, String o2)->{
            //按照字符串的降序排序
            return o2.length()-o1.length();
        };*/

        //继续优化Lambda表达式
        return (o1, o2)->o2.length()-o1.length();
    }

    public static void main(String[] args) {
        //创建一个字符串数组
        String[] arr = {"aaa","b","cccccc","dddddddddddd"};
        //输出排序前的数组
        System.out.println(Arrays.toString(arr));//[aaa, b, cccccc, dddddddddddd]
        //调用Arrays中的sort方法,对字符串数组进行排序
        Arrays.sort(arr,getComparator());
        //输出排序后的数组
        System.out.println(Arrays.toString(arr));//[dddddddddddd, cccccc, aaa, b]
    }

}

```





### 3. 常用函数式接口

#### 3.1 Supplier接口

案例1：

```java
/*
    常用的函数式接口
    java.util.function.Supplier<T>接口仅包含一个无参的方法：T get()。用来获取一个泛型参数指定类型的对象数据。

    Supplier<T>接口被称之为生产型接口,指定接口的泛型是什么类型,那么接口中的get方法就会生产什么类型的数据
 */
public class Demo01Supplier {
    //定义一个方法,方法的参数传递Supplier<T>接口,泛型执行String,get方法就会返回一个String
    public static String getString(Supplier<String> sup){
        return sup.get();
    }

    public static void main(String[] args) {
        //调用getString方法,方法的参数Supplier是一个函数式接口,所以可以传递Lambda表达式
        // get方法没有参数
        String s = getString(()->{
            //生产一个字符串,并返回
            return "胡歌";
        });
        System.out.println(s);

        //优化Lambda表达式
        String s2 = getString(()->"胡歌");
        System.out.println(s2);
    }
}
```

案例2：

```java
/*
    练习：求数组元素最大值
        使用Supplier接口作为方法参数类型，通过Lambda表达式求出int数组中的最大值。
        提示：接口的泛型请使用java.lang.Integer类。
 */
public class Demo02Test {
   //定义一个方法,用于获取int类型数组中元素的最大值,方法的参数传递Supplier接口,泛型使用Integer
   public static int getMax(Supplier<Integer> sup){
       return sup.get();
   }

    public static void main(String[] args) {
        //定义一个int类型的数组,并赋值
        int[] arr = {100,0,-50,880,99,33,-30};
        //调用getMax方法,方法的参数Supplier是一个函数式接口,所以可以传递Lambda表达式
        int maxValue = getMax(()->{
            //获取数组的最大值,并返回
            //定义一个变量,把数组中的第一个元素赋值给该变量,记录数组中元素的最大值
            int max = arr[0];
            //遍历数组,获取数组中的其他元素
            for (int i : arr) {
                //使用其他的元素和最大值比较
                if(i>max){
                    //如果i大于max,则替换max作为最大值
                    max = i;
                }
            }
            //返回最大值
            return max;
        });
        System.out.println("数组中元素的最大值是:"+maxValue);
    }
}
```



#### 3.2 Consumer接口

* 抽象方法：accept方法

```java
/*
    java.util.function.Consumer<T>接口则正好与Supplier接口相反，
        它不是生产一个数据，而是消费一个数据，其数据类型由泛型决定。
    Consumer接口中包含抽象方法void accept(T t)，意为消费一个指定泛型的数据。

   Consumer接口是一个消费型接口,泛型执行什么类型,就可以使用accept方法消费什么类型的数据
   至于具体怎么消费(使用),需要自定义(输出,计算....)
 */
public class Demo01Consumer {
    /*
        定义一个方法
        方法的参数传递一个字符串的姓名
        方法的参数传递Consumer接口,泛型使用String
        可以使用Consumer接口消费字符串的姓名
     */
    public static void method(String name, Consumer<String> con){
        con.accept(name);
    }

    public static void main(String[] args) {
        //调用method方法,传递字符串姓名,方法的另一个参数是Consumer接口,是一个函数式接口,所以可以传递Lambda表达式
        method("赵丽颖",(String name)->{
            //对传递的字符串进行消费
            //消费方式:直接输出字符串
            //System.out.println(name);

            //消费方式:把字符串进行反转输出
            String reName = new StringBuffer(name).reverse().toString();
            System.out.println(reName);
        });
    }
}
```

* 默认方法：andThen

  案例1：

```java
/*
   Consumer接口的默认方法andThen
   作用:需要两个Consumer接口,可以把两个Consumer接口组合到一起,在对数据进行消费

   例如:
    Consumer<String> con1
    Consumer<String> con2
    String s = "hello";
    con1.accept(s);
    con2.accept(s);
    连接两个Consumer接口  再进行消费
    con1.andThen(con2).accept(s); 谁写前边谁先消费
*/
public class Demo02AndThen {
    //定义一个方法,方法的参数传递一个字符串和两个Consumer接口,Consumer接口的泛型使用字符串
    public static void method(String s, Consumer<String> con1 ,Consumer<String> con2){
        //con1.accept(s);
        //con2.accept(s);
        //使用andThen方法,把两个Consumer接口连接到一起,在消费数据
        con1.andThen(con2).accept(s);//con1连接con2,先执行con1消费数据,在执行con2消费数据
    }

    public static void main(String[] args) {
        //调用method方法,传递一个字符串,两个Lambda表达式
        method("Hello",
                (t)->{
                    //消费方式:把字符串转换为大写输出
                    System.out.println(t.toUpperCase());
                },
                (t)->{
                    //消费方式:把字符串转换为小写输出
                    System.out.println(t.toLowerCase());
                });
    }
}

```

​	案例2：

```java
public class Test {

    public static void printInfo(String[] arr,Consumer<String> con1, Consumer<String> con2){
        for (String message:arr){
            con1.andThen(con2).accept(message);
        }
    }

    public static void main(String[] args) {
        String[] arr = {"迪丽热巴,女","古力娜扎,女","马尔扎哈,男"};
        printInfo(arr, (message)->{
            String name = message.split(",")[0];
            System.out.print("姓名："+name);
        },(message)->{
            String age = message.split(",")[1];
            System.out.println("。姓名："+age+"。");
        });
    }
}
姓名：迪丽热巴。姓名：女。
姓名：古力娜扎。姓名：女。
姓名：马尔扎哈。姓名：男。
```





#### 3.3 Predicate接口

* 抽象方法：test

  ```java
  /*
      java.util.function.Predicate<T>接口
      作用:对某种数据类型的数据进行判断,结果返回一个boolean值
  
      Predicate接口中包含一个抽象方法：
          boolean test(T t):用来对指定数据类型数据进行判断的方法
              结果:
                  符合条件,返回true
                  不符合条件,返回false
  */
  public class Demo01Predicate {
      /*
          定义一个方法
          参数传递一个String类型的字符串
          传递一个Predicate接口,泛型使用String
          使用Predicate中的方法test对字符串进行判断,并把判断的结果返回
       */
      public static boolean checkString(String s, Predicate<String> pre){
          return  pre.test(s);
      }
  
      public static void main(String[] args) {
          //定义一个字符串
          String s = "abcdef";
  
          //调用checkString方法对字符串进行校验,参数传递字符串和Lambda表达式
          /*boolean b = checkString(s,(String str)->{
              //对参数传递的字符串进行判断,判断字符串的长度是否大于5,并把判断的结果返回
              return str.length()>5;
          });*/
  
          //优化Lambda表达式
          boolean b = checkString(s,str->str.length()>5);
          System.out.println(b);
      }
  }
  
  ```

  

* 默认方法：and

  ```java
  /*
      逻辑表达式:可以连接多个判断的条件
      &&:与运算符,有false则false
      ||:或运算符,有true则true
      !:非(取反)运算符,非真则假,非假则真
  
      需求:判断一个字符串,有两个判断的条件
          1.判断字符串的长度是否大于5
          2.判断字符串中是否包含a
      两个条件必须同时满足,我们就可以使用&&运算符连接两个条件
  
      Predicate接口中有一个方法and,表示并且关系,也可以用于连接两个判断条件
      default Predicate<T> and(Predicate<? super T> other) {
          Objects.requireNonNull(other);
          return (t) -> this.test(t) && other.test(t);
      }
      方法内部的两个判断条件,也是使用&&运算符连接起来的
   */
  public class Demo02Predicate_and {
      /*
          定义一个方法,方法的参数,传递一个字符串
          传递两个Predicate接口
              一个用于判断字符串的长度是否大于5
              一个用于判断字符串中是否包含a
              两个条件必须同时满足
       */
      public static boolean checkString(String s, Predicate<String> pre1,Predicate<String> pre2){
          //return pre1.test(s) && pre2.test(s);
          return pre1.and(pre2).test(s);//等价于return pre1.test(s) && pre2.test(s);
      }
  
      public static void main(String[] args) {
          //定义一个字符串
          String s = "abcdef";
          //调用checkString方法,参数传递字符串和两个Lambda表达式
          boolean b = checkString(s,(String str)->{
              //判断字符串的长度是否大于5
              return str.length()>5;
          },(String str)->{
              //判断字符串中是否包含a
              return str.contains("a");
          });
          System.out.println(b);
      }
  }
  
  ```

  

* 默认方法：or

  ```java
  /*
       需求:判断一个字符串,有两个判断的条件
          1.判断字符串的长度是否大于5
          2.判断字符串中是否包含a
      满足一个条件即可,我们就可以使用||运算符连接两个条件
  
      Predicate接口中有一个方法or,表示或者关系,也可以用于连接两个判断条件
      default Predicate<T> or(Predicate<? super T> other) {
          Objects.requireNonNull(other);
          return (t) -> test(t) || other.test(t);
      }
      方法内部的两个判断条件,也是使用||运算符连接起来的
   */
  public class Demo03Predicate_or {
      /*
              定义一个方法,方法的参数,传递一个字符串
              传递两个Predicate接口
                  一个用于判断字符串的长度是否大于5
                  一个用于判断字符串中是否包含a
                  满足一个条件即可
           */
      public static boolean checkString(String s, Predicate<String> pre1, Predicate<String> pre2){
          //return pre1.test(s) || pre2.test(s);
          return  pre1.or(pre2).test(s);//等价于return pre1.test(s) || pre2.test(s);
      }
  
      public static void main(String[] args) {
          //定义一个字符串
          String s = "bc";
          //调用checkString方法,参数传递字符串和两个Lambda表达式
          boolean b = checkString(s,(String str)->{
              //判断字符串的长度是否大于5
              return str.length()>5;
          },(String str)->{
              //判断字符串中是否包含a
              return str.contains("a");
          });
          System.out.println(b);
      }
  }
  ```

  

* 默认方法：negate

  ```java
  /*
      需求:判断一个字符串长度是否大于5
          如果字符串的长度大于5,那返回false
          如果字符串的长度不大于5,那么返回true
      所以我们可以使用取反符号!对判断的结果进行取反
  
      Predicate接口中有一个方法negate,也表示取反的意思
      default Predicate<T> negate() {
          return (t) -> !test(t);
      }
   */
  public class Demo04Predicate_negate {
      /*
             定义一个方法,方法的参数,传递一个字符串
             使用Predicate接口判断字符串的长度是否大于5
      */
      public static boolean checkString(String s, Predicate<String> pre){
          //return !pre.test(s);
          return  pre.negate().test(s);//等效于return !pre.test(s);
      }
  
      public static void main(String[] args) {
          //定义一个字符串
          String s = "abc";
          //调用checkString方法,参数传递字符串和Lambda表达式
          boolean b = checkString(s,(String str)->{
              //判断字符串的长度是否大于5,并返回结果
              return str.length()>5;
          });
          System.out.println(b);
      }
  }
  
  ```

  

#### 3.4 Function接口

* 抽象方法：apply

  ```java
  /*
      java.util.function.Function<T,R>接口用来根据一个类型的数据得到另一个类型的数据，
          前者称为前置条件，后者称为后置条件。
      Function接口中最主要的抽象方法为：R apply(T t)，根据类型T的参数获取类型R的结果。
          使用的场景例如：将String类型转换为Integer类型。
   */
  public class Demo01Function {
      /*
          定义一个方法
          方法的参数传递一个字符串类型的整数
          方法的参数传递一个Function接口,泛型使用<String,Integer>
          使用Function接口中的方法apply,把字符串类型的整数,转换为Integer类型的整数
       */
      public static void change(String s, Function<String,Integer> fun){
          //Integer in = fun.apply(s);
          int in = fun.apply(s);//自动拆箱 Integer->int
          System.out.println(in);
      }
  
      public static void main(String[] args) {
          //定义一个字符串类型的整数
          String s = "1234";
          //调用change方法,传递字符串类型的整数,和Lambda表达式
          change(s,(String str)->{
              //把字符串类型的整数,转换为Integer类型的整数返回
              return Integer.parseInt(str);
          });
          //优化Lambda
          change(s,str->Integer.parseInt(str));
      }
  }
  
  ```

  

* 默认方法：andThen

  ```java
  /*
      Function接口中的默认方法andThen:用来进行组合操作
  
      需求:
          把String类型的"123",转换为Inteter类型,把转换后的结果加10
          把增加之后的Integer类型的数据,转换为String类型
  
      分析:
          转换了两次
          第一次是把String类型转换为了Integer类型
              所以我们可以使用Function<String,Integer> fun1
                  Integer i = fun1.apply("123")+10;
          第二次是把Integer类型转换为String类型
              所以我们可以使用Function<Integer,String> fun2
                  String s = fun2.apply(i);
          我们可以使用andThen方法,把两次转换组合在一起使用
              String s = fun1.andThen(fun2).apply("123");
              fun1先调用apply方法,把字符串转换为Integer
              fun2再调用apply方法,把Integer转换为字符串
   */
  public class Demo02Function_andThen {
      /*
          定义一个方法
          参数串一个字符串类型的整数
          参数再传递两个Function接口
              一个泛型使用Function<String,Integer>
              一个泛型使用Function<Integer,String>
       */
      public static void change(String s, Function<String,Integer> fun1,Function<Integer,String> fun2){
          String ss = fun1.andThen(fun2).apply(s);
          System.out.println(ss);
      }
  
      public static void main(String[] args) {
          //定义一个字符串类型的整数
          String s = "123";
          //调用change方法,传递字符串和两个Lambda表达式
          change(s,(String str)->{
              //把字符串转换为整数+10
              return Integer.parseInt(str)+10;
          },(Integer i)->{
              //把整数转换为字符串
              return i+"";
          });
  
          //优化Lambda表达式
          change(s,str->Integer.parseInt(str)+10,i->i+"");
      }
  }
  
  ```

  

## day13【Stream流、方法引用】

### 1. Stream流

IO流主要用于读写，Stream流用于对集合和数组做一些简化操作

#### 1.1 传统多步遍历与Stream流的对比

传统的多步循环遍历的弊端

```java
public class Test {
    public static void main(String[] args) {
        List<String> list = new ArrayList<>();
        list.add("张无忌");
        list.add("周芷若");
        list.add("赵敏");
        list.add("张强");
        list.add("张三丰");
        List<String> zhangList = new ArrayList<>();
        for (String name : list) {
            if (name.startsWith("张")) {
                zhangList.add(name);
            }
        }
        List<String> shortList = new ArrayList<>();
        for (String name : zhangList) {
            if (name.length() == 3) {
                shortList.add(name);
            }
        }
        for (String name : shortList) {
            System.out.println(name);
        }
    }
}

```

以上功能用Stream流写：

```java
public class Test {
    public static void main(String[] args) {
        List<String> list = new ArrayList<>();
        list.add("张无忌");
        list.add("周芷若");
        list.add("赵敏");
        list.add("张强");
        list.add("张三丰");
        list.stream()
                .filter(s -> s.startsWith("张"))
                .filter(s -> s.length() == 3)
                .forEach(name-> System.out.println(name));
    }
}
```

#### 1.2 流式思想概述

**注意：请暂时忘记对传统IO流的固有印象！**

![image-20210301195537145](Java%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0.assets/流式思想示意图.png)

这张图中展示了过滤、映射、跳过、计数等多步操作，这是一种集合元素的处理方案，而方案就是一种“函数模型”。图中的每一个方框都是一个“流”，调用指定的方法，可以从一个流模型转换为另一个流模型。而最右侧的数字3是最终结果。

* 这里的filter 、map 、skip 都是在对函数模型进行操作，**集合元素并没有真正被处理**。**只有当终结方法count执行的时候，整个模型才会按照指定策略执行操作**。

* “Stream流”其实是一个集合元素的**函数模型**，它并不是集合，也不是数据结构，其本身并**不存储任何元素（或其地址值）**。

* 和以前的Collection操作不同， Stream操作还有两个基础的特征：
  * Pipelining：中间操作都会返回流对象本身。 这样**多个操作可以串联成一个管道**， 如同流式风格（fluent style）。 这样做可以对操作进行优化， 比如延迟执行(laziness)和短路( short-circuiting)。
  * 内部迭代：以前对集合遍历都是通过Iterator或者增强for的方式, 显式的在集合外部进行迭代， 这叫做外部迭代。 Stream提供了内部迭代的方式，流可以**直接调用遍历方法**。
* 当使用一个流的时候，通常包括三个基本步骤：**获取一个数据源（source）→ 数据转换→执行操作获取想要的结果**，每次转换原有 Stream 对象不改变，返回一个新的 Stream 对象（可以有多次转换），这就允许对其操作可以像链条一样排列，变成一个管道。

#### 1.3 获取流

`java.util.stream.Stream<T> `是Java 8新加入的最常用的流接口。（这并不是一个函数式接口。）
获取一个流非常简单，有以下几种常用的方式：

* 所有的Collection 集合都可以通过stream 默认方法获取流；
* Stream 接口的静态方法of 可以获取数组对应的流。

```java
/*
    java.util.stream.Stream<T>是Java 8新加入的最常用的流接口。（这并不是一个函数式接口。）
    获取一个流非常简单，有以下几种常用的方式：
        - 所有的Collection集合都可以通过stream默认方法获取流；
            default Stream<E> stream​()
        - Stream接口的静态方法of可以获取数组对应的流。
            static <T> Stream<T> of​(T... values)
            参数是一个可变参数,那么我们就可以传递一个数组
 */
public class Demo01GetStream {
    public static void main(String[] args) {
        //把集合转换为Stream流
        List<String> list = new ArrayList<>();
        Stream<String> stream1 = list.stream();

        Set<String> set = new HashSet<>();
        Stream<String> stream2 = set.stream();

        Map<String,String> map = new HashMap<>();
        //获取键,存储到一个Set集合中
        Set<String> keySet = map.keySet();
        Stream<String> stream3 = keySet.stream();

        //获取值,存储到一个Collection集合中
        Collection<String> values = map.values();
        Stream<String> stream4 = values.stream();

        //获取键值对(键与值的映射关系 entrySet)
        Set<Map.Entry<String, String>> entries = map.entrySet();
        Stream<Map.Entry<String, String>> stream5 = entries.stream();

        //把数组转换为Stream流
        Stream<Integer> stream6 = Stream.of(1, 2, 3, 4, 5);
        //可变参数可以传递数组
        Integer[] arr = {1,2,3,4,5};
        Stream<Integer> stream7 = Stream.of(arr);
        String[] arr2 = {"a","bb","ccc"};
        Stream<String> stream8 = Stream.of(arr2);
    }
}

```

#### 1.4 常用方法

可以被分成两种：

* 延迟方法：返回值类型仍然是Stream 接口自身类型的方法，因此支持链式调用。（除了终结方法外，其余方法均为延迟方法。）
* 终结方法：返回值类型不再是Stream 接口自身类型的方法，因此不再支持类似StringBuilder 那样的链式调用。本小节中，终结方法包括`count `和`forEach` 方法。



**逐一处理：forEach**

```java
/*
    Stream流中的常用方法_forEach
    void forEach(Consumer<? super T> action);
    该方法接收一个Consumer接口函数，会将每一个流元素交给该函数进行处理。
    Consumer接口是一个消费型的函数式接口,可以传递Lambda表达式,消费数据

    简单记:
        forEach方法,用来遍历流中的数据
        是一个终结方法,遍历之后就不能继续调用Stream流中的其他方法
 */
public class Demo02Stream_forEach {
    public static void main(String[] args) {
        //获取一个Stream流
        Stream<String> stream = Stream.of("张三", "李四", "王五", "赵六", "田七");
        //使用Stream流中的方法forEach对Stream流中的数据进行遍历
        /*stream.forEach((String name)->{
            System.out.println(name);
        });*/

        stream.forEach(name->System.out.println(name));
    }
}
```

**过滤：filter**
可以通过filter 方法将一个流转换成另一个子集流

```java
/*
    Stream流中的常用方法_filter:用于对Stream流中的数据进行过滤
    Stream<T> filter(Predicate<? super T> predicate);
    filter方法的参数Predicate是一个函数式接口,所以可以传递Lambda表达式,对数据进行过滤
    Predicate中的抽象方法:
        boolean test(T t);
 */
public class Demo03Stream_filter {
    public static void main(String[] args) {
        //创建一个Stream流
        Stream<String> stream = Stream.of("张三丰", "张翠山", "赵敏", "周芷若", "张无忌");
        //对Stream流中的元素进行过滤,只要姓张的人
        Stream<String> stream2 = stream.filter((String name)->{return name.startsWith("张");});
        //遍历stream2流
        stream2.forEach(name-> System.out.println(name));

        /*
            Stream流属于管道流,只能被消费(使用)一次
            第一个Stream流调用完毕方法,数据就会流转到下一个Stream上
            而这时第一个Stream流已经使用完毕,就会关闭了
            所以第一个Stream流就不能再调用方法了
            IllegalStateException: stream has already been operated upon or closed
         */
        //遍历stream流
        stream.forEach(name-> System.out.println(name));
    }
}
```

**映射：map**：

```java
/*
    Stream流中的常用方法_map:用于类型转换
    如果需要将流中的元素映射到另一个流中，可以使用map方法.
    <R> Stream<R> map(Function<? super T, ? extends R> mapper);
    该接口需要一个Function函数式接口参数，可以将当前流中的T类型数据转换为另一种R类型的流。
    Function中的抽象方法:
        R apply(T t);
 */
public class Demo04Stream_map {
    public static void main(String[] args) {
        //获取一个String类型的Stream流
        Stream<String> stream = Stream.of("1", "2", "3", "4");
        //使用map方法,把字符串类型的整数,转换(映射)为Integer类型的整数
        Stream<Integer> stream2 = stream.map((String s)->{
            return Integer.parseInt(s);
        });
        //遍历Stream2流
        stream2.forEach(i-> System.out.println(i));
    }
}
```



**统计个数：count**：

```java
/*
    Stream流中的常用方法_count:用于统计Stream流中元素的个数
    long count();
    count方法是一个终结方法,返回值是一个long类型的整数
    所以不能再继续调用Stream流中的其他方法了
 */
public class Demo05Stream_count {
    public static void main(String[] args) {
        //获取一个Stream流
        ArrayList<Integer> list = new ArrayList<>();
        list.add(1);
        list.add(2);
        list.add(3);
        list.add(4);
        list.add(5);
        list.add(6);
        list.add(7);
        Stream<Integer> stream = list.stream();
        long count = stream.count();
        System.out.println(count);//7
    }
}

```

**取用前几个：limit**：

```java
/*
    Stream流中的常用方法_limit:用于截取流中的元素
    limit方法可以对流进行截取，只取用前n个。方法签名：
    Stream<T> limit(long maxSize);
        参数是一个long型，如果集合当前长度大于参数则进行截取；否则不进行操作
    limit方法是一个延迟方法,只是对流中的元素进行截取,返回的是一个新的流,所以可以继续调用Stream流中的其他方法
 */
public class Demo06Stream_limit {
    public static void main(String[] args) {
        //获取一个Stream流
        String[] arr = {"美羊羊","喜洋洋","懒洋洋","灰太狼","红太狼"};
        Stream<String> stream = Stream.of(arr);
        //使用limit对Stream流中的元素进行截取,只要前3个元素
        Stream<String> stream2 = stream.limit(3);
        //遍历stream2流
        stream2.forEach(name-> System.out.println(name));
    }
}

```

**跳过前几个：skip**：

```java
/*
    Stream流中的常用方法_skip:用于跳过元素
    如果希望跳过前几个元素，可以使用skip方法获取一个截取之后的新流：
    Stream<T> skip(long n);
        如果流的当前长度大于n，则跳过前n个；否则将会得到一个长度为0的空流。
 */
public class Demo07Stream_skip {
    public static void main(String[] args) {
        //获取一个Stream流
        String[] arr = {"美羊羊","喜洋洋","懒洋洋","灰太狼","红太狼"};
        Stream<String> stream = Stream.of(arr);
        //使用skip方法跳过前3个元素
        Stream<String> stream2 = stream.skip(3);
        //遍历stream2流
        stream2.forEach(name-> System.out.println(name));
    }
}

```

**组合：concat**
如果有两个流，希望合并成为一个流，那么可以使用Stream 接口的静态方法concat ：

```java
/*
    Stream流中的常用方法_concat:用于把流组合到一起
    如果有两个流，希望合并成为一个流，那么可以使用Stream接口的静态方法concat
    static <T> Stream<T> concat(Stream<? extends T> a, Stream<? extends T> b)
 */
public class Demo08Stream_concat {
    public static void main(String[] args) {
        //创建一个Stream流
        Stream<String> stream1 = Stream.of("张三丰", "张翠山", "赵敏", "周芷若", "张无忌");
        //获取一个Stream流
        String[] arr = {"美羊羊","喜洋洋","懒洋洋","灰太狼","红太狼"};
        Stream<String> stream2 = Stream.of(arr);
        //把以上两个流组合为一个流
        Stream<String> concat = Stream.concat(stream1, stream2);
        //遍历concat流
        concat.forEach(name-> System.out.println(name));
    }
}

```



### 2. 方法引用来优化Lambda表达式

#### 2.1 引出方法引用

以往的做法：

```java
public class Demo01Printable {
    //定义一个方法,参数传递Printable接口,对字符串进行打印
    public static void printString(Printable p) {
        p.print("HelloWorld");
    }

    public static void main(String[] args) {
        //调用printString方法,方法的参数Printable是一个函数式接口,所以可以传递Lambda
        printString((s) -> {
            System.out.println(s);
        });

        /*
            分析:
                Lambda表达式的目的,打印参数传递的字符串
                把参数s,传递给了System.out对象,调用out对象中的方法println对字符串进行了输出
                注意:
                    1.System.out对象是已经存在的
                    2.println方法也是已经存在的
                所以我们可以使用方法引用来优化Lambda表达式
                可以使用System.out方法直接引用(调用)println方法
         */
        printString(System.out::println);
    }
}

/*
    定义一个打印的函数式接口
 */
@FunctionalInterface
public interface Printable {
    //定义字符串的抽象方法
    void print(String s);
}
```

上面这段代码的问题在于，对字符串进行控制台打印输出的操作方案，明明已经有了现成的实现，那就是`System.out`对象中的`println(String) `方法。既然Lambda希望做的事情就是调用println(String) 方法，那何必自己手动调用呢？

如果Lambda要表达的函数方案已经存在于某个方法的实现中，那么则可以通过双冒号来引用该方法作为Lambda的替代者。

```java
public class Demo01Printable {
    //定义一个方法,参数传递Printable接口,对字符串进行打印
    public static void printString(Printable p) {
        p.print("HelloWorld");
    }

    public static void main(String[] args) {
        //调用printString方法,方法的参数Printable是一个函数式接口,所以可以传递Lambda
        printString((s) -> {
            System.out.println(s);
        });

        /*
            分析:
                Lambda表达式的目的,打印参数传递的字符串
                把参数s,传递给了System.out对象,调用out对象中的方法println对字符串进行了输出
                注意:
                    1.System.out对象是已经存在的
                    2.println方法也是已经存在的
                所以我们可以使用方法引用来优化Lambda表达式
                可以使用System.out方法直接引用(调用)println方法
         */
        printString(System.out::println);
    }
}
```

#### 2.2 方法引用符

双冒号`::` 为引用运算符，而它所在的表达式被称为方法引用。

`System.out `对象中有一个重载的`println(String) `方法恰好就是我们所需要的。那么对于
`printString` 方法的函数式接口参数，对比下面两种写法，完全等效：

* Lambda表达式写法： s -> System.out.println(s);
* 方法引用写法： System.out::println

第一种语义是指：拿到参数之后经Lambda之手，继而传递给`System.out.println `方法去处理。
第二种等效写法的语义是指：直接让`System.out` 中的`println `方法来取代Lambda。两种写法的执行效果完全一样，而第二种方法引用的写法复用了已有方案，更加简洁。
注:Lambda 中 传递的参数 一定是方法引用中 的那个方法可以接收的类型,否则会抛出异常

#### 2.3 通过对象名引用成员方法

```java
/*
    通过对象名引用成员方法
    使用前提是对象名是已经存在的,成员方法也是已经存在
    就可以使用对象名来引用成员方法
 */
public class Demo01ObjectMethodReference {
    //定义一个方法,方法的参数传递Printable接口
    public static void printString(Printable p){
        p.print("Hello");
    }

    public static void main(String[] args) {
        //调用printString方法,方法的参数Printable是一个函数式接口,所以可以传递Lambda表达式
        printString((s)->{
            //创建MethodRerObject对象
            MethodRerObject obj = new MethodRerObject();
            //调用MethodRerObject对象中的成员方法printUpperCaseString,把字符串按照大写输出
            obj.printUpperCaseString(s);
        });

        /*
            使用方法引用优化Lambda
            对象是已经存在的MethodRerObject
            成员方法也是已经存在的printUpperCaseString
            所以我们可以使用对象名引用成员方法
         */
        //创建MethodRerObject对象
        MethodRerObject obj = new MethodRerObject();
        printString(obj::printUpperCaseString);
    }
}

public class MethodRerObject {
    //定义一个成员方法,传递字符串,把字符串按照大写输出
    public void printUpperCaseString(String str){
        System.out.println(str.toUpperCase());
    }
}

/*
    定义一个打印的函数式接口
 */
@FunctionalInterface
public interface Printable {
    //定义字符串的抽象方法
    void print(String s);
}
```

#### 2.4 通过类名引用静态方法

```java
/*
    通过类名引用静态成员方法
    类已经存在,静态成员方法也已经存在
    就可以通过类名直接引用静态成员方法
 */
public class Demo01StaticMethodReference {
    //定义一个方法,方法的参数传递要计算绝对值的整数,和函数式接口Calcable
    public static int method(int number,Calcable c){
       return c.calsAbs(number);
    }

    public static void main(String[] args) {
        //调用method方法,传递计算绝对值得整数,和Lambda表达式
        int number = method(-10,(n)->{
            //对参数进行绝对值得计算并返回结果
            return Math.abs(n);
        });
        System.out.println(number);

        /*
            使用方法引用优化Lambda表达式
            Math类是存在的
            abs计算绝对值的静态方法也是已经存在的
            所以我们可以直接通过类名引用静态方法
         */
        int number2 = method(-10,Math::abs);
        System.out.println(number2);
    }
}


@FunctionalInterface
public interface Calcable {
    //定义一个抽象方法,传递一个整数,对整数进行绝对值计算并返回
    int calsAbs(int number);
}
```

#### 2.5 通过super引用成员方法

```java
/*
    定义子类
 */
public class Man extends Human{
    //子类重写父类sayHello的方法
    @Override
    public void sayHello() {
        System.out.println("Hello 我是Man!");
    }

    //定义一个方法参数传递Greetable接口
    public void method(Greetable g){
        g.greet();
    }

    public void show(){
        //调用method方法,方法的参数Greetable是一个函数式接口,所以可以传递Lambda
        /*method(()->{
            //创建父类Human对象
            Human h = new Human();
            //调用父类的sayHello方法
            h.sayHello();
        });*/

        //因为有子父类关系,所以存在的一个关键字super,代表父类,所以我们可以直接使用super调用父类的成员方法
       /* method(()->{
            super.sayHello();
        });*/

      /*
           使用super引用类的成员方法
           super是已经存在的
           父类的成员方法sayHello也是已经存在的
           所以我们可以直接使用super引用父类的成员方法
       */
      method(super::sayHello);
    }

    public static void main(String[] args) {
        new Man().show();
    }
}

/*
    定义父类
 */
public class Human {
    //定义一个sayHello的方法
    public void sayHello(){
        System.out.println("Hello 我是Human!");
    }
}
/*
    定义见面的函数式接口
 */
@FunctionalInterface
public interface Greetable {
    //定义一个见面的方法
    void greet();
}
```

#### 2.6 通过this引用成员方法

```java
/*
    使用this引用本类的成员方法
 */
public class Husband {
    //定义一个买房子的方法
    public void buyHouse(){
        System.out.println("北京二环内买一套四合院!");
    }

    //定义一个结婚的方法,参数传递Richable接口
    public void marry(Richable r){
        r.buy();
    }

    //定义一个非常高兴的方法
    public void soHappy(){
        //调用结婚的方法,方法的参数Richable是一个函数式接口,传递Lambda表达式
       /* marry(()->{
            //使用this.成员方法,调用本类买房子的方法
            this.buyHouse();
        });*/

        /*
            使用方法引用优化Lambda表达式
            this是已经存在的
            本类的成员方法buyHouse也是已经存在的
            所以我们可以直接使用this引用本类的成员方法buyHouse
         */
        marry(this::buyHouse);
    }

    public static void main(String[] args) {
        new Husband().soHappy();
    }
}

/*
    定义一个富有的函数式接口
 */
@FunctionalInterface
public interface Richable {
    //定义一个想买什么就买什么的方法
    void buy();
}
```

#### 2.7 类的构造器引用

由于构造器的名称与类名完全一样，并不固定。所以构造器引用使用类名称`::new` 的格式表示

```java
/*
    类的构造器(构造方法)引用
 */
public class Demo {
    //定义一个方法,参数传递姓名和PersonBuilder接口,方法中通过姓名创建Person对象
    public static void printName(String name,PersonBuilder pb){
        Person person = pb.builderPerson(name);
        System.out.println(person.getName());
    }

    public static void main(String[] args) {
        //调用printName方法,方法的参数PersonBuilder接口是一个函数式接口,可以传递Lambda
        printName("迪丽热巴",(String name)->{
            return new Person(name);
        });

        /*
            使用方法引用优化Lambda表达式
            构造方法new Person(String name) 已知
            创建对象已知 new
            就可以使用Person引用new创建对象
         */
        printName("古力娜扎",Person::new);//使用Person类的带参构造方法,通过传递的姓名创建对象
    }
}

/*
    定义一个创建Person对象的函数式接口
 */
@FunctionalInterface
public interface PersonBuilder {
    //定义一个方法,根据传递的姓名,创建Person对象返回
    Person builderPerson(String name);
}

public class Person {
    private String name;

    public Person() {
    }

    public Person(String name) {
        this.name = name;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }
}
```

#### 2.8 数组的构造器引用

数组也是Object 的子类对象，所以同样具有构造器，只是语法稍有不同。

```java
/*
    数组的构造器引用
 */
public class Demo {
    /*
        定义一个方法
        方法的参数传递创建数组的长度和ArrayBuilder接口
        方法内部根据传递的长度使用ArrayBuilder中的方法创建数组并返回
     */
    public static int[] createArray(int length, ArrayBuilder ab){
        return  ab.builderArray(length);
    }

    public static void main(String[] args) {
        //调用createArray方法,传递数组的长度和Lambda表达式
        int[] arr1 = createArray(10,(len)->{
            //根据数组的长度,创建数组并返回
            return new int[len];
        });
        System.out.println(arr1.length);//10

        /*
            使用方法引用优化Lambda表达式
            已知创建的就是int[]数组
            数组的长度也是已知的
            就可以使用方法引用
            int[]引用new,根据参数传递的长度来创建数组
         */
        int[] arr2 =createArray(10,int[]::new);
        System.out.println(Arrays.toString(arr2));
        System.out.println(arr2.length);//10
    }
}

/*
    定义一个创建数组的函数式接口
 */
@FunctionalInterface
public interface ArrayBuilder {
    //定义一个创建int类型数组的方法,参数传递数组的长度,返回创建好的int类型数组
    int[] builderArray(int length);
}
```

