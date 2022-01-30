# Ros的安装步骤

## 添加ros软件源

```
sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'
```

## 添加密钥

```
sudo apt-key adv --keyserver 'hkp://keyserver.ubuntu.com:80' --recv-key C1CF6E31E6BADE8868B172B4F42ED6FBAB17C654
```

## 安装ROS

```
sudo apt update
sudo apt install ros-melodic-desktop-full
```

tips:**melodic**是版本名字，根据最新的版本名改

20.02版的第三步的melodic改成noetic，即

```
sudo apt install ros-noetic-desktop-full
```

且省略了第四部初始化rosdep(可参考wiki)

## 初始化rosdep

```
sudo rosdep init
rosdep update
```

**如果失败**：

#打开hosts文件

```
sudo gedit /etc/hosts
```

\#在文件末尾添加(2021.09.02 最新ip:185.199.108.133)

```
185.199.108.133 raw.githubusercontent.com
```

## 设置环境变量

```
echo "source /opt/ros/melodic/setup.bash" >> ~/.bashrc
source ~/.bashrc
```

## 安装rosinstall

```
sudo apt install python-rosinstall python-rosinstall-generator python-wstool build-essential
```

# 另一种方法，使用rostaller

1. ## 进入https://github.com/RocShi/rostaller

2. ## 克隆仓库

   ```
   git clone https://github.com/RocShi/rostaller.git
   ```

3. ## 进入仓库目录

```
cd rostaller
```

4. ##  为脚本添加可执行权限

```
chmod +x ./run.sh
```

5. ## 运行脚本

```
./run.sh
```
