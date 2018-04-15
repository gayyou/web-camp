### 可变数组  
	public static void main(String[] args) {
		StringBuilder sb = new StringBuilder();  //字符数组长度初始化为32  
		StringBuilder sb = new StringBuilder(32); //32长度 
		StringBuilder sb = new StringBuilder("abcd");//32 value={'a','b','c','d',....}  
		sb2.append("efg");  //在sb2 后面增加efg  
		sb2.append.append(321)   //可以这么做的原因是append的返回值是它本身地址，通过return this 实现方法链；  
		append若是超出长度的话，会额外建立一个新的数组，长度为原来的2倍+2，进行复制赋值，然后返回这个新数组的头个地址，
		}

---

### 基本数据类型的包装类  
八种基本数据类型的包装类是其首字母改为大写（char ->Character，int→Integer）可以有很多种方法处理  

		//声明跟构造器声明一样  
		Integer i =new Integer(); 
但是jdk5.0以后，会有自动装箱。

	Integer i = 1000;  //编译器自动改进代码
int 和 Integer 的区别： int 未赋值时候默认为0，Integer为null。int只能做加减乘除，Integer可以做对象能做的东西。比如学生成绩的时候，包箱类的话可以做到区别没参加考试和0分，而普通类不行（包装类未赋值时候为NULL，普通类为0）  
所以两个Integer用等号相比时候，一般会报错，（比较的是地址）。只是一般，特殊的话就是-127---128之间的数。  

---

### 时间处理相关类  
	java.until.Date A = new Date();
	long t = System.currentTimeMillis();
---

	Calendar c = new GregorianCalendar();
	java.util.Date a = c.getTime();
	System.out.println(a);
定义我们现在用的日历。setTime函数的话，月份是从0开始的，星期日是1，递增到周六是7.
这个可以在查询时候做一个日历表。	

	DateFormat format = new SimpleDateFormat()  //这个函数可以指定输入的模式，了解一下可能会用到。
	
----
### 文件  
文件的读取  

	File f = new File("d:/scr3/TestObject.java");
	File f2 = new File("d:/scr3");	//f2是一个路径
	File f3 = new File(f2,"TestThis.java");		//f3也可以这么写
对未存在的文件的创建
	
	File f4 = new File (f2,"TestFile.java");
	try {
	f4.createNewfile();
	} catch (IOException e){
		e.printStackTrace();
	}  //在目录f2中创建一个文件TestFile.java   //指向的文件不存在的情况下

对目录的创建

	mkdir();		//创建单目录
	mkdirs();		//创建多重目录
	
	File f5 = new File（f2,"/aa/bb/cc/ddd")
	f5.mkdir();   //失败，因为/aa/bb/cc不存在
	f5.mkdir();   //成功，创建了/aa/bb/cc/ddd这个目录

	File[] files = file.listFiles();
	File temp:files

----
### java的异常处理  
可分为编译器或者系统异常自动处理和需要程序员处理两种类型，这里就值写需要程序员处理的异常。  

---
throws声明：

	String openFile() throws FileNotFoundException {
		FileReader reader = new FileReader("");
		return 0;
	}

这里是谁调这个函数谁处理这个错误。  
关于抛出异常的话，有规定的：子类的异常范围不能超过父类声明的范围。
异常往高层上报；
自定义异常，查看别的异常并模仿。并且这个自定义的类要继承Exception或其子项。（错误不是异常，如输入账号错误不可当做异常）。

----
### 容器  
collection是容器，容器内部有很多种，数组是一种容器，链表也是。
  
	Collection c；    //定义接口

List 是有序可重复的。set是无序不可重复的(重复的后者会覆盖前者)。

	ArrayList:底层实现时数组，线程不安全，效率高，查询快，修改、删除。增加慢
	LinkList:底层实现时数组，线程不安全，效率高，查询，慢，修改、删除。增加快
	Vector:线程安全，效率低
怎样声明一个容器呢？
用List（也可以用Collection）
	List list = new ArrayList();   //有次序的，所以只要修改ArrayList就为LinkList就可以变成链表。	
	list.add("aaa");
	list.add(new Date());
	list.add(new Dog);
	list.add(1234);    //自动装箱
	class Dog(){}
	
这段代码中，这些是按照次序排序的。而用Collection 声明的话就不会有次序。