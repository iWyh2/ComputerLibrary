# Linux



# 一. 初识Linux

创始人：林纳斯（炮轰C++是垃圾玩意儿的人，hhhhh）



## Linux内核

> 内核提供系统最核心的功能
>
> 如：
>
> * 调度CPU
> * 调度内存
> * 调度文件系统
> * 调度网络通讯
> * 调度IO



Linux系统的组成：

* Linux系统内核（免费，开源，我们都可以去下载修改）
* 系统程序应用



## Linux发行版

任何人都可以获得Linux内核，并且自行集成系统级应用

内核+系统级应用的完整封装就是Linux发行版



这里选择**CenOS版**本 以及了解Ubuntu

不同版本的Linux指令完全一样



## 虚拟机

通过虚拟化技术，在电脑内虚拟出计算机硬件，并给虚拟的硬件安装操作系统，这样就虚拟出了一台电脑

用虚拟机来获得Linux系统环境



虚拟化软件：选择**VMware**

还要下载CentOS操作系统装入VMware



**远程连接Linux操作系统**：

操作系统的使用：图形化/命令行（Linux也都支持）

但在企业开发和个人开发时，使用Linux作为服务器操作系统，我们都是使用**命令行**进行操作

因为Linux的命令行效率高、直观、资源占用低、程序运行稳定

而我们使用VMware操作Linux命令行并不方便：

* 内容复制粘贴
* 文件上传下载
* 与Linux系统的交互跨越VMware并不方便

所以我们使用第三方软件远程连接Linux操作系统：**FinalShell**

【注】记住远程连接时，我们VMware的NAT service服务要记得已经启动好 这样ifconfig才会成功



[扩展]**WSL获取Ubuntu环境**：

WSL为win10的新特性，可以轻量化的获取Linux环境 

WSL：Windows Subsystem for Linux

* 完全直连计算机硬件，无需虚拟机软件
* 直接在Windows系统中开启这个功能即可
* 然后去搜索下载Ubuntu即可



**虚拟机快照**：

学习阶段如果损坏了Linux系统重装很麻烦

VMware支持为虚拟机制作快照

也就是通过快照将当前虚拟机的状态保存下来。以后通过快照恢复虚拟机的保存状态

**右键当前虚拟计算机，选择快照，点击快照管理器即可**







# 二. Linux基础命令



## Linux目录结构

是一个**树形结构**

没有盘符的概念，**只有一个根目录（/）**，所有的文件都在这个文件之下



**路径的描述**：

路径之间的层级关系用：/

例如：/user/local/hello.txt（**开头的/为根目录**）





## Linux命令入门



**Linux命令基础**：

命令行：Linux终端（Terminal），命令提示符页面，以纯字符操作系统

命令：即Linux程序。一个命令就是一个Linux程序，提供字符化的反馈



命令基础格式：**command [-options] [parameter]**（[]意为可选非必填）

* command：**命令本身**
* -options：可选非必填命令的一些**选项**，控制命令的细节行为
* parameter：可选非必填命令的**参数**，用于命令指向目标



**ls命令入门**：

ls命令：列出目录下的内容

：ls [-a -l -h] [Linux路径]

* -a -l -h分别是可选的选项
* Linux路径为参数

当不使用选项和参数直接使用ls命令本体时为：以平铺的形式，列出当前工作目录下的内容



ls命令为列出当前工作目录下的内容

* 当前工作目录：当前打开的目录，Linux命令行终端在启动时**默认加载当前登录用户的HOME目录为当前工作目录**
* HOME目录：Linux操作用户在Linux系统中的**个人账户目录**，路径为：/home/用户名（我的HOME目录就是为/home/wyh）



**ls命令的参数和选项**：

ls使用参数时，为指定一个Linux路径，列出指定路径的内容

-a选项：列出全部文件，包括隐藏文件/文件夹（a为all的意思）

* Linux中，以.开头的文件为隐藏文件，会自动隐藏，只有-a才看得到

-l选项：以列表（竖向排列）的形式展示内容，并展示更多信息

组合使用：选项是可以组合使用的

* 比如：ls -l -a 或者 ls -la 或者 ls -al，都表示同时应用-a和-l
* 参数也可以和选项同时使用：ls -al /

-h选项：以易于阅读的形式，列出文件大小，如K（KB）、M（MB）、G（GB）（Linux没有单位为默认为B大小，省略了B）





## 目录切换相关命令



cd命令：更改当前所在的工作目录（Change Directory）

：cd [Linux路径]

* cd命令无需选项，只有参数，表示要切换到哪个目录之下
* **只执行cd命令本身没有参数，表示回到用户的HOME目录**



pwd命令：查看当前所在的工作目录（Print Work Directory）

：pwd

pwd命令无选项无参数，直接输入pwd即可





## 相对路径、绝对路径和特殊路径



相对路径：以当前目录为起点，描述路径，无需以/开头

绝对路径：以根目录为起点，描述路径以/开头

例如：当前在HOME目录，要跳转到HOME目录中的Desktop目录

* cd Desktop
* cd /home/wyh/Desktop



特殊路径符：

* （**.**）：表示当前目录
  * cd ./Desktop：表示切换到当前目录下的Desktop目录内
* （..）：表示上一级目录
  * cd .. ：表示切换到上一级目录
  * cd .. ：表示切换到上二级目录，可以嵌套
* （~）：表示HOME目录
  * cd ~：切换到HOME目录 和 直接cd是一样的
  * cd ~/Desktop：切换到HOME目录下的Desktop目录





## 创建目录命令



mkdir命令：创建新的目录（Make Directory）

：mkdir [-p] Linux路径

* **参数必填**：表示Linux路径，既**要创建的文件夹的路径**，相对路径或绝对路径

* -p选项：表示自动创建不存在的父目录，适用于创建连续多层级的目录

  也就是在一次性创建多个层级的目录时要加上 -p选项

  * 例如：mkdir -p wyh/test1/test1

【注】创建文件夹需要修改权限，一般操作在HOME目录内。在HOME目录外会涉及权限问题，是权限管控的知识





## 文件操作命令



touch命令：创建文件（不是目录）

：touch Linux路径

* touch命令无选项，参数必填，表示在指定路径创建文件，路径可以相对，绝对，特殊

例如：touch test.txt

【注】文件和目录的区别：1.颜色（文件为白色，目录在FinalShell中为蓝色）2.ls -l时列出来的开头符号（d为目录，-为文件）



cat命令：查看文件的内容

：cat Linux路径

cat命令没有选项，必填参数，Linux路径表示被查看的文件路径（之后的Linux路径，相对，绝对，特殊都可以表示）

这里还未学习vi编辑器，所以先通过图形化界面在文件里添加内容，然后测试cat命令

例如：cat ~/test/test.txt



more命令：查看文件内容

：more Linux命令

* 没有选项，必填参数
* 查看过程中，空格翻页，按q退出查看

与cat不同的是，cat是直接将内容全部显示出来

而more支持翻页，如果文件内容过多，可以一页页展示

例如：查看一个系统内置文件，more /etc/services

【注】在FinalShell中，清屏的快捷键为Ctrl+l，命令为clear



cp命令：复制文件/目录（Copy）

：cp [-r] 参数1 参数2

* -r选项：可选，用于复制文件夹，r表示递归
* 参数1：Linux路径，表示被复制的文件或文件夹
* 参数2：Linux路径，表示要复制去的地方



mv命令：移动文件/目录（Move）

：mv 参数1 参数2

* 无选项
* 参数1：Linux路径，表示被移动的文件或文件夹
* 参数2：Linux路径，表示要移动去的地方，**如果目标不存在，则进行改名**，确保目标存在

例如：mv ~/test1/test.txt ./test2 或者 mv ./test.txt test1.txt(改名，test1不存在)



rm命令：删除文件、文件夹

：rm [-r -f] 参数1 参数2 ... 参数N

* -r选项：用于删除文件夹，不加就是删除文件，与cp命令一样
* -f选项：强制删除，不会弹出确认信息
  * 一般用户删除内容不会弹出提示，只有root管理员用户删除内容才会有提示，一般用户用不到-f
* 参数1 参数2 ... 参数N：各个参数表示要删除的文件或目录路径，按照空格隔开，表示可以一次性删除多个文件，目录

rm命令支持**通配符**（*）：

* **符号*为通配符，表示匹配任意内容（包含空）**
* test*：匹配以test开头的内容
* \*test*：匹配包含test的内容
* *test：匹配以test结尾的内容

强制删除需要我们临时切换到root用户：

通过：su - root命令，并输入账户密码临时切换到root用户

通过：exit命令，退回普通用户（不要一直使用root用户）

root用户的指示符由$变为了**#**

是否强制删除：y为是，n为否

【注】不要再root用户下使用：rm -rf /* 或者 rm -rf / 相当于Windows的C盘格式化，无法再使用Linux系统了





## 查找命令



grep命令：从文件中通过关键字过滤文件行

：grep [-n] 关键字 文件路径

* -n选项：表示在结果中显示匹配的行的行号
* 关键字参数：必填，表示过滤的关键字，带有空格或特殊字符，使用双引号""包裹关键字（这个**关键字为要查找的内容**，文件要包含）
* 文件路径参数：必填，表示要过滤内容的文件路径，可作为**内容输入端口**，作为管道符的输入



wc命令：统计文件的行数，单词数等

：wc [-c -m -l -w] 文件路径

* -c选项：统计bytes数量
* -m选项：统计字符数量
* -l选项：统计行数
* -w选项：统计单词数量
* 文件路径参数：被统计的文件，可作为**内容输入端口**，作为管道符的输入

**管道符**：

**（符号|）将左边命令的结果，作为右边命令的输入**

左边需要**有结果的输出**，右边**需要命令有内容输入端口**，这样才可以将左边的结果作为输入进行操作

管道符**可以嵌套使用，依次往后传递**

例如：cat test.txt | grep wyh cat test.txt的输出结果为文件内容，拿来做右边过滤查找的过滤文件，查找包含wyh的行



 在此之前，我们学的这些命令都是linux中的一个个二进制可执行程序，相当于Windows中的.exe文件

which命令：查看一系列命令的程序文件存放在哪个位置

：which 要查找的命令

例如：which cd



find命令：按文件名搜索指定文件

：find 起始路径 -name "被查找文件名"

* 起始路径：从哪儿开始搜索
* -name选项：以文件名模式查找
* "被查找文件名"：可以用通配符做模糊匹配

【注】root用户下可以拥有最大权限，可以在整个系统中完成搜索

例如：find / -name "test" 或者 find / -name "*test\*"

find命令：按文件大小查找文件

：find 起始路径 -size +\\-n[kMG]

* -size选项：按文件大小模式查找
* +\\-：大于或小于
* n：数字大小
* [kMG]：k（小写，kb）M（大写，MB）G（大写，GB）

例如：查找小于10kb的文件：find / -size -10k





## 其他命令



echo命令：在命令行输出指定内容

：echo 输出的内容

* 无需选项，只需要一个参数，为指定的输出内容，复杂内容或者特殊字符建议用双引号""包裹

例如：echo "Change The World"

**反引号（`）**：echo中**被反引号包裹的字符会作为命令去执行**，而不是作为字符被输出

例如：echo \`pwd`



**重定向符**：

* \>：将左侧命令的结果，覆盖写入到符号右侧指定的文件中
* \>>：将左侧命令的结果，追加写入到符号右侧指定的文件中



tail命令：查看文件尾部内容或者跟踪文件的最新更改

：tail [-f -num] Linux路径

* Linux路径：表示被跟踪的文件路径
* -f选项：表示持续跟踪，有新的更新就会直接显示
* -num选项：查看尾部num行内容，num为具体数字，不填为默认10行

【注】Ctrl+C退出跟踪模式 键盘↑键回退上一次命令内容到命令行





## VIM编辑器

VI/VIM编辑器，是visual interface的简称，是Linux的经典文本编辑器

vi编辑器是命令行下对文本文件进行编辑的绝佳选择

**vim**是vi的增强版，兼容vi，多了对shell程序编辑的功能，现在一般用这个



VIM编辑器的三种工作模式：

* 命令模式：Command mode 键盘所敲的按键都被编辑器理解为命令，以命令驱动不同功能，此模式下不能自由进行文本编辑
* 输入模式：Insert mode 也就是编辑模式，插入模式，此模式下，可以对文件内容进行自由编辑
* 底线命令模式：Last line mode 以冒号 ：开始，通常用于文件的保存、退出

vim编辑器进去就是命令模式，以命令模式为中心想其他两个模式转换



要通过vim编辑器编辑文件，需要命令：

：`vi 文件路径` 或者 `vim 文件路径`

* 如果**文件路径表示的文件不存在，那么此命令会创建一个出来用于编辑**
* 有则直接编辑



命令模式下的常用快捷键：

* 键盘i：在当前光标位置进入输入模式
* 键盘↑/键盘k：向上移动光标
* 键盘↓/键盘j：向下移动光标
* 键盘←/键盘h：向左移动光标
* 键盘→/键盘l：向后移动光标
* 键盘0：光标移动到当前行开头
* 键盘$：光标移动到当前行结尾
* 键盘PgUp：向上翻页
* 键盘PgDn：向下翻页
* 键盘/：进入搜索模式
* 键盘n：向下继续搜索
* 键盘N：向上继续搜索
* 键盘dd：删除光标所在行的内容
* 键盘ndd：n为数字，删除当前光标向下n行
* 键盘yy：复制当前行
* 键盘nyy：n是数字，复制当前行和向下n行
* 键盘p：粘贴复制的内容
* 键盘u：撤销修改
* 键盘Ctrl+r：反向撤销修改
* 键盘gg：跳到首行
* 键盘G：跳到行尾
* 键盘dG：从当前行开始，向下全部删除
* 键盘dgg：从当前行开始，向上全部删除
* 键盘d$：从当前光标开始，删除到本行结尾
* 键盘d0：从当前光标开始，删除到本行开头



底线命令模式下常用命令：

按冒号 ：进入底线命令模式

* :wq 保存并退出
* :q 仅退出（没有改动时）
* :q! 强制退出（有修改时不保存）
* :w 仅保存
* :set nu 显示文本行号
* :set paste 设置粘贴模式（复制代码时保证格式不会乱）









# 三. Linux权限管控



## Root用户

Linux系统中，拥有最大权限的账户为root用户（超级管理员）

普通用户在许多地方的权限是受限的

例如：在根目录创建目录

普通用户在HOME目录内的权限是不受限的，出了HOME目录，普通用户仅有只读的执行权限，没法修改



su命令：用于账户切换（Switch User）

：su [-] [用户名]

* （-）选项：可选，表示是否在切换用户后加载环境变量，一般建议带上这个选项
* 用户名参数：表示要切换的用户，用户名可以省略，省略之后表示切换到root用户

从普通用户切换到其他用户需要输入密码，而从root用户切换到其他用户无需输入密码，直接切换



exit命令：退回上一个用户，或者使用快捷键Ctrl+d



sudo命令：为普通用户的命令授权。临时以root身份执行

：sudo 其他命令

也就是在其他命令之前加上sudo即可

但不是所有的用户都有权利使用sudo，需要**为普通用户配置sudo认证**



为普通用户配置sudo认证：

切换到root用户，执行visudo命令（用vi编辑器打开/etc/sudoers）

在文件末尾添加：wyh ALL=(ALL)	NOPASSWD: ALL





## 用户与用户组

Linux系统中：

* 可以配置多个用户
* 可以配置多个用户组
* 用户可以加入多个用户组中

Linux关于权限的管控级别有两个，分别是：

* 针对用户的权限控制
* 针对用户组的权限控制

例如：对于一个文件，可以控制用户的权限，也可以控制用户组的权限



用户组管理：

groupadd命令：创建用户组

：groupadd 用户组名



groupdel命令：删除用户组

：groupdel  用户组名

【注】以上命令都需要root管理权限



用户管理：

useradd命令：创建用户

：useradd [-g -d] 用户名

* -g选项：指定用户的组，不指定-g，会创建同名的组并自动加入，且指定的组需要已经存在
* -d选项：指定用户HOME路径，不指定的话，HOME目录默认在 /home/该用户名 下

例如：useradd -g Wang -d /home/test666 test1



userdel命令：删除用户

：userdel [-r] 用户名

* -r选项：删除用户的HOME目录，不加时，删除用户会保留HOME目录



id命令：查看用户所属组

：id [用户名]

* 用户名参数：被查看的用户，如果不提供则查看自身



usermod命令：修改用户所属组

：usermod -aG 用户组 用户名

将指定用户加入到指定用户组



getent命令：

：getent passwd 查看当前系统中有哪些用户

查询出来的一条用户信息有七份信息：用户名:密码(x):用户ID:组ID:描述信息(无用):HOME目录:执行终端(默认bash)

：getent group 查看系统中有哪些用户组

查询出来的一条组信息有三份信息：组名称:组认证(x):组ID





## 权限控制



认知权限信息：

通过ls -l可以列表查看内容，显示权限细节

现实的内容分别为：权限细节 所属用户 所属用户组



1.权限细节

有十位，首位代表文件类型，接着三位一组

：文件类型|所属用户权限|所属用户组权限|其他用户权限

首位分为三个类型：

* -：代表文件
* d：代表文件夹
* l：代表软链接

例如：drwxr-xr-x；意为：

* d -> 这是一个文件夹
* rwx -> 所属用户权限为有r有w有x
* r-x -> 所属用户组权限为有r无w有x（-代表无此权限）
* r-x -> 其他用户权限为有r无w有x（-代表无此权限）



2.rwx含义

* r：读权限
* w：写权限
* x：执行权限

对于文件和目录，rwx有细微区别：

文件：

* r为可以查看文件内容
* w为可以修改此文件
* x为可以将文件作为程序执行

目录：

* r为可以查看文件夹内容，也就是可以ls查看
* w为可以在文件夹内创建，删除，改名等操作
* x为可以更改工作目录到此文件夹，也就是可以cd进入





### 修改权限控制



chmod命令：修改文件、目录的权限信息

：chmod [-R] 权限 文件或文件夹

* 权限参数：
  * u：所属用户权限
  * g：所属用户组权限
  * o：其他用户权限

* -R选项：对文件夹内部的全部内容应用同样的修改权限操作

例如：chmod u=rwx,g=rx,o=x hello.txt 将文件的权限修改为了 rwxr-x--x

修改权限的快捷写法：u=rwx,g=rx,o=x可以写成三位数字来代表 - 751

权限的数字序号

r即为4 w记为2 x记为1

* 0：无任何权限，---
* 1：仅有x权限，--x
* 2：仅有w权限，-w-
* 3：有w有x权限，-wx
* 4：仅有r权限，r--
* 5：有r有x权限，r-x
* 6：有r有w权限，rw-
* 7：有全部权限，rwx

例如：chmod 777 test.txt

【注】只能是文件，文件夹的所属用户或root才有权修改



chown命令：修改文件、文件夹的所属用户和用户组

：chown [-R] [用户]\[:][用户组] 文件或文件夹

* -R选项：与chmod一样，对文件夹内的内容做相同的修改权限操作
* 用户选项：修改所属用户
* 用户组选项：修改所属用户组
* ：选项：用于分割用户和用户组

【注】此命令只适用于root用户执行

例如：chown root:wyh hello.txt 或者 chown :root hello.txt







# 四. Linux实用操作



## 小技巧+快捷键



Ctrl + c：强制停止程序 或 退出当前命令输入

Ctrl + d：退出账户的登录 或 退出某些程序的专属页面

history命令：查看历史输入过的命令

!+命令前缀：自动匹配执行上一次执行过的命令

Ctrl + r：输入内容去匹配历史命令，回车为直接执行，键盘左右键为得到这条命令

Ctrl + a：跳到命令开头

Ctrl + e：跳到命令结尾

Ctrl + 键盘←：向左跳一个单词

Ctrl + 键盘→：向右跳一个单词

Ctrl + l：清空终端内容（也就是clear指令）





## 软件安装



操作系统安装软件的许多方式，一般分为：

* 下载安装包自行安装：win下载exe或msi文件，mac下载dmg或pkg文件
* 系统的应用商店安装：win的Microsoft Store，mac的App Store

Linux也同样支持这两种，为.rpm文件



Linux系统的应用商店：yum命令（CentOS系统）

yum：RPM包软件管理器，用于自动化安装配置Linux软件，并自动解决依赖问题

：yum [-y] [install | remove | search] 软件名称

* -y选项：自动确认，无需手动确认安装过程或卸载过程
* install：安装
* remove：卸载
* search：搜索

【注】yum命令需要有root权限，且需要联网

例如：

* 搜索是否有wget安装包：yum search wget
* 安装wget程序：yum -y install wget
* 卸载wget程序：yum -y remove wget



[扩展]Ubuntu下载安装软件

Ubuntu使用apt管理器

：apt [-y] [install | remove | search] 软件名称

需要联网和root权限





## systemctl



Linux系统很多软件（内置或者第三方）均支持使用systemctl命令控制：启动，停止，开机自启

能够被systemctl管理的软件，一般称之为**服务**

：systemctl start|stop|status|enable|disable 服务名

* start：启动
* stop：停止
* status：查看状态
* enable：开启开机自启
* disable：关闭开机自启

例如：systemctl status firewalld



Linux系统内置服务比较多：

* NetworkManager：主网络服务
* network：副网络服务
* firewalld：防火墙服务
* sshd：ssh服务（FinaShell就是通过这个服务连接Linux的）



除了内置的服务，部分第三方软件安装后也可以通过systemctl进行控制

例如ntp软件和apache的httpd软件

部分软件安装后会自动集成到systemctl中，但有些没有，需要我们手动添加





## 软链接



软链接：将文件或文件夹链接到其他地方，**类似于Windows的快捷方式**，只是一个指向



ln命令：创建软链接

：ln -s 参数1 参数2

* -s选项：表示创建软链接
* 参数1：被链接的文件或文件夹
* 参数2：要要链接去的目的地

例如：ln -s /etc/yum.conf ~/yum.conf





## 日期与时区



date命令：查看系统的时间

：date [-d] [+格式化字符串]

* -d选项：按照给定的字符串显示日期，一般用于日期计算
  * 比如：date -d "+1 day" +%Y%m%d，显示后一天的日期
  * 支持的时间标记：
    * year
    * month
    * day
    * hour
    * minute
    * second
  * 可以和格式化字符串配合使用
* 格式化字符串：通过特定的字符串标记，来控制显示的日期格式
  * %Y：年
  * %y：年份后两位数字（范围：00~99）
  * %m：月份
  * %d：日
  * %H：小时
  * %M：分
  * %S：秒
  * %s：从1970-01-01 00:00:00 UTC到现在的秒数

直接使用date命令本体无选项，为直接查看时间，但格式不是我们能接受的

格式化字符串需要用双引号""包围作为整体



修改Linux时区：

系统默认时区不是中国的东八区

使用root权限：

* rm -f /etc/localtime
* sudo ln -s /user/share/zoneinfo/Asia/Shanghai /etc/localtime

也就是将系统自带的LocalTime文件删除，并将/user/share/zoneinfo/Asia/Shanghai文件链接为localtime文件



ntp程序：自动校准系统时间

需要我们安装，然后即可以联网校准时间，也可以手动校准（需要root权限）：ntpdate -u ntp.aliyun.com

利用阿里云提供的服务网址配合ntpdate命令自动校准





## IP地址与主机名



IP地址：每一台联网的电脑都会有一个地址，用于和其他计算机进行通讯

IP地址主要有两个版本：v4和v6

IPv4版本的地址格式为a.b.c.d，abcd为0~255的数字

Linux通过ifconfig命令查看本机ip地址，如果无法使用ifconfig，那就安装：yum -y install net-tools

特殊IP地址：

* 127.0.0.1：用于指代本机
* 0.0.0.0：可以用于指代本机，可以在端口绑定中用来确定绑定关系，还可以在一些IP地址限制中，表示所有IP的意思



主机名：每一台电脑除了对外联络地址（IP地址）以外，还有一个名字

无论是Windows还是Linux，都可以为系统设置主机名



hostname命令：查看主机名

：hostname



hostnamectl命令：修改主机名（需要root权限）

：hostnamectl set-hostname 主机名

修改完后需要重新登录FinalShell才看得到



**域名解析**：IP地址很难记，所以用字符化的地址去访问服务器，字符化的地址也叫域名

域名解析流程：比如访问`www.baidu.com`

访问`www.baidu.com` => 第一步**先检查：Linux系统中为 /etc/host文件**，Windows系统中为 C:\Windows\System32\drivers\etc\hosts文件，**是否有这个域名的ip记录** => 如果有，那么就打开网站；如果**没有，那么就联网去询问公开DNS服务器是否有这个域名的IP地址** => 有就打开网站；没有就报404未找到

常用DNS服务器（114.114.114.114 或 8.8.8.8）



配置主机名映射：使FinalShell通过主机名连接Linux服务器

需要我们在Windows系统下的C:\Windows\System32\drivers\etc\hosts文件中配置记录



为什么需要固定IP？：当前我们虚拟机的linux系统的IP地址是通过DHCP服务获取的。而DHCP是动态的获取IP地址，也就是每次重启设备之后都会获取一次，可能会使得IP地址频繁更换，对于办公电脑无所谓，但我们远程连接到Linux系统，ip经常变换修改适配会很麻烦，且使得配置的主机名映射IP无效

在VMware中配置固定IP：

* 在VMware中配置IP地址网关和网段（IP地址范围）
* 在Linux系统中手动修改配置文件，固定Ip





## 网络传输



ping命令：检查指定的网络服务器是否是可连通状态

：ping [-c num] ip或主机名

* -c num选项：检查的次数为num，不使用-c选项会无限次数的持续检查
* IP或主机名参数：被检查的服务器的ip地址或主机名地址

例如：ping baidu.com



wget命令：wget是非交互式的文件下载器，可以在命令行内下载网络文件

：wget [-b] url

* -b选项：可选，后台下载，会将日志写入到当前工作目录的wget-log文件
* url参数：下载链接



curl命令：可以发送http网络请求，可以用于下载文件，获取信息

：curl [-O] url

* -O选项：用于下载文件，当url为下载链接时，可以使用此选项保存文件，和wget一样可以下载文件
* url参数：要发起请求的网络地址

等同于打开一个网址，如果响应是一个网页，那么会获取网页源码





## 端口



端口：是设备与外界通讯交流的出入口。

端口可以分为物理端口和虚拟端口

物理端口：这称之为接口，是可见的端口，比如USB接口，RJ45网口，HDMI端口等

**虚拟端口：指计算机内部的端口，是不可见的，是操作系统和外部进行交互使用的**



虚拟端口作用：

计算机程序之间的通讯，通过IP地址只能锁定哪一台计算机，是无法锁定具体的程序的。

通过端口可以锁定计算机上的具体程序，确保程序之间进行沟通

（IP地址相当于小区地址，在小区内有许多住户（程序），他们的门牌号（端口）就是各个住户（程序）的联系地址）



Linux的端口：

Linux可以支持65535个端口，分为三类：

* 公认端口：1~1024，通常用于一些系统内置或知名程序的预留使用，如SSH服务的22端口，HTTPS的443端口，非特殊需要最好别占用
* 注册端口：1024~49151，可以随便使用，用于松散绑定一些程序或服务
* 动态端口：49151~65535，不会固定绑定程序，是当程序对外进行网络连接时，用于临时使用



nmap命令：查看端口的占用情况（没有的需要yum -y install nmap）

：nmap 被查看的IP地址



netstat命令：查看指定端口的占用情况（需要安装netstat：yum -y install net-tools）

：netstat -anp | grep 端口号

例如：netstat -anp | grep 920；查询出来的信息中，0.0.0.0:6000意为6000这个端口绑定在了0.0.0.0这个IP地址上了，表示允许被外界访问







## 进程管理



程序运行在操作系统中，是被操作系统所管理的

为管理运行的程序，每一个程序在运行时，会被操作系统注册为系统中的一个**进程**，并会为每一个进程都分配一个独有的**进程ID**



ps命令：查看系统中的进程信息

：ps [-e -f]

* -e选项：显示出全部的进程
* -f选项：以完全格式化的形式展示全部信息

所以一般这个命令的使用格式就是：ps -ef，列出全部进程的全部信息

查询出来的信息从左到右分别为：

* UID：进程所属的用户ID
* PID：进程的进程号
* PPID：进程的父ID（启动此进程的其它进程）
* C：此进程的CPU占用率（百分比）
* STIME：进程的启动时间
* TTY：启动此进程的终端序号（显示？为非终端启动）
* TIME：进程占用CPU的时间
* CMD：进程对应的名称或启动路径或启动命令



查看指定进程：用ps -ef命令配合管道符和grep即可过滤准确查看指定进程

例如：ps -ef | grep tail



kill命令：关闭进程

：kill [-9] 进程ID

* -9选项：表示强制关闭进程。不使用-9，会向进程发送信号要求其关闭，但是否关闭要看进程本身





## 主机状态



top命令：查看主机CPU、内存的使用情况。相当于Windows的任务管理器，默认五秒刷新一次

：直接输入top

按q或者Ctrl+c退出查看

top命令查询出来的信息：![](.\images\image-20221211172422422.png)

* 第一行：
  * top：命令名称
  * 当前系统时间
  * up 1:26：启动了的时间
  * 3 users：三个用户登录
  * load average：1、5、15分钟的负载（不超过1就是电脑CPU压力不大）
* 第二行：
  * Tasks：214个进程
  * 1 running：一个进程在运行
  * 213 sleeping：213个进程在睡眠
  * 0 stopped：0个进程停止
  * 0 zombie：0个僵尸进程
* 第三行：
  * %Cpu(s)：CPU使用率
  * us：用户CPU使用率
  * sy：系统CPU使用率
  * ni：高优先级进程占用CPU时间百分比
  * id：空闲CPU率
  * wa：IO等待CPU占用率
  * hi：CPU硬件中断率
  * si：CPU软件中断率
  * st：强制等待占用CPU率
* 第四五行：
  * KiB Mem：物理内存
  * total：总量
  * free：空闲
  * used：使用
  * buff/cache：buff和cache的占用
  * KiB Swap：虚拟内存（交换空间）（一般不看）
  * avail Mem：可使用内存

![image-20221211173401052](.\images\image-20221211173401052.png)

* PID：进程id
* USER：进程所属用户
* PR：进程优先级（越小越高）
* NI：负值为高优先级，正值表示低优先级
* VIRT：进程使用虚拟内存（KB）
* RES：进程使用物理内存（KB）
* SHR：进程使用共享内存（KB）
* S：进程状态（S休眠，R运行，Z僵尸状态，N负数优先级，I空闲）
* %CPU：进程占用CPU率
* %MEM：进程占用内存率
* TIME+：进程使用CPU时间总计（单位10毫秒）
* COMMAND：进程的命令或名称或程序文件路径



top命令选项：

* -p：只显示某个进程的信息（top -p 920）
* -d：设置刷新时间，默认五秒（top -d 2）
* -c：显示产生进程的完整命令，默认为进程名（top -c）
* -n：指定刷新次数（top -n 3）
* -b：以非交互非全屏模式运行，以批次方式执行top；一般配合-n，然后重定向输出到指定文件（top -b -n 3 > /tmp/top.tmp）
* -i：不显示空闲或僵尸进程（top -i）
* -u：查找特定用户启动的进程（top -u）



top交互式选项：top命令以非-b选项启动时，可以使用键盘按键控制

* h键：显示帮助画面
* c键：显示产生进程的完整命令，再按恢复（等于-c选项）
* f键：选择需要展示的项目
* M键：根据RES排序
* P键：根据CPU使用百分比排序
* T键：根据时间排序
* E键：切换顶部内存显示单位
* e键：切换进程内存显示单位
* l键：切换显示平均负载和启动时间信息
* i键：不显示空闲（idle）或僵尸（zombie）进程（等于-i选项）
* t键：切换显示CPU状态信息
* m键：切换显示内存信息



df命令：查看磁盘的使用情况

：df [-h]

* -h选项：以更人性化的单位显示



iostat命令：查看CPU，磁盘的相关信息

：iostat [-x] [num1] [num2]

* -x选项：显示更多信息
* num1选项：数字，表示刷新间隔
* num2选项：数字，表示刷新几次

tps：该设备每秒的传输次数。

一次传输意为一次I/O请求，请求大小未知



sar命令：查看网络的相关统计（sar命令很复杂，这里使用固定格式统计网络）

：sar -n DEV num1 num2

* -n选项：查看网络
* DEV：表示接口
* num1：刷新间隔，不填则为查看一次结束
* num2：查看次数，不填为无限次





## 环境变量



环境变量是操作系统在运行时，记录的一些关键性信息，用以辅助系统运行

在Linux系统中，环境变量是一种KeyValue型结构：环境变量名=值



env命令：查看当前系统中记录的环境变量

：env



无论我们在哪个工作目录中，都可以使用cd命令（或者这个程序），就是借助环境变量中的**PATH**

**PATH记录了系统执行任何命令的搜索路径**

当执行任何命令，都会在PATH中按照顺序搜索要执行的程序本体



$符号：

在Linux中，$符号用于取变量的值

环境变量记录的信息，除了操作系统可以使用，我们想要使用也可以

取得环境变量的值的语法：$环境变量名，当与其他内容混合了，可以使用{}来标注变量：${环境变量名}其他内容

例如：echo $PATH 或 echo ${PATH}ABC



**自行设置环境变量**：

* 临时设置：export命令

  ：export 变量名=值

  在退出登陆之后就会消失

* 永久生效：

  * 当前用户：在当前用户的 ~/bashrc文件中，配置export 变量名=值

    然后通过source命令使其立刻永久生效：source 该配置文件（~/bashrc）

  * 所有用户：在系统中的 /etc/profile文件中，配置export 变量名=值

    然后通过source命令使其立刻永久生效：source 该配置文件（/etc/profile）



**自定义环境变量的PATH**：

我们可以自行添加搜索路径到PATH中

* 临时修改PATH：例如，export **PATH=$PATH:**~/myScripts
* 永久修改：将上面的语法填入到~/bashrc文件或者/etc/profile文件中去，然后source 该配置文件





## 上传与下载



可以通过FinalShell工具，方便的和虚拟机进行数据交换

在FinalShell的下方窗体中，有Linux的文件系统视图

我们可以：

* 浏览文件系统，找到合适的文件，右键点击下载，即可完成下载传输到本地电脑
* 浏览文件系统，找到合适的目录，将本地电脑的文件拓展进入，即可完成上传数据到Linux



（yun -y install lrzsz）

rz命令：进行上传

：rz

然后就会弹出本地电脑的文件夹，自己选择文件上传到Linux即可（这样很慢，不如拖拽进入文件夹快）



sz命令：进行下载（下载的文件会到FinalShell设置的文件夹中去）

：sz 要下载的文件





## 压缩与解压



压缩格式：

* **zip**：Linux、Windows、MacOS
* 7zip：Windows
* rar：Windows
* **tar**：Linux、MacOS
* **gzip**：Linux、MacOS



Linux和Mac常用两种压缩格式，后缀为：

* .tar：称之为tarball，归档文件，也就是简单的将文件组装到一个.tar文件内，没有文件体积的减少
* .gz：或者是.tar.gz，为gzip格式压缩文件，使用gzip压缩算法将文件压缩，有文件体积的减少



tar命令：对着两种格式文件进行压缩和解压操作

：tar [-c -v -x -f -z -C] 参数1 参数2 ... 参数N

* -z选项：gzip模式。不使用-z就是普通的tarball格式（一般放在所有选项中第一个）

* -c选项：压缩模式
* -x选项：解压模式
* -v选项：显示压缩、解压过程。用于查看进度
* -f选项：要创建的压缩文件 或 要解压的文件（-f选项必须在所有的选项的最后，因为后面会紧跟一个参数为创建的文件）
* -C选项：选择解压的目的地。用于解压模式（-x），通常在解压最后写

常用例如：

压缩：

* tar -cvf test.tar 1.txt 2.txt 3.txt：将1.txt 2.txt 3.txt压缩到test.tar文件内
* tar -zcvf test.tar 1.txt 2.txt 3.txt：将1.txt 2.txt 3.txt压缩到test.tar.gz文件内，使用了gzip格式压缩

解压：

* tar -xvf test.tar：解压test.tar，将文件解压到当前目录
* tar -xvf test.tar -C /home/wyh/wyh：解压test.tar到指定目录/home/wyh/wyh
* tar -zxvf test.tar.gz -C /home/wyh/wyh：以gzip格式解压test.tar.gz到指定目录/home/wyh/wyh



zip命令：压缩zip文件

：zip [-r] 参数1 参数2 ... 参数N

* -r选项：被压缩的包含文件夹时，需要使用-r选项（和rm和cp命令一样的效果）

常用例如：

* zip test.zip a.txt b.txt c.txt：将a.txt b.txt c.txt压缩到test.zip文件内
* zip -r test.zip test1 test2 a.txt：将a.txt和两个文件夹压缩到test.zip文件内



unzip命令：解压zip文件

：unzip [-d] 参数

* -d选项：指定解压的目的地
* 参数：被解压的zip文件

常用例如：

* unzip test.zip：解压test.zip，将文件解压到当前目录
* unzip test.zip -d /home/wyh/wyh：解压test.zip到指定目录/home/wyh/wyh

【注】解压后系统存在有同名文件会直接被覆盖







# 五. 实战软件部署



## 虚拟机集群

跟着[视频](https://www.bilibili.com/video/BV1n84y1i7td?p=53&vd_source=7b27f94c21d85bcb9034952320b764f6)P53设置即可 是为了集群化而设置



配置jdk环境：Java8



当频繁的在多台服务器之间相互传输数据时方便我们传输的命令：scp

scp命令：通过SSH协议完成文件的复制。是cp命令的升级版。在不同的Linux服务器之间，通过SSH协议完成互相传输文件。

只要知晓服务器的账户和密码（或密钥）即可通过scp互传文件

：scp [-r] 参数1 参数2

* -r选项：用于复制文件夹
* 参数1：本机路径 或 远程目标路径
* 参数2：远程目标路径 或 本机路径

例如：

* scp -r /export/server/jdk root@node2:/export/server/：将本机上的jdk文件夹，以root身份复制到node2的/export/server内。账户名可以省略（使用本地当前的同名账户）
* scp -r node2:/export/server/jdk /export/server/：将远程node2的jdk文件夹，复制到本机的/export/server内



## MySQL

Linux的mysql的账户登录密码为：Wyh0920^









# 六. 脚本&自动化

# 七. 项目实战

# 八. 云平台技术