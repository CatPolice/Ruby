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

