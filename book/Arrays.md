Tutorial
--------
一个数组可以用一个名称保存多个值。数组命名与变量命名相同。
通过分配()中包含的以空格分隔的值来初始化数组

    my_array=(apple banana "Fruit Basket" orange)
    new_array[2]=apricot

数组成员不必是连续的或连续的。数组的某些成员可以保留为未初始化。

数组中元素的总数由$ {#arrayname [@]}引用

    my_array=(apple banana "Fruit Basket" orange)
    echo  ${#my_array[@]}                   # 4

可以使用数字索引访问数组元素。第一个元素的索引为0。

    my_array=(apple banana "Fruit Basket" orange)
    echo ${my_array[3]}                     # orange - note that curly brackets are needed
    # adding another array element
    my_array[4]="carrot"                    # value assignment without a $ and curly brackets
    echo ${#my_array[@]}                    # 5
    echo ${my_array[${#my_array[@]}-1]}     # carrot

Exercise
--------
在本练习中,您将需要将数字和字符串添加到正确的数组中。您必须将数字1,2和3添加到“数字”数组中,并将单词“ hello”和“ world”添加到字符串数组中。

您还必须更正变量NumberOfNames和变量second_name的值。NumberOfNames应该使用$#特殊变量保存NAMES数组中名称的总数。变量second_name应该使用方括号运算符[ ]在NAMES数组中保留第二个名称。请注意,索引是从零开始的,因此,如果您要访问列表中的第二项,则其索引将为1。

Tutorial Code
-------------
    #!/bin/bash
    NAMES=( John Eric Jessica )
    # write your code here
    NUMBERS=()
    STRINGS=()
    NumberOfNames=0
    second_name='Vladimir'

Expected Output
---------------
    1 2 3
    hello world
    The number of names listed in the NAMES array: 3
    The second name on the NAMES list is: Eric

Solution
--------
    #!/bin/bash
    NAMES=( John Eric Jessica )
    # write your code here
    NUMBERS=( 1 2 3 )
    STRINGS=( "hello" "world" )
    NumberOfNames=${#NAMES[@]}
    second_name=${NAMES[1]}
    echo ${NUMBERS[@]}
    echo ${STRINGS[@]}
    echo "The number of names listed in the NAMES array: $NumberOfNames"
    echo "The second name on the NAMES list is:" ${second_name}
