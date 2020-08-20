Tutorial
--------
算术运算符

可以使用以下算术表达式对变量进行简单算术:$((expression))

    A=3
    B=$((100 * $A + 5)) # 305

基本运算符为:

**a + b**加法(a加b)

**a-b**减(a减b)

**a * b**乘法(a乘以b)

**a / b**除法(整数)(a除以b)

**a%b**取模(除以b的整数余数)

**a**********b**取幂(a等于b的幂)

Exercise
--------
在本练习中,您将需要计算一个水果篮的总成本(可变TOTAL),该水果篮包含1个菠萝,2个香蕉和3个西瓜。别忘了包括购物篮的费用。

Tutorial Code
-------------

    #!/bin/bash
	COST_PINEAPPLE=50
	COST_BANANA=4
	COST_WATERMELON=23
	COST_BASKET=1
	TOTAL=
	echo "Total Cost is $TOTAL"

Expected Output
---------------
Total Cost is 128

Solution
--------

    #!/bin/bash
	COST_PINEAPPLE=50
	COST_BANANA=4
	COST_WATERMELON=23
	COST_BASKET=1
	TOTAL=$(($COST_PINEAPPLE + $COST_BANANA + $COST_WATERMELON + $COST_BASKET))
	echo "Total Cost is $TOTAL"
