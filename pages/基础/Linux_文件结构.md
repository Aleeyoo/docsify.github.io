[Linux 系统目录结构 | 菜鸟教程](https://www.runoob.com/linux/linux-system-contents.html)![Linux 系统目录结构](https://www.runoob.com/wp-content/uploads/2014/06/d0c50-linux2bfile2bsystem2bhierarchy.jpg)

<!-- tabs:start -->

#### **/bin <span class="tab-badge-red">重要</span>**

及 Binaries (二进制文件)<br>

存放**常用命令**。

#### **/boot**

系统启动时使用的**核心文件** (链接文件、镜像文件)。

#### **/dev**

及 Device(设备)<br>

将**外部设备**映射为文件，如 cpu 等；通过访问文件来进行访问设备。

#### **/etc：<span class="tab-badge-red">重要</span>**

及 Etcetera (等等)<br>

所有系统管理所需的**配置文件、子目录**。

#### **/home**

**用户主目录**，往下细分为每个用户的目录，以用户账号命名。

#### **/lib**

及 Library (库)<br>

系统最基本的动态链接共享库；等同于 [[Windows 系统]] 的 [[DLL 文件]]。<br>

**是所有的应用程序必要的共享库。**

#### **/lost+found**

存储系统 [[非法关机]] 后生成的文件，默认为空。

#### **/media**

系统识别一些**设备** (如：U盘、光驱...) 后，将识别到的设备挂载到该目录。

#### **/mnt**

**临时挂载别的文件系统。**<br>

例如将光驱挂载到/mnt/上，即可在该目录下浏览光驱内容。

#### **/opt**

及 optional (可选) <br>

为主机**额外安装软件**的目录；默认为空。

#### **/proc**

及 Processes (进程) <br>

一种 [[伪文件系统]] ，存储当前内核运行状态的一些列特殊文件；<br>

通过访问该目录来**获取系统信息**；且存在于**内存，可进行一些修改就行系统配置。**

#### **/root**

系统管理员的用户主目录。

#### **/sbin <span class="tab-badge-red">重要</span>**

及 Superuser Binaries (超级用户的二进制文件) <br>

存放**系统管理员使用的系统管理程序。**

#### **/selinux**

为 [[Redhat]] / [[CentOS]] 特有；**存放 selinux 相关的文件。**<br>

为一个安全机制，等同于 Windows 的防火墙，但更为复杂。

#### **/srv**

**服务启动之后所要提取的数据。**

#### **/sys**

当一个内核对象被创建的时候，对应的文件和目录也在内核对象子系统中被创建。<br>

Linux 2.6 内核安装新文件系统 [[sysfs]]<br>

集成：1. 针对进程信息的 proc 文件系统、2. 针对设备的 devfs 文件系统、3. 针对伪终端的 devpts 文件系统。

#### **/tmp**

及 temporary(临时) <br>

**存放一些临时文件。**

#### **usr**

及 unix system resources(unix 系统资源) <br>

存储**用户的应用程序、文件**；等同于 windows 下的 program files 目录。

#### **/usr/bin <span class="tab-badge-red">重要</span>**

**系统用户使用的应用程序。**

#### **/usr/sbin <span class="tab-badge-red">重要</span>**

超级用户使用的比较高级的管理程序和系统守护程序。

#### **/sur/src**

**内核源代码默认的放置目录。**

#### **/var <span class="tab-badge-red">重要</span>**

及 variable(变量) <br>

存放着在**不断扩充的东西**，比如 **日志文件**。

#### **/run**

**临时文件系统，存储系统启动以来的信息**。<br>

系统重启后，这个目录下的文件应该被删掉或清除。

<!-- tabs:end -->
