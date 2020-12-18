cmake_minimum_required(VERSION 2.8.3)
project(movement_detection)

find_package(catkin REQUIRED COMPONENTS
  geometry_msgs
  roscpp
  rospy
  trajectory_custom_msgs
  trajectory_process_utils_srvs
)

catkin_package(
#  INCLUDE_DIRS include
#  LIBRARIES movement_detection
#  CATKIN_DEPENDS actionlib_msgs geometry_msgs roscpp rospy trajectory_custom_msgs
#  DEPENDS system_lib
)

include_directories(
# include
  ${catkin_INCLUDE_DIRS}
)
