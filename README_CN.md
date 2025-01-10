以下是翻译后的内容，代码部分保持不变：

---

<p align="center">
  <img src="https://cloud.githubusercontent.com/assets/2059754/24601246/753a7f36-1858-11e7-9d6b-7a0e64fb27f7.png" alt="bash logo"/>
</p>

## 目录
  1. [基本操作](#1-基本操作)  
    1.1. [文件操作](#11-文件操作)  
    1.2. [文本操作](#12-文本操作)  
    1.3. [目录操作](#13-目录操作)  
    1.4. [SSH、系统信息与网络操作](#14-ssh系统信息与网络操作)  
    1.5. [进程监控操作](#15-进程监控操作)
  2. [基础 Shell 编程](#2-基础-shell-编程)  
    2.1. [变量](#21-变量)  
    2.2. [数组](#22-数组)  
    2.3. [字符串替换](#23-字符串替换)  
    2.4. [其他字符串技巧](#24-其他字符串技巧)  
    2.5. [函数](#25-函数)  
    2.6. [条件语句](#26-条件语句)  
    2.7. [循环](#27-循环)  
    2.8. [正则表达式](#28-正则表达式)  
    2.9. [管道](#29-管道)  
  3. [技巧](#3-技巧)  
  4. [调试](#4-调试)  
  5. [多线程](#5-多线程)

# 1. 基本操作

### a. `export`
显示所有环境变量。如果你想获取某个特定变量的详细信息，可以使用 `echo $VARIABLE_NAME`。  
```bash
export
```
示例：
```bash
$ export
AWS_HOME=/Users/adnanadnan/.aws
LANG=en_US.UTF-8
LC_CTYPE=en_US.UTF-8
LESS=-R

$ echo $AWS_HOME
/Users/adnanadnan/.aws
```

### b. `whatis`
`whatis` 显示用户命令、系统调用、库函数等的描述信息。
```bash
whatis something
```
示例：
```bash
$ whatis bash
bash (1)             - GNU Bourne-Again SHell
```

### c. `whereis`
`whereis` 使用系统自动构建的数据库搜索可执行文件、源文件和手册页。
```bash
whereis name
```
示例：
```bash
$ whereis php
/usr/bin/php
```

### d. `which`
`which` 在环境变量 `PATH` 指定的目录中搜索可执行文件。该命令将打印可执行文件的完整路径。
```bash
which program_name 
```
示例：
```bash
$ which php
/c/xampp/php/php
```

### e. `clear`
清除窗口内容。

## 1.1. 文件操作
<table>
   <tr>
      <td><a href="#a-cat">cat</a></td>
      <td><a href="#b-chmod">chmod</a></td>
      <td><a href="#c-chown">chown</a></td>
      <td><a href="#d-cp">cp</a></td>
      <td><a href="#e-diff">diff</a></td>
      <td><a href="#f-file">file</a></td>
      <td><a href="#g-find">find</a></td>
      <td><a href="#h-gunzip">gunzip</a></td>
      <td><a href="#i-gzcat">gzcat</a></td>
      <td><a href="#j-gzip">gzip</a></td>
      <td><a href="#k-head">head</a></td>
   </tr>
   <tr>
      <td><a href="#l-less">less</a></td>
      <td><a href="#m-lpq">lpq</a></td>
      <td><a href="#n-lpr">lpr</a></td>
      <td><a href="#o-lprm">lprm</a></td>
      <td><a href="#p-ls">ls</a></td>
      <td><a href="#q-more">more</a></td>
      <td><a href="#r-mv">mv</a></td>
      <td><a href="#s-rm">rm</a></td>
      <td><a href="#t-tail">tail</a></td>
      <td><a href="#u-touch">touch</a></td>
   </tr>
</table>

### a. `cat`
在 UNIX 或 Linux 下，`cat` 命令可用于以下目的：  
* 在屏幕上显示文本文件
* 复制文本文件  
* 合并文本文件  
* 创建新的文本文件  
```bash
cat filename
cat file1 file2 
cat file1 file2 > newcombinedfile
cat < file1 > file2 # 将 file1 复制到 file2
```

### b. `chmod`
`chmod` 命令用于更改文件的读、写和执行权限。更多信息请查看此[链接](https://ss64.com/bash/chmod.html)。
```bash
chmod -options filename
```

### c. `chown`
`chown` 命令用于更改文件或目录的所有者。基本用法是先指定用户（所有者），然后是组，用冒号分隔。
```bash
chown -options user:group filename
```

### d. `cp`
将文件从一个位置复制到另一个位置。  
```bash
cp filename1 filename2
```
其中 `filename1` 是源文件路径，`filename2` 是目标文件路径。

### e. `diff`
比较文件并列出它们的差异。  
```bash
diff filename1 filename2
```

### f. `file`
确定文件类型。  
```bash
file filename
```
示例：
```bash
$ file index.html
 index.html: HTML document, ASCII text
```

### g. `find`
在目录中查找文件。
```bash
find directory options pattern
```
示例：
```bash
$ find . -name README.md
$ find /home/user1 -name '*.png'
```

### h. `gunzip`
解压缩由 `gzip` 压缩的文件。  
```bash
gunzip filename
```

### i. `gzcat`
查看 gzip 压缩文件的内容，而无需解压缩。  
```bash
gzcat filename
```

### j. `gzip`
压缩文件。  
```bash
gzip filename
```

### k. `head`
输出文件的前 10 行。  
```bash
head filename
```

### l. `less`
显示文件内容或命令输出，一次一页。它与 `more` 类似，但具有更多高级功能，并允许你在文件中前后导航。  
```bash
less filename
```

### m. `lpq`
检查打印机队列。  
```bash
lpq
```
示例：
```bash
$ lpq
Rank    Owner   Job     File(s)                         Total Size
active  adnanad 59      demo                            399360 bytes
1st     adnanad 60      (stdin)                         0 bytes
```

### n. `lpr`
打印文件。  
```bash
lpr filename
```

### o. `lprm`
从打印机队列中移除任务。  
```bash
lprm jobnumber
```

### p. `ls`
列出文件。`ls` 有许多选项：`-l` 以“长格式”列出文件，包含文件的确切大小、所有者、权限和最后修改时间。`-a` 列出所有文件，包括隐藏文件。更多信息请查看此[链接](https://ss64.com/bash/ls.html)。  
```bash
ls option
```
示例：
<pre>
$ ls -la
rwxr-xr-x   33 adnan  staff    1122 Mar 27 18:44 .
drwxrwxrwx  60 adnan  staff    2040 Mar 21 15:06 ..
-rw-r--r--@  1 adnan  staff   14340 Mar 23 15:05 .DS_Store
-rw-r--r--   1 adnan  staff     157 Mar 25 18:08 .bumpversion.cfg
-rw-r--r--   1 adnan  staff    6515 Mar 25 18:08 .config.ini
-rw-r--r--   1 adnan  staff    5805 Mar 27 18:44 .config.override.ini
drwxr-xr-x  17 adnan  staff     578 Mar 27 23:36 .git
-rwxr-xr-x   1 adnan  staff    2702 Mar 25 18:08 .gitignore
</pre>

### q. `more`
显示文件的第一部分（按空格键翻页，按 `q` 退出）。  
```bash
more filename
```

### r. `mv`
将文件从一个位置移动到另一个位置。  
```bash
mv filename1 filename2
```
其中 `filename1` 是源文件路径，`filename2` 是目标文件路径。

也可以用于重命名文件。
```bash
mv old_name new_name
```

### s. `rm`
删除文件。如果在目录上使用此命令，会提示错误：
`rm: directory: is a directory`
要删除目录，必须使用 `-r` 选项，递归删除目录内容。可选地，可以使用 `-f` 标志强制删除，即无需确认。
```bash
rm filename
```

### t. `tail`
输出文件的最后 10 行。使用 `-f` 选项可以实时输出文件新增的内容。  
```bash
tail filename
```

### u. `touch`
更新文件的访问和修改时间戳。如果文件不存在，则会创建它。
```bash
touch filename
```
示例：
```bash
$ touch trick.md
```

## 1.2. 文本操作

<table>
    <tr>
      <td><a href="#a-awk">awk</a></td>
      <td><a href="#b-cut">cut</a></td>
      <td><a href="#c-echo">echo</a></td>
      <td><a href="#d-egrep">egrep</a></td>
      <td><a href="#e-fgrep">fgrep</a></td>
      <td><a href="#f-fmt">fmt</a></td>
      <td><a href="#g-grep">grep</a></td>
      <td><a href="#h-nl">nl</a></td>
      <td><a href="#i-sed">sed</a></td>
      <td><a href="#j-sort">sort</a></td>
   </tr>
   <tr>
      <td><a href="#k-tr">tr</a></td>
      <td><a href="#l-uniq">uniq</a></td>
      <td><a href="#m-wc">wc</a></td>
   </tr>
</table>

### a. `awk`
`awk` 是处理文本文件最有用的命令。它逐行处理整个文件。默认情况下，它使用空格分隔字段。最常见的 `awk` 命令语法是：

```bash
awk '/search_pattern/ { action_to_take_if_pattern_matches; }' file_to_parse
```

以 `/etc/passwd` 文件为例，文件内容如下：
```
root:x:0:0:root:/root:/usr/bin/zsh
daemon:x:1:1:daemon:/usr/sbin:/usr/sbin/nologin
bin:x:2:2:bin:/bin:/usr/sbin/nologin
sys:x:3:3:sys:/dev:/usr/sbin/nologin
sync:x:4:65534:sync:/bin:/bin/sync
```
现在让我们从该文件中提取用户名。`-F` 指定字段分隔符，这里是 `:`。`{ print $1 }` 表示打印第一个匹配字段。
```bash
awk -F':' '{ print $1 }' /etc/passwd
```
运行上述命令后，输出如下：
```
root
daemon
bin
sys
sync
```
更多关于 `awk` 的用法，请查看此[链接](https://www.cyberciti.biz/faq/bash-scripting-using-awk)。

### b. `cut`
从每行中删除部分内容。

*example.txt*
```bash
red riding hood went to the park to play
```

*显示第 2、7 和 9 列，以空格分隔*
```bash
cut -d " " -f2,7,9 example.txt
```
```bash
riding park play
```

### c. `echo`
显示一行文本。

*显示 "Hello World"*
```bash
echo Hello World
```
```bash
Hello World
```

*显示 "Hello World"，并在单词之间换行*
```bash
echo -ne "Hello\nWorld\n"
```
```bash
Hello
World
```

### d. `egrep`
打印匹配模式的行 - 扩展表达式（`grep -E` 的别名）。

*example.txt*
```bash
Lorem ipsum
dolor sit amet, 
consetetur
sadipscing elitr,
sed diam nonumy
eirmod tempor
invidunt ut labore
et dolore magna
aliquyam erat, sed
diam voluptua. At
vero eos et
accusam et justo
duo dolores et ea
rebum. Stet clita
kasd gubergren,
no sea takimata
sanctus est Lorem
ipsum dolor sit
amet.
```

*显示包含 "Lorem" 或 "dolor" 的行*
```bash
egrep '(Lorem|dolor)' example.txt
或
grep -E '(Lorem|dolor)' example.txt
```
```bash
Lorem ipsum
dolor sit amet,
et dolore magna
duo dolores et ea
sanctus est Lorem
ipsum dolor sit
```

### e. `fgrep`
打印匹配模式的行 - 固定模式匹配（`grep -F` 的别名）。

*example.txt*
```bash
Lorem ipsum
dolor sit amet,
consetetur
sadipscing elitr,
sed diam nonumy
eirmod tempor
foo (Lorem|dolor) 
invidunt ut labore
et dolore magna
aliquyam erat, sed
diam voluptua. At
vero eos et
accusam et justo
duo dolores et ea
rebum. Stet clita
kasd gubergren,
no sea takimata
sanctus est Lorem
ipsum dolor sit
amet.
```

*查找字符串 '(Lorem|dolor)'*
```bash
fgrep '(Lorem|dolor)' example.txt
或
grep -F '(Lorem|dolor)' example.txt
```
```bash
foo (Lorem|dolor) 
```

### f. `fmt`
简单的文本格式化工具。

*example: example.txt (1 行)*
```bash
Lorem ipsum dolor sit amet, consetetur sadipscing elitr, sed diam nonumy eirmod tempor invidunt ut labore et dolore magna aliquyam erat, sed diam voluptua. At vero eos et accusam et justo duo dolores et ea rebum. Stet clita kasd gubergren, no sea takimata sanctus est Lorem ipsum dolor sit amet.
```

*将 example.txt 的行宽设置为 20 个字符*
```bash
cat example.txt | fmt -w 20
```
```bash
Lorem ipsum
dolor sit amet,
consetetur
sadipscing elitr,
sed diam nonumy
eirmod tempor
invidunt ut labore
et dolore magna
aliquyam erat, sed
diam voluptua. At
vero eos et
accusam et justo
duo dolores et ea
rebum. Stet clita
kasd gubergren,
no sea takimata
sanctus est Lorem
ipsum dolor sit
amet.
```

### g. `grep`
在文件中查找文本。你可以使用 `grep` 搜索匹配一个或多个正则表达式的文本行，并仅输出匹配的行。  
```bash
grep pattern filename
```
示例：
```bash
$ grep admin /etc/passwd
_kadmin_admin:*:218:-2:Kerberos Admin Service:/var/empty:/usr/bin/false
_kadmin_changepw:*:219:-2:Kerberos Change Password Service:/var/empty:/usr/bin/false
_krb_kadmin:*:231:-2:Open Directory Kerberos Admin Service:/var/empty:/usr/bin/false
```
你可以使用 `-i` 选项忽略大小写。`-r` 可以用于搜索指定目录下的所有文件，例如：
```bash
$ grep -r admin /etc/
```
`-w` 用于仅搜索单词。更多关于 `grep` 的详细信息，请查看此[链接](https://www.cyberciti.biz/faq/grep-in-bash)。

### h. `nl`
为文件的行编号。

*example.txt*
```bash
Lorem ipsum
dolor sit amet,
consetetur
sadipscing elitr,
sed diam nonumy
eirmod tempor
invidunt ut labore
et dolore magna
aliquyam erat, sed
diam voluptua. At
vero eos et
accusam et justo
duo dolores et ea
rebum. Stet clita
kasd gubergren,
no sea takimata
sanctus est Lorem
ipsum dolor sit
amet.
```

*显示 example.txt 并添加行号*
```bash
nl -s". " example.txt 
```
```bash
     1. Lorem ipsum
     2. dolor sit amet,
     3. consetetur
     4. sadipscing elitr,
     5. sed diam nonumy
     6. eirmod tempor
     7. invidunt ut labore
     8. et dolore magna
     9. aliquyam erat, sed
    10. diam voluptua. At
    11. vero eos et
    12. accusam et justo
    13. duo dolores et ea
    14. rebum. Stet clita
    15. kasd gubergren,
    16. no sea takimata
    17. sanctus est Lorem
    18. ipsum dolor sit
    19. amet.
```

### i. `sed`
流编辑器，用于过滤和转换文本。

*example.txt*
```bash
Hello This is a Test 1 2 3 4
``` 

*将所有空格替换为连字符*
```bash
sed 's/ /-/g' example.txt
```
```bash
Hello-This-is-a-Test-1-2-3-4
```

*将所有数字替换为 "d"*
```bash
sed 's/[0-9]/d/g' example.txt
```
```bash
Hello This is a Test d d d d
```

### j. `sort`
对文本文件的行进行排序。

*example.txt*
```bash
f
b
c
g
a
e
d
```

*对 example.txt 进行排序*
```bash
sort example.txt
```
```bash
a
b
c
d
e
f
g
```

*随机化已排序的 example.txt*
```bash
sort example.txt | sort -R
```
```bash
b
f
a
c
d
g
e
```

### k. `tr`
转换或删除字符。

*example.txt*
```bash
Hello World Foo Bar Baz!
```

*将所有小写字母转换为大写*
```bash
cat example.txt | tr 'a-z' 'A-Z' 
```
```bash
HELLO WORLD FOO BAR BAZ!
```

*将所有空格转换为换行符*
```bash
cat example.txt | tr ' ' '\n'
```
```bash
Hello
World
Foo
Bar
Baz!
```

### l. `uniq`
报告或忽略重复的行。

*example.txt*
```bash
a
a
b
a
b
c
d
c
```

*显示 example.txt 的唯一行（需要先排序，否则无法识别重复行）*
```bash
sort example.txt | uniq
```
```bash
a
b
c
d
```

*显示每行的唯一项，并显示其出现次数*
```bash
sort example.txt | uniq -c
```
```bash
    3 a
    2 b
    2 c
    1 d
```

### m. `wc`
显示文件的行数、单词数和字符数。  
```bash
wc filename
```
示例：
```bash
$ wc demo.txt
7459   15915  398400 demo.txt
```
其中 `7459` 是行数，`15915` 是单词数，`398400` 是字符数。

## 1.3. 目录操作

<table>
   <tr>
      <td><a href="#a-cd">cd</a></td>
      <td><a href="#b-mkdir">mkdir</a></td>
      <td><a href="#c-pwd">pwd</a></td>
   </tr>
</table>

### a. `cd`
从一个目录切换到另一个目录。运行以下命令：
```bash
$ cd
```
将切换到主目录。该命令接受一个可选的 `dirname` 参数，用于切换到指定目录。
```bash
cd dirname
```
切换到上一个工作目录：
```bash
cd -
```

### b. `mkdir`
创建一个新目录。  
```bash
mkdir dirname
```
你可以在当前目录中一次性创建多个目录：
```bash
mkdir 1stDirectory 2ndDirectory 3rdDirectory
```
你也可以使用 `-p`（或 `--parents`）标志同时创建父目录。例如，如果你想在 `/samples/bash/projects/` 下创建一个名为 `project1` 的目录，可以运行：
```bash 
mkdir -p /samples/bash/projects/project1
mkdir --parents /samples/bash/projects/project1
```
上述两个命令的效果相同。如果这些目录中的任何一个不存在，它们也会被创建。

### c. `pwd`
显示当前所在的目录。  
```bash
pwd
```

## 1.4. SSH、系统信息与网络操作

<table>
   <tr>
      <td><a href="#a-bg">bg</a></td>
      <td><a href="#b-cal">cal</a></td>
      <td><a href="#c-date">date</a></td>
      <td><a href="#d-df">df</a></td>
      <td><a href="#e-dig">dig</a></td>
      <td><a href="#f-du">du</a></td>
      <td><a href="#g-fg">fg</a></td>
      <td><a href="#h-finger">finger</a></td>   
      <td><a href="#i-jobs">jobs</a></td>
      <td><a href="#j-last">last</a></td>
   </tr>
   <tr>
      <td><a href="#k-man">man</a></td>
      <td><a href="#l-passwd">passwd</a></td>
      <td><a href="#m-ping">ping</a></td>
      <td><a href="#n-ps">ps</a></td>
      <td><a href="#o-quota">quota</a></td>
      <td><a href="#p-scp">scp</a></td>
      <td><a href="#q-ssh">ssh</a></td>
      <td><a href="#r-top">top</a></td>
      <td><a href="#s-uname">uname</a></td>
      <td><a href="#t-uptime">uptime</a></td>
   </tr>
   <tr>
      <td><a href="#u-w">w</a></td>
      <td><a href="#v-wget">wget</a></td>
      <td><a href="#w-whoami">whoami</a></td>
      <td><a href="#x-whois">whois</a></td>
      <td><a href="#y-rsync">sync</a></td>
      <td><a href="#z-curl">curl</a></td>
   </tr>
</table>

### a. `bg`
列出已停止或后台的作业；恢复已停止的作业到后台。

### b. `cal`
显示当前月份的日历。

### c. `date`
显示当前日期和时间。

### d. `df`
显示磁盘使用情况。

### e. `dig`
获取域名的 DNS 信息。  
```bash
dig domain
```

### f. `du`
显示文件或目录的磁盘使用情况。更多信息请查看此[链接](http://www.linfo.org/du.html)。
```bash
du [option] [filename|directory]
```
选项：
- `-h`（人类可读）以 KB（K）、MB（M）和 GB（G）显示输出。
- `-s`（汇总）显示目录的总磁盘使用情况，并抑制子目录的报告。

示例：
```bash
du -sh pictures
1.4M pictures
```

### g. `fg`
将最近的作业带到前台。

### h. `finger`
显示用户信息。  
```bash
finger username
```

### i. `jobs`
列出后台运行的作业，并显示作业编号。

### j. `last`
列出指定用户的最后登录记录。  
```bash
last yourUsername
```

### k. `man`
显示指定命令的手册。  
```bash
man command
```

### l. `passwd`
允许当前登录用户更改密码。

### m. `ping`
向主机发送 ping 请求并输出结果。  
```bash
ping host
```

### n. `ps`
列出你的进程。  
```bash
ps -u yourusername
```
使用 `ef` 标志。`e` 表示所有进程，`f` 表示完整列表。
```bash
ps -ef
```

### o. `quota`
显示你的磁盘配额。  
```bash
quota -v
```

### p. `scp`
在本地主机和远程主机之间或两个远程主机之间传输文件。

*从本地主机复制到远程主机*
```bash
scp source_file user@host:directory/target_file
```
*从远程主机复制到本地主机*
```bash
scp user@host:directory/source_file target_file
scp -r user@host:directory/source_folder target_folder
```
该命令还接受 `-P` 选项，用于连接到特定端口。  
```bash
scp -P port user@host:directory/source_file target_file
```

### q. `ssh`
`ssh`（SSH 客户端）是一个用于登录远程机器并执行命令的程序。  
```bash
ssh user@host
```
该命令还接受 `-p` 选项，用于连接到特定端口。  
```bash
ssh -p port user@host
```

### r. `top`
显示当前活动的进程。

### s. `uname`
显示内核信息。  
```bash
uname -a
```

### t. `uptime`
显示当前系统运行时间。

### u. `w`
显示谁在线。

### v. `wget`
下载文件。  
```bash
wget file
```

### w. `whoami`
返回当前登录的用户名。

### x. `whois`
获取域名的 whois 信息。  
```bash
whois domain
```

### y. `rsync`
与 `scp` 命令功能相同，但仅传输更改的文件。在多次向/从服务器传输相同文件夹时非常有用。
```bash
rsync source_folder user@host:target_folder
rsync user@host:target_folder target_folder
```

### z. `curl`
`curl` 是一个用于使用 URL 语法请求或发送数据的命令行工具。在只有终端可用的情况下非常有用。
```bash
curl url
```
使用 `-X` 或 `--request` 指定要调用的方法（GET、POST、DELETE 等）。
使用 `-d <data>` 或 `--data <data>` 在给定 URL 上 POST 数据。

## 1.5. 进程监控操作

<table>
   <tr>
      <td><a href="#a-kill">kill</a></td>
      <td><a href="#b-killall">killall</a></td>
      <td><a href="#c-&">&amp;</a></td>
      <td><a href="#d-nohup">nohup</a></td>
   </tr>
</table>

### a. `kill`
终止指定进程 ID 的进程。  
```bash
kill PID
```

### b. `killall`
终止所有指定名称的进程。  
```bash
killall processname
```

### c. `&`
`&` 符号指示命令在子 shell 中作为后台进程运行。
```bash
command &
```

### d. `nohup`
`nohup` 表示“不挂断”。它允许你在退出 shell 后继续运行命令/进程或 shell 脚本。
```bash
nohup command
```
结合 `&` 创建后台进程：
```bash
nohup command &
```

# 2. 基础 Shell 编程

在 Bash 脚本文件中，你编写的第一行称为 `shebang`。这一行决定了脚本是否可以作为独立可执行文件运行，而无需在终端中键入 `sh`、`bash`、`python`、`php` 等。

```bash
#!/usr/bin/env bash
```

## 2.1. 变量

在 Bash 中创建变量与其他语言类似。没有数据类型。Bash 中的变量可以包含数字、字符、字符串等。你不需要声明变量，只需为其引用赋值即可创建它。

示例：
```bash
str="hello world"
```

上述行创建了一个变量 `str` 并将 "hello world" 赋值给它。通过在其名称前加上 `$` 来检索变量的值。

示例：
```bash
echo $str   # hello world
```

## 2.2. 数组

与其他语言一样，Bash 也有数组。数组是包含多个值的变量。数组的大小没有最大限制。Bash 中的数组从零开始索引。第一个元素的索引为 0。有几种方法可以在 Bash 中创建数组，如下所示。

示例：
```bash
array[0]=val
array[1]=val
array[2]=val
array=([2]=val [0]=val [1]=val)
array=(val val val)
```
要显示特定索引处的值，请使用以下语法：

```bash
${array[i]}     # 其中 i 是索引
```

如果未提供索引，则假定为数组元素 0。要查找数组中有多少个值，请使用以下语法：

```bash
${#array[@]}
```

Bash 还支持三元条件。查看以下示例。

```bash
${varname:-word}    # 如果 varname 存在且不为空，则返回其值；否则返回 word
${varname:=word}    # 如果 varname 存在且不为空，则返回其值；否则将其设置为 word 并返回其值
${varname:+word}    # 如果 varname 存在且不为空，则返回 word；否则返回 null
${varname:offset:length}    # 执行子字符串扩展。它返回从 offset 开始且长度为 length 的 $varname 的子字符串
```

## 2.3. 字符串替换

查看一些用于操作字符串的语法。

```bash
${variable#pattern}         # 如果模式匹配变量值的开头，则删除匹配的最短部分并返回其余部分
${variable##pattern}        # 如果模式匹配变量值的开头，则删除匹配的最长部分并返回其余部分
${variable%pattern}         # 如果模式匹配变量值的结尾，则删除匹配的最短部分并返回其余部分
${variable%%pattern}        # 如果模式匹配变量值的结尾，则删除匹配的最长部分并返回其余部分
${variable/pattern/string}  # 将变量中最长的模式匹配替换为字符串。仅替换第一个匹配项
${variable//pattern/string} # 将变量中最长的模式匹配替换为字符串。替换所有匹配项
${#varname}     # 返回变量值的长度（以字符为单位）
```

## 2.4. 其他字符串技巧

Bash 有许多用于处理字符串的快捷技巧。

```bash
${variable,,}    # 将变量中的每个字母转换为小写
${variable^^}    # 将变量中的每个字母转换为大写

${variable:2:8}  # 返回从第 2 个字符开始的子字符串（字符串从索引 0 开始，因此这是第 3 个字符），
                 # 子字符串长度为 8 个字符，因此这将返回由第 3 到第 11 个字符组成的字符串。
```

以下是一些方便的模式匹配技巧：
```bash
if [[ "$variable" == *subString* ]]  # 如果提供的子字符串在变量中，则返回 true
if [[ "$variable" != *subString* ]]  # 如果提供的子字符串不在变量中，则返回 true
if [[ "$variable" == subString* ]]   # 如果变量以给定的子字符串开头，则返回 true
if [[ "$variable" == *subString ]]   # 如果变量以给定的子字符串结尾，则返回 true
```

上述内容可以使用 `case` 语句和 `IN` 关键字进行简化：
```bash
case "$var" in
	begin*)
		# 变量以 "begin" 开头
	;;
	*subString*)
		# 子字符串在变量中
	;;

	*otherSubString*)
		# 其他子字符串在变量中
	;;
esac
```

## 2.5. 函数

与几乎所有编程语言一样，你可以使用函数以更逻辑的方式分组代码或练习递归的神圣艺术。声明函数只需编写 `function my_func { my_code }`。调用函数就像调用另一个程序一样，只需写出其名称。

```bash
function name() {
    shell commands
}
```

示例：
```bash
#!/bin/bash
function hello {
   echo world!
}
hello

function say {
    echo $1
}
say "hello world!"
```

当你运行上述示例时，`hello` 函数将输出 "world!"。上述两个函数 `hello` 和 `say` 是相同的。主要区别在于函数 `say`。此函数打印它接收到的第一个参数。函数中的参数与提供给脚本的参数处理方式相同。

## 2.6. 条件语句

Bash 中的条件语句与其他编程语言类似。条件有多种形式，最基本的形式是 `if` 表达式 `then` 语句，其中仅当表达式为真时才执行语句。

```bash
if [ expression ]; then
    will execute only if expression is true
else
    will execute if expression is false
fi
```

有时 `if` 条件变得混乱，因此你可以使用 `case` 语句编写相同的条件。

```bash
case expression in
    pattern1 )
        statements ;;
    pattern2 )
        statements ;;
    ...
esac
```

表达式示例：

```bash
statement1 && statement2  # 两个语句都为真
statement1 || statement2  # 至少一个语句为真

str1=str2       # str1 匹配 str2
str1!=str2      # str1 不匹配 str2
str1<str2       # str1 小于 str2
str1>str2       # str1 大于 str2
-n str1         # str1 不为空（长度大于 0）
-z str1         # str1 为空（长度为 0）

-a file         # 文件存在
-d file         # 文件存在且为目录
-e file         # 文件存在；与 -a 相同
-f file         # 文件存在且为普通文件（即不是目录或其他特殊文件类型）
-r file         # 你有读取权限
-s file         # 文件存在且不为空
-w file         # 你有写入权限
-x file         # 你对文件有执行权限，或对目录有搜索权限
-N file         # 文件自上次读取以来已被修改
-O file         # 你拥有文件
-G file         # 文件的组 ID 与你的匹配（或你的多个组之一）

file1 -nt file2     # file1 比 file2 新
file1 -ot file2     # file1 比 file2 旧

-lt     # 小于
-le     # 小于或等于
-eq     # 等于
-ge     # 大于或等于
-gt     # 大于
-ne     # 不等于
```

## 2.7. 循环
### 2.7. 循环（续）

#### `for` 循环
```bash
for name [in list]
do
  statements that can use $name
done
```

#### `for` 循环（C 风格）
```bash
for (( initialisation ; ending condition ; update ))
do
  statements...
done
```

#### `while` 循环
```bash
while condition; do
  statements
done
```

#### `until` 循环
```bash
until condition; do
  statements
done
```

---

## 2.8. 正则表达式

正则表达式是操作和搜索文本的强大工具。以下是一些使用每个元字符的正则表达式示例：

<table>
   <tr>
      <td><a href="#a-dot">`.`（点）</a></td>
      <td><a href="#b-asterisk">`*`（星号）</a></td>
      <td><a href="#c-plus">`+`（加号）</a></td>
      <td><a href="#d-question_mark">`?`（问号）</a></td>
      <td><a href="#e-pipe">`|`（管道）</a></td>
      <td><a href="#f-character_class">`[]`（字符类）</a></td>
      <td><a href="#g-negated_character_class">`[^]`（否定字符类）</a></td>
      <td><a href="#h-grouping">`()`（分组）</a></td>
      <td><a href="#i-quantifiers">`{}`（量词）</a></td>
      <td><a href="#j-escape">`\`（转义）</a></td>
   </tr>
</table>

### a. `.`（点）
匹配除换行符外的任何单个字符。  
```bash
grep h.t file.txt
```
输出：
```bash
hat
hot
hit
```

### b. `*`（星号）
匹配前一个字符或组的零次或多次出现。
```bash
grep ab*c file.txt
```
输出：
```bash
ac
abc
abbc
abbbc
```

### c. `+`（加号）
匹配前一个字符或组的一次或多次出现。
```bash
grep ab+c file.txt
```
输出：
```bash
abc
abbc
abbbc
abbbbc
```

### d. `?`（问号）
匹配前一个字符或组的零次或一次出现。
```bash
grep ab?c file.txt
```
输出：
```bash
ac
abc
```

### e. `|`（管道）
匹配左侧或右侧的模式。
```bash
egrep "cat|dog" file.txt
```
输出：
```bash
cat
dog
```

### f. `[]`（字符类）
匹配括号内的任何字符。
```bash
[aeiou]  # 匹配任何元音
[a-z]    # 匹配任何小写字母
```

### g. `[^]`（否定字符类）
匹配不在括号内的任何字符。
```bash
[^aeiou]  # 匹配任何辅音
[^a-z]    # 匹配任何非小写字母
```

### h. `()`（分组）
将多个标记分组并创建一个捕获组。
```bash
egrep "(ab)+" file.txt
```
输出：
```bash
ab
abab
ababab
```

### i. `{}`（量词）
匹配前一个字符或组的特定次数。
```bash
egrep "a{3}" file.txt
```
输出：
```bash
aaa
aaaa
aaaaa
```

### j. `\`（转义）
转义下一个字符以按字面匹配。
```bash
egrep "a\+" file.txt
```
输出：
```bash
a+
```

---

## 2.9. 管道

多个命令可以通过管道 `|` 链接在一起。`|` 会将命令 A 的标准输出发送到命令 B 的标准输入。
管道也可以用 `|&` 符号构造。这将把命令 A 的标准输出和标准错误发送到命令 B 的标准输入。

---

# 3. 技巧

## 设置别名

运行 `nano ~/.bash_profile` 并添加以下行：

```bash
alias dockerlogin='ssh www-data@adnan.local -p2222'  # 在 .bash_profile 中添加别名
```

## 快速跳转到特定目录

运行 `nano ~/.bashrc` 并添加以下行：

```bash
export hotellogs="/workspace/hotel-api/storage/logs"
```

现在你可以使用保存的路径：

```bash
source ~/.bashrc
cd $hotellogs
```

## 重新执行上一条命令

在键盘没有“上箭头”键的时代，这非常有用，但现在仍然有用。
要运行历史记录中的最后一条命令：
```bash
!!
```
一个常见的错误是忘记在需要特权执行的命令前加上 `sudo`。你可以这样做，而不用重新输入整个命令：
```bash
sudo !!
```
这将把 `mkdir somedir` 改为 `sudo mkdir somedir`。

## 退出陷阱

通过可靠地执行清理操作，使你的 Bash 脚本更健壮。

```bash
function finish {
  # 在这里进行清理操作，例如杀死任何派生的进程
  jobs -p | xargs kill
}
trap finish EXIT
```

## 保存环境变量

当你执行 `export FOO=BAR` 时，变量仅在此 shell 及其子 shell 中导出。要使其持久化，你可以简单地将导出命令附加到 `~/.bash_profile` 文件中：
```bash
echo export FOO=BAR >> ~/.bash_profile
```

## 访问你的脚本

你可以通过在主目录中创建一个 `bin` 文件夹来轻松访问你的脚本：
```bash
mkdir ~/bin
```
现在，你放在此文件夹中的所有脚本都可以在任何目录中访问。

如果无法访问，请尝试将以下代码附加到 `~/.bash_profile` 文件中，然后运行 `source ~/.bash_profile`：
```bash
# 如果存在用户的私有 bin 目录，则将其添加到 PATH
if [ -d "$HOME/bin" ] ; then
    PATH="$HOME/bin:$PATH"
fi
```

---

# 4. 调试

你可以通过向 `bash` 命令传递不同的选项轻松调试 Bash 脚本。例如，`-n` 不会运行命令，仅检查语法错误。`-v` 在运行命令之前回显命令。`-x` 在命令行处理后回显命令。

```bash
bash -n scriptname
bash -v scriptname
bash -x scriptname
```

---

# 5. 多线程

你可以使用 `&` 轻松地将任务多线程化。所有这些任务将在后台同时运行，你可以使用 `jobs` 查看正在运行的进程。

```bash
sleep 15 & sleep 5 &
```

可选的 `wait` 命令将等待所有任务完成。

```bash
sleep 10 & sleep 5 &
wait
```
