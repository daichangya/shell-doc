在本文中,我们介绍如何使用sed替代命令“ s”。

s命令可能是sed中最重要的命令,并且有很多不同的选项。

s命令试图将模式空间与提供的REGEXP相匹配;如果匹配成功,则将匹配的模式空间部分替换为REPLACEMENT。

语法

	#sed 'ADDRESSs/REGEXP/REPLACEMENT/FLAGS' filename
	#sed 'PATTERNs/REGEXP/REPLACEMENT/FLAGS' filename

*   s是替代命令
*   /是定界符
*   REGEXP是匹配的正则表达式
*   REPLACEMENT是要替换的数据

标志可以是以下任意一种

*   g将所有REGEXP实例替换为REPLACEMENT
*   n可以是任何数字,用REPLACEMENT代替REGEXP的第n个实例。
*   p如果进行了替换,则打印新的数据。
*   i以不区分大小写的方式匹配REGEXP。
*   w文件如果进行替换,则将结果写到给定文件中。
*   我们可以使用不同的定界符(@%;:)代替/

让我们首先创建将在下面提到的所有示例中使用的zthinker.txt文件。

	$ cat zthinker.txt
	# Instruction Guides
	1. Linux Sysadmin, Linux Scripting etc.
	2. Databases - Oracle, mySQL etc.
	3. Security (Firewall, Network, Online Security etc)
	4. Storage in Linux
	5. Productivity (Too many technologies to explore, not much time available)
	#  Additional FAQS
	6. Windows- Sysadmin, reboot etc.

现在让我们回顾一些有趣的替换示例。

### 1.使用sed s//将单词“ Linux”替换为“ Linux-Unix”

在下面的示例中,在输出行“ 1。Linux-Unix Sysadmin,Linux Scripting等”,只有第一个Linux被Linux-Unix取代。如果未指定标志,则替换第一行。

	$ sed 's/Linux/Linux-Unix/' zthinker.txt
	# Instruction Guides
	1. Linux-Unix Sysadmin, Linux Scripting etc.
	2. Databases - Oracle, mySQL etc.
	3. Security (Firewall, Network, Online Security etc)
	4. Storage in Linux-Unix
	5. Productivity (Too many technologies to explore, not much time available)
	#  Additional FAQS
	6. Windows- Sysadmin, reboot etc.

### 2.使用sed s//g替换单词的所有匹配数据

下面的sed命令使用全局替换标记“ g”将所有出现的Linux替换为Linux-Unix。

	$ sed 's/Linux/Linux-Unix/g' zthinker.txt
	# Instruction Guides
	1. Linux-Unix Sysadmin, Linux-Unix Scripting etc.
	2. Databases - Oracle, mySQL etc.
	3. Security (Firewall, Network, Online Security etc)
	4. Storage in Linux-Unix
	5. Productivity (Too many technologies to explore, not much time available)
	#  Additional FAQS
	6. Windows- Sysadmin, reboot etc.

### 3.使用sed s//2代替单词的第二次出现

在下面的示例中,在输出行“ 1。Linux Sysadmin,Linux-Unix Scripting等。” 只有Linux的第二次出现被Linux-Unix取代。

	$ sed 's/Linux/Linux-Unix/2' zthinker.txt
	# Instruction Guides
	1. Linux Sysadmin, Linux-Unix Scripting etc.
	2. Databases - Oracle, mySQL etc.
	3. Security (Firewall, Network, Online Security etc)
	4. Storage in Linux
	5. Productivity (Too many technologies to explore, not much time available)
	#  Additional FAQS
	6. Windows- Sysadmin, reboot etc.

### 4.将更改后数据写入文件并使用sed s//gpw打印更改后数据

下面的示例用三个标志替换。它将所有出现的Linux替换为Linux-Unix,并打印替换的输出,并将其写入给定文件。

	$ sed -n 's/Linux/Linux-Unix/gpw output' zthinker.txt
	1. Linux-Unix Sysadmin, Linux-Unix Scripting etc.
	4. Storage in Linux-Unix
	$ cat output
	1. Linux-Unix Sysadmin, Linux-Unix Scripting etc.
	4. Storage in Linux-Unix

### 5.仅当前行与模式匹配时才替换

在此示例中,如果该行与模式“-”匹配,则它将“-”中的所有字符替换为空。

	$ sed '/\-/s/\-.*//g' zthinker.txt
	# Instruction Guides
	1. Linux Sysadmin, Linux Scripting etc.
	2. Databases
	3. Security (Firewall, Network, Online Security etc)
	4. Storage in Linux
	5. Productivity (Too many technologies to explore, not much time available)
	#  Additional FAQS
	6. Windows

### 6.使用sed从每行中删除最后X个字符

此sed示例从每行删除最后3个字符。

	$ sed 's/...$//' zthinker.txt
	# Instruction Gui
	1. Linux Sysadmin, Linux Scripting e
	2. Databases - Oracle, mySQL e
	3. Security (Firewall, Network, Online Security e
	4. Storage in Li
	5. Productivity (Too many technologies to explore, not much time availab
	#  Additional F
	6. Windows- Sysadmin, reboot e

### 7.使用sed删除注释

如下所示,使用sed命令从文件中删除所有注释行。

$  sed -e 's/#.*//' zthinker.txt

	1. Linux Sysadmin, Linux Scripting etc.
	2. Databases - Oracle, mySQL etc.
	3. Security (Firewall, Network, Online Security etc)
	4. Storage in Linux
	5. Productivity (Too many technologies to explore, not much time available)
	
	6. Windows- Sysadmin, reboot etc.

### 8.使用sed删除注释和空白行

在此示例中,有两个命令以“;”分隔

*   第一个命令将以#开头的行替换为空白行
*   第二条命令删除空行。

	$ sed -e 's/#.*//;/^$/d'  zthinker.txt
	1. Linux Sysadmin, Linux Scripting etc.
	2. Databases - Oracle, mySQL etc.
	3. Security (Firewall, Network, Online Security etc)
	4. Storage in Linux
	5. Productivity (Too many technologies to explore, not much time available)
	6. Windows- Sysadmin, reboot etc.

### 9.使用sed将DOS换行符(CR/LF)转换为Unix格式

将DOS文件复制到Unix,您可以在每行末尾找到\r\n。

本示例使用sed命令将DOS文件格式转换为Unix文件格式。

	$sed 's/.$//' filename

### 10.使用sed消除文件中的HTML标记

在此示例中,sed命令中给出的正则表达式与html标签匹配,并替换为空。

	$ sed -e 's/<[^>]*>//g'
	This <b> is </b> an <i>example</i>.
	This  is  an example.