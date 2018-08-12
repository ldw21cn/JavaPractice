# JavaPractice
About Java's daily exercises，Java foundation, advanced personal summary, Oracle database knowledge points

### jvm学习笔记
### java代码是怎样运行的
java虚拟机可以由硬件实现，一个程序被转换成java字节码，那么它就可以在不同的平台上运行了，也就是可移植性。

虚拟机的另一个好处：他带来了托管环境，这个托管环境可以帮助程序员处理一些代码冗长且容易出错的地方，例如：自动内存管理、垃圾回收、数组越界、动态类型、安全权限等动态监测。

#### 那么下面就来说一说Java虚拟机（hoyspot jvm）具体怎样运行的Java字节码：
```
* Java代码首先需要将它编译成class文件加载到Java虚拟机中，加载后的Java类会被存放到方法区(method area)中,实际运行时，
虚拟机会执行方法区中的代码。Java虚拟机也同样在内存中划分出堆和栈存储运行时的数据。

* 不同的是Java虚拟机将栈划分为面向Java方法的`Java方法栈`、面向本地方法的`本地方法栈`、存放各个线程执行位置的`PC寄存器`。

* 从硬件的角度来看，Java字节码无法直接执行，因此Java虚拟机需要将字节码翻译成机器码。

* 在hotspot中。翻译过程有两种形式，第一种解释执行：将字节码翻译成机器码并执行；第二种即时编译：将一个方法中包含所有字节码编译成机器码后在执行。

* 其中前者优势在于无需等待编译，后者优势在于实际运行速度更快。hotspot采用混合模式，综合了解释执行和即时编译两者的优点。
它会先解释执行字节码，而后者将其反复执行热点代码，以方法为单位进行即时编译。
```

#### 总结：
* 之所以要在虚拟机中运行，是因为它提供了可移植性。一旦 Java 代码被编译为 Java 字节码，便可以在不同平台上的 Java 虚拟机实现上运行。此外，虚拟机还提供了* 一个代码托管的环境，代替我们处理部分冗长而且容易出错的事务，例如内存管理。
* Java 虚拟机将运行时内存区域划分为五个部分，分别为方法区、堆、PC 寄存器、Java 方法栈和本地方法栈。Java 程序编译而成的 class 文件，需要先加载至方法区中，方能在 Java 虚拟机中运行。
* 为了提高运行效率，标准 JDK 中的 HotSpot 虚拟机采用的是一种混合执行的策略。
* 它会解释执行 Java 字节码，然后会将其中反复执行的热点代码，以方法为单位进行即时编译，翻译成机器码后直接运行在底层硬件之上。
* HotSpot 装载了多个不同的即时编译器，以便在编译时间和生成代码的执行效率之间做取舍。



