# ros2_install_bash_TYHuse

## 第一步打开Linux命令行，键入下面命令：
wget http://fishros.com/install -O fishros && . fishros
# Linux 与 ROS2 常用命令参考手册
https://img.shields.io/badge/License-MIT-yellow.svg
https://img.shields.io/badge/ROS2-Humble%2520%257C%2520Foxy%2520%257C%2520Galactic-blue

📋 目录
Linux 常用命令

文件与目录操作

权限管理

进程管理

网络相关

系统信息

包管理

ROS2 常用命令

环境设置

工作空间操作

包管理

节点管理

话题管理

服务管理

参数管理

动作管理

启动文件

录制与回放

接口与消息

调试工具

日志管理

常用组合命令

实用技巧

快速开始

🐧 Linux 常用命令
文件与目录操作
bash
# 列出文件
ls                # 列出当前目录内容
ls -la           # 详细列表（含隐藏文件）
ll               # ls -l 的别名（通常已定义）

# 切换目录
cd /path         # 切换到指定路径
cd ~             # 返回家目录
cd ..            # 返回上级目录
cd -             # 返回上次所在目录

# 创建与删除
mkdir dirname    # 创建目录
rmdir dirname    # 删除空目录
rm file          # 删除文件
rm -r dir        # 递归删除目录
touch file       # 创建空文件

# 复制与移动
cp source dest   # 复制文件
cp -r src dir    # 递归复制目录
mv source dest   # 移动/重命名

# 查看文件
cat file         # 显示文件内容
less file        # 分页查看文件
head -n file     # 查看前n行
tail -n file     # 查看后n行
tail -f file     # 实时跟踪文件变化
权限管理
bash
chmod +x file    # 添加执行权限
chmod 755 file   # 设置权限为rwxr-xr-x
chown user:group file  # 更改所有者和组
sudo command     # 以管理员权限执行
进程管理
bash
ps aux           # 查看所有进程
top              # 动态查看进程
htop             # 增强版top（需安装）
kill PID         # 终止进程
kill -9 PID      # 强制终止进程
pkill name       # 按名称终止进程
网络相关
bash
ping host        # 测试网络连通性
ifconfig         # 查看网络接口（旧版）
ip addr          # 查看网络接口（新版）
netstat -tulpn   # 查看端口监听情况
ssh user@host    # SSH远程连接
scp file user@host:path  # 安全复制文件
系统信息
bash
uname -a         # 查看系统信息
df -h            # 查看磁盘使用情况
du -sh dir       # 查看目录大小
free -h          # 查看内存使用
uptime           # 查看系统运行时间
包管理（Ubuntu/Debian）
bash
sudo apt update           # 更新软件包列表
sudo apt upgrade          # 升级所有软件包
sudo apt install package  # 安装软件包
sudo apt remove package   # 移除软件包
sudo apt search keyword   # 搜索软件包
🤖 ROS2 常用命令
环境设置
bash
# 设置ROS2环境（每次打开新终端都需要）
source /opt/ros/humble/setup.bash  # Humble版本
source /opt/ros/foxy/setup.bash     # Foxy版本

# 添加到.bashrc（永久生效）
echo "source /opt/ros/humble/setup.bash" >> ~/.bashrc
source ~/.bashrc
工作空间操作
bash
# 创建工作空间
mkdir -p ~/ros2_ws/src
cd ~/ros2_ws

# 构建工作空间
colcon build                    # 构建所有包
colcon build --packages-select package_name  # 构建指定包
colcon build --symlink-install  # 创建符号链接（开发模式）

# 激活工作空间
source install/setup.bash
包管理
bash
# 创建新包
ros2 pkg create <package_name> --build-type ament_cmake --dependencies rclcpp
ros2 pkg create <package_name> --build-type ament_python --dependencies rclpy

# 列出已安装包
ros2 pkg list

# 查看包信息
ros2 pkg prefix <package_name>
节点管理
bash
# 运行节点
ros2 run <package_name> <node_name>

# 列出活动节点
ros2 node list

# 查看节点信息
ros2 node info <node_name>

# 查看节点发布/订阅的话题
ros2 node info /node_name
话题管理
bash
# 列出所有话题
ros2 topic list
ros2 topic list -t          # 带类型信息

# 查看话题信息
ros2 topic info /topic_name
ros2 topic type /topic_name

# 发布消息到话题
ros2 topic pub /topic_name msg_type "data: value"

# 订阅话题消息
ros2 topic echo /topic_name

# 查看话题带宽
ros2 topic bw /topic_name

# 查看话题延迟
ros2 topic delay /topic_name
服务管理
bash
# 列出所有服务
ros2 service list
ros2 service list -t       # 带类型信息

# 调用服务
ros2 service call /service_name service_type "arguments"

# 查看服务类型
ros2 service type /service_name

# 查找使用某服务的节点
ros2 service find service_type
参数管理
bash
# 列出所有参数
ros2 param list

# 获取参数值
ros2 param get /node_name param_name

# 设置参数值
ros2 param set /node_name param_name value

# 导出参数到文件
ros2 param dump /node_name > params.yaml

# 从文件加载参数
ros2 param load /node_name params.yaml
动作管理
bash
# 列出所有动作
ros2 action list
ros2 action list -t        # 带类型信息

# 查看动作信息
ros2 action info /action_name

# 发送动作目标
ros2 action send_goal /action_name action_type "goal_value"
启动文件
bash
# 启动launch文件
ros2 launch <package_name> <launch_file>.launch.py

# 查看launch文件参数
ros2 launch <package_name> <launch_file>.launch.py --show-args
录制与回放
bash
# 录制所有话题
ros2 bag record -a

# 录制指定话题
ros2 bag record topic1 topic2

# 查看bag文件信息
ros2 bag info bag_file

# 回放bag文件
ros2 bag play bag_file

# 暂停/继续回放
ros2 bag play bag_file --pause
ros2 bag play bag_file --resume
接口与消息
bash
# 列出所有接口
ros2 interface list

# 查看接口详情
ros2 interface show interface_type

# 列出所有消息类型
ros2 msg list

# 查看消息定义
ros2 msg show message_type
调试工具
bash
# 查看系统运行状态
ros2 doctor           # 检查ROS2环境
ros2 wtf              # 诊断工具（Foxy及更早版本）

# 查看节点计算时间
ros2 run rqt_runtime_monitor rqt_runtime_monitor

# 可视化工具
rqt_graph             # 显示节点和话题图
ros2 run rviz2 rviz2  # 3D可视化工具
日志管理
bash
# 设置日志级别
ros2 service call /node_name/set_logger_level rcl_interfaces/srv/SetLoggerParameters "{logger_name: 'ros2', level: 'INFO'}"

# 查看日志
ros2 topic echo /rosout
常用组合命令
bash
# 同时运行多个节点
ros2 launch package_name launch_file.launch.py

# 监控多个话题
ros2 topic echo /topic1 & ros2 topic echo /topic2 &

# 查找节点所在包
ros2 pkg prefix --share $(ros2 pkg list | grep node_name)
💡 实用技巧
命令补全
bash
# 启用ROS2自动补全
source /opt/ros/humble/share/ros2cli/environment/ros2-argcomplete.bash
别名设置（添加到~/.bashrc）
bash
# ROS2常用别名
alias rl='ros2 launch'
alias rr='ros2 run'
alias rt='ros2 topic'
alias rs='ros2 service'
alias rn='ros2 node'
alias rp='ros2 param'
alias rb='ros2 bag'
环境变量检查
bash
# 检查ROS2环境
printenv | grep ROS

# 检查ROS_DISTRO
echo $ROS_DISTRO

# 检查ROS_VERSION
echo $ROS_VERSION
快速创建工作空间结构
bash
create_ros2_ws() {
    mkdir -p ~/$1/src
    cd ~/$1
    echo "ROS2工作空间 $1 已创建"
}
🚀 快速开始
安装ROS2（以Humble为例）
bash
# 设置locale
sudo apt update && sudo apt install locales
sudo locale-gen en_US en_US.UTF-8
sudo update-locale LC_ALL=en_US.UTF-8 LANG=en_US.UTF-8
export LANG=en_US.UTF-8

# 添加ROS2仓库
sudo apt install software-properties-common
sudo add-apt-repository universe
sudo apt update && sudo apt install curl -y
sudo curl -sSL https://raw.githubusercontent.com/ros/rosdistro/master/ros.key -o /usr/share/keyrings/ros-archive-keyring.gpg
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/ros-archive-keyring.gpg] http://packages.ros.org/ros2/ubuntu $(. /etc/os-release && echo $UBUNTU_CODENAME) main" | sudo tee /etc/apt/sources.list.d/ros2.list > /dev/null

# 安装ROS2
sudo apt update
sudo apt install ros-humble-desktop
创建第一个ROS2节点
bash
# 创建工作空间
mkdir -p ~/ros2_ws/src
cd ~/ros2_ws

# 创建包
ros2 pkg create my_first_package --build-type ament_python --dependencies rclpy

# 编写节点代码后构建
colcon build --packages-select my_first_package
source install/setup.bash

# 运行节点
ros2 run my_first_package my_first_node
📝 注意事项
版本兼容性：以上命令基于ROS2 Humble版本，其他版本可能略有差异

环境变量：每次打开新终端都需要重新source ROS2环境

工作空间：每个工作空间都需要单独source其install/setup.bash

权限问题：部分操作可能需要sudo权限，请谨慎使用

🤝 贡献指南
欢迎提交Issue和Pull Request来完善本命令手册！

📄 许可证
本项目采用 MIT 许可证 - 查看 LICENSE 文件了解详情
