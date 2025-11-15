# Shell 脚本

> [!TIP]
> Shell 是一个用 C 语言编写的程序，shell 既是应用程序 又是一种脚本语言。<br>
> shell 命令解析器：sh ash bash<br>
> 查看系统默认解析 `echo $SHELL`<br>
> [在线练习网站。](https://www.runoob.com/try/runcode.php?filename=helloworld&type=bash)

## 调用形式
+ **直接执行（最常用）** +

  先给脚本加权限 `chmod +x script.sh`（仅首次需要）。<br>
  - **相对路径**（脚本在当前目录）：`./script.sh` <br>
  - **绝对路径**（脚本在任意目录）：`/home/user/script.sh` <br> 

+ **指定解释器执行** +

  无需给脚本加执行权限，直接用 Shell 解释器（bash、sh、zsh 等）调用，适配多解释器场景。<br>
  - **Bash** 解释器：`bash script.sh` 或 `sh script.sh` *（sh 通常是 bash 软链接）* <br>
  - **Zsh** 解释器：`zsh script.sh`<br>

  > 脚本未加执行权限、需临时切换解释器验证兼容性。

+ **source 加载执行（融入当前环境）** +

  用 source 或 . 命令调用，脚本在当前 Shell 进程中执行，变量、别名等会保留在当前环境。<br>
  - `source script.sh` 或 `. script.sh`<br>

  > 加载环境变量（如 ~/.bashrc）、脚本内定义的变量需要后续命令使用。

+ **作为命令行参数执行** +

  将脚本内容通过 -c 参数直接传给解释器，无需创建脚本文件，适合简单临时命令。<br>
  - `bash -c "echo 'Hello'; ls -l"`<br>

  > 快速执行少量命令组合，无需保存为脚本文件。

## 变量

+ **命名** +

  **命名应遵循：**
  - 只包含字母、数字和下划线，不能以数字开头
  - 避免使用 Shell 关键字
  - 使用大写字母表示常量，避免使用特殊符、空格（等号两侧避免使用空格）

+ **使用变量** +

  - 在变量名前面加美元符号 `$` 即可引用变量值。<br>
  - `echo $your_name` 或 `echo ${your_name}`<br>
  - `{ }` 适应于例如 `${skill}Script` 场景，**推荐给所有变量加上花括号**。

+ **只读变量** +

  **`readonly`**
  - 定义为只读变量，只读变量的值**不能被改变**。<br>
  - `readonly PI=3.14159` 后，`PI=3.14` 报错 `PI: readonly variable`。

+ **删除变量** +

  **`unset`**
  - 变量被删除后不能再次使用。unset 命令**不能删除只读变量**。<br>
  - `unset variable_name`


### **变量类型** 
<!-- tabs:start -->
#### **字符串变量**
  - 使用单引号 ` 或双引号 " 来定义字符串。<br>
  - `my_string='Hello, World!'`

#### **整数变量**
  - 使用 `declare` 或 `typeset` 命令来声明整数变量，如果尝试将非整数值赋给它，Shell 会尝试将其转换为整数。<br>
  - `declare -i my_int=10` 或 `typeset -i my_int=10`

#### **数组变量**
  - 整数索引数组：`my_array=(1 2 3 4 5)`
  - 关联数组：
  - `declare -A associative_array`
  - `associative_array["name"]="John"`
  - `associative_array["age"]=30`

#### **环境变量**
  - 环境变量是在 Shell 环境中定义的变量，它们对当前 Shell 进程及其子进程可见。
  - 环境变量通常用于存储系统配置、路径信息等。
  - 可以使用 `export` 命令将变量导出为环境变量。
  - 例如：`export PATH=$PATH:~/bin` 将 `~/bin` 目录添加到 `PATH` 环境变量中。

#### **特殊变量**
  - `$0` 表示脚本的名称，`$1, $2...` 等表示脚本的参数。
  - `$#` 表示传递给脚本的参数数量，`$?` 表示上一个命令的退出状态

<!-- tabs:end -->