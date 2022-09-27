
# Installation steps for ROS and PX4 Environment

This Installation will help to set up the environment to start running simulations in Gazebo using ROS and PX4 firmware. The Firmware provides launch files to run a simulation with single or multiple drones.

## Screenshots

![Multi-Drone Shots](https://github.com/Airosspace/ROS_PX4_Installation/blob/main/images/image1.png)\
![Multi-Drone GCS Swarm Operation](https://github.com/Airosspace/ROS_PX4_Installation/blob/main/images/iamge2.png)

## Installation
You will need a clean installation of Ubuntu 20 on your computer.\
First install Git for Cloning the repositories.
```bash
    sudo apt update
    sudo apt upgrade
    sudo apt install git
```
Next clone the PX4 Repository using the command Below.
```bash
    git clone https://github.com/PX4/Firmware.git --recursive
```
Now change to the required directory and run this bash command.
```bash
    cd Firmware
    bash ./Tools/setup/ubuntu.sh
```
After completion of the above executed command, You need to reboot the computer using the command below.
```bash
    sudo reboot now
```
After Rebooting the computer and open a terminal and run the following command.
```bash
    wget https://raw.githubusercontent.com/ktelegenov/sim_ros_setup_noetic/main/ubuntu_sim_ros_noetic.sh
    bash ubuntu_sim_ros_noetic.sh
```
Close the terminal and open it again and Run the Commands for ROS Installation to take place
```bash
    cd src/Firmware
    git submodule update --init --recursive
    DONT_RUN=1 make px4_sitl_default gazebo
```
Now we need to source the path variables into the bashrc file.
```bash
    source Tools/simulation/gazebo/setup_gazebo.bash $(pwd) $(pwd)/build/px4_sitl_default
    export ROS_PACKAGE_PATH=$ROS_PACKAGE_PATH:$(pwd):$(pwd)/Tools/sitl_gazebo
```
Close the terminal and open up a new one and run the below command
```bash
    gedit ~/.bashrc
```
It will open a text file and add these path lines at the last line of the document.
```bash
    source ~/src/Firmware/Tools/simulation/gazebo/setup_gazebo.bash ~/src/Firmware ~/src/Firmware/build/px4_sitl_default
    export ROS_PACKAGE_PATH=$ROS_PACKAGE_PATH:~/src/Firmware
    export ROS_PACKAGE_PATH=$ROS_PACKAGE_PATH:~/src/Firmware/Tools/simulation/gazebo/sitl_gazebo
    export GAZEBO_PLUGIN_PATH=$GAZEBO_PLUGIN_PATH:/usr/lib/x86_64-linux-gnu/gazebo-9/plugins
```
Now All necessary packages and dependencies are installed properly and now we are ready to execute the launch files.
```bash
    cd src/Firmware
    roslaunch px4 multi_uav_mavros_sitl.launch
```
## Acknowledgements

 - [our Website](https://airosspace.com/)
 - [LinkedIn Profile](https://twitter.com/airosspace)
 - [For Video Tutorial use this Link](https://youtube.com/channel/UCjYW5HZyEUAJd96KT5pJPxw)
## Authors

- [@Vasanth Raj](https://github.com/vasantharajr)
- [@Abisheke Selvam](https://www.github.com/abisheke-rgb)


## License

[AIROSSPACE](https://choosealicense.com/licenses/mit/)


![Logo](https://github.com/Airosspace/ROS_PX4_Installation/blob/main/images/logo.png)

