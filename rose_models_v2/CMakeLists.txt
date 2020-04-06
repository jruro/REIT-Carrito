cmake_minimum_required(VERSION 2.8.3)
project(rose_models_v2)

find_package(catkin REQUIRED COMPONENTS
  gazebo_msgs
  gazebo_ros
)
find_package(gazebo REQUIRED)
catkin_package(
  CATKIN_DEPENDS gazebo_ros gazebo_msgs)

link_directories(
  ${GAZEBO_LIBRARY_DIRS}
)

include_directories(
  include
  ${GAZEBO_INCLUDE_DIRS}
  ${GAZEBO_LIBRARY_DIRS}
)

if(CATKIN_ENABLE_TESTING)
  find_package(roslaunch REQUIRED)
  roslaunch_add_file_check(launch)
endif()

install(DIRECTORY images meshes launch rviz urdf
  DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION})
