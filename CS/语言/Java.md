为了改进Java不足而设计了[[Kotlin]]语言，面向对象，应用场景广泛，最常用于后端开发和[[Android]] APP开发。
### Java三大特征

Java是一个面向对象的高级语言,Java三大特征分别是封装、继承、多态。

封装就是将类的属性私有化，并提供Get、Set方法以操作属性，把对属性的约束统一放在Get、Set中，避免直接操作属性时重复的进行约束，方便进行对属性的约束进行统一的管理，对于只在内部使用的方法可以定义为私有方法，外部无法直接调用，这样可以隐藏类的内部实现逻辑。

Java不支持多继承，被继承的类叫父类，继承它的类叫子类，子类继承父类，子类拥有父类的除Private修饰的一切属性和方法 。

多态的本质就是同一行为的不同表现形式，多态的前提是子类继承父类，有重写，父类引用指向子类对象。多态的表现形式有三种，重写、重载、实现接口，重写就是子类对父类某个方法的重新定义，子类重写的方法的参数与返回值必须与父类一致。重载就是在一个类中同一个方法，方法名相同，但是它的参数和返回值不相同。子类父类实现同一个接口，对同一方法的具体实现可能不一致。

### 抽象类与接口

  抽象类对属性的约束与普通类一致，而接口中的属性必须是由Public Static Final来修饰，方法必须是抽象方法，在实际使用中，如果实现接口，在接口中的增加或减少抽象方法时，实现它的类必须跟着修改，而抽象类可以有方法的具体实现，所以不需要修改。Java中只能继承一个抽象类，但是可以实现多个接口，所以抽象类在Android中一般作为Activity或者Fragment的基类来用，用来复用一些重复的代码，而接口更多的适用于功能的扩展，约束类的行为。

### Final、Static、Synchronize

被final修饰的类将不能被继承；被final修饰的方法将不能被重写，final方法比非final方法要快，因为在编译的时候已经静态绑定了，不需要在运行时再动态绑定；被final修饰的变量将不可改变，将作为常量使用，如果是一个实例对象，其内部的值可以更改。

被static修饰的内部类可以直接作为普通类使用，不需要引用外部类；被static修饰的方法可以直接调用，不需要实例化对象；被static修饰的变量可以直接访问，不需要实例化对象。

被 synchronized 修饰的方法在同一时刻只能被一个线程访问，其他线程将会被阻塞，直到当前线程释放锁；被 synchronized 修饰的代码块：其实和修饰方法差不多，只不过修饰代码块可以使用类锁。方法如果要使用类锁，只能设置为静态的方法。

### 深拷贝与浅拷贝的区别

浅拷贝和深拷贝都是针对一个已有对象的操作。在Java中，除了基本数据类型之外，还存在类的实例对象，也就是引用数据类型。而一般使用『=』号做赋值操作的时候。对于基本数据类型，实际上是拷贝的它的值，但是对于对象而言，其实赋值的只是这个对象的引用，将原对象的引用传递过去，他们实际上还是指向的同一个对象。而浅拷贝和深拷贝就是在这个基础之上做的区分，如果在拷贝这个对象的时候，只对基本数据类型进行了拷贝，而对引用数据类型只是进行了引用的传递，而没有真实的创建一个新的对象，则认为是浅拷贝。反之，在对引用数据类型进行拷贝的时候，创建了一个新的对象，并且复制其内的成员变量，则认为是深拷贝。所以到现在，就应该了解了，所谓的浅拷贝和深拷贝，只是在拷贝对象的时候，对类的实例对象这种引用数据类型的不同操作而已。总结来说：1、浅拷贝：对基本数据类型进行值传递，对引用数据类型进行引用传递般的拷贝，此为浅拷贝。2、深拷贝：对基本数据类型进行值传递，对引用数据类型，创建一个新的对象，并复制其内容，此为深拷贝。

### Java成员变量，局部变量和静态变量的创建和回收时机

*  成员变量:随着类对象的创建而创建,类对象回收时回收，存在堆里  
*  静态变量:不回收，随着类的加载而加载，随着类的消失而消失，由于类需要非常长时间的不使用，不利用，不关联，才有可能会被回收机制回收。所以静态成员变量的生命周期特别长，除非是共享数据，否则不建议使用静态；  
*  局部变量:方法调用时创建，方法结束时被标记为可回收 存在栈里

### 强引用，弱引用，软引用，虚引用

* 强引用：如果一个对象被强引用持有，则垃圾回收器不会回收这个对象。

* 弱引用（WeakReference）：即使对象被弱引用持有，垃圾回收器仍然可以回收这个对象。

* 软引用（SoftReference）：当内存紧张时，垃圾回收器也可能回收被软引用持有的对象。

* 虚引用（PhantomReference）：虚引用相当于没有引用，作用是在对象被回收时执行一些额外的操作

### Java中的基础类型(属性)

Java 是静态类型的语言，必须先声明再使用，基本数据类型之间不会共享状态。

Byte：1 bit八位，是最小的整数类型，一般在操作来自网络、文件或者其他 IO 的数据流时使用，用于节省内存空间，它的取值范围是[-128,127]，如果我们试图将取值范围外的值赋

给 byte类型变量，则会出现编译错误。对byte类型进行数学运算时，会自动提升为int类型，如果表达式中有double或者float等类型，也是自动提升。

Short：2 bit十六位，取值为[- 2^15, 2^15 - 1]，short类型参与运算的时候，一样被提升为int或者更高的类型。（顺序为 byte short int long float double).

Int：4 bit三十二位，取值为[- 2^31, 2^31 - 1]。

Long：8 bit六十四位，取值为 [- 2^63, 2^63 - 1,默认值为0L]，当需要计算非常大的数时，如果int不足以容纳大小，可以使用long类型。如果long也不够，可以使用BigInteger类。

Char：16 bit, [0, 65535], [0, 2^16 -1],从'\u0000'到'\uffff'。无符号，默认值为'\u0000'。Java使用Unicode字符集表示字符，Unicode是完全国际化的字符集，可以表示全部人类语言中的字符。Unicode需要16位宽，所以Java中的char类型也使用16 bit表示。

Float：32 bit，对应单精度浮点数，运行速度相比double更快，占内存更小，但是当数值非常大或者非常小的时候会变得不精确。精度要求不高的时候可以使用float类型。Double：64bit，将浮点子面子赋给某个变量时，如果不显示在字面值后面加f或者F，则默认为double类型。java.lang.Math中的函数都采用double类型。如果double和float都无法达到想要的精度，可以使用BigDecimal类。

Boolean：boolean类型只有两个值true和false，默认为false。

关于浮点类型精度损失的解决方案，用整形代替或者是通过BigDecimal类进行运算。

### 什么叫精度损失？

在java中，所有的基础类型的存储方式都是二进制，精度损失的本质是与二进制的表示和有限的计算机资源有关。

二进制表示问题：某些十进制小数无法精确的表示为有限的二进制小数，例如：0.1在二进制中是一个无线循环小数：0.0001100110011,因此在进行浮点数计算中可能会出现近似值。

有限的计算资源：计算机的内存和处理器资源是有限的，无法无限精确地表示和处理所有的小数。因此在进行浮点数计算时，计算机会使用一定的精度来表示和处理浮点数，从而导致精度损失。

在相关场景时可以使用整数代替小数避免精度损失，使用BigDecimal，它采用定点小数表示法(将数字以十进制表示并记录位数信息)和十进制运算，避免了二进制的舍入误差。

### String、StringBuffer、StringBuilder

双引号包围的字符串会自动创建一个新的 String 对象,tring 对象是不可变的，这意味着一旦创建，它们的值不能改变。String每次拼接字符串时每次都会创建新的对象，适合少量拼接使用，速度最慢，而StringBuffer和StringBuilder提供了可变的字符串操作，他们内部维护一个可变的字符数组，可以在不创建新的字符串对象的情况下修改字符串内容。这样可以避免创建大量临时字符串对象，提高了字符串连接的性能。;  
StringBuffer因为被Synchronize修饰，所以它适合多线程使用，比String快；  
StringBuilder因为它没有被Synchronize修饰，所以它的速度最快。

String不可被继承，因为它被Final修饰了，这样设计的理由是：

1. 字符串常量池的需要：当创建一个 String 对象时，如果此字符串已经存在于常量池中，则不会创建一个新的对象，而是引用已经存在的对象，如果允许改变，那么将导致各种逻辑错误，比如改变一个对象将会影响另一个独立对象，严格来说，这种常量池的思想是一种优化手段
2. 允许String对象缓存 HashCode：Java 中 String 对象的哈希码会被频繁的使用，比如在 hashMap中。字符串的不变形保证了hash码的唯一性，因此可以放放心的进行缓存。这也是一种优化手段，意味着不必每次都计算新的哈希码。
3. 安全性：String 被许多的类来当做参数，如 网络url，文件路径path 等等，如果String 不是固定的，将会引起各种安全隐患

### List,Set,Map的区别
List：有序，可重复  
set：无序，不可重复，但元素在集合中的位置是由元素的hashcode决定，就是说位置是固定的，但是这个位置不是用户可以控制的，所以对于用户来说set中的元素还是无序的  
map：键值对

### Error和Exception的区别

Exception是java程序运行中可预料的异常情况，我们可以获取到这种异常，并且对这种异常进行业务外的处理。

Error则是java程序运行中不可预料的异常情况，这种异常发生以后，会直接导致JVM不可处理或者不可恢复的情况。所以这种异常不可能抓取到，比如OutOfMemoryError、NoClassDefFoundError等。

其中的Exception又分为检查性异常和非检查性异常。两个根本的区别在于，检查性异常 必须在编写代码时，使用try catch捕获（比如：IOException异常）。非检查性异常在代码编写时可以忽略捕获操作（比如：NullPointException,ClassCastException），这种异常是在代码编写或者使用过程中通过规范可以避免发生的。 切记，Error是Throw不是Exception 。
![[Pasted image 20250122142826.png]]

### 注解

是提供元数据的机制，这些信息不会影响程序的逻辑执行，但可以被编译器、开发工具或框架使用。

在编译阶段让编译器进行检查，可以生成和验证代码，运行时被反射机制读取，并根据注解进行特定操作

### 反射

反射用于在运行时进行类的加载、字段访问、方法调用，一般用于动态加载、动态代理，序列化，代码注入，它的缺点是影响性能，降低可读性和可维护性。

他的运行依赖于类加载机制，通过类加载器JVM可以在运行时加载类信息并创建相应的Class对象，影响性能的原因是他在运行时会进行动态查找和解析，使用unsafe类绕过Java的访问控制等。

在android中使用热更新会用到这个技术，一般是通过自定义类加载器在运行时加载服务器下载的文件替换旧代码或是动态扩展功能，在一些框架比如Tinker和AndResGuard会通过重新加载类和替换类定义将修改过的代码动态加载到内存来实现更新代码。然后通过反射获取新的class类和调用方法。

主要是通过自定义类加载器实现Dex文件热替换，然后在加载新的Dex文件后使用反射来调用新版本的类和方法，替换原本的实现。

另一种是在编译阶段通过字节码注入修改原始代码，并使用反射来调用更新后的方法
![[Pasted image 20250122143144.png]]

### 泛型

泛型是一种允许在编译时指定类型的机制也就是延迟类型的具体化，是代码更灵活、类型安全且客服用。

关于他的特性有类型擦除，即java在运行时不会保留泛型信息，所有泛型类型的会被擦除为原始类型。通配符：上界通配符表示类型必须是它和它的子类，下界通配符表示必须是它或它的父类

在使用中一般是用于定义集合类类型，避免大量类型转换。
### 协变与逆变？

用于处理泛型类型、接口的集成和类型转换问题，他们决定在继承结构中，泛型参数如何与类型或接口的继承关系保持一致或相反。

协变允许在一个方法、接口中返回子类型，而类型参数是其基类也就是java多态中的一种：父类引用指向子类对象。

逆变中如果A类是B类的子类，那么B类可以看作是A类的子类，它允许使用父类代替子类。

普通的类继承关系就是协变，在kotlin中，函数类型的参数类型是逆变的。

在泛型中，out是协变，通常用于返回值类型、in是逆变，通常用于参数类型。

### GC垃圾回收

Gc垃圾回收机制用于自动回收不再使用的对象，以释放内存，避免内存泄漏。

关于java堆内存的分代分为新生代->老年代->永久代/元空间

1. 新生代：新创建的对象首先分配到这里
2. 老年代：生命周期较长的对象通常是经历多次gc后存活的对象。
3. 永久代：主要用于存放静态文件，如：java类，方法。

GC回收的算法分为标记清除、复制、标记整理。

1. 标记清除算法，GC首先标记处需要回收的对象，然后统一清除标记的对象，缺点是效率低，且会导致碎片化。
2. 复制算法，将内存分为两块，通常是新生代的Eden区和Survivor区，只使用其中一块，当GC时，把存活对象复制到另一块，清理当前块的内存空间，适合对象存活率低的区域。
3. 标记整理算法，先标记存活的对象，然后将存活的对象移动到内存的一端，在清理无效内存，避免了碎片化的问题，适合老年代。

分代收集算法：结合以上算法，针对新生代老年代特点进行优化，新生代使用复制算法，老年代使用标记清除或标记整理算法。

gc垃圾回收機制分為手动触发和自动触发，手动触发是当前程序调用System.gc()的时候触发，自动触发是根据Eden区和From Space区的内存大小来决定，当内存大小不足时，会自动启动GC线程并停止应用线程。

### 类加载机制

    类加载机制指的是将.class文件加载到内存，并生成Class对象的过程，java的类加载在运行时进行，通过类加载机制，java能够在运行时动态加载类，并实现类的动态扩展和安全隔离。

    类加载的生命周期分为加载loading，验证verification，准备preparation，解析resolution，初始化initialization。

加载：将类的二进制数据.class文件读入内存，并生成Class对象。
验证：确保加载的类符合JVM的要求，包括文件格式，字节码指令合法性等。
准备：为累的静态变量分配内存，并将其初始化为默认值
解析：将常量池中的符号引用替换为直接引用
初始化：执行类的静态初始化块和静态变量的赋值操作
类的加载、验证、准备、解析也被成为类的连接linking过程。

   Java的类加载器负责加载Java类，主要分为
Bootstrap ClassLoader（启动类加载器）：用来加载核心类库，由JVM实现，属于最底层的类加载器。
Extension ClassLoader(扩展类加载器)：加载jre/lib/ext目录下的扩展类库
Application ClassLoader(系统类加载器)：加载用户类路径（classpath）下的类文件，是在应用开发中最常用的加载器。
自定义ClassLoader：java允许开发者自定义类加载器，适用于一些动态加载，热替换和模块隔离的场景。

   关于双亲委派，指的是类加载时，子类加载器会先委托父类加载器加载类，只有当父类加载器无法加载时，子类加载器才会尝试自己加载。
双亲委托可以确保Java核心类库的安全，避免重复加载。



