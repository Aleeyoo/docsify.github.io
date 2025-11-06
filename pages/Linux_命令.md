## 帮助命令

<!-- tabs:start -->

#### **help命令**

语法格式： ==命令 --help==
作用: 查看某个命令的帮助信息

> 示例:
> ls --help     查看ls命令的帮助信息
> netstat --help    查看netstat命令的帮助信息

#### **man命令**

语法格式： ==man 命令==
作用: 查看某个命令的帮助手册

> 示例:
> man ls        #查看ls命令的帮助手册
> man netstat   #查看netstat命令的帮助手册

<!-- tabs:end -->

## 路径切换及查看

<!-- tabs:start -->

#### **cd 命令**

语法格式：==cd 目录 ==
作用：切换到指定目录

> 示例:
> cd /opt       切换到 /opt 目录下
> cd ~          切换到用户目录
> cd -          切换到上一次访问的目录
> cd ..         切换到上级目录

#### **pwd 命令**

语法格式：==pwd==
作用：查看当前所在路径

> 示例:
> pwd           查看当前路径，会将当前路径回显

#### **ls 命令**

语法格式：==ls [-la] [文件 / 目录]==
作用：查看当前路径下的文件和目录，若指定文件或目录，则仅查看该目标

> 示例:
> ls            查看当前路径下所有的文件或目录
> ls -l         查看当前路径下所有文件和目录的详细信息
> ls -a         查看当前路径下所有文件和目录，包含隐藏文件
> ls -l a.log   查看当前路径下 a.log 文件的详细信息

#### **find 命令**

语法格式：==find [路径] [参数] [匹配模式]==
作用：根据给定的路径和表达式查找文件或目录

> 示例:
> find /-name "*.txt"    查询根目录下所有以.txt 结尾的文件
> find /test -perm 644    查询 /test 目录下权限为 644 的所有文件
> find . -type f          查询当前目录下所有的文件
> find . -type f -name "abc"  查询当前目录下名称包含 abc 字符的所有文件
> find . -type f | sort   查询当前目录下所有文件并排序
> find . -type d          查询当前目录下所有目录
> find . -size 10M        查询当前目录下大小为 10M 的文件

<!-- tabs:end -->

## 文件目录基本操作

<!-- tabs:start -->

#### **touch 命令**

语法格式：==touch 文件名 ==
作用：创建一个文件

> 示例:
> touch a.log   创建一个 a.log 文件

#### **ln 命令**

语法格式：
==ln 源文件名 硬链接文件名 ==
==ln -s 源文件名 软链接文件名 ==
作用：创建文件链接

> 示例:
> ln a.txt a.txt.link     为 a.txt 创建硬链接文件 a.txt.link
> ln -s a.txt a.txt.link  为 a.txt 创建软链接文件
> 备注：软链接类似 Windows 快捷方式，删除软链接不影响源文件；硬链接与源文件占用同一磁盘空间，修改任一文件内容会同步变更

#### **mkdir 命令**

语法格式：==mkdir 目录名 ==
作用：创建目录

> 示例:
> mkdir test              创建 test 目录
> mkdir -p test           若 test 不存在则创建，存在则不操作
> mkdir -p test/a/b       递归创建 test/a/b 目录结构

#### **rm 命令**

语法格式：==rm [-rf] 文件 | 目录 ==
作用：删除文件或目录

> 示例:
> rm a.txt                删除 a.txt，删除前询问
> rm -f a.txt             直接删除 a.txt，不询问
> rm -r test              删除 test 目录，删除前询问
> rm -rf test             直接删除 test 目录，不询问
> 备注：删除操作不可逆，需谨慎使用

#### **mv 命令**

语法格式：==mv 源文件 | 目录 目标文件 | 目标目录 ==
作用：重命名文件 / 目录或移动文件 / 目录到目标位置

> 示例:
> mv a.txt b.txt          将 a.txt 重命名为 b.txt
> mv a.txt test/          将 a.txt 移动到 test 目录下
> mv abc bcd              将目录 abc 重命名为 bcd
> mv abc bcd/             将 abc 目录移动到 bcd 目录下

#### **cp 命令**

语法格式：==cp [-rf] 源文件 | 目录 目标文件 | 目录 ==
作用：拷贝文件或目录到指定位置

> 示例:
> cp a.txt b.txt          拷贝 a.txt 为 b.txt，若 b.txt 存在则提示是否覆盖
> cp -f a.txt b.txt       拷贝 a.txt 为 b.txt，强制覆盖已有文件
> cp -r abc bcd           拷贝 abc 目录为 bcd，若 bcd 存在则提示是否覆盖
> cp -rf abc bcd          拷贝 abc 目录为 bcd，强制覆盖已有目录

<!-- tabs:end -->

## 文件压缩与解压缩

<!-- tabs:start -->

#### **zipinfo 命令**

语法格式：==zipinfo zip 文件 ==
作用：查看 zip 压缩文件内的信息

> 示例:
> zipinfo abc.zip         查看 abc.zip 内的文件信息
> zipinfo -v abc.zip      显示 abc.zip 内每个文件的详细信息

#### **zip 命令**

语法格式：==zip 压缩文件 文件 | 目录 ==
作用：将目标文件或目录压缩为 zip 格式

> 示例:
> zip a.zip a.txt         将 a.txt 压缩为 a.zip
> zip a.zip test/         将 test 目录下所有文件和目录压缩到 a.zip

#### **gzip 命令**

语法格式：==gzip [-d] 文件 | 目录 ==
作用：压缩文件 / 目录或解压缩 gzip 格式文件

> 示例:
> gzip a.txt              将 a.txt 压缩为 a.txt.gz，压缩后源文件消失
> gzip -d a.txt.gz        解压 a.txt.gz 文件

#### **unzip 命令**

语法格式：==unzip 压缩文件 ==
作用：解压缩 zip 格式文件

> 示例:
> unzip a.zip             解压 a.zip 到当前目录
> unzip a.zip -d test/    解压 a.zip 到 test 目录下

#### **gunzip 命令**

语法格式：==gunzip 压缩文件 ==
作用：解压 gzip 格式压缩文件

> 示例:
> gunzip a.txt.gz         解压 a.txt.gz
> gunzip test.tar.gz      解压 test.tar.gz

#### **tar 命令**

语法格式：==tar [-c|xzvf] 文件 | 压缩文件 ==
作用：归档并压缩文件，或解压归档压缩文档

> 示例:
> tar -cvzf a.tar.gz a.txt  将 a.txt 压缩归档为 a.tar.gz
> tar -xvzf a.tar.gz .      解压 a.tar.gz 到当前目录

<!-- tabs:end -->

## 文件传输

<!-- tabs:start -->

#### **tftp 命令**

语法格式：==tftp 远程主机 ==
作用：连接远程主机，实现文件上传或下载

> 示例:
> tftp 192.168.1.100      连接远程主机 192.168.1.100
> get a.txt               从远程主机下载 a.txt 文件
> put a.txt               向远程主机上传 a.txt 文件

#### **curl 命令**

语法格式：==curl url==
作用：下载文件或发送 HTTP 协议请求

> 示例:
> curl http://www.baidu.com  向百度发送 HTTP 请求并显示响应
> curl -o baidu.html http://www.baidu.com  将请求结果保存到 baidu.html

#### **scp 命令**

语法格式：==scp 远程主机账号 @远程 IP 地址：源路径 本地目录 ==
作用：登录远程主机拷贝文件或目录到本地

> 示例:
> scp root@192.168.12.11:/soft/test.tar.gz/tools/  拷贝远程文件到本地 /tools 目录
> scp root@192.168.12.11:/soft//tools/             拷贝远程 soft 目录到本地 /tools 目录

#### **rcp 命令**

语法格式：==rcp 源文件 | 目录 目标主机：目标路径 ==
作用：实现远程主机间的文件或目录拷贝

> 示例:
> rcp test 192.168.128.169:/test  拷贝当前目录下的 test 到目标主机的 /test 目录
> rcp root@192.168.128.169:./test/test  复制远程目录到本地 /test 目录
> 
> <!-- tabs:end -->

## 文件属性查看

<!-- tabs:start -->

#### **file 命令**

语法格式：==file 文件名 ==
作用：查看文件的类型

> 示例:
> file a.txt              查看 a.txt 的文件类型
> file abc                查看 abc 的文件类型

#### **du 命令**

语法格式：==du [-h] 文件名 ==
作用：查看文件或目录的大小

> 示例:
> du a.txt                查看 a.txt 的大小，默认以 KB 为单位
> du -h a.txt             查看 a.txt 的大小，以易读单位（如 M、G）显示

<!-- tabs:end -->

## 文件目录权限设置

<!-- tabs:start -->

#### **chmod 命令**

语法格式：
==chmod [u/g/o/a][+/-/=] rwx 文件 / 目录 ==
==chmod 数字 文件 / 目录 ==
作用：为文件或目录设置访问权限（u = 所有者，g = 所属组，o = 其他用户，a = 所有用户；+ 增权，- 减权，= 定权）

> 示例:
> chmod a=rw a.txt        为所有用户设置 a.txt 的读写权限
> chmod 644 a.txt         以数字方式设置权限（所有者读 + 写，其他读）

<!-- tabs:end -->

## 文本内容查看

<!-- tabs:start -->

#### **cat 命令**

语法格式：==cat 文件名 ==
作用：查看文本文件内容，一次性全部显示

> 示例:
> cat a.txt               显示 a.txt 的全部内容

#### **more 命令**

语法格式：==more 文件名 ==
作用：分页显示文件内容，按 Enter 键继续查看

> 示例:
> more a.txt              分页显示 a.txt 内容，若文件不足一页则全部显示

#### **tail 命令**

语法格式：
==tail 文件名 ==
==tail -n 数量 文件名 ==
==tail -f 文件名 ==
作用：查看文本文件尾部内容，支持实时监控

> 示例:
> tail a.txt              查看 a.txt 的尾部内容
> tail -n 2 a.txt         显示 a.txt 的最后两行
> tail -f a.txt           实时监控 a.txt 的内容更新

#### **head 命令**

语法格式：
==head 文件名 ==
==head -n 数量 文件名 ==
作用：查看文本文件头部内容

> 示例:
> head a.txt              查看 a.txt 的头部内容
> head -n 2 a.txt         显示 a.txt 的前两行

<!-- tabs:end -->

## 文本内容筛选过滤

<!-- tabs:start -->

#### **grep 命令**

语法格式：==grep [选项] [模式] 文件 ==
作用：文本搜索工具，按指定模式匹配行

> 示例:
> grep "aaa" a.txt        从 a.txt 中搜索包含 "aaa" 的行
> grep -v "aaa" a.txt     从 a.txt 中搜索不包含 "aaa" 的行
> grep -n "aaa" a.txt     搜索包含 "aaa" 的行并显示行号
> grep -i "aaa" a.txt     忽略大小写搜索包含 "aaa" 的行
> grep -e "a*" a.txt      搜索匹配 "a" 字符任意次数的行
> ps -ef | grep "mysql"   查看 mysql 相关进程

#### **sed 命令**

语法格式：==sed [选项] 脚本 文件名 ==
作用：流式文本编辑工具

> 示例:
> sed -n '2p' a.txt       显示 a.txt 的第二行内容
> sed '3,5d' a.txt        输出删除第 3-5 行后的内容（源文件不变）
> sed '/aaa/d' a.txt      输出删除包含 "aaa" 行后的内容（源文件不变）

#### **awk 命令**

语法格式：==awk [选项] ' 脚本 ' 文件 ==
作用：文本分析和处理工具

> 示例:
> awk '{print $5}' a.txt  显示a.txt中每行的第5个字段
> awk 'NR <=2 {print $1,$3,$5}' a.txt  显示前两行的第 1、3、5 字段
> awk '/^d/ {print $1,$9}' a.txt  显示以 "d" 开头行的第 1、9 字段

#### **cut 命令**

语法格式：==cut [选项] 文件 ==
作用：剪切文本中的指定字符或字段

> 示例:
> cut -c 1-3 a.txt        输出每行的第 1-3 个字符
> cut -f4 -d" " a.txt     以空格为分隔符，显示每行的第 4 个字段

#### **col 命令**

语法格式：==col [选项] 文件 ==
作用：过滤文本中的控制字符

> 示例:
> man ls | col -b > ls_help  过滤 ls 手册中的控制字符并保存到 ls_help 文件

<!-- tabs:end -->

## 文本编辑、输出到文本文件

<!-- tabs:start -->

#### **vi/vim 命令**

语法格式：==vi 文件名 == / ==vim 文件名 ==
作用：文本编辑工具（vim 是 vi 的增强版）

> 示例:
> vi a.txt                用 vi 编辑 a.txt 文件
> vim a.txt               用 vim 编辑 a.txt 文件

#### **> 命令**

语法格式：== 命令 > 文件名 ==
作用：将命令输出重定向到文件，覆盖原有内容（文件不存在则创建）

> 示例:
> ll > a.txt              将 ls -l 的输出保存到 a.txt（覆盖原有内容）
> cat a.txt > b.txt       将 a.txt 的内容覆盖到 b.txt

#### **>> 命令**

语法格式：== 命令 >> 文件名 ==
作用：将命令输出追加到文件尾部（文件不存在则创建）

> 示例:
> ll >> a.txt             将 ls -l 的输出追加到 a.txt 尾部
> cat a.txt >> b.txt      将 a.txt 的内容追加到 b.txt 尾部

#### **tee 命令**

语法格式：== 命令 | tee 文件名 ==
作用：将命令输出同时显示在终端和保存到文件（文件不存在则创建）

> 示例:
> cat a.txt | tee b.txt   将 a.txt 的内容显示在终端并保存到 b.txt

<!-- tabs:end -->

## 文本内容处理

<!-- tabs:start -->

#### **join 命令**

语法格式：==join 文件 1 文件 2==
作用：按相同字段连接两个文件的行

> 示例:
> join a.txt b.txt        连接两个文件中第一字段相同的行

#### **split 命令**

语法格式：==split [选项] 文件 ==
作用：将一个文件分割成多个小文件

> 示例:
> split -l 5 c.txt        按每 5 行分割 c.txt 文件

#### **uniq 命令**

语法格式：==uniq [选项] 文件 ==
作用：去除文本中相邻的重复行

> 示例:
> uniq d.txt              去除 d.txt 中相邻的重复行
> uniq d.txt | sort       去除重复行并排序

#### **sort 命令**

语法格式：==sort [选项] 文件 ==
作用：对文本内容进行排序

> 示例:
> sort a.txt              对 a.txt 内容按默认规则升序排序
> sort -r a.txt           对 a.txt 内容降序排序
> uniq d.txt | sort -r    去除重复行并降序排序

#### **paste 命令**

语法格式：==paste 文件 1 文件 2 ...==
作用：合并多个文件的列

> 示例:
> paste a.txt b.txt       合并 a.txt 和 b.txt 的列并显示

<!-- tabs:end -->

## 用户增删改、用户密码设置

<!-- tabs:start -->

#### **useradd 命令**

语法格式：==useradd [选项] 新用户 ==
作用：创建新用户

> 示例:
> useradd test            创建 test 用户
> useradd -d /home/test test  创建 test 用户并指定家目录为 /home/test
> useradd -u 666 test     为 test 用户指定 UID 为 666

#### **adduser 命令**

语法格式：==adduser [选项] 新用户 ==
作用：创建新用户（与 useradd 功能一致）

> 示例:
> adduser test            创建 test 用户
> adduser -d /home/test test  创建 test 用户并指定家目录为 /home/test
> adduser -u 666 test     为 test 用户指定 UID 为 666

#### **userdel 命令**

语法格式：==userdel [选项] 用户 ==
作用：删除用户

> 示例:
> userdel test            删除 test 用户
> userdel -r test         删除 test 用户及其家目录

#### **usermod 命令**

语法格式：==usermod [选项] 用户 ==
作用：修改用户属性

> 示例:
> usermod -l test1 test   将用户 test 重命名为 test1
> usermod -d /home/test00 test  修改 test 用户的家目录为 /home/test00
> usermod -L test         锁定 test 用户的密码
> usermod -U test         解锁 test 用户的密码

#### **passwd 命令**

语法格式：==passwd 用户 ==
作用：修改用户密码（执行后按提示输入新密码）

> 示例:
> passwd test             修改 test 用户的密码

<!-- tabs:end -->

## 组的增删改

<!-- tabs:start -->

#### **groupadd 命令**

语法格式：==groupadd [选项] 用户组 ==
作用：创建新用户组

> 示例:
> groupadd test           创建 test 用户组
> groupadd -g 9999 test   创建 test 用户组并指定 GID 为 9999

#### **groupdel 命令**

语法格式：==groupdel 用户组 ==
作用：删除用户组

> 示例:
> groupdel test           删除 test 用户组

#### **groupmod 命令**

语法格式：==groupmod [选项] 用户组 ==
作用：修改用户组属性

> 示例:
> groupmod -n root test   将 test 用户组重命名为 root

<!-- tabs:end -->

## 文件设置用户权限、切换用户

<!-- tabs:start -->

#### **chown 命令**

语法格式：==chown [用户][: 用户组] 文件 | 目录 ==
作用：修改文件或目录的所有者和 / 或所属组

> 示例:
> chown root /test/a.txt  将 a.txt 的所有者设置为 root
> chown root:root /test/a.txt  将 a.txt 的所有者和所属组均设为 root
> chown -R test:test *    将当前目录下所有文件的所有者和所属组设为 test

#### **su 命令**

语法格式：==su [-] 用户 ==
作用：切换当前登录用户

> 示例:
> su test                 切换到 test 用户（保留当前环境变量）
> su - test               切换到 test 用户并加载其环境变量
> 备注：首次切换到其他用户需输入目标用户密码

<!-- tabs:end -->

## 进程管理、系统资源监控

<!-- tabs:start -->

#### **ps 命令**

语法格式：==ps [参数]==
作用：显示系统当前运行的进程状态

> 示例:
> ps -ef                  显示所有进程的详细信息
> ps -aux                 显示所有进程的详细信息（BSD 风格）
> ps -ef | grep mysql     查看 mysql 相关进程
> ps -u root              显示 root 用户的所有进程

#### **kill 命令**

语法格式：==kill [参数] 进程 ID==
作用：终止指定进程

> 示例:
> kill 319877             终止进程 ID 为 319877 的进程
> kill -9 319877          强制终止进程 ID 为 319877 的进程

#### **top 命令**

语法格式：==top [参数]==
作用：实时显示系统进程的资源占用情况（CPU、内存等）

> 示例:
> top                     实时监控进程资源占用
> top -n 5                动态更新 5 次后退出
> top -d 5                每隔 5 秒更新一次监控信息

#### **vmstat 命令**

语法格式：==vmstat [参数]==
作用：显示系统虚拟内存状态

> 示例:
> vmstat                  显示虚拟内存基本信息
> vmstat -s               以列表形式显示虚拟内存详细信息
> vmstat 2                每隔 2 秒刷新一次虚拟内存信息

#### **free 命令**

语法格式：==free [参数]==
作用：查看系统内存使用情况

> 示例:
> free                    显示内存信息（默认 KB 单位）
> free -m                 以 MB 单位显示内存信息
> free -g                 以 GB 单位显示内存信息

#### **df 命令**

语法格式：==df [参数] [分区]==
作用：查看磁盘分区的空间占用情况

> 示例:
> df                      查看所有分区的磁盘占用情况
> df -h                   以易读单位显示磁盘占用情况
> df /dev/shm             查看 /dev/shm 挂载点的磁盘使用情况

#### **fdisk 命令**

语法格式：==fdisk [参数]==
作用：磁盘分区管理工具

> 示例:
> fdisk -l                查看系统所有磁盘分区信息

#### **netstat 命令**

语法格式：==netstat [参数]==
作用：显示系统网络连接、端口等网络信息

> 示例:
> netstat                 查看所有网络连接信息
> netstat -an | grep 3306 查看 3306 端口的使用情况

<!-- tabs:end -->

## 服务管理

<!-- tabs:start -->

#### **service 命令**

语法格式：==service 服务名 [操作]==
作用：管理系统服务（启动、停止、重启等）

> 示例:
> service --status-all    查看所有服务的运行状态
> service mysql start     启动 mysql 服务
> service mysql stop      停止 mysql 服务
> service mysql restart   重启 mysql 服务

#### **chkconfig 命令**

语法格式：==chkconfig [参数] 服务名 ==
作用：管理系统服务的运行级别（设置自启等）

> 示例:
> chkconfig -list         显示所有服务在各运行级的状态
> chkconfig --add httpd   添加 httpd 服务到系统服务列表
> chkconfig --del httpd   从系统服务列表删除 httpd 服务

<!-- tabs:end -->

## 网络管理

<!-- tabs:start -->

#### **ifconfig 命令**

语法格式：==ifconfig [网络设备] [参数]==
作用：查看或配置网络设备（IP、MAC 地址等）

> 示例:
> ifconfig                查看所有网络设备的配置信息
> ifconfig eth0 down      关闭 eth0 网卡
> ifconfig eth0 up        开启 eth0 网卡
> ifconfig eth0 hw ether 00:AA:BB:CC:DD:EE  修改 eth0 的 MAC 地址
> ifconfig eth0 add 32ffe:3840:320:2007::2/64  为 eth0 配置 IPv6 地址
> ifconfig eth0 del 32ffe:3840:320:2007::2/64  删除 eth0 的 IPv6 地址
> ifconfig eth0 192.168.128.169  修改 eth0 的 IP 地址
> ifconfig eth0 192.168.128.169 netmask 255.255.255.0  修改 IP 和子网掩码
> ifconfig eth0 192.168.1.56 netmask 255.255.255.0 broadcast 192.168.1.255  修改 IP、子网掩码和广播地址

#### **ping 命令**

语法格式：==ping [参数] IP 地址 / 域名 ==
作用：测试网络连通性

> 示例:
> ping 192.168.12.12      测试与 192.168.12.12 的连通性
> ping www.baidu.com      测试与百度的连通性
> ping -c 4 www.baidu.com 只发送 4 个 ping 包
> ping -c 4 -i 2 www.baidu.com  发送 4 个 ping 包，间隔 2 秒

#### **systemctl 命令**

语法格式：==systemctl [操作] 服务名 ==
作用：系统服务管理（适用于 systemd 系统）

> 示例:
> systemctl status httpd.service  查看 httpd 服务状态
> systemctl start httpd.service   启动 httpd 服务
> systemctl stop httpd.service    停止 httpd 服务
> systemctl restart httpd.service 重启 httpd 服务
> systemctl status firewalld      查看防火墙状态
> systemctl start firewalld       开启防火墙
> systemctl stop firewalld        关闭防火墙

#### **firewall-cmd 命令**

语法格式：==firewall-cmd [参数]==
作用：防火墙端口管理（firewalld 服务相关）

> 示例:
> firewall-cmd --state    查看防火墙运行状态
> firewall-cmd --zone=public --list-ports  查看 public 区域放行的端口
> firewall-cmd --reload   重新加载防火墙配置
> firewall-cmd --query-port=8888/tcp  查询 8888/tcp 端口是否开放
> firewall-cmd --add-port=8888/tcp   临时开放 8888/tcp 端口
> firewall-cmd --permanent --remove-port=123/tcp  永久关闭 123/tcp 端口

<!-- tabs:end -->

## 安装更新配置

<!-- tabs:start -->

#### **yum 命令**

语法格式：==yum [操作] [软件包名]==
作用: RPM 包管理器，用于软件安装、卸载、更新等

> 示例:
> yum install mysql       安装 mysql 软件包
> yum remove mysql        卸载 mysql 软件包
> yum clean all           清除 yum 缓存目录下的安装包
> yum update              更新系统所有已安装软件包
> yum update mysql        仅更新 mysql 软件包
> yum info mysql          显示 mysql 软件包的详细信息
> yum list mysql          显示 mysql 软件包的安装状态
> yum list                显示所有已安装和可安装的软件包

#### **sh 命令**

语法格式：==sh [参数] 脚本文件 ==
作用：执行 shell 脚本文件

> 示例:
> sh a.sh                 运行 a.sh 脚本文件
> sh -x a.sh              运行 a.sh 脚本并显示调试信息

<!-- tabs:end -->

## 环境变量

<!-- tabs:start -->

#### **set 命令**

语法格式：==set [参数]==
作用：显示或设置当前 shell 的变量

> 示例:
> abcd=100                定义变量 abcd 的值为 100
> set | grep abcd         查看变量 abcd 的值

#### **unset 命令**

语法格式：==unset 变量名 ==
作用：删除 shell 变量

> 示例:
> abcd=100                定义变量 abcd
> unset abcd              删除变量 abcd

#### **env 命令**

语法格式：==env [参数] [变量名 = 值]==
作用：显示或设置系统环境变量

> 示例:
> env                     显示当前所有环境变量
> env abcd=10             临时定义环境变量 abcd=10
> env -u abcd             删除已定义的环境变量 abcd

#### **export 命令**

语法格式：==export [变量名 = 值]==
作用：设置环境变量（全局有效）

> 示例:
> export                  显示当前所有导出的环境变量
> export abcd=101         定义全局环境变量 abcd=101

<!-- tabs:end -->

## 重启与关机

<!-- tabs:start -->

#### **shutdown 命令**

语法格式：==shutdown [参数]==
作用：关闭或重启系统

> 示例:
> shutdown -h now         立即关机
> shutdown -r now         立即重启
> shutdown -h 22:30       设定 22:30 关机

#### **reboot 命令**

语法格式：==reboot==
作用：重启计算机

> 示例:
> reboot                  立即重启系统

#### **poweroff 命令**

语法格式：==poweroff==
作用：关闭计算机及电源

> 示例:
> poweroff                立即关闭系统和电源

#### **halt 命令**

语法格式：==halt [参数]==
作用：关闭操作系统

> 示例:
> halt                    关闭系统
> halt -p                 关闭系统和电源（等同于 poweroff）
> halt -f                 强制关闭系统

#### **exit 命令**

语法格式：==exit==
作用：退出当前登录的 shell

> 示例:
> exit                    退出当前 shell 会话

<!-- tabs:end -->

## 查看系统信息

<!-- tabs:start -->

#### **uname 命令**

语法格式：==uname [参数]==
作用：显示系统内核、架构等相关信息

> 示例:
> uname                   显示当前操作系统名称
> uname -an               显示系统详细信息（内核版本、主机名、架构等）
> uname -r                显示内核版本号
> uname -i                显示系统硬件架构

#### **date 命令**

语法格式：==date [参数] [日期时间字符串]==
作用：显示或设置系统日期和时间

> 示例:
> date                    查看当前系统日期和时间
> date -s "2021-04-04 22:38:56"  设置系统时间为 2021-04-04 22:38:56

#### **last 命令**

语法格式：==last [参数]==
作用：显示最近用户或终端的登录记录

> 示例:
> last                    显示最近的用户登录情况

#### **history 命令**

语法格式：==history [参数]==
作用：查看当前用户的历史输入命令

> 示例:
> history                 查看所有历史输入命令
> history | grep "sed"    查看包含 "sed" 的历史命令
> history -5              查看最近 5 条历史命令

#### **who 命令**

语法格式：==who [参数]==
作用：查看当前登录系统的用户信息

> 示例:
> who                     查看当前登录用户的基本信息
> who -H                  带标题显示登录用户信息
> who -b                  显示系统最近的启动时间

<!-- tabs:end -->

## 定时任务、运行管理员权限、其他

<!-- tabs:start -->

#### **crontab 命令**

语法格式：==crontab [参数]==
作用：管理用户的定时任务（任务调度）

> 示例:
> crontab -l              查看当前用户的定时任务列表
> crontab -e              编辑当前用户的定时任务（打开编辑器编写）
> 备注：定时任务格式为：minute (0-59) hour (0-23) day (1-31) month (1-12) week (0-7) command，无设置项用*填充
> *举例：* * 1 * * tar -czvf bk.tar.gz/log_backup  每月 1 日的每分钟执行一次日志归档备份

#### **sudo 命令**

语法格式：==sudo 命令 ==
作用：以管理员（root）权限执行命令（非 root 用户使用）

> 示例:
> sudo mkdir abc          以管理员权限创建 abc 目录

#### **clear 命令**

语法格式：==clear==
作用：清空终端屏幕（等同于快捷键 Ctrl+L）

> 示例:
> clear                   清空当前终端屏幕内容

#### **echo 命令**

语法格式：==echo [内容 / 变量]==
作用：输出指定内容或变量值

> 示例:
> echo $abc               输出变量 abc 的值（需提前定义 abc）
> echo `pwd`              执行 pwd 命令并输出其结果（显示当前路径）
> echo "Hello Linux"      输出字符串 "Hello Linux"

<!-- tabs:end -->




