Tutorial
---------
管道(通常称为管道)是一种链接命令并将命令的输出连接到命令的输入的方法。
管道由管道字符``|``表示。当命令需要复杂或长输入时,它特别方便。

    command1 | command2

默认情况下,管道仅重定向标准输出,如果要包括标准错误,则需要使用格式``|&``,这是``2>&1 |``的简写形式。

### 示例:
想象一下,您很快想知道目录中的条目数,可以使用管道使用选项``-l``将``ls``命令的输出重定向到``wc``命令。

    ls / | wc -l

然后,您只想查看前10个结果

    ls / | head
    
 *注意:head默认情况下输出前10行,请使用选项-n更改此行为*

Exercise
--------
在本练习中,您将需要根据cpuinfo文件(/proc/cpuinfo)中的信息打印处理器数量。

*提示:每个处理器都有一个唯一的编号,例如第一个处理器将包含行``processor: 0``*

Tutorial Code
-------------
    cat /proc/cpuinfo # | some command

Expected Output
---------------
    4

Solution
--------
    #!/bin/bash
    cat /proc/cpuinfo | grep processor | wc -l
