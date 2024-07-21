# FIVE-DOF-ROBOTIC-ARM
## Installation
The package was made using [ROS2 Humble](https://docs.ros.org/en/humble/index.html)
## Dependencies
You need to have installed:
<br>
1. ros-xacro:
   ```console
   sudo apt install ros-<ros2-distro>-xacro
   ```
2. ros-joint-state-publisher:
   ```console
   sudo apt install ros-<ros2-distro>-joint-state-publisher-gui
   ```
3. gazebo-ros:
   ```console
   sudo apt install ros-<ros2-distro>-gazebo-ros-pkgs
   ```
4. ros2-control and ros2-controllers:
   ```console
   sudo apt install ros-<ros2-distro>-ros2-control ros-<ros2-distro>-ros2-controllers
   ```
4. colcon:
   ```console
   sudo apt install python3-colcon-common-extensions
   ```
5. moveit:

   [moveit installtion](https://moveit.ros.org/install-moveit2/source/)
## :hammer: Design
The design was made in fusion360 and used a [fusion2urdf](https://github.com/SpaceMaster85/fusion2urdf) exporter to obtain the urdf files needed 
## :hammer: How to build
To build the packages in this repository follow these steps:
1. `cd` into an existing or create a new [workspace](https://docs.ros.org/en/foxy/Tutorials/Beginner-Client-Libraries/Creating-A-Workspace/Creating-A-Workspace.html)
   ```console
   mkdir -p robotarm/src
   ```
2. clone this repository in the `src` folder of your workspace
   ```console
   cd robotarm/src
   ```
   ```console
   git clone https://github.com/odobot/pentabot_description.git
   ```
3. Naviage back to the workspace folder
   ```console
   cd ../
   ```
4. build the workspace using the [colcon](https://colcon.readthedocs.io/en/released/reference/verb/build.html) build tool
   ```console
   colcon build --symlink-install
   ```
5. source the `setup.bash` file
   ```console
   source install/setup.bash
   ```
6. You can add the `setup.bash` file on the bashrc script file, just open the file and add it at end:
    ```console
    gedit ~/.bashrc
    ```
    ```console
    source ~/robotarm/install/setup.bash
    ```
## :movie_camera: Rviz
To view the urdf in rviz open 3 terminals:
<br>
On the first terminal (needs to the terminal you sourced your setup.bash file in) type: 
```console
  ros2 launch pentabot_description robot_description.launch.py
  ```
Second terminal
 ```console
  rviz2
  ```
In rviz for the Fixed frame use `base_link` add RobotModel at the Displays under the robot model there is Description topic add `/robot_description`
third terminal
 ```console
  ros2 run joint_state_publisher_gui joint_state_publisher_gui
 ```

## 🎥 Gazebo
To launch your robot arm in gazebo, run:
 ```console
  ros2 launch pentabot_description robot_gazebo.launch.py
  ```
if you get an error with the launch file above, run:
 ```console
  ros2 launch pentabot_description gazebo.launch.py
 ```
## 🎥 All in one
To launch rviz2, joint_state_publisher_gui and the robot all at once use the command:
 ```console
  ros2 launch pentabot_description robot_sim.launch.py
 ```

Gazebo will be  launched haven't added the needed code for the arm to be launched in it thus you can just close Gazebo if it opens.(will be adding the code soon)
## 🎥 Intergrating Moveit
Navigate to your workspace and build the package using colcon, launch the moveit assistant:
```console
ros2 launch moveit_setup_assistant setup_assistant.launch.py
```
## Reference
https://wiki.ros.org/urdf/XML/joint .
https://moveit.picknik.ai/humble/doc/tutorials/quickstart_in_rviz/quickstart_in_rviz_tutorial.html .
http://docs.ros.org/en/kinetic/api/moveit_tutorials/html/index.html.
https://control.ros.org/master/index.html.
https://moveit.picknik.ai/main/doc/examples/setup_assistant/setup_assistant_tutorial.html.
https://classic.gazebosim.org/tutorials?tut=ros_urdf