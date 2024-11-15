### Installation and testing

1. In a terminal run: `sudo apt-get install ros-humble-septentrio-gnss-driver`
2. Once installed the driver can be launched by launching the launch file **rover.launch.py**: ros2 launch septentrio_gnss_driver rover.launch.py. This will launch the GPS in this terminal window.
3. To confirm this, in another terminal window, echo the ROS topics beings published by driver: `ros2 topic echo /gpsfix` [message definition](https://docs.ros.org/en/noetic/api/gps_common/html/msg/GPSFix.html) or `ros2 topic echo /navsatfix` [message deifinition](https://docs.ros.org/en/noetic/api/sensor_msgs/html/msg/NavSatFix.html). A list of additonal topics (data) can be viewed using the command: `ros2 topic list`.
4. The driver launches with the default [config file](https://github.com/PADIH-EUDALD-MASSANA/septentrio_gnss_driver/blob/master/config/rover.yaml) located at the path `/opt/ros/humble/share/septentrio_gnss_driver/config`. This file needs to be edited with sudo permissions so an easier way would be to copy its contents in another file and point to that new file when launching the driver. This makes changing different params and relaunching easier:
  `ros2 launch septentrio_gnss_driver rover.launch.py path_to_config:=/path/to/your/config.yaml`
5. To check if RTK corrections are being received, echo the relavant topics pointed to in step 3. If corrections are being received the status in these topics will have a value of `2` according to [status definition](https://docs.ros.org/en/noetic/api/sensor_msgs/html/msg/NavSatStatus.html) .
