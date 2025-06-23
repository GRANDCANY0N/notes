# Screen

**Screen**: Linux一般预装 Ubuntu 和 Centos 有命令

**screen -v**查看版本

**screen -s (+name)** 创建一个命名会话

**screen -ls** 查看所有窗口  Attached 表示有窗口在使用 Detached表示可以进入

**screen -r (+id)** 恢复到最近的窗口，可以指定id

**screen -x user/session_name** 共享窗口

ctrl +A,D 退出当前窗口

进入窗口后激活环境 选择文件位置

 **python -u density_profile_data.py > output.log 2>&1 &** (使用后可以关机)

- u 表示不启用缓存，实时输出打印信息到日志文件
- density_profile_data.py 表示python的源代码文件
- “>” 表示将打印信息重定向到日志文件
- output.log 表示输出的日志文件
- 2>&1 表示将标准错误输出转变化标准输出，可以将错误信息也输出到日志文件中

# SSH连接服务器

#### 华为 ssh huawei 

官网文档(https://support.huawei.com/enterprise/zh/doc/EDOC1100079287/10dcd668)

飞书链接(https://xadd0sgwtg.feishu.cn/docx/DNXqd7j1LoFQR7xRjK6cMgq1nje?from=from_copylink)密码：>Pm9hmsnbdVL=j+_8D

(貌似不是同一类卡，但是指令可能大差不差😓)

**watch -n 1 npu-smi info**  每秒查询所有npu设备上所有芯片的监测数据（显存）

默认 **watch  npu-smi info**   间隔两秒

**htop** 查看进程信息 内存使用情况等(单卡最好不要超过125G内存)

#### 空研院2080ti  ssh 2080ti

**nvtop** 查看gpu使用情况

# Git

怎么在本地构建代码仓库

保存服务器端的代码

## 