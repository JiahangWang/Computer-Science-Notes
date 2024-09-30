# <center>Linux常用命令</center>

## 查询系统版本和相关信息
- `uname` 命令：此命令用于显示有关系统内核的信息。使用以下选项可以获取系统版本信息：
```
	uname -a ：显示所有可用信息，包括内核版本、主机名、操作系统版本等。
	uname -r ：显示内核版本。
	uname -v ：显示内核版本和日期。
```
- `lsb_release` 命令：此命令用于显示 Linux 标准库（LSB）版本信息。使用以下选项可以获取系统版本信息：
```
lsb_release -a ：显示所有可用信息，包括发行版名称、版本号、描述等。
```
- `/etc/os-release` 文件：此文件包含有关操作系统的信息，可以直接查看它以获取系统版本。使用以下命令可以查看文件内容：
```
cat /etc/os-release
```

## 查看内存大小和相关信息
- `free` 命令：此命令用于显示系统内存的使用情况和空闲情况。执行以下命令可以查看内存大小：
```
free -h
```
- `cat /proc/meminfo` 命令：通过查看 `/proc/meminfo` 文件，你可以获取有关系统内存的详细信息，包括总内存大小、可用内存、缓存等。执行以下命令可以查看内存信息：
```
cat /proc/meminfo
```

## 查看 CPU 资源的占用情况
- `top` 命令：此命令用于实时查看系统资源的使用情况，包括 CPU 的占用率：
```
top
```
- `mpstat` 命令：此命令用于显示多处理器的统计信息，包括每个 CPU 的使用率。执行以下命令可以查看 CPU 的使用率统计：
```
mpstat
```

## 杀死进程（终止运行中的进程）
- `kill` 命令：使用进程 ID（PID）来杀死进程。执行以下命令：
```
kill 1234
```
- `kill -9` 是一个用于终止进程的命令选项，被称为 "SIGKILL" 信号。它是 `kill` 命令的一个特殊选项，用于强制终止无法通过常规方式终止的进程。

- `killall` 命令：使用进程名（或命令名）来杀死所有匹配的进程。执行以下命令：
```
killall <process_name>
```


## 防火墙相关命令

```
systemctl status firewalld //查看防火墙状态
```

```
systemctl start firewalld  //启动防火墙
```

```
systemctl stop firewalld   //禁用防火墙
```

## telnet 相关命令
- Telnet 是一种用于远程登录和远程管理设备的网络协议。虽然在许多现代系统中已经被更安全的协议（如 SSH）所取代，但在某些情况下，仍可以使用 Telnet 进行基本的网络连接和测试

- 连接到远程主机：
```
telnet hostname
```
- 指定端口号连接：
```
telnet hostname port
```

```
telnet 10.143.132.51 3306 
```
- 在 Telnet 会话中，你可以使用以下命令退出 Telnet：
```
quit
```


## kafka 相关命令

```
nohup ./kafka-server-start.sh ../config/server.properties &&>/dev/null 2>&1 &    //启动kafka
```

## zookeeper 相关命令

```
systemctl start zookeeper //启动
```

```
systemctl status zookeeper  //查看状态
```

```
systemctl stop zookeeper   //停用
```

## 启动 mysql 命令

```
systemctl start mysqld //启动
```

```
systemctl status mysqld  //查看状态
```

```
systemctl restart mysqld   //重启
```

## 修改系统时间
- 使用 `date` 命令：
```
date -s "YYYY-MM-DD HH:MM:SS"
```

```
date -s "2020-02-02 08:09:20"
```

## scp 命令
- `scp` 是一个用于在本地主机和远程主机之间进行安全文件传输的命令。它基于 SSH（Secure Shell）协议，提供了加密的传输通道，用于在两个主机之间复制文件和目录。
```
scp [options] source_file destination_file
```
- `source_file`：指定要复制的源文件或目录的路径。
- `destination_file`：指定目标文件或目录的路径。

- 要从本地主机复制文件到远程主机，使用以下命令：
```
scp source_file user@remote_host:destination_path
```
- 要从远程主机复制文件到本地主机，使用以下命令：
```
scp user@remote_host:source_file destination_path
```


## ssh 远程登录
- 要使用 SSH 远程登录到另一台计算机，你可以使用以下命令：
```
ssh username@hostname
```
- `username` 是你在远程计算机上的用户名。
- `hostname` 是远程计算机的主机名或 IP 地址。
```
ssh root@192.168.1.203
```
- 在执行命令后，系统将提示你输入密码。输入正确的密码后，你将成功连接到远程计算机，并在远程计算机上的命令行终端上获得控制权。

- 如果你使用的是 SSH 密钥对进行身份验证而不是密码，可以使用 `-i` 选项指定私钥文件的路径。例如：
```
ssh -i /path/to/private_key user@192.168.0.100
```
- 这将使用指定的私钥文件进行身份验证，并登录到远程计算机。

## linux 查看开放哪些端口

```
 netstat -ntpl | grep 9092     //指定查看tcp端口
```

```
 netstat -nupl | grep 9092     //指定查看udp端口
```

```
 netstat -ntpl -t    //查看开放所有端口
```

## 指定网卡配置文件修改ip

```
cd /etc/sysconfig/network-scripts    //ifcfg-eth0 指定网卡配置文件修改ip,
```

```
 systemctl restart network    //然后重新启动网络，让所有的网卡配置生效
```

## 指定网卡的启动或禁用

```
ifdown ifcfg-eth0    //禁用，ifcfg-eth0 指定网卡配置名称
```

```
ifup ifcfg-eth0    //启用，ifcfg-eth0 指定网卡配置名称
```

## 查看所有打开的端口

```
firewall-cmd --zone=public --list-ports 
```

## 打开防火墙的端口

```
firewall-cmd --add-port=465/tcp --permanent 
```

## 关闭防火墙的端口

```
firewall-cmd --zone=public --remove-port=465/tcp --permanent
```

## 重载生效刚才的端口设置

```
firewall-cmd --reload //重载生效刚才的端口设置
```

## 查看磁盘相关命令
- `df` 命令：此命令用于显示文件系统的磁盘空间使用情况。执行以下命令可以查看磁盘空间信息：
```
df -TH 
```
- `du` 命令：此命令用于估算文件和目录的磁盘使用情况。执行以下命令可以查看指定目录的磁盘使用情况：
```
du -sh /path/to/directory
```
- `lsblk` 命令：此命令用于列出系统中的块设备信息，包括磁盘和分区。执行以下命令可以查看磁盘和分区信息：
```
lsblk
```


## 查询 java 进程详细信息

```
top -b -n 1 | grep java | awk '{print "PID: "$1" \t 虚拟内存: "$5" \t 物理内存: "$6" \t 共享内存: "$7" \t CPU使用率: "$9"% \t 内存使用率: "$10"%"}'
```
- 该命令将输出类似以下格式的 Java 进程详细信息：
```
PID: 1234    虚拟内存: 123456KB    物理内存: 7890KB    共享内存: 1234KB    CPU使用率: 12.3%    内存使用率: 45.6%
```
- powersehll 版本
```
Get-Process | Where-Object { $_.Name -eq "java" } | Select-Object Id, VirtualMemorySize, WorkingSet, SharedMemorySize, CPU, PM | Format-Table -AutoSize
```

- `jps` 是 Java Development Kit (JDK) 自带的一个工具，用于显示 Java 进程的相关信息，如进程 ID (PID) 和主类名称。
```
jps
```
- 以详细模式显示 Java 进程的信息：
```
jps -l
```



## 启动 java 程序输出日志到 info

```
 nohup java -jar -Xmx1024M -Xss256k anpm-plug-taskapi-2.0.0.jar &>/dev/null&
```

## 查看端口是否被占用

```
lsof -i:8080 
```

## 设置开机自启脚本或命令

```
vim /etc/rc.local   //在文件末尾加上你开机需要执行的命令即可
```

```
/etc/profile.d/   //自己写一个shell脚本将写好的脚本（.sh文件）放到目录下，系统启动后就会自动执行该目录下的所有shell脚本
```
- 使用 cron 任务：你可以将自启动脚本或命令添加到 cron 任务中，使其在系统启动时自动执行。
	- 使用以下命令编辑 cron 任务：
```
crontab -e
```
- 在打开的编辑器中，添加一行类似于以下内容的条目：
```
@reboot /path/to/script.sh
```
- 保存更改后，cron 将在系统启动时执行指定的脚本或命令。

## 启动 nginx

```
systemctl start nginx  
```

## 检查 SELinux status

```
/usr/sbin/sestatus //返回值disabled 或 enabled

setenforce 0      //表示关闭selinux防火墙，重启会失效
```

## 进入 mysql 命令

```
mysql -uroot -p
```

## 导入 mysql 的 sql 文件

```
mysql -uroot -pWdkj@2019! </web/sql/anpm.sql
```

## 导入 mysql 的 sql 文件，指定数据库

```
mysql -uroot -pWdkj@2019! anpm </web/sql/anpm.sql
```

## 导入 clickhouse 的 sql 文件

```
clickhouse-client --host 10.0.0.192 --user default --password wdkj@2021! --multiquery < /web/sql/clickhouse/ddl/clickhouse.sql
```

## 导入 clickhouse 的 sql 文件，指定数据库

```
clickhouse-client --host 10.0.0.192 --user default --password wdkj@2021! -d anpm_data --multiquery < /web/sql/clickhouse/ddl/clickhouse.sql
```

## 检查文件描述符限制

```
ulimit -n //查看open file限制数量
cat /etc/security/limits.conf //查看修改openfile数量的配置文件

```

## 查看服务或程序进程的打开文件数信息

```
cat /proc/24875/limits //24875为进程号
```

## 查看当前系统的打开文件数

```
lsof | wc -l  
```

## 查看某个进程的打开文件数

```
lsof -p  1234|wc -l   //1234为进程号
```



## 获得允许的最大打开文件数

```
cat /proc/sys/fs/file-max
```

## 定时任务相关命令

```

crontab -l	// -l 查看计划任务列表
crontab -e  //编辑定时任务
service crond restart //重启crond服务
service crond reload //重新载入配置
```

## 查看文件大小，包括目录里面的

```
du -sh filename    //filename指文件名称
```

## 查看端口占用

```
netstat -anp | grep 8080    
```

## zip压缩、解压文件夹

```
zip [选项] 压缩文件名 源文件或目录
```
- `选项`：`zip` 命令支持多个选项来控制压缩的行为，如压缩级别、文件权限、排除特定文件等。以下是一些常用的选项：
  
  - `-r`：递归压缩目录及其子目录下的所有文件。
  - `-q`：安静模式，不显示压缩过程中的输出信息。
  - `-9`：最高压缩级别，即最大压缩比。
  - `-x`：排除指定的文件或目录。
  - `-P`：设置压缩文件的密码。
  - `-u`：仅更新压缩文件中修改过的文件。
  - `-j`：仅压缩文件，不包括路径信息。
- `压缩文件名`：指定生成的压缩文件的名称。
  
- `源文件或目录`：指定要压缩的源文件或目录的路径。
```
zip -r archive.zip folder1
```
- 要解压缩文件，可以使用 `unzip` 命令
```
unzip [选项] 压缩文件名
```
- `选项`：`unzip` 命令支持多个选项来控制解压缩的行为，如解压到指定目录、覆盖文件、显示详细信息等。以下是一些常用的选项：
  
  - `-d 目标目录`：指定解压缩的目标目录。
  - `-o`：覆盖已存在的文件。
  - `-q`：安静模式，不显示解压缩过程中的输出信息。
  - `-l`：列出压缩文件中的内容，而不解压缩。
  - `-p`：解压缩文件时保留文件的原始权限。
- `压缩文件名`：指定要解压缩的压缩文件的名称。

```
unzip archive.zip -d target_directory
```


## tar 压缩、解压文件
- 打包并压缩
```
tar -czf <压缩文件名>.tar.gz <文件1> <文件2>
```
- 解压并解包
```
tar -xzf <压缩文件名>.tar.gz
```


## 查看进程运行了多长时间 

```
ps -p ,8299是指进程号 -o etime //查看进程运行了多长时间 ,8299是指进程号
```

## 修改用户密码

```
passwd * //*是指修改的密码
```

## 其他常用命令
* [grep 命令](https://www.runoob.com/linux/linux-comm-grep.html)
* [find 命令](https://www.runoob.com/linux/linux-comm-find.html)
* [awk 命令](https://www.runoob.com/linux/linux-comm-awk.html)
* [sed 命令](https://www.runoob.com/linux/linux-comm-sed.html)
* [sort 命令](https://www.runoob.com/linux/linux-comm-sort.html)


## 安装 git
```
sudo yum install git
```
## 安装 vim-plug
```
git clone https://github.com/junegunn/vim-plug.git ~/.vim/autoload/plug.vim
```
- 注：这是个文件夹，只要里面的 plug.vim 文件
- 在 `.vimrc` 文件中添加以下内容：
```
set nocompatible              " 确保使用 Vim 的改进模式
filetype off                  " 必须在插件之前加上此行

" 在此处插入 vim-plug 相关配置
call plug#begin('~/.vim/plugged')

" 添加插件列表，比如：
" Plug '插件名称/仓库'
" 例如：Plug 'vim-airline/vim-airline'

call plug#end()              " 必须在插件之后加上此行
filetype plugin indent on    " 必须在插件之后加上此行
```

