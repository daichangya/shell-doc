Process Substitution
-----------------
在上一节中,我们已经看到了如何将一个命令的输出链接到下一个命令。
但是,如果要将两个或多个命令的输出链接到另一个命令,该怎么办?
如果您有一个将文件作为参数但又想处理发送到该文件的内容的命令,该怎么办?

进程替换允许使用文件名引用进程的输入或输出。
它有两种形式:输出``<(cmd)``和输入``>(cmd)``。

### 示例:
#### 输出
假设您有两个要比较其内容的文件。如果没有对行进行排序,则使用``diff file1 file2``可能会产生误报。
因此,如果要比较这些文件,可以创建两个有序的新文件,然后进行比较。它看起来像:

    sort file1 > sorted_file1
    sort file2 > sorted_file2
    diff sorted_file1 sorted_file2

使用流程替换,您可以在一行中完成:

    diff <(sort file1) <(sort file2)

#### 输入
假设您要将应用程序的日志存储到文件中,同时在控制台上将其打印出来。一个非常方便的命令是``tee``。

    echo "Hello, world!" | tee /tmp/hello.txt

现在,假设您只想在文件中使用小写字符,但在输出中保留常规大小写。
您可以通过以下方式使用流程替换:

    echo "Hello, world!" | tee >(tr '[:upper:]' '[:lower:]' > /tmp/hello.txt)

Exercise
--------

本节没有练习。