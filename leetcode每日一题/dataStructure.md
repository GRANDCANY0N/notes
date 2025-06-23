# HashMap

``` java
HashMap<Integer, String> hash = new HashMap<>();
//put方法往哈希表中加入数据
hash.put(1,"string1"); 

//返回key=1的value
hash.get(1); 

//替代哈希表中对应key的value值
hash.replace(1,"string2"); 

//获取key为1的value，如果没有返回定义的默认值
hash.getOrDefault(1,null); 

//判断hash表中是否存在key=1的键值对，存在返回true，否则false
hash.containsKey(1); 

//返回包含所有value的集合
Collection<Integer> va =  hash.values(); 

//删除key=1的键值对
hash.remove(1);

//清空
hash.clear();

//结合使用
//向hash表中加入key和value，这一步用来统计数字出现次数好用，如果第一次出现则默认值加1，否则在原来的基础数字出现次数上+1
hash.put(1,hash.getOrDefault(1, 0)+1); 

//三个参数，hash表的key，第二个是如果不存在该key，则给予的默认值，第三个是后续相同key冲突时，如何将旧值（oldValue）和新值（newValue）的结合方法
hash.merge(key, value, remappingFunction);

//hash.merge(num[i], 1, Integer::sum)作用等同于hash.put(1,hash.getOrDefault(1, 0)+1); 
hash.merge(num[i], 1, Integer::sum);

//使用hashMap存储一个值及其对应的索引，索引放在列表中，computeIfAbsent是如果不存在列表则新建一个列表
map.computeIfAbsent(nums[i], k -> new ArrayList<>()).add(i);
```

# ArrayList

```java
List<Integer> list = new ArrayList<>();
//将值按顺序放到列表中
list.add(1);

//将列表原地排序,默认正序
list.sort([Comparator.naturalOrder() || Comparator.reverseOrder()]);

//先了解
people.sort(Comparator.comparingInt(p -> p.age));

//list配合map使用 如果是新值则新建一个ArrayList并将索引放入list中， lambda表达式,
map.computeIfAbsent(nums[i], k -> new ArrayList<>()).add(i);
```

# String

String的方法

```java
//字符串转化为字符数组
char[] ch = str.toCharArray();

//判断字符串中是否存在某个字符个数是否>=0
boolean isVowel = str.indexOf(b) >= 0;
```



```java
String a = "abc";String b = "a";
/*
两个结果一样但是运行速度不一样，result1由于ab已经在常量池中存在，需要重新new一个字符串并且再运行一遍，而result2是在编译时拼接，所以只需要一遍即可
*/
String result1 = a+b;
String result2 = "abc" + "a";
//a+b的底层原理就是new StringBuilder().append(a).append(b).toString()
a+b; 
```

```java
//为什么同样的循环a+b会超时？
String[] str = {"ab","cd","ef","gh"}
string c = "";
for(int i=0;i<str.length;i++){
	c += str[i];
}
//等于
for(int i=0;i<str.length;i++){
    c = new StringBuilder().append(c).append(str[i]).toString;
}
//需要每次新建一个stringbuilder之后再拼接在转换为字符串

//先建立stringbuilder存储最后转化为字符串，省去中间new stringbuilder和复制之前所有字符的内容
StringBuilder sb = new StringBuilder();
for(int i=0;i<str.length;i++){
    sb.append(str[i]);
}
c = sb.toString();
```

String不可变的原因
1.String是final类型的类，value也是final类型的数组，但这不是String不可变的根本原因，String不可变是因为value是private，且并没有提供对外的get和set
2.底层char[]数组有final修饰，意味着这个数组不能扩容等，来达到存更多的字符，final修饰char类型数组，保证数组一旦被赋值 不能在重新赋值，修改char类型数组后，地址不能改变，内容可变，但是没有具体的方法去修改内容
3.char[]数组是私有的，我们程序员无法直接操作这个char[]数组，而且String没有提供这样的方法，来修改char[]数组的元素的值。

String不可变的好处
可以共享，也是为了安全

# Set

```java
Set<Integer> set = new HashMap<>();
//set.add方法返回boolean，如果为true则添加成功，false则添加失败
boolean flag = set.add(1);;
```

##### set和SrtingBuilder的冲突

```java
Set<SrtingBuilder> set = new HashSet<>();

//SrtingBuildernew出对象后，之后的所有操作不会改变内存地址
StringBuilder sb = new StringBuilder();

//集合中存储的是 sb 的引用（即内存地址），而非 StringBuilder 对象的拷贝
set.add(sb);

//集合中存储的是 sb 的引用,sb进行操作之后，集合访问该引用会变成修改后的内容
sb.deleteCharAt(0);
```



# SrtingBuilderd

```java
//字符串拼接使用stringbuilder,append方法将要拼接的字符放到当前字符串后面，避免使用a+b
StringBuilder sb = new StringBuilder();
sb.append("a");
sb.toString();

//根据索引删除StringBuilder中的内容，但是注意sb是会动态维护的
//在循环中每一次删除最左边的值
sb.deleteChatAt(0);
```

![img](dataStructure.assets/image-20250501113738540.png)

# StringBuffer

# Array

```java
//将指定数组填充为指定值，数组必须为1维数组
Arrays.fill([数组], [填充值]); 

//lambda写法，将list中的数据按顺序放到数组中
Integer[] arr = nums.toArray(Integer[]::new);

//字符串划分成每个字符存到字符数组中
char[] ch = s.toCharArray();

//数组原地排序
Arrays.sort([数组], [start index], [end index])
```

