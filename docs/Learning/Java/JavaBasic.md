# java_note

# class 规则

1. class名称一定要跟文件名相同
2. class名称一定要大写英文字母当开头
3. public static void main(String[] args)会被执行 这是java的规定

# 创建数组

Java语言使用new操作符来创建数组，语法如下：

~~~java
arrayRefVar = new dataType[arraySize];
~~~

上面的语法语句做了两件事：

- 一、使用 dataType[arraySize] 创建了一个数组。
- 二、把新创建的数组的引用赋值给变量 arrayRefVar。

数组变量的声明，和创建数组可以用一条语句完成，如下所示：

```java
dataType[] arrayRefVar = new dataType[arraySize];
```

数组变量的声明，和创建数组可以用一条语句完成，如下所示：

dataType[] arrayRefVar = new dataType[arraySize];

# Return Value 返回值

![image-20221218015410707](/Users/chenduo/Library/Application Support/typora-user-images/image-20221218015410707.png)

- break 和 return 区别

  假如现在有两层循环

  return会结束自己循环和外层循环

  break结束自己循环但是不会结束外层循环

# Reference  Date type

没有定义数据属性的，java会自动执行 copy value

![image-20221218144837947](/Users/chenduo/Library/Application Support/typora-user-images/image-20221218144837947.png)

# String型に変換するvalueOfメソッドとtoStringメソッドについて

## valueOf()

~~~java
String.valueOf(変換する値);

public class Main {
    public static void main(String[] args) throws Exception {

       // short型からString型に変換する
        short sh = 100;
        String strsh = String.valueOf(sh);
        System.out.println("short型からString型 : " + strsh);

        // int型からString型に変換する
        int num = 100;
        String strnum = String.valueOf(num);
        System.out.println("int型からString型 : " + strnum);

        // long型からString型に変換する
        long lon = 100;
        String strlon = String.valueOf(lon);
        System.out.println("long型からString型 : " + strlon);

        // float型からString型に変換する
        float fl = 100;
        String strfl = String.valueOf(fl);
        System.out.println("float型からString型 : " + strfl);

        // double型からString型に変換する
        double db = 100;
        String strdb = String.valueOf(db);
        System.out.println("double型からString型 : " + strdb);
    }
}
~~~

~~~tex
short型からString型 : 100
int型からString型 : 100
long型からString型 : 100
float型からString型 : 100.0
double型からString型 : 100.0
~~~

## toString

~~~java
public class Main {
  pubic static void main(String[] args) {
    int num1 = 1234;
    int num2 = 5678;
    System.out.println(num1 + num2);

    // 数値を文字列に変換する
    String str1 = Integer.toString(num1);
    String str2 = Integer.toString(num2);
    System.out.println(str1 + str2);
  }
}
~~~

~~~tex
6912
12345678
~~~

- 基本的にはメソッドの目的は同じであるが、変換する対象の値が**nullの場合の動作が異なる**。Integer型の値にnullを設定してString型に変換する場合、valueOfメソッドの場合はString型のnullを返すが、toStringメソッドの場合はnull参照時の例外が発生する。なので、**toStringメソッドを使用する場合は変換する値がnullでどうか確かめる**必要がある。

#  Character.getNumericValue（）

getNumericValue 获得字符的int值。

~~~java
import java.lang.*;

public class CharacterDemo {

   public static void main(String[] args) {

      // create 2 character primitives ch1, ch2
      char ch1, ch2;

      // assign values to ch1, ch2
      ch1 = 'j';
      ch2 = '4';

      // create 2 int primitives i1, i2
      int i1, i2;

      // assign numeric values of ch1, ch2 to i1, i2
      i1 = Character.getNumericValue(ch1);
      i2 = Character.getNumericValue(ch2);

      String str1 = "Numeric value of " + ch1 + " is " + i1;
      String str2 = "Numeric value of " + ch2 + " is " + i2;

      // print i1, i2 values
      System.out.println( str1 );
      System.out.println( str2 );
   }
}

~~~

~~~
Numeric value of j is 19
Numeric value of 4 is 4
~~~

方法返回特定字符的int值。字母 A-Z, a-z ，以及全宽变体的数值从10到35. 该方法和Unicode表示独立。

如何字符没有数值，返回 -1，如何数值不能表示成正数，返回 -2.

# charAt() 获取文字列第几位

