Tutorial
--------

像其他编程语言一样,shell可能具有函数。函数是实现一组命令和操作的子例程。这对于重复任务很有用。

    # basic construct
    function_name {
      command...
    }

简单地通过写函数名称来调用它们。函数调用等效于命令。通过在函数名称后面指定参数,可以将参数传递给函数。函数中的第一个参数称为$ 1,第二个参数称为$ 2等。

    function function_B {
      echo "Function B."
    }
    function function_A {
      echo "$1"
    }
    function adder {
      echo "$(($1 + $2))"
    }

    # FUNCTION CALLS
    # Pass parameter to function A
    function_A "Function A."     # Function A.
    function_B                   # Function B.
    # Pass two parameters to function adder
    adder 12 56                  # 68

Exercise
--------
在本练习中,您将需要编写一个称为ENGLISH_CALC的函数,该函数可以处理以下语句:

“ 3加5”,“ 5减1”或“ 4乘6”,并将结果分别打印为:“ 3 + 5 = 8”,“ 5-1 = 4”或“ 4 * 6 = 24”。

Tutorial Code
-------------
    #!/bin/bash
    # enter your function code here
    
    # testing code
    ENGLISH_CALC 3 plus 5
    ENGLISH_CALC 5 minus 1
    ENGLISH_CALC 4 times 6

Expected Output
---------------
    3 + 5 = 8
    5 - 1 = 4
    4 * 6 = 24

Solution
--------
    #!/bin/bash
    # enter your function code here
    
    function ENGLISH_CALC {
      a=$1
      b=$3
      signn=$2
      if [ $signn == "plus" ]; then
        echo "$a + $b = $(($a+$b))"
      elif [ $signn == "minus" ]; then
        echo "$a - $b = $(($a-$b))"
      elif [ $signn == "times" ]; then
        echo "$a * $b = $(($a*$b))"
      fi
    }
    
    # testing code
    ENGLISH_CALC 3 plus 5
    ENGLISH_CALC 5 minus 1
    ENGLISH_CALC 4 times 6
