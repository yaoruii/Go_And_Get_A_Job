1，面向对象的编程：根据分析问题时发现的对象设计应用程序。类是对现实世界的抽象，对象是类的实例化，对象是组成程序的基本模块。

2,java关键字：boolean	byte	char	double	float	int	long，short	null	true	false	
基本类型是，对应的Integer,character不是。[所有的总结](http://cyw3.github.io/YalesonChan/2016/Java-key.html)

3，public static void main(string[] args):String第一个字母大写。

4，空引用（null）可用于访问**静态变量或方法** ？：可以，调用静态成员或方法的时候不需要实例，静态方法不属于对象，属于类本身，

5，double a2 =(float)a1：编译不会报错：小转大可以，大转小不可以：

6，采用"666"这种字面量的方式创建字符串，会将其自动地放入string pool中，并且两个对象如果都是“666”，那么他们是相同的引用。（看是否是相同的引用：直接使用==)

7,调用string1.intern()的时候，从string pool中看是否已经存在和string1 equal()的字符串，如果存在，就返回该存在的字符串，否则将其放入到string pool中，并返回新字符串的引用。

8，[string的常量池](https://tech.meituan.com/2014/03/06/in-depth-understanding-string-intern.html):1,直接使用双引号声明出来的String对象会直接存储在常量池中。2,如果不是用双引号声明的String对象，可以使用String提供的intern方法。intern 方法会从字符串常量池中查询当前字符串是否存在，若不存在就会将当前字符串放入常量池中
接下来我们主要来谈一下String#intern方法。

9, ![](https://tva1.sinaimg.cn/large/00831rSTgy1gdana0t07lj30v60elmys.jpg)
