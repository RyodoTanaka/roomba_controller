# Roomba 500 Series Controller
![roomba](./.images/roomba.png)
This repository provides following ROS packages...
- [Roomba 500 series driver](http://github.com/Arkapravo/roomba_500_ROS_drivers)
- [Joy Controler](http://github.com/RyodoTanaka/joy_controler)

# Installation

Type following commands ...

```bash
mkdir -p <catkin_ws>/src
cd <catkin_ws>/src
catkin_init_workspace
git clone http://github.com/RyodoTanaka/roomba_controller.git
cd <catkin_ws>
wstool init src
wstool merge -t src https://raw.githubusercontent.com/RyodoTanaka/roomba_controler/master/roomba.rosinstall
wstool update -t src
rosdep install -y -r --from-paths src --ignore-src
catkin_make
export ROS_PACKAGE_PATH=$ROS_PACKAGE_PATH:<catkin_ws> >> ~/.bashrc
source ~/.bashrc
source devel/setup.bash
cd <catkin_ws>/src/roomba_500_ROS_drivers
rosmake roomba_robot
rosmake serial_communication
sudo apt-get install ros-indigo-joy
```

#####*Tips* : It is recomended to make shell script about above commands.


# Usage
- We need a permission to connect serial port. (default is /dev/ttyUSB0)
```bash
sudo chmod 777 /dev/ttyUSB0
```

- Connect Joy Controler (PS3 or PS2 controller, you can change parameters. [details](http://github.com/RyodoTanaka/joy_controler)). 

- roslaunch
```bash
roslaunch roomba_controller roomba_controller.launch
```

# Trouble Shooting
If you encounter following error ...
```bash
[ERROR] [1437553377.085503543]: Could not retrieve sensor packets.
```
The reason is bad connection.  
Please check & reentry the serial plug.
