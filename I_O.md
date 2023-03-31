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

