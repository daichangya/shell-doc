Tutorial
--------
本教程通常讨论shell编程,重点是**Bash**(“ Bourne Again Shell”)shell作为主要的shell解释器。由于有时与bash不同,因此还将引用使用sh,csh,tcsh等其他常见Shell的Shell编程。

Shell编程可以通过在Shell提示符下直接执行Shell命令或按照执行顺序将它们存储在称为Shell脚本的文本文件中,然后执行Shell脚本来完成。要执行,只需在文件具有执行许可权(chmod + x文件名)后编写shell脚本文件名。

Shell脚本文件的第一行以“ sha-bang”(#!)开头,该注释不作为注释读取,其后是Shell解释器所在的完整路径。此路径告诉操作系统此文件是一组将输入到指示的解释器中的命令。请注意,如果在“ sha-bang”处给出的路径不正确,则可能是脚本执行的结果,例如“找不到命令”的错误消息。通常以“ .sh”扩展名命名shell脚本。第一行可能看起来像这样:

	#!/bin/bash 

添加注释:“#”之后的任何文本均被视为注释

要找出当前活动的shell程序及其路径,请在shell程序提示符下键入突出显示的命令(以下是示例响应):

	ps | grep $$
	
	987 tty1 00:00:00 bash

此响应表明您正在使用的shell的类型为“ bash”。接下来找出shell解释器的完整路径

**which bash**

/bin/bash

该响应显示了shell解释器的完整执行路径。确保脚本开头的“ sha-bang”行与此相同的执行路径匹配。

Exercise
-------------
使用“ echo”命令来打印“ Hello,World!”行。

Tutorial Code
-------------
    #!/bin/bash
    # Text to the right of a '#' is treated as a comment - below is the shell command
    echo 'Goodbye, World!'

Expected Output
---------------
    Hello, World!

Solution
--------
    #!/bin/bash
    # Text to the right of a '#' is treated as a comment - below is the shell command
    echo 'Hello, World!'
