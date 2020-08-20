Tutorial
--------

数组比较
Shell可以处理数组
数组是包含多个值的变量。任何变量都可以用作数组。数组的大小没有最大限制,也没有要求成员变量被连续索引或连续分配。
数组从零开始:第一个元素的编号为0。 
   
 # basic construct
	# array=(value1 value2 ... valueN)
	array=(23 45 34 1 2 3)
	#To refer to a particular value (e.g. : to refer 3rd value)
	echo ${array[2]}  
    
	#To refer to all the array values
	echo ${array[@]}
	
	#To evaluate the number of elements in an array
	echo ${#array[@]}
 
Exercise
--------
在本练习中,您将需要比较三个数组列表并编写所有三个数组的公共元素:

`a=(3 5 8 10 6)`,`b=(6 5 4 12)`,`c=(14 7 5 7)`
结果是共同点5。

Tutorial Code
-------------
 #!/bin/bash
	# enter your array comparison code here
        

Expected Output
---------------
 5

Solution
--------

	#!/bin/bash
	# enter your array comparison code here
	# initialize arrays a b c
	a=(3 5 8 10 6) 
	b=(6 5 4 12) 
	c=(14 7 5 7)
	#comparison of first two arrays a and b
	for x in "${a[@]}"; do 
	  in=false 
	  for y in "${b[@]}"; do 
	    if [ $x = $y ];then 
	      # assigning the matching results to new array z
	      z[${#z[@]}]=$x
	    fi
	  done 
	done
	#comparison of third array c with new array z
	for i in "${c[@]}"; do 
	  in=false
	  for k in "${z[@]}"; do
	    if [ $i = $k ];then
	      # assigning the matching results to new array j
	      j[${#j[@]}]=$i
	    fi
	  done 
	done 
	# print content of array j
	echo ${j[@]}
