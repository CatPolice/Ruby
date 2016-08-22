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

  		def test_name
    		name = "Ruby"          为局部变量赋值
    		self.name = "Ruby"     调用name= 方法

    	另外,在调用像 name= 方法这样的以 = 结束的方法时,有一点需要特别注意。
    	即使实例方法中已经有了 name = "Ruby" 这样的定义,但如果仅在方法内部 定义名为 name 的局部变量,也不能以缺省接收者的方式调用 name= 方法。
    	这种情况下,我们需要用 self.name = "Ruby" 的形式来显式调用 name 方法。

		end

		类方法
		def HelloWorld.hello(name)
    		puts "#{name} said hello."
  		end

	end


	bob = HelloWorld.new("Bob")
	bob.hello
	bob.setName("change")
	p bob.getName

### 类方法
	备注 class << 类名 ~ end 这种写法的类定义称为单例类定义,单例类定义中定义的方法称为单例方法。

	class << HelloWorld 
		def hello(name)
			puts "#{name} said hello." end
	end
	HelloWorld.hello("John")


	class HelloWorld
		def self.hello(name)
			puts "#{name} said hello." 
		end
	end

### 常量
	在 class 上下文中可以定义常量。

	class HelloWorld 
		Version = "1.0"
	end
	对于在类中定义的常量,我们可以像下面那样使用 :: 通过类名来实现外部访问。
	p HelloWorld::Version  #=> "1.0"

### 类变量
	以 @@ 开头的变量称为类变量。类变量是该类所有实例的共享变量,这一点与常量类似,不同的是我们可以多次修改类变量的值。
	另外,与实例变量一样, 从类的外部访问类变量时也需要存取器。不过,由于 attr_accessor 等存取器都不能使用,因此需要直接定义。


	class HelloCount

		@@count = 0 # 调用hello 方法的次数

		def HelloCount.count 		# 读取调用次数的类方法 @@count
		end
                           
		def initialize(myname="Ruby") 
			@name = myname
		end

		def hello
			@@count += 1 # 累加调用次数
			puts "Hello, world. I am #{@name}.\n"
		end 
	end

	bob = HelloCount.new("Bob") 
	alice = HelloCount.new("Alice") 
	ruby = HelloCount.new

	p HelloCount.count      #=> 0
	bob.hello 
	alice.hello 
	ruby.hello
	p HelloCount.count      #=> 3

### 块
	我们使用 module 关键字来创建模块。
	语法与创建类时几乎相同。模块名的首字母必须大写。

	module 模块名  
		模块定义 
	end


	module HelloModule					module 关键字 
		Version = "1.0"					定义常量

		def hello(name)					定义方法
			puts "Hello, #{name}."
		end

	module_function :hello				指定 hello 方法为模块函数
	end

	p HelloModule::Version				=> "1.0"
	HelloModule.hello("Alice")			=> Hello, Alice.
	include HelloModule					包含模块
	p Version							=> "1.0"
	hello("Alice")						=> Hello, Alice.		

