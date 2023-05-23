# Reading 1 Static Checking

鉴于本人学习MIT网站时发现无法提交CHECK,给出我自己对文章中题目的理解

## 练习1
```java
int n = -5;
if (n) {
  System.out.println("n is a positive integer");
}
```
- [x] static error
- [ ] dynamic error
- [ ] no error, wrong answer

> Explanation:
> 
> 需要的类型为Boolean类型,提供的却是int类型

## 练习2
```java
int big = 200000; // 200,000
big = big * big;  // big should be 40 billion now
```
- [ ] static error
- [ ] dynamic error
- [x] no error, wrong answer

>Explanation:
>
>Java中int的最大整型为$2^{31}$(约21亿左右)而4,000,000超过此界限,故Java会返回一个不确定的数

## 练习3

```java
double probability = 1/5;
```
- [ ] static error
- [ ] dynamic error
- [x] no error, wrong answer
>Explanation:
>
>Java中/号返回的是一个整数,而不是预期的0.2

## 练习4
```java
int sum = 0;
int n = 0;
int average = sum/n;
```
- [ ] static error
- [ ] dynamic error
- [x] no error, wrong answer
>Explanation:
>
>在2023的IDEA中,只会有一个提醒,并不会报错,且结果为NaN[^1]

[^1]:NaN属性代表一个“不是数字”的值.这个特殊的值是因为运算不能执行而导致的,不能执行的原因要么是因为其中的运算对象之一非数字（例如, "abc" / 4）,要么是因为运算的结果非数字（例如,除数为零).

## 练习5
```java
double sum = 7;
double n = 0;
double average = sum/n;
```
- [ ] static error
- [ ] dynamic error
- [x] no error, wrong answer
>Explanation:
>
>在2023的IDEA中,只会有一个提醒,并不会报错,且结果为Infinity[^2]

[^2]:Java在浮点数运算中有特殊的情况即Infinity,且有以下解释1.Float中的无限和Double中的无限是相等的.2.无限乘以0得到的值为NAN,即非数字.3.除了乘以0外,对无限值做运算所得的值还是无限

## 练习6
```java
public static List<Integer> hailstoneSequence(int n) {
    List<Integer> list = new ArrayList<Integer>();
    while (n != 1) {
        list.add(n);
        if (n % 2 == 0) {
            n = n / 2;
        } else {
            n = 3 * n + 1;
        }
    }
    list.add(n);
    return list;
}
```
- [ ] `int n`
- [x] `List<Integer> list`
>Explanation:
>
>final对于引用数据类型,不能改变的是引用（即：引用的首地址的值）,可以改变引用的内容.而append方法追加字符后引用内容发生改变,但是首地址的之并没有改变

## 练习7
```python
from math import sqrt
def funFactAbout(person):
  if sqrt(person.age) == int(sqrt(person.age)):
    print("The age of " + person.name + " is a perfect square: " + str(person.age))
```
- [x] `person` must be an object with `age` and `name` instance variables
- [x] `person` is not None
- [x] `person.age` must be a nonnegative number
- [ ] `person.age` must be an integer
- [x] `person.name` must be a string
  
>Explanation:
>
>虽然Python中定义类并不像Java中这么严格,但大部分是一样的,该方法利用了类中的实例变量,故person 必须是带有 age 和 name 实例变量的对象,且person类不能为空,除此之外该函数中使用了`sqrt(person.age)`,故`person.age`必须为正整数.
而$+$号运算符的运算对象必须是同类型的,所以`person.name`也必须是字符串

### Question:如果此代码改为用 Java 编写,则以下哪些假设可以通过类型声明记录并由 Java 编译器进行静态检查？ （独立于上面的问题回答这个问题,即包括代码实际上不依赖的假设.）
- [x] `person` must be an object with `age` and `name` instance variables
- [x] `person` is not None
- [x] `person.age` must be a nonnegative number
- [x] `person.age` must be an integer
- [x] `person.name` must be a string
  
>Explanation:
>
>Java中的定义类及方法都比Python重要严格得多,请各位各自运行一下上面的代码即可得出答案.






