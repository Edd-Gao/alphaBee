# alphaBee
Here is the guide for setup sitl environment. I assume that your catkin workspace is ~/catkin_ws and workspace is ~/workspace
##get the PX4 firmware
Follow the guide on dev.px4.io to install the necessary toolchains on linux.type the following commands in bash.
```bash
cd ~/workspace
git clone https://github.com/PX4/Firmware.git
cd Firmware
git submodule init
git submodule update
git checkout v1.4.4 -b v1.4.4
make posix_sitl_default
```

##get the source code
In your workspace, type the following commands to get the source code.
```bash
cd workspace
git clone https://github.com/gaochangyu/alphaBee.git
cd alphaBee
git submodule init
git submodule update
git checkout indigo-dev
```

##ROS installation
The current sitl software works on Ubuntu 14.04 with ROS indigo.

1. follow the guide on to install ros indigo on your computer. Better not use virtual machine because the simulation is resource hunger.

2. setup a soft link in your catkin workspace to the source.
```bash
cd catkin_ws
ln -s ~/workspace/alphaBee/src
cd src
catkin_init_workspace
cd ..
catkin_make
```

##setup shell environment
if you are using bash, append the following content to the end of ~/.bashrc
```bash
source ~/catkin_ws/devel/setup.bash
source ~/workspace/Firmware/integrationtests/setup_gazebo_ros.bash ~/workspace/Firmware
```

##test
open a new terminal and type:
`roslaunch swarm_sitl_launcher single_drone.launch`

