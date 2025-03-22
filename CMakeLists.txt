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
find_package(builtin_interfaces REQUIRED)
find_package(geometry_msgs REQUIRED)
find_package(sensor_msgs REQUIRED)

rosidl_generate_interfaces(${PROJECT_NAME}
  "action/Segments.action"
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


  # basic meassages
  "msg/Float32Stamped.msg"
  "msg/Float64Stamped.msg"
  # blockchain messages
  "msg/Block.msg"
  "msg/Chain.msg"
  "msg/Transaction.msg"
  "srv/JoinChain.srv"
  "srv/VoteChain.srv"
  "srv/UpdateChain.srv"
  # job messages
  "msg/KeyValue.msg"
  "msg/Job.msg"
  # navigation messages
  "msg/Waypoint.msg"
  "msg/Waypoints.msg"
  "msg/State.msg"
  "msg/States.msg"
  "msg/Segment.msg"
  "msg/Segments.msg"
  # line messages
  "msg/Line.msg"
  "msg/Lines.msg"
  # beacon messages
  "msg/Beacon.msg"
  "msg/Beacons.msg"
  # map messages
  "msg/GeoJson.msg"
  "msg/Cordinate.msg"
  "msg/Cordinates.msg"
  "msg/Geometry.msg"
  "msg/Feature.msg"
  "msg/Propertie.msg"
  "msg/GeoTiff.msg"
  "msg/Band.msg"
  "msg/Grid.msg"
  DEPENDENCIES nav_msgs std_msgs geometry_msgs sensor_msgs
)

if(BUILD_TESTING)
  find_package(ament_lint_auto REQUIRED)
  set(ament_cmake_copyright_FOUND TRUE)
  set(ament_cmake_cpplint_FOUND TRUE)
  ament_lint_auto_find_test_dependencies()
endif()

ament_package()
