---
tags:
  - Java
  - Stream流
---

# Stream流

## 获取Stream流
### 单列集合
Collection中的默认方法
```java
default Stream<E> stream();

ArrayList<String> list = new ArrayList<>();
list.stream().forEach(s -> System.out.print(s));
```
### 双列集合
无法直接使用stream流
```java
无

HashMap<String,Integer> hm = new HashMap<>();
//获取键
hm.keySet().stream().forEach(s -> System.out.print(s));
//获取键值对
hm.entrySet().stream().forEach(s -> System.out.print(s));
```
### 数组
Arrays工具类中的静态方法
```java
public static<T> Stream<T> stream(T[] array);

Arrays.stream(arr).forEach(s -> System.out.print(s));
```
### 零散数据
Stream接口中的静态方法
```java
public static<T> Stream<T> of(T...values);

Stream.of(arr).forEach(s -> System.out.print(s));
//细节
//方法的形参是一个可变同类型参数，可以传递一堆零散数据，也可以传递数组
//但是数组必须是引用数据类型的，如果传递基本数据类型，是会把整个数组当做一个元素放入Stream中，返回地址值
```
## 中间方法
```java
Stream<T> filter(Predicate<? super T> predicate);
过滤
```
```java
Stream<T> limit(long maxSize);
获取前面几个元素
```
```java
Stream<T> skip(long n);
跳过前几个元素
```
```java
Stream<T> distinct();
元素去重，依赖hashCode和equals方法，必要时必须重写方法
```
```java
static<T> Stream<T> concat(Stream a,Stream b);
合并a和b两个流为一个流，数据类型尽量一致，否则会变成二者的父类
```
```java
Stream<R> map(Function<T,R> mapper);
转换流中的数据类型
例:
//"张无忌-15"
list.stream()
	.map(s -> Integer.parseInt(s.split("-")[1]))
	.forEach(s -> System.out.print(s));
```
细节:
1. 中间方法，返回新的Stream流，原来的Stream流只能使用一次，建议使用链式编程
2. 修改Stream流中的数据，不会影响原来集合或数组中的数据
##  终结方法
### 遍历
```java
void forEach(Consumer action);
```
### 统计
```java
long count();
long count = list.stream().count();
sout(count);
```
### 收集流中数据，放入数组
```java
toArray();
//1.空参
Object[] arr=list.stream().toArray();
sout(Arrays.toString(arr));
//2.有参(IntFunction的泛型)
String[] arr=list.stream().toArray(valus -> new String[valus]);
sout(Arrays.toString(arr));
```
### 收集流中数据，放入集合(List,Set,Map)
```java
collect(Collector collector);

eg:
ArrayList<String> list = new ArrayList<>();
Collections.addAll(list,"张无忌-男-15","周芷若-女-14","赵敏-女-13","张强-男-20",
	"张三丰-男-100","张翠山-男-40","张亮-男-35","王二-男-37","韩立-男-18");
```
#### List
```java
List<String> newList = list.stream()
	.filter(s -> "男".equals(s.split("-")[1]))
	.collect(Collectors.toList());
```
#### Set
```java
Set<String> newList = list.stream()
	.filter(s -> "男".equals(s.split("-")[1]))
	.collect(Collectors.toSet());
```
#### Map
需求：收集男性；姓名作为键，年龄作为值。
```java
Map<String,Integer> map = list.stream()
	.filter(s -> "男".equals(s.split("-")[1]))
	.collect(Collectors.toMap(
		new Function<String,String>(){
			@Override
			public String apply(String s){
				return s.split("-")[0];
			}
		},
		new Function<String,Integer>(){
			@Override
			public Integer apply(String s){
				return Integer.parseInt(s.split("-")[2]);
			}
		}));

改Lambda:
Map<String,Integer> map = list.stream()
	.filter(s -> "男".equals(s.split("-")[1]))
	.collect(Collectors.toMap(
		s -> s.split("-")[0],
		s -> Integer.parseInt(s.split("-")[2])));
```
toMap：
参数一表示键的生成规则
参数二表示值的生成规则
.
参数一：
Function
泛型一：表示流中每个数据的类型；
泛型二：表示Map集合中键的数据类型；
方法apply
形参：依次表示流里面的每个数据；
方法体：生成键的代码；
返回值：已经生成的键；
.
参数二：
Function
泛型一：表示流中每个数据的类型；
泛型二：表示Map集合中键的数据类型；
方法apply
形参：依次表示流里面的每个数据；
方法体：生成值的代码；
返回值：已经生成的值；
**注意**：数据的键不能重复，否则会报错

## 相关笔记

- [[lambda表达式]]
- [[方法引用]]
- [[集合]]

