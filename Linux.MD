# Linux基础教程


### Linux目录结构

+ /bin (/usr/bin、/usr/local/bin)： 是Binary的缩写，这个目录存放着最经常使用的命令

+ /sbin（/usr/sbin、/usr/local/bin）: s就是Super User的意思，这里存放的是系统管理员使用的系统管理程序

+ /home： 存放普通用户的主目录，在Linux中每个用户都有一个自己的目录，一般该目录名是以用户的账号命名的

+ /root： 该目录为系统管理员，也称作超级权限者的用户主目录

+ /lib： 系统开机所需要的最基本的动态连接共享库，其作用类似于Windows里的DLL文件。几乎所有的应用程序都需要用到这些共享库

+ /lost+found：这个目录一般情况下是空的，当系统非法关机后，这里就存放一些文件

+ /etc： 所有的系统管理所需要的配置文件和子目录

+ /usr： 用户的很多应用程序和文件都会放在这个目录下，类似Windows下的program files目录

+ /boot：存放的是启动Linux时使用的一些核心文件，包括一些连接文件以及镜像文件

+ /proc： 是一个虚拟目录，是系统内存的映射，访问这个目录来获取系统信息

+ /srv： service缩写，该目录存放一些服务启动之后需要提取的数据

+ /sys： 这是Linux2.6内核的一个很大的变化，该目录下安装了2.6内核中新出现的一个文件系统

+ /tmp： 用来存放临时文件的

+ /dev： 类似于Windows的设备管理器，把所有的硬件用文件的形式储存

+ /media： Linux系统会自动识别一些设备，例如U盘、光驱等等，当时别后，Linux会把识别的设备挂载到这个目录下

+ /mnt： 系统提供该目录是为了让用户临时挂载别的文件系统的，我们可以将外部的储存挂载在/mnt/上，然后该目录就可以查看里面的内容了

+ /opt： 这是给主机额外安装软件所摆放的目录，如安装oracle数据库就可以放到该目录下

+ /usr/local： 这是另一个给主机额外安装软件所安装的目录。一般是通过编译源码方式安装的程序

+ /var： 这个目录存放着在不断扩充者的东西，习惯将经常被修改的目录放在这个目录下。包括各种日志文件

+ /selinux（security-enhanced linux）： SELinux是一种安全子系统，它能控制程序只能访问特定文件

### 关机重启命令

+ shutdown -h now：表示立即关机

+ shutdown -h 1：表示1分钟后关机

+ shutdown -r now：立刻重启

+ halt：关机

+ reboot：重启计算机

+ sync：把内存的数据同步到磁盘

### 用户登录和注销

+ logout：注销登录

### 用户管理

+ useradd [选项] 用户名：添加用户，同时默认创建一个与用户名相同的组，同时将用户添加到改组中

+ useradd -d 指定目录 用户名：创建用户，同时指定家目录

+ passwd 用户名：修改密码

+ del 用户名：删除用户，保留家目录

+ del -r 用户名：删除用户，同时删除家目录

+ id 用户名：查询用户信息

+ su - 用户名：切换用户

+ whoami/who am i：查询当前用户身份

+ groupadd 组名：添加用户组

+ groupdel 组名：删除用户组

+ useradd -g 用户组 用户名：创建用户，并将其添加到指定用户组

+ usermod -g 用户组 用户名：修改用户的用户组

+ /etc/passwd：用户的配置文件，记录用户的各种信息。每行的含义：用户名:口令:用户标识号:组标识号:注释性描述:主目录:登录shell

+ /etc/shadow：口令配置文件。每行含义：登录名:加密口令:最后一次修改时间:最小时间间隔:最大时间间隔:警告时间:不活动时间:失效时间:标志

+ /etc/group：组（group）的配置文件。每行含义：组名:口令:组标识号:组内用户


### Linux运行级别

+ 0：关机

+ 1：单用户（找回丢失密码）

+ 2：多用户无网络服务

+ 3：多用户有网络服务

+ 4：保留

+ 5：图形界面

+ 6：重启

+ /etc/inittab：系统运行级别配置文件

+ init 级别：切换到指定运行级别

+ 找回root密码：TODO

+ man 命令或配置文件：获取帮助信息

+ help 命令：获得shell内置命令的帮助信息

+ pwd：获取当前工作目录的绝对路径

+ ls [选项] [目录或是文件]：
    常用选项：
        -a：显示当前目录所有的文件和目录，包含隐藏的
        -l：以列表的方式显示信息

+ cd [参数]：切换到指定目录，cd ~或cd 回到自己的家目录，cd ..回到上级目录

+ mkdir：创建目录
    基本语法：mkdir [选项] 要创建的目录
    常用选项 -p：创建多级目录

+ rmdir：删除空目录，只能删除空目录，如果需要删除非空目录，则需要使用rm -rf 要删除的目录

+ touch：创建空文件，可以一次性创建多个文件

+ cp [选项] source dest：拷贝文件到指定目录
    常用选项：-r 递归复制整个文件夹
    \cp：强制覆盖

+ rm：删除文件或目录
    基本语法：rm [选项] 要删除的文件或目录
    常用选项：
        -r：递归删除整个文件夹
        -f：强制删除不提示

+ mv：移动文件或目录或重命名
    基本语法：
        mv oldNameFile newNameFile：重命名
        mv /tmp/movefile /targetFloder：移动文件

+ cat：查看文件内容（只读）
    基本语法：cat [选项] 要查看的文件
    常用选项：-n：显示行号
    示例：cat -n /etc/profile | more：分页查看

+ more：基于VI编辑器的文本过滤器，它以全屏的方式按页显示文本文件的内容。
    基本语法：more 要查看的文件
    操作：

操作 | 功能说明
:-: | :-:
空格键(Space) | 代表向下翻一页
Enter | 代表向下翻[一行]
q | 代表立刻离开more，不再显示该文件的内容
Ctrl + F | 向下滚动一屏
Ctrl + B | 返回上一屏
= | 输出当前行的行号
:f | 输出文件名和当前行的行号

+ less：用来分屏查看文件内容，功能与more指令类似，但是比more指令更加强大，支持各种显示终端。less指令在显示文件内容时，并不是一次性将整个文件加载之后才显示，而是根据显示需要加载内容，对于显示大型文件具有较高效率。
    基本语法：less 要查看的文件

操作 | 功能说明
:-: | :-:
空白键 | 向下翻动一页
[pgDn] | 向下翻动一页
[pgUp] | 向上翻动一页
/字符串 | 向下搜索字符串的功能：n：向下查找；N：向上查找
?字符串 | 向上搜索字符串的功能：n：向上查找；N：向下查找
q | 退出



+ [>] 指令：将内容写入某个文件（覆盖写）
    示例：
        ls -l > file.txt
        cat 某个文件 > file.txt
        echo "xxx" > echo.txt

+ [>>] 指令：将内容写入某个文件（末尾追加）
    示例：
        ls -l >> file.txt
        cat 某个文件 >> file.txt
        echo "xxx" >> echo.txt

+ echo：输出内容到控制台
    基本用法：echo [选项] [输出内容]

+ head：显示文件开头部分，默认情况下head指令显示文件的前10行内容
    基本语法：
            head 文件：查看文件前10行内容
            head -n 5 文件：查看文件前5行内容

+ tail：输出文件中尾部的内容，默认情况下tail指令显示文件的后10行内容
    基本语法：
        tail 文件：查看文件后10行内容
        tail -n 5 文件：查看文件后5行内容
        tail -f 文件：实时追踪该文档的所有更新

+ ln：软连接，类似windows里的快捷方式，主要存放了链接其他文件的路径
    基本语法：ln -s [原文件或目录] [软连接名]给原文件创建一个软链接

+ history：查看已经执行过历史命令，也可以执行历史命令
    示例：history 10：显示最近10条指令
        !x：执行编号为x的指令：如!999

+ date：显示当前时间
    基本语法：
        date：显示当前时间
        date +%Y：显示当前年份
        date +%m：显示当前月份
        date +%d：显示当前日
        date "+%Y-%m-%d %H:%M:%S"：显年月日时分秒
        date -s "2020-05-20 22:48:00"：设置电脑时间

+ cal：显示日历
    基本语法：cal [选项]
    示例：cal 2020：显示一年的日历
