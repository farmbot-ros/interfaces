cmake_minimum_required(VERSION 3.15)
project(farmbot_interfaces)

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()
cmake_policy(SET CMP0074 NEW)
set(CMAKE_EXPORT_COMPILE_COMMANDS ON)
include(FetchContent)


# find dependencies
find_package(ament_cmake REQUIRED)
find_package(rosidl_default_generators REQUIRED)
find_package(nav_msgs REQUIRED)
find_package(std_msgs REQUIRED)
find_package(geometry_msgs REQUIRED)
find_package(sensor_msgs REQUIRED)

rosidl_generate_interfaces(${PROJECT_NAME}
  "action/Nav.action"
  "action/Obstacle.action"
  "action/Waypoints.action"
  "action/Control.action"
  "srv/Reset.srv"
  "srv/Datum.srv"
  "srv/Gps2Ecef.srv"
  "srv/Ecef2Gps.srv"
  "srv/Ecef2Enu.srv"
  "srv/Enu2Ecef.srv"
  "srv/Gps2Enu.srv"
  "srv/Enu2Gps.srv"
  "srv/Threshold.srv"
  "srv/Trigger.srv"
  "srv/Value.srv"
  "srv/Spawn.srv"
  "srv/GoToField.srv"
  "srv/GetTheField.srv"
  "msg/Float32Stamped.msg"
  "msg/Float64Stamped.msg"
  "msg/Waypoints.msg"
  "msg/Waypoint.msg"
  "msg/State.msg"
  "msg/States.msg"
  "msg/Segment.msg"
  "msg/Segments.msg"
  "msg/Borders.msg"
  DEPENDENCIES nav_msgs std_msgs geometry_msgs sensor_msgs
)

if(BUILD_TESTING)
  find_package(ament_lint_auto REQUIRED)
  set(ament_cmake_copyright_FOUND TRUE)
  set(ament_cmake_cpplint_FOUND TRUE)
  ament_lint_auto_find_test_dependencies()
endif()

ament_package()
