
- 当对字符串进行修改的时候，需要使用 StringBuffer 和 StringBuilder 类。
- 和 String 类不同的是，StringBuffer 和 StringBuilder 类的对象能够被多次的修改，并且不产生新的未使用对象。
- 在使用 StringBuffer 类时，每次都会对 StringBuffer 对象本身进行操作，而不是生成新的对象，所以如果需要对字符串进行修改推荐使用 StringBuffer。
- StringBuilder 类在 Java 5 中被提出，它和 StringBuffer 之间的最大不同在于 StringBuilder 的方法不是线程安全的（不能同步访问）。
- StringBuilder 相较于 StringBuffer 有速度优势，但不保证线程安全。

**使用环境**

- 操作少量的数据使用 String。
- 单线程操作大量数据使用 StringBuilder。
- 多线程操作大量数据使用 StringBuffer。

![10-1](https://images-1302683597.cos.ap-nanjing.myqcloud.com/images/StudyNotes/Java/JDK/10-1.png)

- StringBuffer、StringBuilder、String 中都实现了 CharSequence 接口。CharSequence 是一个定义字符串操作的接口，它只包括 length()、charAt(int index)、subSequence(int start, int end) 这几个 API。

- StringBuffer、StringBuilder、String 对 CharSequence 接口的实现过程不一样。
- 可见，String 直接实现了 CharSequence 接口，StringBuilder 和 StringBuffer 都是可变的字符序列，它们都继承于 AbstractStringBuilder，实现了 CharSequence 接口。

## 定义一个 SpringBuffer **字符串**

```java
// 定义一个空的字符串缓冲区，含有16个字符的容量
StringBuffer str1 = new StringBuffer();
// 定义一个含有10个字符容量的字符串缓冲区
StringBuffer str2 = new StringBuffer(10);
// 定义一个含有(16+4)的字符串缓冲区，"青春无悔"为4个字符
StringBuffer str3 = new StringBuffer("青春无悔");
/*
*输出字符串的容量大小
*capacity()方法返回字符串的容量大小
*/
System.out.println(str1.capacity());    // 输出 16
System.out.println(str2.capacity());    // 输出 10
System.out.println(str3.capacity());    // 输出 20
```

## 一些方法

```java
String str = "hello,World!";
System.out.println(buffer.substring(1));    // 输出：ello,World!，用法和 String 类的方法一致
System.out.println(str.length()); //内容长度
System.out.println(str.capacity());//总空间
StringBuffer 对象.setCharAt(int index, char ch); //替换字符串 StringBuffer 类的 setCharAt() 方法用于在字符串的指定索引位置替换一个字符。
StringBuffer 对象.reverse(); // 反转字符串
str.delete(4, 10);//删除4-10之间的字符
StringBuffer 对象.deleteCharAt(int index); // deleteCharAt() 方法用于移除序列中指定位置的字符
str.insert(4, "there ");//在4这个位置插入 there
```

## 自己实现一个 StringBuffer

