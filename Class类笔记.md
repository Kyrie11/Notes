# Class笔记:
Java程序在运行时，Java运行时系统一直对所有的对象进行所谓的运行时类型标识。这项信息纪录了每个对象所属的类。虚拟机通常使用运行时类型信息选准正确方法去执行，用来保存这些类型信息的类是Class类。Class类封装一个对象和接口运行时的状态，当装载类时，Class类型的对象自动创建。Class 没有公共构造方法。Class 对象是在加载类时由Java虚拟机以及通过调用类加载器中的 defineClass 方法自动构造的，因此不能显式地声明一个Class对象。虚拟机为每种类型管理一个独一无二的Class对象。也就是说，每个类（型）都有一个Class对象。运行程序时，Java虚拟机(JVM)首先检查是否所要加载的类对应的Class对象是否已经加载。如果没有加载，JVM就会根据类名查找.class文件，并将其Class对象载入。基本的 Java 类型（boolean、byte、char、short、int、long、float 和 double）和关键字 void 也都对应一个 Class对象。每个数组属于被映射为Class对象的一个类，所有具有相同元素类型和维数的数组都共享该Class对象。一般某个类的Class对象被载入内存，它就用来创建这个类的所有对象。

## 得到Class对象
1. 调用object类的getClass()方法。例如：
```java
MyObject x;
Class clazz = x.getClass();
```
2. 使用Class类中的静态方法forName()。例如
```java
Class clazz = Class.forName("MyObject");
```
3. .class后缀。如果T是一个java类型，那么T.class就代表了匹配的类对象。例如:
````java
Class clazz = MyObject.class
````

## Class类常用方法
1. getName()
一个Class对象描述了一个特定类的属性，Class类中最常用的方法getName以 String 的形式返回此 Class 对象所表示的实体（类、接口、数组类、基本类型或 void）名称
2. newInstance()
3. getClassLoader()
返回该类的类加载器
4. getComponentType()
5. getSuperClass()
6. isArray()
    
### Class.forName()


<table>
    <tr>
        <td color ='green'>static Class</td>
        <td color='green'>forName(String className)Returns the Class object associated with the class or interface with the given string name.</td>
    </tr>
    <tr>
        <td color='blue'>static Class</td>
        <td color='blue'>forName(String name, boolean initialize, ClassLoader loader)Returns the Class object associated with the class or interface with the given string name, using the given class loader.</td>
    </tr>
</table>

__@parameter:className--the fully qualifiedname of the desired class__

##### Class装载在jvm上才能运行
1.forName()即用来装载类。 
2.A是一个类，则 A a = (A)Class.forName("package.A").newInstance()和 new A()效果一样。
3. jvm在装载类时会执行类的静态代码段，静态代码段是和class绑定的。
4. Class.forName(className)的作用是要求jvm查找并加载指定的类，即要求JVM执行该类的静态代码。

### 在初始化一个类，生成一个实例的时候，new() 和 newInstance()的区别
1. new()是关键字，newInstance()是方法
2. new()创建一个新类，newInstance()使用类加载机制。
