# nav2_bringup

The `nav2_bringup` package is an example bringup system for Nav2 applications. 

This is a very flexible example for nav2 bringup that can be modified for different maps/robots/hardware/worlds/etc. It is our expectation for an application specific robot system that you're mirroring `nav2_bringup` package and modifying it for your specific maps/robots/bringup needs. This is an applied and working demonstration for the default system bringup with many options that can be easily modified. 

Usual robot stacks will have a `<robot_name>_nav` package with config/bringup files and this is that for the general case to base a specific robot system off of.

Composed bringup (based on  [ROS2 Composition](https://docs.ros.org/en/galactic/Tutorials/Composition.html)) is optional for users. It can be used to compose all Nav2 nodes in a single process instead of launching these nodes separately, which is useful for embedded systems users that need to make optimizations due to harsh resource constraints. Manually composed bring up is used by default, but can be disabled by using the launch argument `use_composition:=False`.

* Some discussions about performance improvement of composed bringup could be found here: https://discourse.ros.org/t/nav2-composition/22175.
* Currently, manual composition is used in this package. Dynamic composition is more flexible than manual composition, but is not currently applied in nav2 due to various issues, you could find more details here: https://github.com/ros-planning/navigation2/issues/2147.

To use, please see the Nav2 [Getting Started Page](https://navigation.ros.org/getting_started/index.html) on our documentation website. Additional [tutorials will help you](https://navigation.ros.org/tutorials/index.html) go from an initial setup in simulation to testing on a hardware robot, using SLAM, and more. 

Note:
* gazebo should be started with both libgazebo_ros_init.so and libgazebo_ros_factory.so to work correctly.
* spawn_entity node could not remap /tf and /tf_static to tf and tf_static in the launch file yet, used only for multi-robot situations. Instead it should be done as remapping argument <remapping>/tf:=tf</remapping>  <remapping>/tf_static:=tf_static</remapping> under ros2 tag in each plugin which publishs transforms in the SDF file. It is essential to differentiate the tf's of the different robot.
