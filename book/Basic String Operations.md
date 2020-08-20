Tutorial
--------
Shell允许一些常见的字符串操作,这对于脚本编写非常有用。

### 字符串长度

    #       1234567890123456
    STRING="this is a string"
    echo ${#STRING}            # 16

### 索引

在$SUBSTRING中找到匹配的任何单个字符的$STRING中找到数字位置。注意,在这种情况下使用“ expr”命令。

    STRING="this is a string"
    SUBSTRING="hat"
    expr index "$STRING" "$SUBSTRING"     # 1 is the position of the first 't' in $STRING

### 子串提取

从$STRING开始,在位置$POS之后提取长度$LEN的子字符串。请注意,第一个位置是0。

    STRING="this is a string"
    POS=1
    LEN=3
    echo ${STRING:$POS:$LEN}   # his

如果省略:$LEN,则将$POS的子字符串提取到行尾

    STRING="this is a string"
    echo ${STRING:1}           # $STRING contents without leading character
    echo ${STRING:12}          # ring

### 简单数据提取示例:

    # Code to extract the First name from the data record
    DATARECORD="last=Clifford,first=Johnny Boy,state=CA"
    COMMA1=`expr index "$DATARECORD" ','`  # 14 position of first comma
    CHOP1FIELD=${DATARECORD:$COMMA1}       #
    COMMA2=`expr index "$CHOP1FIELD" ','`
    LENGTH=`expr $COMMA2 - 6 - 1`
    FIRSTNAME=${CHOP1FIELD:6:$LENGTH}      # Johnny Boy
    echo $FIRSTNAME

### 子串替换

    STRING="to be or not to be"

用替换替换第一次出现的子字符串

    STRING="to be or not to be"
    echo ${STRING[@]/be/eat}        # to eat or not to be

替换所有出现的子串

    STRING="to be or not to be"
    echo ${STRING[@]//be/eat}        # to eat or not to eat

删除所有出现的子字符串(替换为空字符串)

    STRING="to be or not to be"
    echo ${STRING[@]// not/}        # to be or to be

如果在$STRING开头替换子字符串的出现

    STRING="to be or not to be"
    echo ${STRING[@]/#to be/eat now}    # eat now or not to be

如果在$STRING结尾,则替换子字符串的出现

    STRING="to be or not to be"
    echo ${STRING[@]/%be/eat}        # to be or not to eat

用shell命令输出替换出现的子字符串

    STRING="to be or not to be"
    echo ${STRING[@]/%be/be on $(date +%Y-%m-%d)}    # to be or not to be on 2012-06-14

Exercise
--------
在此练习中,您将需要更改沃伦·巴菲特的名言。首先创建一个变量ISAY并为其分配原始值。然后使用字符串操作并按照定义的4个更改将其重新分配为新的更改值:

- 变更1:将“snow”的第一个出现替换为“foot”。 
- 变更2:删除第二次出现的“snow”。 
- 变更3:将“finding”替换为“getting”。 
- 更改4:删除“wet”之后的所有字符。提示:一种实现Change4的方法是,如果要在单词'wet'中找到'w'的索引,然后使用子字符串提取。

Tutorial Code
-------------

    #!/bin/bash
	BUFFETT="Life is like a snowball. The important thing is finding wet snow and a really long hill."
	# write your code here
	ISAY=
	ISAY=



# Test code - do not modify

    echo "Warren Buffett said:"
	echo $BUFFETT
	echo "and I say:"
	echo $ISAY

Expected Output
---------------
沃伦·巴菲特(Warren Buffett)说:
Life is like a snowball. The important thing is finding wet snow and a really long hill.
and I say:
Life is like a football. The important thing is getting wet

Solution
--------

    #!/bin/bash
    BUFFETT="Life is like a snowball. The important thing is finding wet snow and a really long hill."
    # write your code here
    ISAY=$BUFFETT
    change1=${ISAY[@]/snow/foot}
    change2=${change1[@]//snow/}
    change3=${change2[@]/finding/getting}
    loc=`expr index "$change3" 'w'`
    ISAY=${change3::$loc+2}

# Test code - do not modify

    echo "Warren Buffett said:"
	echo $BUFFETT
	echo "and I say:"
	echo "$ISAY"
