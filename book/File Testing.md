File Testing
-----------------

通常,您将需要对正在运行的文件系统进行一些文件测试。在这种情况下,shell将为您提供一些有用的命令来实现它。

该命令如下所示

* `-<command> [filename]`
* `[filename1] -<command> [filename2]`

我们将简要介绍您在日常生活中可能会遇到的一些常见命令。

Example
-------

**使用“ -e”测试文件是否存在**
 
    #!/bin/bash
	filename="sample.md"
	if [ -e "$filename" ]; then
	    echo "$filename exists as a file"
	fi
     
**使用“ -d”测试目录是否存在**

    #!/bin/bash
    directory_name="test_directory"
    if [ -d "$directory_name" ]; then
        echo "$directory_name exists as a directory"
    fi
    
**使用“ -r”测试文件是否对运行脚本/测试的用户具有读取权限**

    #!/bin/bash
    filename="sample.md"
    if [ ! -f "$filename" ]; then
        touch "$filename"
    fi
    if [ -r "$filename" ]; then
        echo "you are allowed to read $filename"
    else
        echo "you are not allowed to read $filename"
    fi


Exercise
--------
本节没有练习。