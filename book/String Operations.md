在bash shell中，当您使用美元符号后跟变量名称时，shell会使用其值扩展该变量。Shell的此功能称为参数扩展。

但是参数扩展还有许多其他形式，可让您扩展参数并修改值或在扩展过程中替换其他值。在本文中，让我们介绍一下如何使用参数扩展概念进行字符串操作。

### 1.确定Bash Shell脚本中的字符串长度

    ${#string}

上面的格式用于获取给定bash变量的长度。
	
	$ cat len.sh
	#!/bin/bash
	var="Welcome to the geekstuff"
	echo ${#var}
	
	$ ./len.sh

	24


### 2.从Bash Shell脚本中的变量中提取子字符串

Bash提供了一种从字符串中提取子字符串的方法。下面的示例说明如何解析从特定位置开始的n个字符。

	${string:position}

在$position处从$string中提取子字符串

	${string:position:length}

从$position开始，从$string提取$length个字符子串。在下面的示例中，第一个echo语句返回从第15个位置开始的子字符串。第二个echo语句从第15个位置开始返回4个字符。长度必须是大于或等于零的数字。

	$ cat substr.sh
	#!/bin/bash
	
	var="Welcome to the zthinker.com"
	
	echo ${var:15}
	echo ${var:15:4}
	
	$ ./substr.sh
	zthinker.com
	zthi

另外，请参阅我们前面的文章以了解有关[$\*，$@，$#，$$，$！，$？，$-，$\_ bash特殊参数的更多信息](https://www.thegeekstuff.com/2010/05/bash-shell-special-parameters/)。

### 3.最短子串匹配

以下语法从$string前面删除$substring的最短匹配项

	${string#substring}

以下语法从$string的后面删除$substring的最短匹配项

    ${string%substring}

以下示例Shell脚本解释了上面两个最短的子字符串匹配概念。

    $ cat shortest.sh
    #!/bin/bash
    
    filename="bash.string.txt"
    
    echo ${filename#*.}
    echo ${filename%.*}
    
    $ ./shortest.sh
    从最前面删除最短匹配项后：string.txt 
    从背面删除最短匹配项后：bash.string

在第一个echo语句中，子字符串“*,”。匹配字符和一个点，并且#从字符串的开头剥离，因此将子字符串“ bash”剥离。来自名为filename的变量。在第二个echo语句中，子字符串'.\*'与子字符串匹配，以点开头，并且%从字符串后面剥离，因此它删除了子字符串'.txt'。

### 4.最长子串匹配

以下语法从$string前面删除$substring的最长匹配项

    ${string##substring}

以下语法从$string的后面删除$substring的最长匹配项

    ${string%%substring}

下面的示例Shell脚本解释了上面两个最长的子字符串匹配概念。

    $ cat longest.sh
    #!/bin/bash
    
    filename="bash.string.txt"
    
    echo "After deletion of longest match from front:" ${filename##*.}
    echo "After deletion of longest match from back:" ${filename%%.*}
    
    $ ./longest.sh
    After deletion of longest match from front: txt
    After deletion of longest match from back: bash

在上面的示例中，##*. 去除“\*.”的最长匹配项。匹配“ bash.string”。因此，将其剥离后，它将打印剩余的txt。然后%%.*从后面匹配“ .string.txt”的.\*中删除最长匹配项，删除后返回“ bash”。

### 5.在Bash Shell脚本中查找和替换字符串值

#### 只替换第一个比赛

	${string/pattern/replacement}

它与变量$string中的模式匹配，并仅用替换替换模式的第一个匹配项。

	$ cat firstmatch.sh
	#!/bin/bash
	
	filename="bash.string.txt"
	
	echo "After Replacement:" ${filename/str*./operations.}
	
	$ ./firstmatch.sh
	After Replacement: bash.operations.txt

#### 替换所有比赛

	${string//pattern/replacement}

它用替换替换模式的所有匹配项。

	$ cat allmatch.sh
    #!/bin/bash
    
    filename="Path of the bash is/bin/bash"
    
    echo "After Replacement:" ${filename//bash/sh}
    
    $ ./allmatch.sh
    After Replacement: Path of the sh is/bin/sh

关于查找和替换，请参考我们之前的文章[\-sed替代示例](https://www.thegeekstuff.com/2009/09/unix-sed-tutorial-replace-text-inside-a-file-using-substitute-command/)和[Vim查找和替换](https://www.thegeekstuff.com/2009/04/vi-vim-editor-search-and-replace-examples/)。

#### 替换开始和结束

	${string/#pattern/replacement}

仅当模式与$string的开头匹配时，以下语法才用替换字符串替换。

	${string/%pattern/replacement}

仅当模式在给定的$string末尾匹配时，以下语法才用替换字符串替换。

	$ cat posmatch.sh
    #! /bin/bash
    
    filename="/root/admin/monitoring/process.sh"
    
    echo "Replaced at the beginning:" ${filename/#\/root/\/tmp}
    echo "Replaced at the end": ${filename/%.*/.ksh}
    
    $ ./posmatch.sh
    Replaced at the beginning: /tmp/admin/monitoring/process.sh
    Replaced at the end: /root/admin/monitoring/process.ksh
