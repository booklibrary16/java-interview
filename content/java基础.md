# [返回主页](https://github.com/yisainan/java-interview/blob/master/README.md)

<b><details><summary>1、面向对象的特征有哪些方面</summary></b>

答案：

(1).抽象：

抽象就是忽略一个主题中与当前目标无关的那些方面，以便更充分地注意与当前目标有关的方面。抽象并不打算了解全部问题，而只是选择其中的一部分，暂时不用部分细节。抽象包括两个方面，一是过程抽象，二是数据抽象。

(2).继承：

继承是一种联结类的层次模型，并且允许和鼓励类的重用，它提供了一种明确表述共性的方法。对象的一个新类可以从现有的类中派生，这个过程称为类继承。新类继承了原始类的特性，新类称为原始类的派生类（子类），而原始类称为新类的基类（父类）。派生类可以从它的基类那里继承方法和实例变量，并且类可以修改或增加新的方法使之更适合特殊的需要。

(3).封装：

封装是把过程和数据包围起来，对数据的访问只能通过已定义的界面。面向对象计算始于这个基本概念，即现实世界可以被描绘成一系列完全自治、封装的对象，这些对象通过一个受保护的接口访问其他对象。

(4). 多态性：

多态性是指允许不同类的对象对同一消息作出响应。多态性包括参数化多态性和包含多态性。多态性语言具有灵活、抽象、行为共享、代码共享的优势，很好的解决了应用程序函数同名问题。

</details>

<b><details><summary>2、String是最基本的数据类型吗?</summary></b>

答案：

不是。基本数据类型就只有八个，数值型：byte，short，int，long，浮点型：float，double，字符型：char，布尔型：boolean。

</details>

<b><details><summary>3、int 和 Integer 有什么区别</summary></b>

答案：

1、Integer是int的包装类，int则是java的一种基本数据类型

2、Integer变量必须实例化后才能使用，而int变量不需要

3、Integer实际是对象的引用，当new一个Integer时，实际上是生成一个指针指向此对象；而int则是直接存储数据值 。

4、Integer的默认值是null，int的默认值是0

</details>

<b><details><summary>4、String 和 StringBuffer的区别</summary></b>

答案：

JAVA平台提供了两个类：String和StringBuffer，它们可以储存和操作字符串，即包含多个字符的字符数据。这个String类提供了数值不可改变的字符串。而这个StringBuffer类提供的字符串进行修改。当你知道字符数据要改变的时候你就可以使用StringBuffer。典型地，你可以使用StringBuffers来动态构造字符数据。

</details>

<b><details><summary>5、运行时异常与一般异常有何异同？</summary></b>

答案：

异常表示程序运行过程中可能出现的非正常状态，运行时异常表示虚拟机的通常操作中可能遇到的异常，是一种常见运行错误。java编译器要求方法必须声明抛出可能发生的非运行时异常，但是并不要求必须声明抛出未被捕获的运行时异常。

</details>

<b><details><summary>6、说出Servlet的生命周期，并说出Servlet和CGI的区别。</summary></b>

答案：

Servlet被服务器实例化后，容器运行其init方法，请求到达时运行其service方法，service方法自动派遣运行与请求对应的doXXX方法（doGet，doPost）等，当服务器决定将实例销毁的时候调用其destroy方法。

与cgi的区别在于servlet处于服务器进程中，它通过多线程方式运行其service方法，一个实例可以服务于多个请求，并且其实例一般不会销毁，而CGI对每个请求都产生新的进程，服务完成后就销毁，所以效率上低于servlet。

</details>

<b><details><summary>7、说出ArrayList,Vector, LinkedList的存储性能和特性</summary></b>

答案：

ArrayList和Vector都是使用数组方式存储数据，此数组元素数大于实际存储的数据以便增加和插入元素，它们都允许直接按序号索引元素，但是插入元素要涉及数组元素移动等内存操作，所以索引数据快而插入数据慢，Vector由于使用了synchronized方法（线程安全），通常性能上较ArrayList差，而LinkedList使用双向链表实现存储，按序号索引数据需要进行前向或后向遍历，但是插入数据时只需要记录本项的前后项即可，所以插入速度较快。

</details>

<b><details><summary>8、EJB是基于哪些技术实现的？并说出SessionBean和EntityBean的区别，StatefulBean和StatelessBean的区别。</summary></b>

答案：

EJB包括Session Bean、Entity Bean、Message Driven Bean，基于JNDI、RMI、JAT等技术实现。

SessionBean在J2EE应用程序中被用来完成一些服务器端的业务操作，例如访问数据库、调用其他EJB组件。EntityBean被用来代表应用系统中用到的数据。
对于客户机，SessionBean是一种非持久性对象，它实现某些在服务器上运行的业务逻辑。

对于客户机，EntityBean是一种持久性对象，它代表一个存储在持久性存储器中的实体的对象视图，或是一个由现有企业应用程序实现的实体。

Session Bean 还可以再细分为 Stateful Session Bean 与 Stateless Session Bean ，这两种的 Session Bean都可以将系统逻辑放在 method之中执行，不同的是 Stateful Session Bean 可以记录呼叫者的状态，因此通常来说，一个使用者会有一个相对应的 Stateful Session Bean 的实体。Stateless Session Bean 虽然也是逻辑组件，但是他却不负责记录使用者状态，也就是说当使用者呼叫 Stateless Session Bean 的时候，EJB Container 并不会找寻特定的 Stateless Session Bean 的实体来执行这个 method。换言之，很可能数个使用者在执行某个 Stateless Session Bean 的 methods 时，会是同一个 Bean 的 Instance 在执行。从内存方面来看， Stateful Session Bean 与 Stateless Session Bean 比较， Stateful Session Bean 会消耗 J2EE Server 较多的内存，然而 Stateful Session Bean 的优势却在于他可以维持使用者的状态。

</details>

<b><details><summary>9、Collection 和 Collections的区别。 </summary></b>

答案：

Collection是集合类的上级接口，继承与他的接口主要有Set 和List.
Collections是针对集合类的一个帮助类，他提供一系列静态方法实现对各种集合的搜索、排序、线程安全化等操作。

</details>

<b><details><summary>10、&和&&的区别。 </summary></b>

答案：

&是位运算符，表示按位与运算，&&是逻辑运算符，表示逻辑与（and）。

</details>

<b><details><summary>11、HashMap和Hashtable的区别。 </summary></b>

答案：

HashMap是Hashtable的轻量级实现（非线程安全的实现），他们都完成了Map接口，主要区别在于HashMap允许空（null）键值（key）,由于非线程安全，效率上可能高于Hashtable。

HashMap允许将null作为一个entry的key或者value，而Hashtable不允许。

HashMap把Hashtable的contains方法去掉了，改成containsvalue和containsKey。因为contains方法容易让人引起误解。

Hashtable继承自Dictionary类，而HashMap是Java1.2引进的Map interface的一个实现。

最大的不同是，Hashtable的方法是Synchronize的，而HashMap不是，在多个线程访问Hashtable时，不需要自己为它的方法实现同步，而HashMap 就必须为之提供外同步。

Hashtable和HashMap采用的hash/rehash算法都大概一样，所以性能不会有很大的差异。

</details>

<b><details><summary>12、final, finally, finalize的区别。 </summary></b>

答案：

* final 用于声明属性，方法和类，分别表示属性不可变，方法不可覆盖，类不可继承。
* finally是异常处理语句结构的一部分，表示总是执行。
* finalize是Object类的一个方法，在垃圾收集器执行的时候会调用被回收对象的此方法，可以覆盖此方法提供垃圾收集时的其他资源回收，例如关闭文件等。

</details>

<b><details><summary>13、sleep() 和 wait() 有什么区别? </summary></b>

答案：

* sleep是线程类（Thread）的方法，导致此线程暂停执行指定时间，给执行机会给其他线程，但是监控状态依然保持，到时后会自动恢复。调用sleep不会释放对象锁。
* wait是Object类的方法，对此对象调用wait方法导致本线程放弃对象锁，进入等待此对象的等待锁定池，只有针对此对象发出notify方法（或notifyAll）后本线程才进入对象锁定池准备获得对象锁进入运行状态。

</details>

<b><details><summary>14、Overload和Override的区别。Overloaded的方法是否可以改变返回值的类型?</summary></b>

答案：

方法的重写Overriding和重载Overloading是Java多态性的不同表现。
重写Overriding是父类与子类之间多态性的一种表现，重载Overloading是一个类中多态性的一种表现。
如果在子类中定义某方法与其父类有相同的名称和参数，我们说该方法被重写 (Overriding)。
子类的对象使用这个方法时，将调用子类中的定义，对它而言，父类中的定义如同被"屏蔽"了。
如果在一个类中定义了多个同名的方法，它们或有不同的参数个数或有不同的参数类型，则称为方法的重载(Overloading)。
Overloaded的方法是可以改变返回值的类型。

</details>

<b><details><summary>15、error和exception有什么区别?</summary></b>

答案：

* error 表示恢复不是不可能但很困难的情况下的一种严重问题。比如说内存溢出。不可能指望程序能处理这样的情况。
* exception 表示一种设计或实现问题。也就是说，它表示如果程序运行正常，从不会发生的情况。

</details>

<b><details><summary>16、同步和异步有何异同，在什么情况下分别使用他们？举例说明。</summary></b>

答案：

* 如果数据将在线程间共享。例如正在写的数据以后可能被另一个线程读到，或者正在读的数据可能已经被另一个线程写过了，那么这些数据就是共享数据，必须进行同步存取。
* 当应用程序在对象上调用了一个需要花费很长时间来执行的方法，并且不希望让程序等待方法的返回时，就应该使用异步编程，在很多情况下采用异步途径往往更有效率。

</details>

<b><details><summary>17、abstract class和interface有什么区别?</summary></b>

答案：

声明方法的存在而不去实现它的类被叫做抽象类（abstract class），它用于要创建一个体现某些基本行为的类，并为该类声明方法，但不能在该类中实现该类的情况。不能创建abstract 类的实例。然而可以创建一个变量，其类型是一个抽象类，并让它指向具体子类的一个实例。不能有抽象构造函数或抽象静态方法。Abstract 类的子类为它们父类中的所有抽象方法提供实现，否则它们也是抽象类为。取而代之，在子类中实现该方法。知道其行为的其它类可以在类中实现这些方法。

接口（interface）是抽象类的变体。在接口中，所有方法都是抽象的。多继承性可通过实现这样的接口而获得。接口中的所有方法都是抽象的，没有一个有程序体。接口只可以定义static final成员变量。接口的实现与子类相似，除了该实现类不能从接口定义中继承行为。当类实现特殊接口时，它定义（即将程序体给予）所有这种接口的方法。然后，它可以在实现了该接口的类的任何对象上调用接口的方法。由于有抽象类，它允许使用接口名作为引用变量的类型。通常的动态联编将生效。引用可以转换到接口类型或从接口类型转换，instanceof 运算符可以用来决定某对象的类是否实现了接口。

</details>

<b><details><summary>18、heap和stack有什么区别。</summary></b>

答案：

* 栈是一种线形集合，其添加和删除元素的操作应在同一段完成。栈按照后进先出的方式进行处理。
* 堆是栈的一个组成元素

</details>

<b><details><summary>19、forward 和redirect的区别</summary></b>

答案：

* forward是服务器请求资源，服务器直接访问目标地址的URL，把那个URL的响应内容读取过来，然后把这些内容再发给浏览器，浏览器根本不知道服务器发送的内容是从哪儿来的，所以它的地址栏中还是原来的地址。
* redirect就是服务端根据逻辑,发送一个状态码,告诉浏览器重新去请求那个地址，一般来说浏览器会用刚才请求的所有参数重新请求，所以session,request参数都可以获取。

</details>

<b><details><summary>20、EJB与JAVA BEAN的区别？</summary></b>

答案：

Java Bean 是可复用的组件，对Java Bean并没有严格的规范，理论上讲，任何一个Java类都可以是一个Bean。但通常情况下，由于Java Bean是被容器所创建（如Tomcat）的，所以Java Bean应具有一个无参的构造器，另外，通常Java Bean还要实现Serializable接口用于实现Bean的持久性。Java Bean实际上相当于微软COM模型中的本地进程内COM组件，它是不能被跨进程访问的。

Enterprise Java Bean 相当于DCOM，即分布式组件。它是基于Java的远程方法调用（RMI）技术的，所以EJB可以被远程访问（跨进程、跨计算机）。但EJB必须被布署在诸如Webspere、WebLogic这样的容器中，EJB客户从不直接访问真正的EJB组件，而是通过其容器访问。EJB容器是EJB组件的代理，EJB组件由容器所创建和管理。客户通过容器来访问真正的EJB组件。

</details>

<b><details><summary>21、Static Nested Class 和 Inner Class的不同。</summary></b>

答案：

Static Nested Class是被声明为静态（static）的内部类，它可以不依赖于外部类实例被实例化。而通常的内部类需要在外部类实例化后才能实例化。

</details>

<b><details><summary>22、JSP中动态INCLUDE与静态INCLUDE的区别？</summary></b>

答案：

动态INCLUDE用jsp:include动作实现 <jsp:include page="included.jsp" flush="true" />它总是会检查所含文件中的变化，适合用于包含动态页面，并且可以带参数。

静态INCLUDE用include伪码实现,定不会检查所含文件的变化，适用于包含静态页面`<%@ include file="included.htm" %> `

</details>

<b><details><summary>23、什么时候用assert。 </summary></b>

答案：

assertion(断言)在软件开发中是一种常用的调试方式，很多开发语言中都支持这种机制。在实现中，assertion就是在程序中的一条语句，它对一个boolean表达式进行检查，一个正确程序必须保证这个boolean表达式的值为true；如果该值为false，说明程序已经处于不正确的状态下，系统将给出警告或退出。一般来说，assertion用于保证程序最基本、关键的正确性。assertion检查通常在开发和测试时开启。为了提高性能，在软件发布后，assertion检查通常是关闭的。

</details>

<b><details><summary>24、GC是什么? 为什么要有GC? </summary></b>

答案：

GC是垃圾收集的意思（Gabage Collection）,内存处理是编程人员容易出现问题的地方，忘记或者错误的内存回收会导致程序或系统的不稳定甚至崩溃，Java提供的GC功能可以自动监测对象是否超过作用域从而达到自动回收内存的目的，Java语言没有提供释放已分配内存的显示操作方法。

</details>

<b><details><summary>25、short s1 = 1; s1 = s1 + 1;有什么错? short s1 = 1; s1 += 1;有什么错? </summary></b>

答案：

short s1 = 1; s1 = s1 + 1; （s1+1运算结果是int型，需要强制转换类型）

short s1 = 1; s1 += 1;（可以正确编译）

</details>

<b><details><summary>26、Math.round(11.5)等于多少? Math.round(-11.5)等于多少? </summary></b>

答案：

```java
Math.round(11.5)==12
Math.round(-11.5)==-11
```
round方法返回与参数最接近的长整数，参数加1/2后求其floor.

</details>

<b><details><summary>27、String s = new String("xyz");创建了几个String Object? </summary></b>

答案：

两个

</details>

<b><details><summary>28、设计4个线程，其中两个线程每次对j增加1，另外两个线程对j每次减少1。写出程序。</summary></b>

答案：

以下程序使用内部类实现线程，对j增减的时候没有考虑顺序问题。
```java
public class ThreadTest1{
  private int j;
  public static void main(String args[]){
ThreadTest1 tt=new ThreadTest1();
Inc inc=tt.new Inc();
Dec dec=tt.new Dec();
for(int i=0;i<2;i++){
Thread t=new Thread(inc);
t.start();
t=new Thread(dec);
t.start();
}
}
  private synchronized void inc(){
j++;
System.out.println(Thread.currentThread().getName()+"-inc:"+j);
  }
  private synchronized void dec(){
j--;
System.out.println(Thread.currentThread().getName()+"-dec:"+j);
  }
  class Inc implements Runnable{
public void run(){
for(int i=0;i<100;i++){
inc();
}
}
  }
  class Dec implements Runnable{
public void run(){
for(int i=0;i<100;i++){
dec();
}
 }
  }
}
```

</details>

<b><details><summary>29、Java有没有goto?</summary></b>

答案：

java中的保留字，现在没有在java中使用。

</details>

<b><details><summary>30、启动一个线程是用run()还是start()?</summary></b>

答案：

启动一个线程是调用start()方法，使线程所代表的虚拟处理机处于可运行状态，这意味着它可以由JVM调度并执行。这并不意味着线程就会立即运行。run()方法可以产生必须退出的标志来停止一个线程。

</details>

<b><details><summary>31、EJB包括（SessionBean,EntityBean）说出他们的生命周期，及如何管理事务的？</summary></b>

答案：

SessionBean：Stateless Session Bean 的生命周期是由容器决定的，当客户机发出请求要建立一个Bean的实例时，EJB容器不一定要创建一个新的Bean的实例供客户机调用，而是随便找一个现有的实例提供给客户机。当客户机第一次调用一个Stateful Session Bean 时，容器必须立即在服务器中创建一个新的Bean实例，并关联到客户机上，以后此客户机调用Stateful Session Bean 的方法时容器会把调用分派到与此客户机相关联的Bean实例。

EntityBean：Entity Beans能存活相对较长的时间，并且状态是持续的。只要数据库中的数据存在，Entity beans就一直存活。而不是按照应用程序或者服务进程来说的。即使EJB容器崩溃了，Entity beans也是存活的。Entity Beans生命周期能够被容器或者 Beans自己管理。

EJB通过以下技术管理实务：对象管理组织（OMG）的对象实务服务（OTS），Sun Microsystems的Transaction Service（JTS）、Java Transaction API（JTA），开发组（X/Open）的XA接口。

</details>

<b><details><summary>32、应用服务器有那些？</summary></b>

答案：

BEA WebLogic Server，IBM WebSphere Application Server，Oracle9i Application Server，jBoss，Tomcat

</details>

<b><details><summary>33、给我一个你最常见到的runtime exception。</summary></b>

答案：

ArithmeticException, ArrayStoreException, BufferOverflowException, BufferUnderflowException, CannotRedoException, CannotUndoException, ClassCastException, CMMException, ConcurrentModificationException, DOMException, EmptyStackException, IllegalArgumentException, IllegalMonitorStateException, IllegalPathStateException, IllegalStateException, ImagingOpException, IndexOutOfBoundsException, MissingResourceException, NegativeArraySizeException, NoSuchElementException, NullPointerException, ProfileDataException, ProviderException, RasterFormatException, SecurityException, SystemException, UndeclaredThrowableException, UnmodifiableSetException, UnsupportedOperationException

</details>

<b><details><summary>34、接口是否可继承接口? 抽象类是否可实现(implements)接口? 抽象类是否可继承实体类(concrete class)?</summary></b>

答案：

接口可以继承接口。抽象类可以实现(implements)接口，抽象类是否可继承实体类，但前提是实体类必须有明确的构造函数。

</details>

<b><details><summary>35、List, Set, Map是否继承自Collection接口?</summary></b>

答案：

List，Set是，Map不是

</details>

<b><details><summary>36、说出数据连接池的工作机制是什么?</summary></b>

答案：

J2EE服务器启动时会建立一定数量的池连接，并一直维持不少于此数目的池连接。客户端程序需要连接时，池驱动程序会返回一个未使用的池连接并将其表记为忙。如果当前没有空闲连接，池驱动程序就新建一定数量的连接，新建连接的数量有配置参数决定。当使用的池连接调用完成后，池驱动程序将此连接表记为空闲，其他调用就可以使用这个连接。

</details>

<b><details><summary>37、abstract的method是否可同时是static,是否可同时是native，是否可同时是synchronized?</summary></b>

答案：

都不能

</details>

<b><details><summary>38、数组有没有length()这个方法? String有没有length()这个方法？</summary></b>

答案：

数组没有length()这个方法，有length的属性。String有有length()这个方法。

</details>

<b><details><summary>39、Set里的元素是不能重复的，那么用什么方法来区分重复与否呢? 是用==还是equals()? 它们有何区别?</summary></b>

答案：

* Set里的元素是不能重复的，那么用iterator()方法来区分重复与否。equals()是判读两个Set是否相等。
* equals()和==方法决定引用值是否指向同一对象equals()在类中被覆盖，为的是当两个分离的对象的内容和类型相配的话，返回真值。

</details>

<b><details><summary>40、构造器Constructor是否可被override?</summary></b>

答案：

构造器Constructor不能被继承，因此不能重写Overriding，但可以被重载Overloading。

</details>

<b><details><summary>41、是否可以继承String类?</summary></b>

答案：

String类是final类故不可以继承。

</details>

<b><details><summary>42、swtich是否能作用在byte上，是否能作用在long上，是否能作用在String上?</summary></b>

答案：

switch（expr1）中，expr1是一个整数表达式。因此传递给 switch 和 case 语句的参数应该是 int、 short、 char 或者 byte。long,string 都不能作用于swtich。

</details>

<b><details><summary>43、try {}里有一个return语句，那么紧跟在这个try后的finally {}里的code会不会被执行，什么时候被执行，在return前还是后?</summary></b>

答案：

会执行，在return前执行。

</details>

<b><details><summary>44、编程题: 用最有效率的方法算出2乘以8等於几?</summary></b>

答案：

2 << 3

</details>

<b><details><summary>45、两个对象值相同(x.equals(y) == true)，但却可有不同的hash code，这句话对不对?</summary></b>

答案：

不对，有相同的hash code。

</details>

<b><details><summary>46、当一个对象被当作参数传递到一个方法后，此方法可改变这个对象的属性，并可返回变化后的结果，那么这里到底是值传递还是引用传递? </summary></b>

答案：

是值传递。Java 编程语言只有值传递参数。当一个对象实例作为一个参数被传递到方法中时，参数的值就是对该对象的引用。对象的内容可以在被调用的方法中改变，但对象的引用是永远不会改变的。

</details>

<b><details><summary>47、当一个线程进入一个对象的一个synchronized方法后，其它线程是否可进入此对象的其它方法?</summary></b>

答案：

不能，一个对象的一个synchronized方法只能由一个线程访问。

</details>

<b><details><summary>48、编程题: 写一个Singleton出来。</summary></b>

答案：

Singleton模式主要作用是保证在Java应用程序中，一个类Class只有一个实例存在。
一般Singleton模式通常有几种种形式:
第一种形式: 定义一个类，它的构造函数为private的，它有一个static的private的该类变量，在类初始化时实例话，通过一个public的getInstance方法获取对它的引用,继而调用其中的方法。
```java
public class Singleton {
private Singleton(){}
　　    //在自己内部定义自己一个实例，是不是很奇怪？
　　    //注意这是private 只供内部调用
　　    private static Singleton instance = new Singleton();
　　    //这里提供了一个供外部访问本class的静态方法，可以直接访问　　
　　    public static Singleton getInstance() {
　　　　    return instance; 　　
　　    }
    }
```
```java
    第二种形式:
public class Singleton {
　　private static Singleton instance = null;
　　public static synchronized Singleton getInstance() {
　　//这个方法比上面有所改进，不用每次都进行生成对象，只是第一次　　　 　
　　//使用时生成实例，提高了效率！
　　if (instance==null)
　　　　instance＝new Singleton();
return instance; 　　}
}
```
其他形式:
定义一个类，它的构造函数为private的，所有方法为static的。
一般认为第一种形式要更加安全些

</details>

<b><details><summary>49、Java的接口和C++的虚类的相同和不同处。</summary></b>

答案：

由于Java不支持多继承，而有可能某个类或对象要使用分别在几个类或对象里面的方法或属性，现有的单继承机制就不能满足要求。与继承相比，接口有更高的灵活性，因为接口中没有任何实现代码。当一个类实现了接口以后，该类要实现接口里面所有的方法和属性，并且接口里面的属性在默认状态下面都是public static,所有方法默认情况下是public.一个类可以实现多个接口。

</details>

<b><details><summary>50、Java中的异常处理机制的简单原理和应用。</summary></b>

答案：

当JAVA程序违反了JAVA的语义规则时，JAVA虚拟机就会将发生的错误表示为一个异常。违反语义规则包括2种情况。一种是JAVA类库内置的语义检查。例如数组下标越界,会引发IndexOutOfBoundsException;访问null的对象时会引发NullPointerException。另一种情况就是JAVA允许程序员扩展这种语义检查，程序员可以创建自己的异常，并自由选择在何时用throw关键字引发异常。所有的异常都是java.lang.Thowable的子类。

</details>

<b><details><summary>51、垃圾回收的优点和原理。并考虑2种回收机制。</summary></b>

答案：

Java语言中一个显著的特点就是引入了垃圾回收机制，使c++程序员最头疼的内存管理的问题迎刃而解，它使得Java程序员在编写程序的时候不再需要考虑内存管理。由于有个垃圾回收机制，Java中的对象不再有"作用域"的概念，只有对象的引用才有"作用域"。垃圾回收可以有效的防止内存泄露，有效的使用可以使用的内存。垃圾回收器通常是作为一个单独的低级别的线程运行，不可预知的情况下对内存堆中已经死亡的或者长时间没有使用的对象进行清楚和回收，程序员不能实时的调用垃圾回收器对某个对象或所有对象进行垃圾回收。回收机制有分代复制垃圾回收和标记垃圾回收，增量垃圾回收。

</details>

<b><details><summary>52、请说出你所知道的线程同步的方法。</summary></b>

答案：

* wait():使一个线程处于等待状态，并且释放所持有的对象的lock。
* sleep():使一个正在运行的线程处于睡眠状态，是一个静态方法，调用此方法要捕捉InterruptedException异常。
* notify():唤醒一个处于等待状态的线程，注意的是在调用此方法的时候，并不能确切的唤醒某一个等待状态的线程，而是由JVM确定唤醒哪个线程，而且不是按优先级。
* Allnotity():唤醒所有处入等待状态的线程，注意并不是给所有唤醒线程一个对象的锁，而是让它们竞争。

</details>

<b><details><summary>53、你所知道的集合类都有哪些？主要方法？</summary></b>

答案：

最常用的集合类是 List 和 Map。 List 的具体实现包括 ArrayList 和 Vector，它们是可变大小的列表，比较适合构建、存储和操作任何类型对象的元素列表。 List 适用于按数值索引访问元素的情形。
Map 提供了一个更通用的元素存储方法。 Map 集合类用于存储元素对（称作"键"和"值"），其中每个键映射到一个值。

</details>

<b><details><summary>54、描述一下JVM加载class文件的原理机制?</summary></b>

答案：

JVM中类的装载是由ClassLoader和它的子类来实现的,Java ClassLoader 是一个重要的Java运行时系统组件。它负责在运行时查找和装入类文件的类。

</details>

<b><details><summary>55、char型变量中能不能存贮一个中文汉字?为什么? </summary></b>

答案：

能够定义成为一个中文的，因为java中以unicode编码，一个char占16个字节，所以放一个中文是没问题的

</details>

<b><details><summary>56、多线程有几种实现方法,都是什么?同步有几种实现方法,都是什么? </summary></b>

答案：

多线程有两种实现方法，分别是继承Thread类与实现Runnable接口
同步的实现方面有两种，分别是synchronized,wait与notify

</details>

<b><details><summary>57、JSP的内置对象及方法。</summary></b>

答案：

request表示HttpServletRequest对象。它包含了有关浏览器请求的信息，并且提供了几个用于获取cookie, header, 和session数据的有用的方法。
    response表示HttpServletResponse对象，并提供了几个用于设置送回 浏览器的响应的方法（如cookies,头信息等）
    out对象是javax.jsp.JspWriter的一个实例，并提供了几个方法使你能用于向浏览器回送输出结果。
    pageContext表示一个javax.servlet.jsp.PageContext对象。它是用于方便存取各种范围的名字空间、servlet相关的对象的API，并且包装了通用的servlet相关功能的方法。
    session表示一个请求的javax.servlet.http.HttpSession对象。Session可以存贮用户的状态信息
    applicaton 表示一个javax.servle.ServletContext对象。这有助于查找有关servlet引擎和servlet环境的信息
    config表示一个javax.servlet.ServletConfig对象。该对象用于存取servlet实例的初始化参数。
    page表示从该页面产生的一个servlet实例

</details>

<b><details><summary>58、线程的基本概念、线程的基本状态以及状态之间的关系</summary></b>

答案：

线程指在程序执行过程中，能够执行程序代码的一个执行单位，每个程序至少都有一个线程，也就是程序本身。
Java中的线程有四种状态分别是：运行、就绪、挂起、结束。

</details>

<b><details><summary>59、JSP的常用指令</summary></b>

答案：

```
<%@page language="java" contenType="text/html;charset=gb2312" session="true" buffer="64kb" autoFlush="true" isThreadSafe="true" info="text" errorPage="error.jsp" isErrorPage="true" isELIgnored="true" pageEncoding="gb2312" import="java.sql.*"%>
isErrorPage(是否能使用Exception对象)，isELIgnored(是否忽略表达式)
<%@include file="filename"%>
<%@taglib prefix="c"uri="http://......"%>
```

</details>

<b><details><summary>60、什么情况下调用doGet()和doPost()？</summary></b>

答案：

Jsp页面中的form标签里的method属性为get时调用doGet()，为post时调用doPost()。

</details>

<b><details><summary>61、servlet的生命周期</summary></b>

答案：

web容器加载servlet，生命周期开始。通过调用servlet的init()方法进行servlet的初始化。通过调用service()方法实现，根据请求的不同调用不同的do***()方法。结束服务，web容器调用servlet的destroy()方法。

</details>

<b><details><summary>62、如何现实servlet的单线程模式</summary></b>

答案：

```
<%@ page isThreadSafe="false"%>
```

</details>

<b><details><summary>63、页面间对象传递的方法</summary></b>

答案：

request，session，application，cookie等

</details>

<b><details><summary>64、JSP和Servlet有哪些相同点和不同点，他们之间的联系是什么？ </summary></b>

答案：

JSP是Servlet技术的扩展，本质上是Servlet的简易方式，更强调应用的外表表达。JSP编译后是"类servlet"。Servlet和JSP最主要的不同点在于，Servlet的应用逻辑是在Java文件中，并且完全从表示层中的HTML里分离开来。而JSP的情况是Java和HTML可以组合成一个扩展名为.jsp的文件。JSP侧重于视图，Servlet主要用于控制逻辑。

</details>

<b><details><summary>65、四种会话跟踪技术</summary></b>

答案：

会话作用域ServletsJSP 页面描述
page否是代表与一个页面相关的对象和属性。一个页面由一个编译好的 Java servlet 类（可以带有任何的 include 指令，但是没有 include 动作）表示。这既包括 servlet 又包括被编译成 servlet 的 JSP 页面
request是是代表与 Web 客户机发出的一个请求相关的对象和属性。一个请求可能跨越多个页面，涉及多个 Web 组件（由于 forward 指令和 include 动作的关系）
session是是代表与用于某个 Web 客户机的一个用户体验相关的对象和属性。一个 Web 会话可以也经常会跨越多个客户机请求
application是是代表与整个 Web 应用程序相关的对象和属性。这实质上是跨越整个 Web 应用程序，包括多个页面、请求和会话的一个全局作用域

</details>

<b><details><summary>66、Request对象的主要方法：</summary></b>

答案：

```
setAttribute(String name,Object)：设置名字为name的request的参数值
getAttribute(String name)：返回由name指定的属性值
getAttributeNames()：返回request对象所有属性的名字集合，结果是一个枚举的实例
getCookies()：返回客户端的所有Cookie对象，结果是一个Cookie数组
getCharacterEncoding()：返回请求中的字符编码方式
getContentLength()：返回请求的Body的长度
getHeader(String name)：获得HTTP协议定义的文件头信息
getHeaders(String name)：返回指定名字的request Header的所有值，结果是一个枚举的实例
getHeaderNames()：返回所以request Header的名字，结果是一个枚举的实例
getInputStream()：返回请求的输入流，用于获得请求中的数据
getMethod()：获得客户端向服务器端传送数据的方法
getParameter(String name)：获得客户端传送给服务器端的有name指定的参数值
getParameterNames()：获得客户端传送给服务器端的所有参数的名字，结果是一个枚举的实例
getParameterValues(String name)：获得有name指定的参数的所有值
getProtocol()：获取客户端向服务器端传送数据所依据的协议名称
getQueryString()：获得查询字符串
getRequestURI()：获取发出请求字符串的客户端地址
getRemoteAddr()：获取客户端的IP地址
getRemoteHost()：获取客户端的名字
getSession([Boolean create])：返回和请求相关Session
getServerName()：获取服务器的名字
getServletPath()：获取客户端所请求的脚本文件的路径
getServerPort()：获取服务器的端口号
removeAttribute(String name)：删除请求中的一个属性
```

</details>

<b><details><summary>67、J2EE是技术还是平台还是框架？</summary></b>

答案：

J2EE本身是一个标准，一个为企业分布式应用的开发提供的标准平台。
    J2EE也是一个框架，包括JDBC、JNDI、RMI、JMS、EJB、JTA等技术。

</details>

<b><details><summary>68、我们在web应用开发过程中经常遇到输出某种编码的字符，如iso8859-1等，如何输出一个某种编码的字符串？</summary></b>

答案：

  Public String translate (String str) {
    String tempStr = "";
    try {
      tempStr = new String(str.getBytes("ISO-8859-1"), "GBK");
      tempStr = tempStr.trim();
    }
    catch (Exception e) {
      System.err.println(e.getMessage());
    }
    return tempStr;
  }

</details>

<b><details><summary>69、简述逻辑操作(&,|,^)与条件操作(&&,||)的区别。</summary></b>

答案：

区别主要答两点：a.条件操作只能操作布尔型的,而逻辑操作不仅可以操作布尔型,而且可以操作数值型
b.逻辑操作不会产生短路

</details>

<b><details><summary>70、XML文档定义有几种形式？它们之间有何本质区别？解析XML文档有哪几种方式？ </summary></b>

答案：

a: 两种形式 dtd  schema，b: 本质区别:schema本身是xml的，可以被XML解析器解析(这也是从DTD上发展schema的根本目的)，c:有DOM,SAX,STAX等
    DOM:处理大型文件时其性能下降的非常厉害。这个问题是由DOM的树结构所造成的，这种结构占用的内存较多，而且DOM必须在解析文件之前把整个文档装入内存,适合对XML的随机访问
SAX:不现于DOM,SAX是事件驱动型的XML解析方式。它顺序读取XML文件，不需要一次全部装载整个文件。当遇到像文件开头，文档结束，或者标签开头与标签结束时，它会触发一个事件，用户通过在其回调事件中写入处理代码来处理XML文件，适合对XML的顺序访问
    STAX:Streaming API for XML (StAX)

</details>

<b><details><summary>71、简述synchronized和java.util.concurrent.locks.Lock的异同 ？</summary></b>

答案：

主要相同点：Lock能完成synchronized所实现的所有功能
主要不同点：Lock有比synchronized更精确的线程语义和更好的性能。synchronized会自动释放锁，而Lock一定要求程序员手工释放，并且必须在finally从句中释放。

</details>

<b><details><summary>72、EJB的角色和三个对象</summary></b>

答案：

一个完整的基于EJB的分布式计算结构由六个角色组成，这六个角色可以由不同的开发商提供，每个角色所作的工作必须遵循Sun公司提供的EJB规范，以保证彼此之间的兼容性。这六个角色分别是EJB组件开发者（Enterprise Bean Provider） 、应用组合者（Application Assembler）、部署者（Deployer）、EJB 服务器提供者（EJB Server Provider）、EJB 容器提供者（EJB Container Provider）、系统管理员（System Administrator）
三个对象是Remote（Local）接口、Home（LocalHome）接口，Bean类

</details>

<b><details><summary>73、EJB容器提供的服务</summary></b>

答案：

主要提供声明周期管理、代码产生、持续性管理、安全、事务管理、锁和并发行管理等服务。

</details>

<b><details><summary>74、EJB规范规定EJB中禁止的操作有哪些？ </summary></b>

答案：

1.不能操作线程和线程API(线程API指非线程对象的方法如notify,wait等)，
2.不能操作awt，
3.不能实现服务器功能，
4.不能对静态属生存取，
5.不能使用IO操作直接存取文件系统，
6.不能加载本地库.，
7.不能将this作为变量和返回，
8.不能循环调用。

</details>

<b><details><summary>75、remote接口和home接口主要作用</summary></b>

答案：

remote接口定义了业务方法，用于EJB客户端调用业务方法。
home接口是EJB工厂用于创建和移除查找EJB实例

</details>

<b><details><summary>76、bean 实例的生命周期</summary></b>

答案：

对于Stateless Session Bean、Entity Bean、Message Driven Bean一般存在缓冲池管理，而对于Entity Bean和Statefull Session Bean存在Cache管理，通常包含创建实例，设置上下文、创建EJB Object（create）、业务方法调用、remove等过程，对于存在缓冲池管理的Bean，在create之后实例并不从内存清除，而是采用缓冲池调度机制不断重用实例，而对于存在Cache管理的Bean则通过激活和去激活机制保持Bean的状态并限制内存中实例数量。

</details>

<b><details><summary>77、EJB的激活机制</summary></b>

答案：

以Stateful Session Bean 为例：其Cache大小决定了内存中可以同时存在的Bean实例的数量，根据MRU或NRU算法，实例在激活和去激活状态之间迁移，激活机制是当客户端调用某个EJB实例业务方法时，如果对应EJB Object发现自己没有绑定对应的Bean实例则从其去激活Bean存储中（通过序列化机制存储实例）回复（激活）此实例。状态变迁前会调用对应的ejbActive和ejbPassivate方法。

</details>

<b><details><summary>78、EJB的几种类型</summary></b>

答案：

会话（Session）Bean ，实体（Entity）Bean 消息驱动的（Message Driven）Bean
会话Bean又可分为有状态（Stateful）和无状态（Stateless）两种
实体Bean可分为Bean管理的持续性（BMP）和容器管理的持续性（CMP）两种

</details>

<b><details><summary>79、客服端调用EJB对象的几个基本步骤</summary></b>

答案：

设置JNDI服务工厂以及JNDI服务地址系统属性，查找Home接口，从Home接口调用Create方法创建Remote接口，通过Remote接口调用其业务方法。

</details>

<b><details><summary>80、如何给weblogic指定大小的内存? </summary></b>

答案：

在启动Weblogic的脚本中（位于所在Domian对应服务器目录下的startServerName），增加set MEM_ARGS=-Xms32m -Xmx200m，可以调整最小内存为32M，最大200M

</details>

<b><details><summary>81、如何设定的weblogic的热启动模式(开发模式)与产品发布模式?</summary></b>

答案：

可以在管理控制台中修改对应服务器的启动模式为开发或产品模式之一。或者修改服务的启动文件或者commenv文件，增加set PRODUCTION_MODE=true。

</details>

<b><details><summary>82、如何启动时不需输入用户名与密码?</summary></b>

答案：

修改服务启动文件，增加 WLS_USER和WLS_PW项。也可以在boot.properties文件中增加加密过的用户名和密码.

</details>

<b><details><summary>83、在weblogic管理制台中对一个应用域(或者说是一个网站,Domain)进行jms及ejb或连接池等相关信息进行配置后,实际保存在什么文件中?</summary></b>

答案：

保存在此Domain的config.xml文件中，它是服务器的核心配置文件。

</details>

<b><details><summary>84、说说weblogic中一个Domain的缺省目录结构?比如要将一个简单的helloWorld.jsp放入何目录下,然的在浏览器上就可打入http://主机:端口号//helloword.jsp就可以看到运行结果了? 又比如这其中用到了一个自己写的javaBean该如何办?</summary></b>

答案：

Domain目录\服务器目录\applications，将应用目录放在此目录下将可以作为应用访问，如果是Web应用，应用目录需要满足Web应用目录要求，jsp文件可以直接放在应用目录中，Javabean需要放在应用目录的WEB-INF目录的classes目录中，设置服务器的缺省应用将可以实现在浏览器上无需输入应用名。

</details>

<b><details><summary>85、在weblogic中发布ejb需涉及到哪些配置文件</summary></b>

答案：

不同类型的EJB涉及的配置文件不同，都涉及到的配置文件包括ejb-jar.xml,weblogic-ejb-jar.xmlCMP实体Bean一般还需要weblogic-cmp-rdbms-jar.xml

</details>

<b><details><summary>86、如何在weblogic中进行ssl配置与客户端的认证配置或说说j2ee(标准)进行ssl的配置</summary></b>

答案：

缺省安装中使用DemoIdentity.jks和DemoTrust.jks  KeyStore实现SSL，需要配置服务器使用Enable SSL，配置其端口，在产品模式下需要从CA获取私有密钥和数字证书，创建identity和trust keystore，装载获得的密钥和数字证书。可以配置此SSL连接是单向还是双向的。

</details>

<b><details><summary>87、如何查看在weblogic中已经发布的EJB?</summary></b>

答案：

可以使用管理控制台，在它的Deployment中可以查看所有已发布的EJB

</details>

<b><details><summary>88、CORBA是什么?用途是什么? </summary></b>

答案：

CORBA 标准是公共对象请求代理结构(Common Object Request Broker Architecture)，由对象管理组织 (Object Management Group，缩写为 OMG)标准化。它的组成是接口定义语言(IDL), 语言绑定(binding:也译为联编)和允许应用程序间互操作的协议。 其目的为：用不同的程序设计语言书写在不同的进程中运行，为不同的操作系统开发。

</details>

<b><details><summary>89、说说你所熟悉或听说过的j2ee中的几种常用模式?及对设计模式的一些看法</summary></b>

答案：

Session Facade Pattern：使用SessionBean访问EntityBean
Message Facade Pattern：实现异步调用
EJB Command Pattern：使用Command JavaBeans取代SessionBean，实现轻量级访问
Data Transfer Object Factory：通过DTO Factory简化EntityBean数据提供特性
Generic Attribute Access：通过AttibuteAccess接口简化EntityBean数据提供特性
Business Interface：通过远程（本地）接口和Bean类实现相同接口规范业务逻辑一致性
ＥＪＢ架构的设计好坏将直接影响系统的性能、可扩展性、可维护性、组件可重用性及开发效率。项目越复杂，项目队伍越庞大则越能体现良好设计的重要性。

</details>

<b><details><summary>90、说说在weblogic中开发消息Bean时的persistent与non-persisten的差别</summary></b>

答案：

persistent方式的MDB可以保证消息传递的可靠性,也就是如果EJB容器出现问题而JMS服务器依然会将消息在此MDB可用的时候发送过来，而non－persistent方式的消息将被丢弃。

</details>

<b><details><summary>91、Servlet执行时一般实现哪几个方法？</summary></b>

答案：

public void init(ServletConfig config)
public ServletConfig getServletConfig()
public String getServletInfo()
public void service(ServletRequest request,ServletResponse response)
public void destroy()

</details>

<b><details><summary>92、j2ee常用的设计模式？说明工厂模式。</summary></b>

答案：

Java中的23种设计模式：
Factory（工厂模式），      Builder（建造模式），       Factory Method（工厂方法模式），
Prototype（原始模型模式），Singleton（单例模式），    Facade（门面模式），
Adapter（适配器模式），    Bridge（桥梁模式），        Composite（合成模式），
Decorator（装饰模式），    Flyweight（享元模式），     Proxy（代理模式），
Command（命令模式），      Interpreter（解释器模式）， Visitor（访问者模式），
Iterator（迭代子模式），   Mediator（调停者模式），    Memento（备忘录模式），
Observer（观察者模式），   State（状态模式），         Strategy（策略模式），
Template Method（模板方法模式）， Chain Of Responsibleity（责任链模式）
工厂模式：工厂模式是一种经常被使用到的模式，根据工厂模式实现的类可以根据提供的数据生成一组类中某一个类的实例，通常这一组类有一个公共的抽象父类并且实现了相同的方法，但是这些方法针对不同的数据进行了不同的操作。首先需要定义一个基类，该类的子类通过不同的方法实现了基类中的方法。然后需要定义一个工厂类，工厂类可以根据条件生成不同的子类实例。当得到子类的实例后，开发人员可以调用基类中的方法而不必考虑到底返回的是哪一个子类的实例。

</details>

<b><details><summary>93、EJB需直接实现它的业务接口或Home接口吗，请简述理由。</summary></b>

答案：

远程接口和Home接口不需要直接实现，他们的实现代码是由服务器产生的，程序运行中对应实现类会作为对应接口类型的实例被使用。

</details>

<b><details><summary>94、排序都有哪几种方法？请列举。用JAVA实现一个快速排序。</summary></b>

答案：

 排序的方法有：插入排序（直接插入排序、希尔排序），交换排序（冒泡排序、快速排序），选择排序（直接选择排序、堆排序），归并排序，分配排序（箱排序、基数排序）
快速排序的伪代码。
/ /使用快速排序方法对a[ 0 :n- 1 ]排序
从a[ 0 :n- 1 ]中选择一个元素作为m i d d l e，该元素为支点
把余下的元素分割为两段left 和r i g h t，使得l e f t中的元素都小于等于支点，而right 中的元素都大于等于支点
递归地使用快速排序方法对left 进行排序
递归地使用快速排序方法对right 进行排序
所得结果为l e f t + m i d d l e + r i g h t

</details>

<b><details><summary>95、请对以下在J2EE中常用的名词进行解释(或简单描述)</summary></b>

答案：

web容器：给处于其中的应用程序组件（JSP，SERVLET）提供一个环境，使JSP,SERVLET直接更容器中的环境变量接口交互，不必关注其它系统问题。主要有WEB服务器来实现。例如：TOMCAT,WEBLOGIC,WEBSPHERE等。该容器提供的接口严格遵守J2EE规范中的WEB APPLICATION 标准。我们把遵守以上标准的WEB服务器就叫做J2EE中的WEB容器。
EJB容器：Enterprise java bean 容器。更具有行业领域特色。他提供给运行在其中的组件EJB各种管理功能。只要满足J2EE规范的EJB放入该容器，马上就会被容器进行高效率的管理。并且可以通过现成的接口来获得系统级别的服务。例如邮件服务、事务管理。
JNDI：（Java Naming & Directory Interface）JAVA命名目录服务。主要提供的功能是：提供一个目录系统，让其它各地的应用程序在其上面留下自己的索引，从而满足快速查找和定位分布式应用程序的功能。
JMS：（Java Message Service）JAVA消息服务。主要实现各个应用程序之间的通讯。包括点对点和广播。
JTA：（Java Transaction API）JAVA事务服务。提供各种分布式事务服务。应用程序只需调用其提供的接口即可。
JAF：（Java Action FrameWork）JAVA安全认证框架。提供一些安全控制方面的框架。让开发者通过各种部署和自定义实现自己的个性安全控制策略。
RMI/IIOP:（Remote Method Invocation /internet对象请求中介协议）他们主要用于通过远程调用服务。例如，远程有一台计算机上运行一个程序，它提供股票分析服务，我们可以在本地计算机上实现对其直接调用。当然这是要通过一定的规范才能在异构的系统之间进行通信。RMI是JAVA特有的。

</details>

<b><details><summary>96、JAVA语言如何进行异常处理，关键字：throws,throw,try,catch,finally分别代表什么意义？在try块中可以抛出异常吗？</summary></b>

答案：

Java通过面向对象的方法进行异常处理，把各种不同的异常进行分类，并提供了良好的接口。在Java中，每个异常都是一个对象，它是Throwable类或其它子类的实例。当一个方法出现异常后便抛出一个异常对象，该对象中包含有异常信息，调用这个对象的方法可以捕获到这个异常并进行处理。Java的异常处理是通过5个关键词来实现的：try、catch、throw、throws和finally。一般情况下是用try来执行一段程序，如果出现异常，系统会抛出（throws）一个异常，这时候你可以通过它的类型来捕捉（catch）它，或最后（finally）由缺省处理器来处理。
用try来指定一块预防所有"异常"的程序。紧跟在try程序后面，应包含一个catch子句来指定你想要捕捉的"异常"的类型。
throw语句用来明确地抛出一个"异常"。
throws用来标明一个成员函数可能抛出的各种"异常"。
Finally为确保一段代码不管发生什么"异常"都被执行一段代码。
可以在一个成员函数调用的外面写一个try语句，在这个成员函数内部写另一个try语句保护其他代码。每当遇到一个try语句，"异常"的框架就放到堆栈上面，直到所有的try语句都完成。如果下一级的try语句没有对某种"异常"进行处理，堆栈就会展开，直到遇到有处理这种"异常"的try语句。

</details>

<b><details><summary>97、一个".java"源文件中是否可以包括多个类（不是内部类）？有什么限制？</summary></b>

答案：

可以。必须只有一个类名与文件名相同。

</details>

<b><details><summary>98、MVC的各个部分都有那些技术来实现?如何实现? </summary></b>

答案：

MVC是Model－View－Controller的简写。"Model" 代表的是应用的业务逻辑（通过JavaBean，EJB组件实现）， "View" 是应用的表示面（由JSP页面产生），"Controller" 是提供应用的处理过程控制（一般是一个Servlet），通过这种设计模型把应用逻辑，处理过程和显示逻辑分成不同的组件实现。这些组件可以进行交互和重用。

</details>

<b><details><summary>99、java中有几种方法可以实现一个线程？用什么关键字修饰同步方法? stop()和suspend()方法为何不推荐使用？</summary></b>

答案：

有两种实现方法，分别是继承Thread类与实现Runnable接口
用synchronized关键字修饰同步方法
反对使用stop()，是因为它不安全。它会解除由线程获取的所有锁定，而且如果对象处于一种不连贯状态，那么其他线程能在那种状态下检查和修改它们。结果很难检查出真正的问题所在。suspend()方法容易发生死锁。调用suspend()的时候，目标线程会停下来，但却仍然持有在这之前获得的锁定。此时，其他任何线程都不能访问锁定的资源，除非被"挂起"的线程恢复运行。对任何线程来说，如果它们想恢复目标线程，同时又试图使用任何一个锁定的资源，就会造成死锁。所以不应该使用suspend()，而应在自己的Thread类中置入一个标志，指出线程应该活动还是挂起。若标志指出线程应该挂起，便用wait()命其进入等待状态。若标志指出线程应当恢复，则用一个notify()重新启动线程。

</details>

<b><details><summary>100、java中有几种类型的流？JDK为每种类型的流提供了一些抽象类以供继承，请说出他们分别是哪些类？</summary></b>

答案：

字节流，字符流。字节流继承于InputStream \ OutputStream，字符流继承于InputStreamReader \ OutputStreamWriter。在java.io包中还有许多其他的流，主要是为了提高性能和使用方便。

</details>

<b><details><summary>101、java中会存在内存泄漏吗，请简单描述。</summary></b>

答案：

会。如：int i,i2;  return (i-i2);   //when i为足够大的正数,i2为足够大的负数。结果会造成溢位，导致错误。

</details>

<b><details><summary>102、java中实现多态的机制是什么？</summary></b>

答案：

方法的重写Overriding和重载Overloading是Java多态性的不同表现。重写Overriding是父类与子类之间多态性的一种表现，重载Overloading是一个类中多态性的一种表现。

</details>

<b><details><summary>103、垃圾回收器的基本原理是什么？垃圾回收器可以马上回收内存吗？有什么办法主动通知虚拟机进行垃圾回收？</summary></b>

答案：

对于GC来说，当程序员创建对象时，GC就开始监控这个对象的地址、大小以及使用情况。通常，GC采用有向图的方式记录和管理堆(heap)中的所有对象。通过这种方式确定哪些对象是"可达的"，哪些对象是"不可达的"。当GC确定一些对象为"不可达"时，GC就有责任回收这些内存空间。可以。程序员可以手动执行System.gc()，通知GC运行，但是Java语言规范并不保证GC一定会执行。

</details>

<b><details><summary>104、静态变量和实例变量的区别？</summary></b>

答案：

static i = 10; //常量
   class A a;  a.i =10;//可变

</details>

<b><details><summary>105、什么是java序列化，如何实现java序列化？</summary></b>

答案：

序列化就是一种用来处理对象流的机制，所谓对象流也就是将对象的内容进行流化。可以对流化后的对象进行读写操作，也可将流化后的对象传输于网络之间。序列化是为了解决在对对象流进行读写操作时所引发的问题。
序列化的实现：将需要被序列化的类实现Serializable接口，该接口没有需要实现的方法，implements Serializable只是为了标注该对象是可被序列化的，然后使用一个输出流(如：FileOutputStream)来构造一个ObjectOutputStream(对象流)对象，接着，使用ObjectOutputStream对象的writeObject(Object obj)方法就可以将参数为obj的对象写出(即保存其状态)，要恢复的话则用输入流。

</details>

<b><details><summary>106、是否可以从一个static方法内部发出对非static方法的调用？</summary></b>

答案：

不可以,如果其中包含对象的method()；不能保证对象初始化.

</details>

<b><details><summary>107、写clone()方法时，通常都有一行代码，是什么？</summary></b>

答案：

Clone 有缺省行为，super.clone();他负责产生正确大小的空间，并逐位复制。

</details>

<b><details><summary>108、在JAVA中，如何跳出当前的多重嵌套循环？</summary></b>

答案：

用break; return 方法。

</details>

<b><details><summary>109、List、Map、Set三个接口，存取元素时，各有什么特点？</summary></b>

答案：

List 以特定次序来持有元素，可有重复元素。Set 无法拥有重复元素,内部排序。Map 保存key-value值，value可多值。

</details>

<b><details><summary>110、J2EE是什么？</summary></b>

答案：

J2EE是Sun公司提出的多层(multi-diered),分布式(distributed),基于组件(component-base)的企业级应用模型(enterpriese application model).在这样的一个应用系统中，可按照功能划分为不同的组件，这些组件又可在不同计算机上，并且处于相应的层次(tier)中。所属层次包括客户层(clietn tier)组件,web层和组件,Business层和组件,企业信息系统(EIS)层。

</details>

<b><details><summary>111、UML方面</summary></b>

答案：

标准建模语言UML。用例图,静态图(包括类图、对象图和包图),行为图,交互图(顺序图,合作图),实现图。

</details>   

<b><details><summary>112、说出一些常用的类，包，接口，请各举5个</summary></b>

答案：

常用的类：BufferedReader  BufferedWriter  FileReader  FileWirter  String  Integer
常用的包：java.lang  java.awt  java.io  java.util  java.sql
常用的接口：Remote  List  Map  Document  NodeList

</details>

<b><details><summary>113、开发中都用到了那些设计模式?用在什么场合?</summary></b>

答案：

每个模式都描述了一个在我们的环境中不断出现的问题，然后描述了该问题的解决方案的核心。通过这种方式，你可以无数次地使用那些已有的解决方案，无需在重复相同的工作。主要用到了MVC的设计模式。用来开发JSP/Servlet或者J2EE的相关应用。简单工厂模式等。

</details>

<b><details><summary>114、jsp有哪些动作?作用分别是什么?</summary></b>

答案：

JSP共有以下6种基本动作 jsp:include：在页面被请求的时候引入一个文件。 jsp:useBean：寻找或者实例化一个JavaBean。 jsp:setProperty：设置JavaBean的属性。 jsp:getProperty：输出某个JavaBean的属性。 jsp:forward：把请求转到一个新的页面。 jsp:plugin：根据浏览器类型为Java插件生成OBJECT或EMBED标记。

</details>

<b><details><summary>115、Anonymous Inner Class (匿名内部类) 是否可以extends(继承)其它类，是否可以implements(实现)interface(接口)?</summary></b>

答案：

可以继承其他类或完成其他接口，在swing编程中常用此方式。

</details>

<b><details><summary>116、应用服务器与WEB SERVER的区别？</summary></b>

答案：

应用服务器：Weblogic、Tomcat、Jboss
WEB SERVER：IIS、 Apache

</details>

<b><details><summary>117、BS与CS的联系与区别。</summary></b>

答案：

```
C/S是Client/Server的缩写。服务器通常采用高性能的PC、工作站或小型机，并采用大型数据库系统，如Oracle、Sybase、Informix或 SQL Server。客户端需要安装专用的客户端软件。
B/Ｓ是Brower/Server的缩写，客户机上只要安装一个浏览器（Browser），如Netscape Navigator或Internet Explorer，服务器安装Oracle、Sybase、Informix或 SQL Server等数据库。在这种结构下，用户界面完全通过WWW浏览器实现，一部分事务逻辑在前端实现，但是主要事务逻辑在服务器端实现。浏览器通过Ｗeb Server 同数据库进行数据交互。
C/S 与 B/S 区别：
１．硬件环境不同:
　　C/S 一般建立在专用的网络上, 小范围里的网络环境, 局域网之间再通过专门服务器提供连接和数据交换服务.
　　B/S 建立在广域网之上的, 不必是专门的网络硬件环境,例与电话上网, 租用设备. 信息自己管理. 有比C/S更强的适应范围, 一般只要有操作系统和浏览器就行
２．对安全要求不同
　　C/S 一般面向相对固定的用户群, 对信息安全的控制能力很强. 一般高度机密的信息系统采用C/S 结构适宜. 可以通过B/S发布部分可公开信息.
　　B/S 建立在广域网之上, 对安全的控制能力相对弱, 可能面向不可知的用户。
３．对程序架构不同
　　C/S 程序可以更加注重流程, 可以对权限多层次校验, 对系统运行速度可以较少考虑.
　　B/S 对安全以及访问速度的多重的考虑, 建立在需要更加优化的基础之上. 比C/S有更高的要求 B/S结构的程序架构是发展的趋势, 从MS的.Net系列的BizTalk 2000 Exchange 2000等, 全面支持网络的构件搭建的系统. SUN 和IBM推的JavaBean 构件技术等,使 B/S更加成熟.
４．软件重用不同
　　C/S 程序可以不可避免的整体性考虑, 构件的重用性不如在B/S要求下的构件的重用性好.
　　B/S 对的多重结构,要求构件相对独立的功能. 能够相对较好的重用.就入买来的餐桌可以再利用,而不是做在墙上的石头桌子
５．系统维护不同 
　　C/S 程序由于整体性, 必须整体考察, 处理出现的问题以及系统升级. 升级难. 可能是再做一个全新的系统
　　B/S 构件组成,方面构件个别的更换,实现系统的无缝升级. 系统维护开销减到最小.用户从网上自己下载安装就可以实现升级.
６．处理问题不同
　　C/S 程序可以处理用户面固定, 并且在相同区域, 安全要求高需求, 与操作系统相关. 应该都是相同的系统
　　B/S 建立在广域网上, 面向不同的用户群, 分散地域, 这是C/S无法作到的. 与操作系统平台关系最小.
７．用户接口不同
　　C/S 多是建立的Window平台上,表现方法有限,对程序员普遍要求较高
　　B/S 建立在浏览器上, 有更加丰富和生动的表现方式与用户交流. 并且大部分难度减低,减低开发成本.
８．信息流不同
　　C/S 程序一般是典型的中央集权的机械式处理, 交互性相对低
　　B/S 信息流向可变化, B-B B-C B-G等信息、流向的变化, 更像交易中心。
```
</details>

<b><details><summary>118、LINUX下线程，GDI类的解释。</summary></b>

答案：

LINUX实现的就是基于核心轻量级进程的"一对一"线程模型，一个线程实体对应一个核心轻量级进程，而线程之间的管理在核外函数库中实现。
GDI类为图像设备编程接口类库。

</details>

<b><details><summary>119、STRUTS的应用(如STRUTS架构)</summary></b>

答案：

Struts是采用Java Servlet/JavaServer Pages技术，开发Web应用程序的开放源码的framework。 采用Struts能开发出基于MVC(Model-View-Controller)设计模式的应用构架。 Struts有如下的主要功能：

一.包含一个controller servlet，能将用户的请求发送到相应的Action对象。

二.JSP自由tag库，并且在controller servlet中提供关联支持，帮助开发员创建交互式表单应用。 三.提供了一系列实用对象：XML处理、通过Java reflection APIs自动处理JavaBeans属性、国际化的提示和消息。

</details>

<b><details><summary>120、Jdo是什么?</summary></b>

答案：

JDO是Java对象持久化的新的规范，为java data object的简称,也是一个用于存取某种数据仓库中的对象的标准化API。JDO提供了透明的对象存储，因此对开发人员来说，存储数据对象完全不需要额外的代码（如JDBC API的使用）。这些繁琐的例行工作已经转移到JDO产品提供商身上，使开发人员解脱出来，从而集中时间和精力在业务逻辑上。另外，JDO很灵活，因为它可以在任何数据底层上运行。JDBC只是面向关系数据库（RDBMS）JDO更通用，提供到任何数据底层的存储功能，比如关系数据库、文件、XML以及对象数据库（ODBMS）等等，使得应用可移植性更强。

</details>

<b><details><summary>121、内部类可以引用他包含类的成员吗？有没有什么限制？</summary></b>

答案：

一个内部类对象可以访问创建它的外部类对象的内容

</details>

<b><details><summary>122、WEB SERVICE名词解释。JSWDL开发包的介绍。JAXP、JAXM的解释。SOAP、UDDI,WSDL解释。</summary></b>

答案：

Web ServiceWeb Service是基于网络的、分布式的模块化组件，它执行特定的任务，遵守具体的技术规范，这些规范使得Web Service能与其他兼容的组件进行互操作。

JAXP(Java API for XML Parsing) 定义了在Java中使用DOM, SAX, XSLT的通用的接口。这样在你的程序中你只要使用这些通用的接口，当你需要改变具体的实现时候也不需要修改代码。
JAXM(Java API for XML Messaging) 是为SOAP通信提供访问方法和传输机制的API。

WSDL是一种 XML 格式，用于将网络服务描述为一组端点，这些端点对包含面向文档信息或面向过程信息的消息进行操作。这种格式首先对操作和消息进行抽象描述，然后将其绑定到具体的网络协议和消息格式上以定义端点。相关的具体端点即组合成为抽象端点（服务）。

SOAP即简单对象访问协议(Simple Object Access Protocol)，它是用于交换XML编码信息的轻量级协议。

UDDI 的目的是为电子商务建立标准；UDDI是一套基于Web的、分布式的、为Web Service提供的、信息注册中心的实现标准规范，同时也包含一组使企业能将自身提供的Web Service注册，以使别的企业能够发现的访问协议的实现标准。

</details>

<b><details><summary></summary></b>

答案：

</details>

<b><details><summary></summary></b>

答案：

</details>

<b><details><summary></summary></b>

答案：

</details>
