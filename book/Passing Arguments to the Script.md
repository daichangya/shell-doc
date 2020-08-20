Passing Arguments to the Script
--------
可以在执行脚本时将参数传递为脚本,方法是在脚本文件名后将其作为空格分隔的列表编写。

在脚本内部,$1变量引用命令行中的第一个参数,$2引用第二个参数,依此类推。
变量$0引用当前脚本。在以下示例中,脚本名称后跟6个参数。

	./bin/my_shopping.sh apple 5 banana 8 "Fruit Basket" 15
	echo $3                          --> results with: banana
	BIG=$5
	echo "A $BIG costs just $6"      --> results with: A Fruit Basket costs just 15


变量$#保留传递给脚本的参数数量

**echo $#               --> results with: 6**

变量$@包含一个以空格分隔的字符串,其中包含传递给脚本的所有参数

Exercise
-------------
本节没有练习。您可以继续。

Tutorial Code
-------------
    #!/bin/bash
    # There is no exercise for this section.
    # You may proceed.

Solution
--------
    #!/bin/bash
    # There is no exercise for this section.
    # You may proceed.

Expected Output
---------------
    #!/bin/bash
    # There is no exercise for this section.
    # You may proceed.
