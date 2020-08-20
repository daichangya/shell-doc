Tutorial
--------
与流行的编程语言一样,shell也支持逻辑决策。

基本的条件决策构造为:

**if [ expression ]; then**

如果'expression'为true的代码

**fi**

    NAME="John"
    if [ "$NAME" = "John" ]; then
      echo "True - my name is indeed John"
    fi

可以用“ else”扩展

    NAME="Bill"
    if [ "$NAME" = "John" ]; then
      echo "True - my name is indeed John"
    else
      echo "False"
      echo "You must mistaken me for $NAME"
    fi

可以使用'elif'(else-if)进行扩展

    NAME="George"
    if [ "$NAME" = "John" ]; then
      echo "John Lennon"
    elif [ "$NAME" = "George" ]; then
      echo "George Harrison"
    else
      echo "This leaves us with Paul and Ringo"
    fi

条件构造使用的表达式被评估为true或false。
表达式可以是单个字符串或变量。空字符串或由空格或未定义的变量名组成的字符串将被评估为false。
该表达式可以是比较的逻辑组合:负号由!表示,逻辑与(连接)由&&表示,逻辑或(分离)由||表示。条件表达式应用双括号\[\[]括起来]。

### 数值比较的类型

    comparison    Evaluated to true when
    $a -lt $b    $a < $b
    $a -gt $b    $a > $b
    $a -le $b    $a <= $b
    $a -ge $b    $a >= $b
    $a -eq $b    $a is equal to $b
    $a -ne $b    $a is not equal to $b

### 字符串比较的类型

    comparison    Evaluated to true when
    "$a" = "$b"     $a is the same as $b
    "$a" == "$b"    $a is the same as $b
    "$a" != "$b"    $a is different from $b
    -z "$a"         $a is empty

-note1:=周围必须有空格

-note2:在字符串变量周围使用“”,以避免将特殊字符的shell扩展为*

### 逻辑组合

    if [[ $VAR_A -eq 1 && ($VAR_B = "bee" || $VAR_T = "tee") ]] ; then
        command...
    fi

### 案例结构

    case "$variable" in
        "$condition1" )
            command...
        ;;
        "$condition2" )
            command...
        ;;
    esac

### 简单案例bash结构

请注意,在这种情况下,$ case是可变的,不必命名为case-这仅是示例

    mycase=1
    case $mycase in
        1) echo "You selected bash";;
        2) echo "You selected perl";;
        3) echo "You selected phyton";;
        4) echo "You selected c++";;
        5) exit
    esac

Exercise
--------
在第一部分中更改变量,以便每个if语句都解析为True。

Tutorial Code
-------------

    #!/bin/bash
    # change these variables
    NUMBER=10
    APPLES=12
    KING=GEORGE
    # modify above variables
    # to make all decisions below TRUE
    if [ $NUMBER -gt 15 ] ; then
      echo 1
    fi
    if [ $NUMBER -eq $APPLES ] ; then
      echo 2
    fi
    if [[ ($APPLES -eq 12) || ("$KING" = "LUIS") ]] ; then
      echo 3
    fi
    if [[ $(($NUMBER + $APPLES)) -le 32 ]] ; then
      echo 4
    fi

Expected Output
---------------
    1
    2
    3
    4

Solution
--------

    #!/bin/bash
    # change these variables
    NUMBER=16
    APPLES=16
    KING="LUIS"
    # modify above variables
    # to make all decisions below TRUE
    if [ $NUMBER -gt 15 ] ; then
      echo 1
    fi
    if [ $NUMBER -eq $APPLES ] ; then
      echo 2
    fi
    if [[ ($APPLES -eq 12) || ("$KING" = "LUIS") ]] ; then
      echo 3
    fi
    if [[ $(($NUMBER + $APPLES)) -le 32 ]] ; then
      echo 4
    fi
