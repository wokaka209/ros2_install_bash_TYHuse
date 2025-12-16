# ros2_install_bash_TYHuse

## 第一步打开Linux命令行，键入下面命令：
wget http://fishros.com/install -O fishros && . fishros
Linux 与 ROS2 常用命令手册
Linux 常用命令
文件与目录操作   
bash
# 列出目录内容
ls -la           # 显示详细信息
ll               # 简化列表显示
ls -lh           # 人性化显示文件大小

# 切换目录
cd ~             # 返回家目录
cd ..            # 返回上级目录
cd /home/user    # 切换至指定目录

# 文件操作
cp file1 file2   # 复制文件
mv old new       # 移动/重命名
rm file          # 删除文件
rm -rf dir       # 强制删除目录

# 查看文件
cat file         # 显示文件内容
less file        # 分页查看
head -n 10 file  # 查看前10行
tail -f logfile  # 实时跟踪日志
系统管理
bash
# 进程管理
ps aux           # 查看所有进程
top              # 动态查看系统状态
kill PID         # 终止进程
pkill name       # 按名称终止

# 网络命令
ifconfig         # 查看网络配置
ping baidu.com   # 测试网络连通
netstat -tulpn   # 查看端口占用

# 系统信息
df -h            # 磁盘使用情况
free -h          # 内存使用情况
uname -a         # 系统信息
uptime           # 运行时间
包管理（Ubuntu）
bash
# 更新系统
sudo apt update
sudo apt upgrade

# 安装软件
sudo apt install package_name
sudo apt remove package_name

# 搜索软件
apt search keyword
apt show package_name
ROS2 常用命令
环境设置
bash
# 设置ROS2环境
source /opt/ros/humble/setup.bash

# 永久设置（加入.bashrc）
echo "source /opt/ros/humble/setup.bash" >> ~/.bashrc
source ~/.bashrc
工作空间管理
bash
# 创建工作空间
mkdir -p ~/ros2_ws/src
cd ~/ros2_ws

# 编译工作空间
colcon build
colcon build --packages-select package_name

# 激活工作空间
source install/setup.bash
节点操作
bash
# 运行节点
ros2 run package_name node_name

# 查看节点
ros2 node list
ros2 node info /node_name

# 启动多个节点
ros2 launch package_name launch_file.launch.py
话题管理
bash
# 查看话题
ros2 topic list
ros2 topic echo /topic_name

# 发布消息
ros2 topic pub /topic_name msg_type "data: value"

# 查看话题信息
ros2 topic info /topic_name
ros2 topic hz /topic_name
服务与参数
bash
# 查看服务
ros2 service list
ros2 service call /service_name service_type "arguments"

# 参数管理
ros2 param list
ros2 param get /node_name param_name
ros2 param set /node_name param_name value
调试工具
bash
# 可视化工具
rqt_graph        # 查看节点图
ros2 run rviz2 rviz2  # 3D可视化

# 录制与回放
ros2 bag record -a
ros2 bag play recorded_bag
常用快捷命令
bash
# 快速创建工作空间
mkdir -p ~/ros2_ws/src && cd ~/ros2_ws

# 一键编译运行
colcon build && source install/setup.bash && ros2 run package node

# 查看所有ROS2命令
ros2 --help
安装ROS2（快速方法）
bash
# 使用一键安装脚本
wget http://fishros.com/install -O fishros && bash fishros

# 或使用官方方法
sudo apt update
sudo apt install ros-humble-desktop
