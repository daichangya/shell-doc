Contributing Tutorials
----------------------

要贡献教程,只需派生以下存储库即可:

[[https://github.com/ronreiter/interactive-tutorials]]

然后,您可以添加或编辑教程,然后向我发送请求请求。

要编写教程,只需在`tutorials`目录中相关目录下创建一个Markdown页面,并将其链接在相关部分的欢迎屏幕中。添加后,请通过运行Flask Web服务器确保其正确链接。

要链接到您创建的教程,请使用双括号从您要链接的页面(通常是`Welcome.md`页面)创建一个链接。

每个教程都包含对该主题的简要说明和一个简短的练习,它将测试用户。用户根据练习完成对代码的修改后,应执行该命令以打印出您将提供的预期输出。

每个教程必须具有以下结构:

###文件名.md

    Tutorial
    --------
    Here you may write text that explains a certain feature.

    Exercise
    --------
    Here you will need to write the purpose of the exercise. Finishing the exercise correctly
    must be accomplished using the new feature that you are explaining.

    Tutorial Code
    -------------
    Write a code block that will appear on the interpreter window. For example, you may
    write an empty function, which the user must complete in order to finish the exercise.

    Expected Output
    ---------------
    Write a code block that will describe the exact output expected from the modified code,
    if it has been modified correctly.

    Solution
    --------
    Write the solution code to the problem.
