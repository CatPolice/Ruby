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