Clone from EAI dashgo D1 branch slam_02

sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'\
sudo apt-key adv --keyserver 'hkp://keyserver.ubuntu.com:80' --recv-key C1CF6E31E6BADE8868B172B4F42ED6FBAB17C654\
sudo apt update\
sudo apt install ros-melodic-desktop-full\

echo "source /opt/ros/melodic/setup.bash" >> ~/.bashrc\
source ~/.bashrc\

sudo apt install python-rosdep python-rosinstall python-rosinstall-generator python-wstool build-essential\
sudo rosdep init\
rosdep update\

sudo usermod -a -G dialout dashgo

sudo apt-get install python-serial ros-melodic-serial g++ ros-melodic-teleop-twist-keyboard ros-melodic-move-base-msgs libghc-sdl-image-dev libsdl-image1.2-dev ros-melodic-navigation ros-melodic-slam-gmapping ros-melodic-teb-local-planner ros-melodic-yujin-ocs ros-melodic-depthimage-to-laserscan ros-melodic-pointcloud-to-laserscan

mkdir -p ~/dashgo/src\
cd dashgo/src/\
git clone https://github.com/unicorntyw/dashgo.git\
git clone https://github.com/turtlebot/turtlebot_interactions.git\

sudo sh ./dashgo/src/dashgo/dashgo_bringup/startup/create_dashgo_udev.sh

sudo apt-key adv --keyserver keys.gnupg.net --recv-key F6E65AC044F831AC80A06380C8B3A55A6F3EFCDE || sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-key F6E65AC044F831AC80A06380C8B3A55A6F3EFCDE

sudo add-apt-repository "deb http://realsense-hw-public.s3.amazonaws.com/Debian/apt-repo bionic main" -u

sudo apt-get install librealsense2-dkms librealsense2-utils librealsense2-dev librealsense2-dbg ros-melodic-realsense2-camera ros-melodic-rgbd-launch


