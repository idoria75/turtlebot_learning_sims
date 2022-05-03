# Turtlebot Learning Sims

This is a repo to manage code for simulations with the turtlebot robot.

## Installing dependencies

First, configure [catkin tools](https://catkin-tools.readthedocs.io/en/latest/installing.html#installing-on-ubuntu-with-apt-get):

```bash
sudo sh \
    -c 'echo "deb http://packages.ros.org/ros/ubuntu `lsb_release -sc` main" \
        > /etc/apt/sources.list.d/ros-latest.list'
wget http://packages.ros.org/ros.key -O - | sudo apt-key add -
```

This package requires the installation of several Turtlebot packages. To install these, run:

```bash
sudo apt install ros-melodic-turtlebot3 ros-melodic-turtlebot3-bringup ros-melodic-turtlebot3-description ros-melodic-turtlebot3-gazebo ros-melodic-turtlebot3-msgs ros-melodic-turtlebot3-navigation ros-melodic-turtlebot3-simulations ros-melodic-turtlebot3-slam ros-melodic-turtlebot3-teleop ros-melodic-turtlebot3   
```

# Creating the Turtlebot Workspace

Create a new workspace for the turtlebot simulations:

```bash
cd ~/
mkdir turtlebot_ws
cd ~/turtlebot_ws
mkdir src
catkin init
catkin config --extend /opt/ros/melodic/
```

Add the Turtlebot3 Simulations package:

```bash
cd ~/turtlebot_ws/src
git clone -b melodic-devel https://github.com/ROBOTIS-GIT/turtlebot3_simulations.git
cd ..
catkin build
source devel/setup.bash
```

Add environment variables to `bashrc`:

```bash
source /home/<your_user>/turtlebot_ws/devel/setup.bash
echo "export TURTLEBOT3_MODEL=burger" >> ~/.bashrc
source ~/.bashrc
```

Launch the Turtlebot3 Simulation with an empty world:

```bash
roslaunch turtlebot3_gazebo turtlebot3_empty_world.launch
```

To run RVIZ, run in a new terminal:

```bash
roslaunch turtlebot3_gazebo turtlebot3_gazebo_rviz.launch 
```


# Notes about Gazebo

Gazebo processes usually times some time to conclude when killed. In case the terminal hangs up for a long time, just tipe the following command on a new terminal:

```
pkill gzserver && pkill gzclient
```