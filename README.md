# iai_table_robot_bringup

## Setup workspace

```
source /opt/ros/kinetic/setup.bash         # start using ROS kinetic
mkdir -p ~/table_robot_ws/src              # create directory for workspace
cd ~/table_robot_ws                        # go to workspace directory
catkin init                                # init workspace
cd src                                     # go to source directory of workspace
wstool init                                # init rosinstall
wstool merge https://raw.githubusercontent.com/code-iai/iai_table_robot_bringup/master/rosinstall/driver_only.rosinstall
                                           # update rosinstall file
wstool update                              # pull source repositories
rosdep install --ignore-src --from-paths . # install dependencies available through apt
touch iai_robot_drivers/omni_ethercat/CATKIN_IGNORE		   
touch iai_robot_drivers/igh_eml/CATKIN_IGNORE				   
cd ..                                      # go to workspace directory
catkin build                               # build packages
source ~/table_robot_ws/devel/setup.bash   # source new overlay
```

To start the robot:
```
roslaunch iai_table_robot_bringup bringup.launch
```