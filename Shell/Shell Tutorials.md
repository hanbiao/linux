# Shell [Tutorials](http://www.ee.surrey.ac.uk/Teaching/Unix/)

### 常用命令

```shell
ls -a -l -g			//'-g' print group name
mkdir dir
cd ~ or cd			//return to home directory
cp s_file d_file
cp s_file .			//copy to home directory
mv s_file d_file	//rename
mv s_file /..path/. //move to other directory
rm file
rmdir dir			//only remove emputy directory
rmdir -f dir		
cat file			//display the last file contents
less file			//display page by page, press 'space' or 'q', '/word' to search', 'n' to search next
head file			//display first 10 lines
tail file			//display the last 10 lines
grep word file		//case sensitive
grep -i word file	//no case sensitive
grep 'multi word' file
grep -c word file	//print count of matched line
grep -n word file	//show line number of matched line
grep -v word file	//display not matched line
grep -icv word file //show not matched line count
wc -w file			//display word count
wc -l file			//display line count
cat					//read frome standard input(keyboard), end with 'Ctrl+D'
cat > file			//redirect what cat read to file
cat >> file			//append what cat read to file
cat file1 file2 > file3	//redirect output
sort < file			//redirect input from file, then output on standard output
sort < f_file > t_file	//redirect input from f_file, and redirect output to t_file
cat file | sort		//sort what the cat command output
cat file1 file2 | grep word | sort //search word cat output pipe and sort
cat file | wc -l	//dispay line number of file
grep *word file		//'*' will match none or more charactors
grep ?word file		//'?' will match exactly one charactor
ls *.c				//list all .c source file
chmode u/g/o+/-rwx file	//change file access attribute
sleep 10 &			//wait 10s background before go back to shell prompt
bg					//first type'Ctrl+Z'to suspend current process and then put it to backgound
fg %jobnumber		//store suspended process back to foreground
kill %jobnumber		//kill suspended or backgrounded process, type'Ctrl+C' kill current foreground process
kill pid
gzip file			//compress to file.gz
gunzip file.gz
zcat file.gz		//read gzipped file, but not uncompress them
zcat file.gz | less
tar -xvf file.tar	//extract the content of .tar file
diff file1 file2	//compare two file and display difference
find dir -name "*.text" -print
find dir -size +1M -ls
!! 					//recall last command
!5					//recall 5th comand in command history list
!-3					//recall third most recent command 
!grep				//recall last command begine with grep
source file			//force shell to re-read the file content
```

### 编译

```shel
./configure			//this is a shell script, attemp to guess system-dependent variable
./configure --help
./configure --prefix dir	//where to install machine independent file，data,configure file,documentation
./configure --exec-prefix dir	//where to hold machine dependent file
make				//compile source code
make check			//run self-tests that come with the package
make install		//install the program and data, documentation, cofigure file
make clean			//remove intermediate object file from source code
strip program		//strip all debug infomation
make install-strip	//install stripped program
```

信息打印

```sheel
pwd					//print working directory
who					//who is on the system
ps					//list all process info including status/time...
jobs				//display current process status(running/suspended/backgrounded)
df					//display left space of file system
du -s file/dir		//dislay kb of file or directory, '-s' display only summary
file				//classify file dependent on data type in file, text/picture/...
history				//display command history
```

### 帮助文档

```sh
man command			//on-line manual
whatis command		//only one line description of the command
apropos keyword		//search keyword in all manuals descriprion to find related command
info --file=xx.info //display documentation
```

### 环境变量

```shell
$HOME				//home directory
$OSTYPE				//OS type
$USER 				//login name
$HOST				//computer name
$ARCH				//processor architecture
$PATH				//directories where shell to find a command you typed
$DISPLAY			//screen name
$PRINTER			//default printer

setenv NAME value
unsetenv NAME
printenv NAME
env | less			//print all enviroment variables
```

### shell变量

```she
//shell variables apply only to the current instance of the shell
$history
$home
$path
$prompt
$cwd				//current working directory 

set name=value
unset name
set name			//display shell variable
set | less
set history = 200	//resize hostory buffer size
set path = ($path new_bin_path)
```

### 配置文件

```shell
.login	//in home directory, apply to whole session after login, set enviroment variable here
.bshrc	//in home dierctory, apply to each new shell, set shell vairable here
```

### 文本编辑

```shel
gedit file
```



