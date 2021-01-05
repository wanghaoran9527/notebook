## Java向上转型和向下转型

## 派生类的初始化顺序

## 内部类的**.class** 文件

内部类也必须生成一个 **.class** 文件以包含它们的 **Class** 对象信息。这些类文件的命名有严格的规则：外部类的名字，加上 **$**，再加上内部类的名字。

如果内部类是匿名的，编译器会简单地产生一个数字作为其标识符。如果内部类是嵌套在别的内部类之中，只需直接将它们的名字加在其外部类标识符与 **$** 的后面。

## 集合Collection

**HashSet** ,**TreeSet** 和 **LinkedHashSet** 是 **Set** 的类型。**HashSet** 检索元素最快,**TreeSet** 把对象按照比较规则来排序； **LinkedHashSet**把对象按照被添加的先后顺序来排序。

**Map** 的三种基本风格： **HashMap**,**TreeMap** 和 **LinkedHashMap**。**HashMap** 查找速度快， **TreeMap** 把所有的键按照比较规则来排序， **LinkedHashMap** 在保持 **HashMap** 查找速度的同时按照键的插入顺序来排序。

### [Java中Collection和Collections的区别](https://www.cnblogs.com/dashi/p/3597937.html)

1. java.util.Collection 是一个**集合接口（集合类的一个顶级接口）**。它提供了对集合对象进行基本操作的通用接口方法。Collection接口在Java 类库中有很多具体的实现。Collection接口的意义是为各种具体的集合提供了最大化的统一操作方式，其直接继承接口有List与Set。

   Collection 
   ├List 
   │├LinkedList 
   │├ArrayList 
   │└Vector 
   │　└Stack 
   └Set 

2. java.util.Collections 是一个包装类（工具类/帮助类）。它包含有各种有关集合操作的**静态多态方法**。此类**不能实例化**，就像一**个工具类**，用于对集合中元素进行排序、搜索以及线程安全等各种操作，服务于Java的Collection框架。

 