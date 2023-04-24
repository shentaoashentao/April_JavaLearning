**字符串常用api**
1. length 获取字符串的长度
trim() 去掉前后空格
equals()比较字符串是否相等 返回true false 
equalignorecase 忽视大小写
2.charAt(下标) 获取下标对应的字符，也可以使用数组的写法 字符串[下标]
  str1="Hello"
str2=str1.charAt(1)  输出e
3.indexOf() 查找字符串中是否含有某个字符串，返回满足条件的第一个的下标，找不到返回-1
  str1="Hello"
int n =str1.indexof("l")  输出2
4.lastIndexOf() 查找字符串中是否含有某个字符串，返回满足条件的最后一个的下标，找不到返回-1
  str1="Hello"
int n =str1.lastindexof("l")  输出3
5. toUpperCase() 英文字母转大写
6. toLowerCase() 英文字母转小写
7.slice(start, end) 截取字符串，start开始的下标，end结束的下标(不包括结束下标)，end为空截取到最后，下标是负数表示倒数
8. split() 将字符串转为数组，可以指定分隔的符号
9. substring() 用于提取字符串中介于两个指定下标之间的字符。返回的子串包括 开始 处的字符，但不包括 结束 处的字符。
10.concat() 连接 str1="Hello" str2="World".concat(str1)   输出WorldHello
**数组常用api**
1.fill(a,b)  数组a内元素全填充为b
 fill(a,b,c,d) 数组a从b开始到c结束 填充d  位置包括b不包括c
2.sort(a)  将数组a内的数据从小到大排序 
3. b=arrays.copyof(a,a.length)   参数 （复制的第一个数组，复制后数组的长度） 
          arrays.copyofRange(a,b,c)    复制从a[b]开始的 c-b个
4. binarySearch()  采用的是二分查找法，找到了则返回索引值，没有找到则返回-1
5.Arrays.equals(arr1,arr2); 比较两个数组是否相等

 

**单例模型：**在整个程序中，同一个类始终只会有一个对象来进行操作
	懒汉式单例：多线程线程安全问题 加锁 添加关键字(synchronized),使得同一时间只有一个线程进入
饿汉式单例

**泛型**  	泛型提供了编译时类型安全检测机制，该机制允许程序员在编译时检测到非法的类型。
	泛型的本质是参数化类型，也就是说所操作的数据类型被指定为一个参数。
	本质时参数化类型 即所操作的数据类型被指定为一个参数
利用泛型 可以达到代码的复用 抽奖案例：奖金int与物品string

**自定义泛型方法**	  在静态方法中使用泛型public static <E> void test<E e>
                                成员方法自定义泛型，在实际使用中再进行类型确定 public <E> void test(E e)

泛型类派生子类 子类也是泛型类  那么子类的泛型标识<>要与父类一致

**泛型上限通配符**  ：类/接口<?** extends **实参类型> 要求该泛型类型，只能是实参类型或者实参类型的**子类**类型 。不可以list.add()填充元素
minicat extends cat / cat extends animils
当show(ArryList<? extends Cat> list)
传递集合类型 只能是Cat 或Cat的子类
**泛型下限通配符 ： **类/接口<? **super** 实参类型> 要求该泛型类型，只能是实参类型或者实参类型的**父类**类型。 可以list.add()填充元素
P10通配符比较器下限（2）


**多态**	(方法重写 +类型转换)多态就是同一个接口，使用不同的实例而执行不同操作  
	根据父类创建了一个实例对象，但是指向某个子类。这个实例对象在调用该类的类方法时
	如果子类重写父类则执行子类的方法 否则执行父类

方法**重写**时（父类已有 子类再写一遍 ）
在子类下使用super.fangfa()  可以调用父类

instanceof关键字 
用法：Student student = new SportStudent()

public static void test(Student student)//不知道参数进来的student的类型
if（student instanceof SportStudent）
用来判断类型转换 就可以SportStudent  sportStudent =(SportStudent ) student 

**Stream流**
1.获取方法
2.中间过滤，去重  （方法.方法）
3.end

1.获取方法 条件：单列集合 双列集合 数组 同种数据类型的多个数据
单列集合：把数据加入list中 调用stream方法输出即可
双列集合：构造HashMap 1.keySet/entrySet获取
数组：定义一个数组后 Arrays.stream(arr)
同种数据类型的多个数据：stream.of(放数据)
2.中间方法 filter 
a.命名内部类_Predicate接口的_ test 里面加一个判断 ture则留下
b.lambda表达式 (String s)->{判断表达式}
 其他中间方法
               a.list.stream().limit(x).forEach(s -> System.**_out_**.println(s));  截取从前往后x个数据输出
b.list.stream().skip(x).forEach(s -> System.**_out_**.println(s));跳过前x个输出后面的
c._concat_(stream1, stream2); 把两个stream合起来
d.stream().distinct()去重
3.终结方法
a.forEach()    内只有一个accept方法 在accept中写业务
b.count()返回流中的元素数
收集方法 collect
filter(条件).collect(Collectors._toList_())//把过滤好的数据 放到新的集合内 可以有重复
filter(条件).collect(Collectors._toSet_())//没重复的新数据
collect(Collectors._toMap_()) //把数据添加到Map集合

**I/O**
I:  硬盘中文件的读写，O:把数据从内存保存到本地
字节流：音频图片
字符流：java文件 txt文件

**字节流输出流**
1.写数据进文件FileOutputStream()      
 a.()内第一个参数写文件的路径 若不存在会创建 若存在会清空里面的数据再写
b.第二个参数 表示是否续写 默认false
2.write()  写数据 ()内写数字 文件内显示 相对应的字符 100--d
若要一次输出多个 先定义数组 write(数组名)
若要输出中间几个 write(数组名,第几个开始，几个)
实现换行 write(**"\r\n"**.getBytes())
3.close() 释放资源 若不写 该文件删不掉

**字节流输入流**
1.写数据进文件FileInputStream()      
a.文件必须要存在
2.read()  读的是字符对应的数字 若还要看字符 要char()一下
a.读一个 直接调用read
b.读多个 使用while循环     条件是 读进去的值    !=-1

**字符流输出流**  底层是字节流+编码 FileWrite
1.write
a.write(int c) 写一个字符
b.write(char[] cbuf) 字符数组
c.write(char[] cbuf,int off,int len)字符数组的一部分
d.write(String s)字符串
e.write(String str, int off,int len)字符串的一部分
ps:在write完后 加一条 flush()刷新流 ，刷新完可以再写数据。close()后数据不能再写 
**字符流输入流**

**类加载**
类加载器：把.class文件加载到内存中
加载 验证 准备 解析 初始化
**加载**：
1.通过包名+类名，获取这个类，用流进行传输
2.把类加载到内存
3.加载完毕 创建class对象
验证
准备
解析
初始化

**类加载器 **
启动类加载器 Bootstrap Classloader
平台类加载器 Platform Classloader
系统类加载器 System Classloader
自定义加载器  UserClassloader

**JDBC**
步骤：
1.注册驱动
2.获取连接DriverManager.getConnection(url,urlname,password);
3.定义SQL语句
4.获取sql执行的对象 statement
ps:一直有报错
String url=**"jdbc:mysql://127.0.0.1:3306/db01?useSSL=false"**;禁用安全连接

API
DriverManger 注册驱动
Connection  获取执行SQL的对象 管理异常 trycatch
Statement  执行sql语句
int executeUpdate(sql) 执行DML DDL语句
返回（1）DML语句影响行数
（2）DDL执行成功也可能返回0
ResultSet
                 1.使用游标向下移动一行 并判断该行是否有数据 next()
2.获取数据 getXXX()
PrepareStatement   Statement的强化版

sql添加语句   **INSERT into account(Name,money) values(?,?)    **id是自动增长所以不用写
   修改 ** ** **"UPDATE account\n" **+
       		 **"SET name=?,\n" **+
      		  **"**_money_**=?\n" **+
        	**"WHERE id= ?"**;
删除    **"DELETE from account\n" **+
        **"WHERE id= ?"**;

**日志**
logger日志的几个方法
logger.debug、logger.info、logger.warn、logger.error、logger.fatal 的区别：

相同处：
它们的作用都是把错误信息写到文本日志里

不同的是它们表示的日志级别不同：
日志级别由高到底是：fatal -> error -> warn -> info -> debug,低级别的会输出高级别的信息，高级别的不会输出低级别的

# junit单元测试
针对最小的功能单元编写测试代码
@Test：测试方法 
@Before：用来修饰实例方法，该方法会在每一个测试方法执行**之前**执行一次
@After：用来修饰实例方法，该方法会在每一个测试方法执行**之后**执行一次
@BeforeClass :用来静态修饰方法，该方法会在所有测试方法**之前** 只执行一次
@AfterClass ：用来静态修饰方法，该方法会在所有测试方法**之后** 只执行一次

**网络编程**
在网络通信协议下 实现网络互连的不同计算机上运行的程序间可以进行数据交换

UDP
Java提供了DatagramSocket类作为基于UDP协议的Socket
TCP
发送数据
1.创建客户端的Socket对象  Socket(String host,int port)
2.获取输出流 写数据  OutputStream getOutputStream()
3.释放资源
接收对象
1.创建服务器的Socket对象（ServerSocket）
ServerSocket(int port)
2.监听客户端连接 返回一个Socket对象
Socket accept()
3.获取输入流 读数据 显示数据
inputStream getinputStream()
4.释放

# Servlet
1.加载和实例化
2.初始化
3.请求处理。每次调用Servlet时，Servlet容器都会调Service()方法对请求进行处理
4.服务终止  需要释放内存或容器关闭时  destory()

HttpSelvet使用步骤
1.继承HttpSelvet
2.重新doGet doPost 
Servlet urlPattern配置
1.精确匹配
配置路径@WebServlet(urlPatterns = **"/user/select"**)
访问路径 [http://localhost:8080/WebDemo/](http://localhost:8080/WebDemo/aa.do)user/select
2目录匹配
配置路径@WebServlet(urlPatterns = **"/user/*"**)
访问路径 [http://localhost:8080/WebDemo/](http://localhost:8080/WebDemo/aa.do)user/aaa
访问路径 [http://localhost:8080/WebDemo/](http://localhost:8080/WebDemo/aa.do)user/bbb
3.扩展名匹配
配置路径@WebServlet(urlPatterns = **"*.do"**)
访问路径 [http://localhost:8080/WebDemo/](http://localhost:8080/WebDemo/aa.do)aaa.do
访问路径 [http://localhost:8080/WebDemo/](http://localhost:8080/WebDemo/aa.do)bbb.do
4.任意匹配
配置路径@WebServlet(urlPatterns = **"/"**)
配置路径@WebServlet(urlPatterns = **"/*"**)
访问路径 [http://localhost:8080/WebDemo/](http://localhost:8080/WebDemo/aa.do)aaa

**反射**
指对于任何一个Class类 在 运行的时候都可以直接得到这个类的全部成分

1. 先得到编译后的Class类对象 然后就可以得到Class的全部成分

    Hello.java-->javac-->Hello.class
Class c = Hello.class

反射机制
先获取配置文件中的信息，动态获取信息并创建对象和调用方法

1.获取class对象
Class clazz = Class._forName_(**"Reflect.myreflect.Student"**);
2.获取里面的构造方法对象
clazz.getDeclaredConstructor
clazz.getConstructor
3.若是public的 则直接通过newInstance()创建对象
若是私有 需要加上一句constructor.setAccessible(**true**);
