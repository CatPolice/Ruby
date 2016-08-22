# Ruby 学习

### 变量 常量
	变量前加上*,表示 Ruby 会将未分配的值封装为数组赋值给该变量。

### 控制语句
	unless语句用法刚好与 if 语句相反。

### 循环语句用法
	times:
		循环次数.times do         
			希望循环的处理 
		end

	for:
		for 变量 in 开始时的数值..结束时的数值 do  
			希望循环的处理
		end
		※ 可以省略 do

	使用 for 语句的程序为:
		from = 10
		to = 20
		sum = 0
		for i in from..to
		sum = sum + i end
		puts sum

	until:
		与 if 语句相对的有 unless 语句,同样地,与 while 语句相对的有 until 语句。
		until 语句的结构与 while 语句完全一样,只是条件判断刚好相反,不满 足条件时才执行循环处理。
		换句话说,while 语句是一直执行循环处理,直到条件不成立为止;until 语句是一直执行循环处理,直到条件成立为止。

		until 条件 do  
			希望循环的处理 
		end
		※ 可以省略 do

	使用 until 语句的程序为:
		sum = 0
		i = 1 
		until sum >= 50
			sum += i
			i += 1
		end
		puts sum

	each 方法:  each 方法将对象集合里的对象逐个取出，这与 for 语句循环取出数组元素非常的相似

	使用 each 语句的程序为:
		names = ["awk","Perl","Python","Ruby"] 
		names.each do |name|
			puts name 
		end

	each 方法的结构如下:
		对象.each do |变量 | 
			希望循环的处理 
		end

	loop 方法:  没有终止循环条件,只是不断执行循环处理


### 方法
	实例方法: 实例方法是最常用的方法。假设有一个对象(实例),那么以这个对象为接收者的方法就被称为实例方法。

	类方法: 接收者不是对象而是类本身时的方法,我们称之为类方法。
		File.open("some_file")  创建新的文件对象
		调用类方法时,可以使用 :: 代替 . 在 Ruby 语法中,两者所代表的意思是一样的。

	函数式方法: 虽说是没有接收者,但并不表示该方法就真的没有可作为接收者的对象,只是在函数式方法这个特殊情况下,可以省略接收者而已。
		print "hello!"  在命令行输出字符串

### 类和模块
	当想知道某个对象属于哪个类时,我们可以使用 class 方法。
		ary = []
		p ary.class #=> Array
	当判断某个对象是否属于某个类时,我们可以使用 instance_of 方法
		ary = []
		p ary.instance_of?(Array)  #=>true

### 类的创建
	attr_reader :name  只读(定义 name 方法)
	attr_writer :name  只写(定义 name= 方法)
	attr_accessor :name  读写(定义以上两个方法)


	class HelloWorld

		attr_accessor :name

		def initialize(myName = "ruby")
    		@name = myName				实例变量name 
  		end

  		def setName(value)
    		@name = value
  		end

  		def getName
    		@name
  		end

  		def hello
    		print "hello world I am"
  		end
	end


	bob = HelloWorld.new("Bob")
	bob.hello
	bob.setName("change")
	p bob.getName


