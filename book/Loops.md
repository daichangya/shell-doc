Tutorial
--------
### bash for循环

    # basic construct
    for arg in [list]
    do
     command(s)...
    done

对于每次通过循环,arg都会使用列表中每个连续值的值。然后执行命令。

    # loop on array member
    NAMES=(Joe Jenny Sara Tony)
    for N in ${NAMES[@]} ; do
      echo "My name is $N"
    done

    # loop on command output results
    for f in $( ls prog.sh /etc/localtime ) ; do
      echo "File is: $f"
    done

### bash while循环

    # basic construct
    while [ condition ]
    do
     command(s)...
    done

while构造会测试条件,如果为true,则执行命令。只要条件为真,它就会不断循环。

    COUNT=4
    while [ $COUNT -gt 0 ]; do
      echo "Value of count is: $COUNT"
      COUNT=$(($COUNT - 1))
    done

### bash直到循环

    # basic construct
    until [ condition ]
    do
     command(s)...
    done

直到构造测试条件,如果为false,则执行命令。只要条件为假,它就保持循环(与while构造相反)

    COUNT=1
    until [ $COUNT -gt 5 ]; do
      echo "Value of count is: $COUNT"
      COUNT=$(($COUNT + 1))
    done

### “break”和“continue”语句

break和continue可用于控制for,while和直到构造的循环执行。continue用于跳过特定循环迭代的其余部分,而break用于跳过整个循环的其余部分。一些例子:

    # Prints out 0,1,2,3,4

    COUNT=0
    while [ $COUNT -ge 0 ]; do
      echo "Value of COUNT is: $COUNT"
      COUNT=$((COUNT+1))
      if [ $COUNT -ge 5 ] ; then
        break
      fi
    done

    # Prints out only odd numbers - 1,3,5,7,9
    COUNT=0
    while [ $COUNT -lt 10 ]; do
      COUNT=$((COUNT+1))
      # Check if COUNT is even
      if [ $(($COUNT % 2)) = 0 ] ; then
        continue
      fi
      echo $COUNT
    done

Exercise
--------
在本练习中,您将需要循环访问并按接收顺序从数字列表中打印出所有偶数。不要打印序列中237之后的任何数字。

Tutorial Code
-------------
    #!/bin/bash
    NUMBERS=(951 402 984 651 360 69 408 319 601 485 980 507 725 547 544 615 83 165 141 501 263 617 865 575 219 390 237 412 566 826 248 866 950 626 949 687 217 815 67 104 58 512 24 892 894 767 553 81 379 843 831 445 742 717 958 609 842 451 688 753 854 685 93 857 440 380 126 721 328 753 470 743 527)
    
    # write your code here

Expected Output
---------------
402
984
360
408
980
544
390

Solution
--------
    #!/bin/bash
    NUMBERS=(951 402 984 651 360 69 408 319 601 485 980 507 725 547 544 615 83 165 141 501 263 617 865 575 219 390 237 412 566 826 248 866 950 626 949 687 217 815 67 104 58 512 24 892 894 767 553 81 379 843 831 445 742 717 958 609 842 451 688 753 854 685 93 857 440 380 126 721 328 753 470 743 527)
    
    # write your code here
    for gg in ${NUMBERS[@]}; do
    	
        if [ $gg == 237 ]; then
        	break;
        elif [ $(($gg % 2)) == 0 ]; then
        	echo $gg
        fi
    done
