1，面向对象的编程：根据分析问题时发现的对象设计应用程序。类是对现实世界的抽象，对象是类的实例化，对象是组成程序的基本模块。

2,java关键字：boolean	byte	char	double	float	int	long，short	null	true	false	
基本类型是，对应的Integer,character不是。[所有的总结](http://cyw3.github.io/YalesonChan/2016/Java-key.html)

3，public static void main(string[] args):String第一个字母大写。

4，空引用（null）可用于访问**静态变量或方法** ？：可以，调用静态成员或方法的时候不需要实例，静态方法不属于对象，属于类本身，

5，double a2 =(float)a1：编译不会报错：小转大可以，大转小不可以：**隐式类型转换：**
* short s1 = 1：1这个字面量是int类型，比short精度要高，所以不可以将其隐式地向下转换为short。
* 复合运算会执行隐式符合运算：A compound assignment expression of the form E1 op= E2 is equivalent to E1 = (T)((E1) op (E2)), where T is the type of E1, except that E1 is evaluated only once.
* 1.1f 字面量才是 float 类型。float f = 1.1：是错的，1.1字面量是double，比float精度大。

6，采用"666"这种字面量的方式创建字符串，会将其自动地放入string pool中，并且两个对象如果都是“666”，那么他们是相同的引用。（看是否是相同的引用：直接使用==)

7,调用string1.intern()的时候，从string pool中看是否已经存在和string1 equal()的字符串，如果存在，就返回该存在的字符串，否则将其放入到string pool中，并返回新字符串的引用。

8，[string的常量池](https://tech.meituan.com/2014/03/06/in-depth-understanding-string-intern.html):1,直接使用双引号声明出来的String对象会直接存储在常量池中。2,如果不是用双引号声明的String对象，可以使用String提供的intern方法。intern 方法会从字符串常量池中查询当前字符串是否存在，若不存在就会将当前字符串放入常量池中
接下来我们主要来谈一下String#intern方法。

9, ![](https://tva1.sinaimg.cn/large/00831rSTgy1gdana0t07lj30v60elmys.jpg)
从这张图中可以看出：
* 是 jdk7 中常量池不在 Perm 区域了，这块做了调整。常量池中不需要再存储一份对象了，**可以直接存储堆中的引用**。这份引用指向 s3 引用的对象。 也就是说引用地址是相同的
* String s = new String("1"); **第一句代码，生成了2个对象：常量池中的“1” 和 JAVA Heap 中的字符串对象。s.intern(); 这一句是 s 对象去常量池中寻找后发现 “1” 已经在常量池里了。**
* 接下来String s2 = "1"; 这句代码是生成一个 s2的引用指向常量池中的“1”对象。 结果就是 s 和 s2 的引用地址明显不同：

10，从 Java 7 开始，可以在 switch 条件判断语句中使用 String 对象。一直都可以的：byte、short、int 或者 char

11，switch case 语句中的值的数据类型必须与变量的数据类型相同，而且只能是常量或者字面常量。

## 关键字
### final
#### 数据：
1，声明数据是常量，可以是编译时是常量，也可以是运行时初始化后不能改变的量。

2，基本类型是数值不变，引用类型是引用不变。但是被引用的对象可以本身可以修改，就是不能再引用其他对象。
#### 方法：
1，方法不能被子类重写，private 方法隐式地被指定为 final，如果在子类中定义的方法和基类中的一个 private 方法签名相同，此时子类的方法不是重写基类方法，而是在子类中定义了一个新的方法。
#### 类：
1，声明该类不能被继承

### static
#### 静态变量：
1，又称为类变量，这个变量属于类。类的所有实例都共享静态变量，可以直接通过类名访问它，不需要再实例化一个对象。静态变量在内存中只存在一份。

2，实例变量：每创建一个实例就会产生一个实例变量，它与该实例同生共死。

#### 静态方法：
1，静态方法在类加载的时候就存在了，它不依赖于任何实例。所以静态方法必须有实现，也就是说它不能是抽象方法。

2，静态方法中：Non-static field 'y' cannot be referenced from a static context，非静态的数据不能被引用。方法中不能有 this 和 super 关键字，因此这两个关键字与具体对象关联。
#### 静态语句块：语句块：{}括起来的内容
```
public class A {
    static {
        System.out.println("123");
    }

    public static void main(String[] args) {
        A a1 = new A();
        A a2 = new A();
    }
}
```
1，在类初始化的时候运行一次，输出123
 #### 静态内部类：
 1，非静态内部类依赖于外部类的实例，也就是说需要先创建外部类实例，才能用这个实例去创建非静态内部类。InnerClass innerClass = outerClass.new InnerClass();
 
 2，而静态内部类不需要。StaticInnerClass staticInnerClass = new StaticInnerClass();
 
 3，静态内部类不能访问外部类的非静态的变量和方法。
 #### 静态导包：
 1，在使用静态变量和方法时不用再指明 ClassName，从而简化代码，但可读性大大降低。？？？？？？？？？
 
 #### 初始化顺序：
 1，**静态变量和静态语句块优先于实例变量和普通语句块，最后才是构造函数的初始化**，静态变量和静态语句块的初始化顺序取决于它们在代码中的顺序。
 
 ## Object的通用方法：
 
 
 
