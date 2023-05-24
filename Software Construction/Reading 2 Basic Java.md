# Reading 2: Basic Java

***以下答案基于本人对题目的理解，如有错误，请大家务必指出***
## 练习1
```java
int a = 5;     // (1)
if (a > 10) {  // (2)
    int b = 2; // (3)
} else {       // (4)
    b = 4;     // (5)
}              // (6)
b *= 3;        // (7)
```

>Answer: Line 5

>Explanation:
>
>在第五行会报错，因为变量b没有声明

### Question1 假设我们只需要一个名为 b 的变量，选择将修复错误并允许此代码编译的最小更改集：
>Answer: 
- [x] Declare `int b`;
- [ ] Assign `b = 0`;
- [x] Assign `b = 2`; instead of line 3
- [ ] Declare and assign `int b = 4`; instead of line 5
- [ ] Declare and assign `int b *= 3`; instead of line 7
>Explanation:
>
>只有在一开始声明b，再将之后对b的重声明去掉就可以使程序正常的运行

### Question2 如果我们进行了上述所需的更改，如果我们从 if-else 中注释掉 else 子句的主体，会发生什么情况?
>Answer:
- [ ] `b` will be 0
- [ ] `b` will be 3
- [ ] `b` will be 6
- [x] We will receive an error from the Java compiler, before we run the program
- [ ] We will receive an error when we run the program, before we reach the last line
- [ ] We will receive an error when we run the program, when we reach the last line
  
>Explanation:
>
>Java编译器会提醒变量未初始化，会产生静态错误

## 练习2
```python
fahrenheit = 212.0
celsius = (fahrenheit - 32) * 5 / 9
```
>Answer:
- [x] Yes
- [ ] No: integer arithmetic will cause `celsius` to be zero
- [ ] No: integer arithmetic will cause `celsius` to be rounded down
  
>Explanation:
>
>Python中`/`号返回的是一个浮点数，所以运算结果正确，而`//`号返回的才是一个整数且结果向下取余

### Question 用Java重写第一行
>Answer:

- [ ] `int fahrenheit = 212.0;`
- [ ] `Integer fahrenheit = 212.0;`
- [ ] `float fahrenheit = 212.0;`
- [ ] `Float fahrenheit = 212.0;`
- [x] `double fahrenheit = 212.0;`
- [x] `Double fahrenheit = 212.0;`
>Explanation:
>
>在Java编译器中，基本数据类型，分为boolean、byte、int、char、long、short、double、float；但是为了能够将这些基本数据类型当成对象操作，Java为每一个基本数据类型都引入了对应的包装类型（wrapper class）

|基本数据类型|boolean|byte|int|char|long|short|double|float|
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|封装类类型|Boolean|Byte|Integer|Character|Long|Short|Double|Float|

>在这里应该使用基本数据类型，只有double类型和Double封装类类型符合条件

### Question 用Java重写第二行
>Answer:

- [x] `??? celsius = (fahrenheit - 32) * 5/9;`
- [ ] `??? celsius = (fahrenheit - 32) * (5 / 9);`
- [x] `??? celsius = (fahrenheit - 32) * (5.0 / 9);`

>Explanation
>
>只有第二个答案会计算错误，其余两种计算方法都正确，第一种方法会自动向double类型转化，第三种方法括号里面的内容计算会返回一个浮点数，计算出的也是正确答案。

## 练习3
>Answer:
- [ ] BigInteger
- [x] char
- [x] int
- [x] float
- [ ] List
- [ ] String

## 练习4
>Answer:
- [ ] primitive types are numeric; object types are strings and characters
- [x] primitive types are conventionally lowercase; object types are conventionally capitalized
- [x] object types can contain internal structure (references to other primitives or objects); primitive types have no internal structure
- [x] a primitive value uses a small, fixed amount of memory; an object value may use varying, sometimes large amounts of memory
>Explanation
>
>这里的答案是根据我自己的理解给出的，可能会有错误，只是我自己的主观想法。

## 练习5
```Java
void f(String s, StringBuilder sb) {
  s.concat("b");
  s += "c";
  sb.append("d");
}
String t = "a";
StringBuilder tb = new StringBuilder(t);
f(t, tb);
```
>Answer1:
- [ ] `abcd`
- [ ] `abc`
- [ ] `acd`
- [ ] `ac`
- [ ] `ad`
- [x] `a`
  
>Answer2:
- [ ] `abcd`
- [ ] `abc`
- [ ] `acd`
- [ ] `ac`
- [x] `ad`
- [ ] `a`
>Explanation：
>
>字符串t的值为:"a"因为String类型为final型，在定义后不可改变，而contact()方法也仅仅是执行后的结果为拼接后的字符串，原来的字符串不会改变
>
>字符串tb的值为:"ad"因为StringBuilder是一个表示字符串的可变对象，它可以通过append方法来更改对象的值

## 练习6
```java
void f(String s1, String s2, int i1, int i2, char c1, char c2)
```
>Answer:

`s1==s2` no error but this is a bug

`i1==i2` correct

`s1==i1` static error

`c1==c2` correct

`s1.equals(s2)` correct

`i1.equals(s2)` static error

>Explanation:
>
>在编译器内运行即可得到结果

## 练习7
```java
String s = "foobar";
String t = "foobar";
if (s == t) { ... }
```
>Answer:
- [ ] s == t is a static error, because == can’t be used on strings
- [ ] s == t will always return false, because strings are never == to each other
- [ ] s == t might return true, because Java might cleverly reuse the same String object for both s and t
- [x] s == t will always return true, because s and t both have the same sequence of characters, "foobar"

>Explanation:
>
>返回 true 因为 s 和 t 指向同一个对象

## 练习8
>Answer:

`List<String> names = new ArrayList<>();`

`List<Integer> numbers = new ArrayList<>();`

`List<List<Character>> grid = new ArrayList<>();`

>Explanation:
>
>阅读文章即可得出答案，泛型使用大写字母的类对象类型表示

## 练习9
```java
Map<String, Double> treasures = new HashMap<>();
String x = "palm";
treasures.put("beach", 25.);
treasures.put("palm", 50.);
treasures.put("cove", 75.);
treasures.put("x", 100.);
treasures.put("palm", treasures.get("palm") + treasures.size());
treasures.remove("beach");
double found = 0;
for (double treasure : treasures.values()) {
    found += treasure;
}
```
>Answer:

`treasures.get(x)`为54.0

`treasures.get("x")`为100.0

`found`为229.0

>Explanation:
>
>x指的是字符串"palm",与"x"不同，故所对应的值不一样，found则是对Map中的所有的字典的值的求和

## 练习10
```java
Map<String, TreasureChest> treasures = new HashMap<>();
treasures.put("beach", new TreasureChest(25));
TreasureChest result = treasures.putIfAbsent("beach", new TreasureChest(75));
```
>Answer:
- [x] 25 treasure
- [ ] 75 treasure
- [ ] another amount of treasure
- [ ] `null`
  
>Explanation:
>
>putIfAbsent() 方法会先判断指定的键（key）是否存在，不存在则将键/值对插入到 HashMap 中。在以上实例中，我们创建了一个名为treasures的HashMap,key 为 "beach" 已经存在于 treasures 中，所以不会执行插入操作。

## 练习11
```java
Map<String, String> translations = new HashMap<>();
translations.put("green", "verde");
result = translations.replace("green", "verde", "ahdar");
```
>Answer:
- [ ] `"green"`
- [ ] `"verde"`
- [ ] `"ahdar"`
- [x] `true`
- [ ] `false`
- [ ] `l`
- [ ] `null`
- [ ] code won’t compile, because there is no appropriate static type for `result`

>Expalnation:
>
>replace() 方法替换 hashMap 中是指定的 key 对应的 value。如果 oldValue不存在，则替换key对应的值，返回 key对应的旧值，如果存在oldValue，替换成功返回true，如果key不存在，则返回 null。