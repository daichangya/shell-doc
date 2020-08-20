Bash Trap Command
-----------------

您经常想遇到的情况 
脚本中的特殊信号/中断/用户输入 
防止不可预测的事情。

trap是您尝试执行的命令:

* `trap <arg/function> <signal>`

### 例

    #!/bin/bash
	# traptest.sh
	# notice you cannot make Ctrl-C work in this shell, 
	# try with your local one, also remeber to chmod +x 
	# your local .sh file so you can execute it!

	trap "echo Booh!" SIGINT SIGTERM
	echo "it's going to run until you hit Ctrl+Z"
	echo "hit Ctrl+C to be blown away!"

	while true        
	do
	    sleep 60       
	done

当然,您可以将`"echo Booh!"`替换为一个函数:

 function booh {
		echo "booh!"
	}

并在trap中调用它:

 trap booh SIGINT SIGTERM


您可以捕获的一些常见信号类型:

* `SIGINT`:用户发送中断信号(Ctrl + C)

* `SIGQUIT`:用户发送退出信号(Ctrl + C)

* `SIGFPE`:尝试了非法的数学运算

您可以通过输入以下命令来检查所有信号类型:
 
    kill -l

注意每个信号名称之前的数字,您可以使用该数字来避免在trap中键入长字符串:

    #2 corresponds to SIGINT and 15 corresponds to SIGTERM
	trap booh 2 15	


trap的常见用法之一是清理临时文件:


    trap "rm -f folder; exit" 2


Exercise
--------

本节没有练习。