## 基础操作

### 查看帮助：whatis/man/info

常见参数：

```
-v ： 一般是指verbose
-h ： 一般是human
```

### 切换目录：cd

```
cd -  ：切换到上一个目录
cd .. ：切换到上级目录
cd ~  ：切换到当前用户的home目录
cd ~username ：切换到其它用户的home目录
```

### 查看当前目录：pwd

```
pwd ：查看当前目录
pwd -P ：
```

### 查看目录下文件：ls

```
ls -a ：查看所有文件，包括隐藏文件
ls -l ：显示文件详细信息
ls -ld ：只看目录本身
ls -ltr ： 按修改时间顺序查看文件
```

### 创建文件夹：mkdir

```
mkdir dirname ： 创建目录，如果父目录不存在会报错
mkdir -p dirname ：创建多层目录，如果父目录不存在会自动创建
mkdir -m=755 dirname ：创建目录，并设置目录权限
```

### 复制文件：cp

```
cp -p source target ： 保留原始文件属性
cp -r source target ： 复制文件夹
cp -i source target ： 目录文件存在则询问
```

### 移动文件：mv

```
mv -u source target ： 只有target不存在或者旧时才move
mv -b source target ： 备份文件
mv -n source target ： 不要覆盖文件
```

### 删除文件：rm

```
rm -rf ： 删除文件或文件夹，忽略警告
rm -ir ： 删除前先询问
```

### 重命名文件：rename

一般重命名文件使用mv命令就足够了，rename命令主要用来批量重命名文件。

```
rename source target filename ： 将文件名中的source字符串替换为target字符串，支持正则表达式
rename reguler filename ： 对文件名执行正则表达式
```

### 转换文件：dd

```
dd if=source of=target ： source和target可以是设备也可以是文件
```

### 查找文件：which/whereis/locate/find

```
which ： 在PATH环境变量制定的位置中，寻找某个命令的位置，并返回第一个搜索结果
whereis ： 查找代码，帮助文件和二进制文件。-b只查找二进制文件，-m只查找说明文件，-s只查找源代码
locate ：去/var/lib/mlocate/mlocage.db中查找文件，一般一天运行一次updatedb更新一次数据库，可以在crontab中设置。
find dir -name "" ： 遍历文件，参数比较复杂
```

### 输出字符串：echo

```
echo -e ： 开启转义，默认不开启
```

### 环境变量：env

```
env ： 显示当前用户全部环境变量
```

### 一次性计划任务：at

```
at ： 在指定时间执行任务
atq ： 查看任务列表
atrm ： 删除任务
batch ： 与at类似，只有系统不繁忙时才执行。
```

### 长期计划任务：crontab

crontab的格式为：分钟 小时 日期 月份 星期几 命令，星期天等于0或者7

```
* ： 代表所有允许的取值
/n ： 代表一定时间间隔
n-m ： 代表一定取值范围
x,y,z ： 代表离散的取值
% ： 代表换行，可以用\%转义
```

## 文本文件操作

### 查看短文本文件：cat

```
cat -n file ： 查看文本文件，显示行号
cat -n file ： 查看文本文件，显示行号，空行不加行号
```

### 查看长文本文件：more

```
more file ： 查看文件
```

### 查看文件前n行：head

```
head -n 10 file ： 显示头10行
head -n -10 file ： 不显示后10行
```

### 查看文件后n行：tail

```
tail -n 10 file ： 查看文件后10行
tail -f file ： 持续刷新显示文件末尾
```

### 通过分割列来提取字符：cut

类似python的split()

```
cut -d: -f1 -s file ： -d后为分隔符,-f后为提取第几列，-s不显示不含分隔符的行
```

### 以不同格式输出：od

```
od -b file ： 以8进制输出
od -c file ： 以ascii码输出
```

### 转换或删除字符：tr

```
[:alnum:] ： 所有的字母和数字
[:alpha:] ： 所有的字母
[:blank:] ： 所有的水平空格
[:space:] ： 所有的水平和垂直空格
[:cntrl:] ： 所有的控制字符
[:digit:] ： 所有的数字
[:graph:] ： 所有可打印的字符，不包括空格
[:lower:] ： 所有的小写字母
[:upper:] ： 所有的大写字母
[:punct:] ： 所有的标点
[=CHAR=] ： 所有符合指定的字符
```

### 比较文件差异：diff

```
diff -b -B source target ： -b忽略空格差异，-B忽略空行差异
diff -q source target ： 仅显示是否有差异
```

### 查看文件的时间属性：stat

```
stat file ： 查看文件的inode内容
atime ： 
mtime ： 
ctime ：
```

### 修改文件的时间属性：touch

```
touch file ： 将文件的atime,mtime,ctime修改为系统当前时间，文件不存在则创建
touch -m/-c/-a file ： 单独修改一个时间
```

### 识别文件格式：file

```
file filename ： 识别文件格式
file -f filename ： 从文件中读取文件列表
```

## Vi基础操作

### 删除：dd

```
dd ： 删除光标所在行
5dd ： 删除光标处开始的5行
```

### 复制：yy

```
5yy ： 复制光标处开始的5行
```

### 粘贴：p

```
p ： 将之前删除或复制的数据粘贴到光标后
```

### 搜索：/和？

```
/ ： 从上到下搜索
? ： 从下到上搜索
n : 跳到搜索到的下一行
N ： 跳到搜索到的上一行
```

### 撤销：u

```
撤销之前的操作
```

### 保存及退出：:q,:w

```
:w ： 保存
:q ： 退出
:q! ： 强制退出，放弃修改
:wq! ： 强制保存退出
```

### 显示行号：:set nu

```
:set nu ： 显示行号
:set nonu ： 不显示行号
```

### 跳转：:n

```
:n ：跳转到第n行
:1 ：跳转到第一行
:$ ：跳转到最后一行
```

### 清空文件：:%d

```
:%d ： 清空小文件，大文件会比较慢
cat /dev/null > filename ： 推荐方法
```

### 显示格式：:set ff

```
:set ff ： 显示文件格式
:set ff=unix ： 将文件格式转换为unix 
```

## 用户管理

### 创建用户：useradd

### 修改密码：passwd

### 删除用户：userdel

### 修改用户：usermod

### 创建组：groupadd

### 切换用户身份：su

```
su username ： 切换用户身份，但环境变量和工作目录还是原来用户的
su - username ： 切换用户身份和环境变量
```

### 临时使用root权限：sudo

可以使用visudo命令修改/etc/sudoers

### 查看用户登录记录：last

用户登录信息保存在/var/log/wtmp

```
last user ： 显示用户的登录记录
```

### 查看用户登录失败记录：lastb

用户登录失败信息保存在/var/log/btmp

### 查看用户历史命令：history

命令历史储存在 ~/.bash_history

```
export HISTTIMEFORMAT='%F %T ' ： 设置环境变量后的命令才会有时间戳
ctrl + R ： 可以搜索自己使用过的命令
!n ： 执行第n条命令
```

### 查看登录用户信息：w/who/whoami

```
w ： 查看登录用户信息
whoami ： 
who ： 
```

### 查看用户组信息：id

## 权限管理

### 用户身份：UID

```
0 ： root用户
1-999 ： 系统服务用户，默认不可登录
1000+ ： 普通用户
```

### 组身份：GID

组信息保存在/etc/group中

```
默认组 ： 与UID相同，用户创建时创建
扩展组 ： 后加入的组
```

### 文件权限：

```
读 ：r或者4
写 ： w或者2
执行 ： x或者1，目录的x权限代表用户可以进入
```

ls -l的结果总共10位

```
第一位 ： 文件类型，-普通文件，d目录，l链接，b块设备，c字符设备，p管道
2-4位 ： 文件所有者权限，顺序r,w,x，没有该项权限用-代替
5-7位 ： 文件所属组权限
8-10位 ： 其它用户权限
```

### 临时属主权限：SUID

### 临时属组权限：SGID

### 只可管理自己的数据不能删除他人文件：SBID

### 设置隐藏权限：chattr

```
i ： 仅能修改，不能删除和新建
a ： 仅允许追加内容
S ： 内部变化后马上同步到硬盘
s ： 彻底删除，不可恢复
A ： 不再更新文件的最后修改时间
D ： 检查压缩文件中的错误
d ： 默认将文件或目录进行压缩
u ： 删除后保留硬盘中的数据，日后可恢复
X ： 可以直接访问压缩文件的内容
```

### 显示隐藏属性：lsattr

## 磁盘操作

### 常见目录定义：

```
/boot ： 开机所需文件，内核，开机菜单等
/dev ： 任何设备与接口都以文件形式保存在此目录
/etc ： 配置文件
/home ： 用户目录
/opt ： 放置第三方软件
/tmp ： 任何人都可以使用的共享临时目录
/proc ： 虚拟文件系统，包括系统内核，进程
/var ： 日志
/lost+found ： 文件系统发生错误后保存丢失的文件片段
```

### 常见文件系统：

```
Ext4 ： RHEL6默认
XFS ： RHEL7默认
NFS ： 网络文件系统，主要用于远程文件共享
PROC ： 虚拟的进程文件系统
EFS ： aws提高的弹性文件系统
```

### 挂载硬件设备：mount

挂载点必须是一个已经存在的目录。

需要mount重启后还生效的，需要在/etc/fstab添加mount，否则重启后会失效。

/etc/fstab格式：设备文件 挂载目录 格式类型 权限选项（默认为default） 自检 优先级

```
mount -a ： 挂载所有在/etc/fstab中设置的mount
```

### 取消挂载：umount

### 查看挂载点信息：df

```
df -a ： 显示所有的文件系统
df --total ： 显示总体使用量
df -h : 易读格式
df -i ： 展示Inode的信息
df -T ： 显示文件系统类型
```

### 查看磁盘使用量：du

```
du -sh dirname ： -s仅显示使用量总和,-h易读格式
```

### 文件链接：ln

```
ln ： 硬链接，相当于创建副本，修改一个与其链接的文件也会被修改，但删除文件后与其链接的文件不会被删除
ln -s ： 软链接（符号链接），原文件删除就失效，相当于快捷方式
```

### 逻辑卷：

### 用户磁盘空间限制：quota

### 虚拟文件系统：VFS

## 内存操作

### 查看内存占用：free

free命令读取的是/proc/meminfo，可以在/etc/sysctl.conf中调整swappiness来调整swap使用策略。

```
free -h -s 3 ： 每3秒查询一次内存使用情况，以易读方式显示
free ： 正在未被使用的内存
available ： free + cache + buffer
```

### 查看进程：ps

```
ps -ef 
ps aux
```



### 查看进程占用资源：top

### 改变进程优先级：nice

### 结束进程：kill

### ulimit

### 显示进程号：pgrep

### 后台执行程序：nohup

### 使程序后台执行：bg

### 使程序前台执行：fg

### 查看后台进程：jobs

### 查看进程间通信状态：ipcs

## 网络设置

### 查看网卡状态：ifconfig

### 查看端口状态：netstat

### 查看路由设置：route

### 域名解析：nslookup

### 测试网络状况：ping

### 测试远程端口是否开放：telnet

### 路由跟踪：traceroute

### 下载文件：wget

### curl

### 监听网卡数据包：tcpdump

## 管道与重定向

### 管道命令符：|

### 重定向：>/>>/</<<

```

```

### 通配符：

### 特殊字符转义：
