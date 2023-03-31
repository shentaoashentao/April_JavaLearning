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

