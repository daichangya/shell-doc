Special Variables
-----------------

在上一个有关shell函数的教程中,您使用“ $ 1”表示传递给function_A的第一个参数。此外,这是shell中的一些特殊变量:


* `$0`-当前脚本的文件名|
* `$n`-调用传递给脚本的第N个参数或调用函数|
* `$#`-传递给脚本或函数的参数数量|
* `$@`-所有传递给脚本或函数的参数|
* `$*`-所有传递给脚本或函数的参数|
* `$?`-最后执行的命令的退出状态|
* `$$`-当前shell的进程ID。对于shell脚本,这是它们正在执行的进程ID.|
* `$!`-最后一个后台命令的进程号|
    

### 示例:

    #!/bin/bash
    echo "Script Name: $0"
    function func {
        for var in $*
        do
            let i=i+1
            echo "The \$${i} argument is: ${var}"
        done
        echo "Total count of arguments: $#"
    }
    func We are argument


`$@`和`$*`用双引号引起来时的行为不同。

    #!/bin/bash
    function func {
        echo "--- \"\$*\""
        for ARG in "$*"
        do
            echo $ARG
        done
    
        echo "--- \"\$@\""
        for ARG in "$@"
        do
            echo $ARG
        done
    }
    func We are argument

Exercise
--------

本节没有练习。