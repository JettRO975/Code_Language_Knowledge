---
tags:
  - Java
  - lambda表达式
---

# lambda表达式

lambda表达式是一个匿名函数
```java
lambda表达式：
Arrays.sort(arr,new Comperator<Integer>(){
	@Override
		publci int compare(Integer o1,Integer o2){
				return o1-o2;
		}
});
改为：
Arrays.sort(arr,(Integer o1,Integer o2)->{
	return o1-o2
		}
);
```
细节：
1. lambda表达式用来简化匿名内部类的书写
2. lambda表达式只能用来简化函数式接口的匿名内部类的书写
3. 函数式接口：有且仅有一个抽象方法的接口叫做函数式接口，接口上方可以加`@Functionallnterface`注解是否为函数式接口

省略写法：
4. 参数类型可以省略
5. 如果只有一个参数，参数类型可以省略，同时()也可以省略
6. 如果lambda表达式的方法体只有一行，大括号，分号，return可以省略，三者省略时需要同时省略
## 常见Lambda表达式
遍历集合:
```java
list.forEach (str -> System.out.println (str));
```
集合排序(整数升序):
```java
numList.sort ((a, b) -> a - b);
```
集合排序(字符串长度):
```java
strList.sort ((s1, s2) -> s1.length () - s2.length ());
```
过滤集合(Stream):
```java
list.stream ().filter (num -> num > 5).forEach (System.out::println);
```
映射集合(Stream):
```java
list.stream ().map (str -> str.toUpperCase ()).forEach (System.out::println);
```
线程创建:
```java
new Thread (() -> System.out.println ("Lambda 线程运行")).start ();
```
函数式接口实现(Supplier):
```java
Supplier<String> sup = () -> "Hello Lambda";String result = sup.get();
```
比较器(Comparator):
```java
Comparator<Integer> comp = (x, y) -> y - x; // 降序
```


***

## 相关笔记

- [[方法引用]]
- [[Stream流]]

