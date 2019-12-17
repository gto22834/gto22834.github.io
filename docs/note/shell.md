# SHELL

為了`自動化管理`!! 學 `shell` 吧！  

## Useful commands

### alias / unalias

暱稱命令

```sh
# alias mkdir
alias md="mkdir"

# Create a directory
md my-folder

# unalias
unalias md

# unalias all
unalias -a
```

### cd

更换目录到指定资料夹，如果没指定会转移到 HOME

```sh
cd m-folder
```

### mkdir

Allows the user to create directories.

> mkdir [options...] [directories ...]

```sh
# Create directories with name one, two and three
mkdir one two three

# Create directories with message
mkdir -v test1 test2

# Create parent directories as necessary
mkdir -p first/second/third
```

### rm

**注意：核弹级命令**

`rm` command is used to remove objects such as files, directories, symbolic links and so on from the file system like UNIX

> rm [OPTION]... FILE...

```sh
# Remove file
rm a.text

# Remove force
rm -f a.text

# Remove all file and directories
# dir
#   |- a.text
#   |- dir1
#   |    |- b.text
#   |    `- c.text
#   `- d.text
rm -rf dir
```

### echo 

输出显示的值

```sh
TEST='Testing...'

# output: Testing...
echo "${TEST}"

# output: Ok,Testing...
echo "Ok,${TEST}"

# substring a string
# output: Test
echo "${TEST:0:4}"

# Assign a variable for substring
# output: Te
sub=2
echo "${TEST:0:${sub}}"
```

### export

将name输出给环境，给往後的命令使用
- `-f` 选项表示name是函数
- `-p` 显示出所有export的名称
- `-n` 移除name

### pwd

列出目前工作目录的绝对路径。 

### date

列出当前时间，可以指定时间格式

```sh
# output: 2019年 8月23日 週五 11時37分35秒 CST
date

# output: 20190823 11:41:51
date +"%Y%m%d %H:%M:%S"

# 以今天为基础，读取其他时间
# @see https://www.jianshu.com/p/f750879120e4
# linux
# yesterday
date +%Y%m%d --date='-1 day'
# tomorrow
date +%Y%m%d --date='+1 day'

# mac
# yesterday
date -v -1d +%Y-%m-%d
# tomorrow
date -v +1d +%Y-%m-%d
```

### chmod

> chmod [-option] mode file ...

修改 单个/多个 档案权限。
- `-c` 若该档案权限确实已经更改，才显示其更改动作
- `-v` 显示权限变更的详细资料
- `-r` 以递归的方式对目前目录下的所有档案与子目录进行相同的权限变更

> permission

一共有 10 个字元  
r: 可读  
w: 可写  
x: 可执行  

```sh
# 档案拥有者
#    |     其他人之权限
#    |         |
# -[rwx][rwx][rwx]
#         |
#  档案所属群组之权限
chmod -vc -rwxrwxrwx shell.sh
```

### function

[more](https://www.tutorialspoint.com/unix/unix-shell-functions.htm)

> function name [()] compound-command [ redirections ]

`return` 会回传一个值，可利用 `$?` 去接

```sh
# Define your function here
Hello () {
  echo "Hello World $1 $2"
  return 10
}

# Invoke your function
Hello Zara Ali

# Capture value returnd by last command
ret=$?
echo "Return value is $ret"
```

### for in

[for in](https://www.cyberciti.biz/faq/bash-for-loop/)

Bash's `for loop`

```sh
for index in {0, 1, 2, 3}
do
  echo "Good item ${index}"
done
```

## Plugin

### crul

> curl [options] [URL...]

`curl` is a command line tool to transfer data to or from a server

```sh
curl https://gto22834.github.io/docs/#/

# download file
# curl -o [file_name] [URL...]
curl -# -o hello.zip ftp://speedtest.tele2.net/1MB.zip

# proxy
# -x POST => Use POST
# -x POST --prox => Use POST with proxy
curl \
  -X POST \
  --data "chat_id=${CHAT_ID}" \
	--data "text=${message}" \
	--sockts5 xxxx.xxx.xxx.xxx:xxx "https://api.telegram.org/${BOT}/sendMessage"

```

### jq

Bash JSON parser, 一般情况下要自行安装

[more](https://stedolan.github.io/jq/tutorial/)
[Manual](https://stedolan.github.io/jq/manual/)

```sh
brew install jq
```

A json data below:
```json
{
  "code": 0,
  "data": {
    "array": [
      {
        "id": 1,
        "name": "name1"
      },
      {
        "id": 2,
        "name": "name2"
      }
    ],
    "update": ""
  }
}
```

```sh
# output: 0
echo data | jq '.code'

# output: "name1"
echo data | jq '.data.array[0].name'

# written directly to standard output (very useful)
# output: name1
echo data | jq -r '.data.array[0].name'

# Output base64
echo data | jq -r '.data.array[0].name | @base64'
# Return to raw
_test=$(echo data | jq -r '.data.array[0].name | @base64')
echo ${_text} | base64 --decode
```

Other example

```sh
send=""
total=0
for row in $(echo "${guixiaotu_order}" | jq -r '.data.list[] | @base64')
	do
		_jq() {
      echo "${row}" | base64 --decode | jq -r ${1}
    }
		user=$(_jq '.user.id')
		total=$[${total}+$(_jq '.price')]
		send="${send}${user:0:8} $(_jq '.user.name') $(_jq '.price') $(_jq '.create')\n"
done
income=$(echo ${total}*0.01 | bc)
send="${send}\nTotal: ${income}"
```

### crontab

`crontab` 为一个固定时间或是间隔执行系统指令或是 shell 脚本的命令，时间单位可以为分钟、小时、日、月、周及以上的任意组合。

> crontab [-u user] file  
> crontab [-u user] { -l | -r | -e }

- `-u` 用来设定某个用户的crontab服务；  
- `-e` 用来编辑某个用户的crontab文件内容。如果不指定用户，则表示编辑当前用户的crontab文件。
- `-l` 显示某个用户的crontab文件内容，如果不指定用户，则表示显示当前用户的crontab文件内容。  
- `-r` 从/var/spool/cron目录中删除某个用户的crontab文件，如果不指定用户，则默认删除当前用户的crontab文件。
- `-i` 在删除用户的crontab文件时给确认提示。
- `file` file是命令文件的名字,表示将file做为crontab的任务列表文件并载入crontab。如果在命令行中没有指定这个文件，crontab命令将接受标准输入（键盘）上键入的命令，并将它们载入crontab。

[more](https://medium.com/@jsstrn/scheduling-with-cron-c5e5191663c6)

```sh
# ${minute} ${hour} ${date} ${month} ${week} 执行的命令
# minute: 0～59
# hour: 0～23
# date: 1～31
# month: 1～12
# week: 0～6（0 表示星期天）
# 每分钟执行一次
* * * * * shell.sh

# 每 5 分钟执行一次
*/5 * * * * shell.sh
```

**注意**

当设定好 `crontab` 时候，会发现还是无法执行，原因是在 macOS 系统下，会检查 `/etc/crontab` 是否存在，所以要先创建 `/etc/crontab` 档案。

[参考资料](https://segmentfault.com/a/1190000017493725)

```sh
sudo touch /etc/crontab
```

过些时间以后，`crontab` 开始执行，但是却发了 `mail` 出来。使用 `mail` 指令查看原因。（如果没有错误可以跳过）

```sh
mail
```

发现是档案权限的问题，所以要设定 `shell.sh` 档案的权限，让 `crontab` 可以使用这个档案。

```sh
chmod -vc -rwxrwxrwx shell.sh
```

假设 script 里面有使用像 `jq` 之类的工具指令，可能会发现错误 log 里面会显示找不到 `jq` 这类工具指令。但是如果手动执行 script 却又可以运行

```sh
# 成功运行
bash shell.sh
```

`crontab` 执行任务调度时，是不会加载任何环境变量的，因此，就需要在 `crontab` 文件中指定任务运行所需的所有环境变量。

[参考资料](https://linuxtools-rst.readthedocs.io/zh_CN/latest/tool/crontab.html)

```sh
# 编辑 crontab
crontab -e
```

```sh
# 设定 PATH 环境变量给 crontab 使用
PATH=/usr/local/bin:/usr/bin:/bin

# ${minute} ${hour} ${date} ${month} ${week} 执行的命令
# minute: 0～59
# hour: 0～23
# date: 1～31
# month: 1～12
# week: 0～6（0 表示星期天）
# 每分钟执行一次
* * * * * shell.sh

# 每 5 分钟执行一次
*/5 * * * * shell.sh
```

#### Log

为了能够记录 log，需要修改一下执行的 `crontab`

```sh
# 编辑 crontab
crontab -e
```

```sh
# 设定 PATH 环境变量给 crontab 使用
PATH=/usr/local/bin:/usr/bin:/bin

# ${minute} ${hour} ${date} ${month} ${week} 执行的命令
# minute: 0～59
# hour: 0～23
# date: 1～31
# month: 1～12
# week: 0～6（0 表示星期天）
# 每分钟执行一次
# `>>` 是  把 stdout append 到指定的档案
# 2>&1 是指 把 stderr 并到 stdout，并可借由 echo output 出来
* * * * * shell.sh >> /log/shell.log >> 2>&1

# 每 5 分钟执行一次
*/5 * * * * shell.sh
```

## Calculate in bash

[bc](https://www.gnu.org/software/bc/manual/html_mono/bc.html)

```sh
# output: 1.00
echo "100*0.01" | bc

# output: 3.00
test=300*0.01
echo "${test}" | bc
```

## Read/write CSV

假定一个 data.csv 档案为

```csv
id,name,number
1,TT,0
2,Ben,0
3,Justin,0
4,Thomas,0
```

echo 输出出内容
```sh
# output: 1,2,3,4
file=data.csv
ids=""
while read id
do
  ids=$ids,$id
done < $file
echo ${ids}
```

写入新的资料
```sh
string="id,name,number\n5,GG,100"
echo -e ${string} >> data2.csv
```

## Reference

[GeeksforGeeks](https://www.geeksforgeeks.org/mkdir-command-in-linux-with-examples/)

[鳥哥](http://linux.vbird.org/linux_basic/0340bashshell-scripts.php#script)

