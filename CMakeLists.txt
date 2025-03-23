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
  # "interfaces/navigation/Waypoints.action"
  # "interfaces/navigation/Segments.action"
  # "interfaces/navigation/Control.action"
  "navigation/Waypoint.msg"
  "navigation/Waypoints.msg"
  "navigation/State.msg"
  "navigation/States.msg"
  "navigation/Segment.msg"
  "navigation/Segments.msg"

  "localization/Datum.srv"
  "localization/Gps2Ecef.srv"
  "localization/Ecef2Gps.srv"
  "localization/Ecef2Enu.srv"
  "localization/Enu2Ecef.srv"
  "localization/Gps2Enu.srv"
  "localization/Enu2Gps.srv"

  "generic/Float32Stamped.msg"
  "generic/Float64Stamped.msg"
  "generic/KeyValue.msg"
  "generic/Value.srv"
  "generic/Spawn.srv"
  "generic/Trigger.srv"
  "generic/Threshold.srv"
  "generic/Reset.srv"

  "blockchain/Block.msg"
  "blockchain/Chain.msg"
  "blockchain/Transaction.msg"
  "blockchain/JoinChain.srv"
  "blockchain/VoteChain.srv"
  "blockchain/UpdateChain.srv"

  "jobs/Job.msg"
  "jobs/JobAck.msg"

  "field/Line.msg"
  "field/Lines.msg"

  "agents/Agent.msg"
  "agents/Agents.msg"

  "mapping/GeoJson.msg"
  "mapping/Cordinate.msg"
  "mapping/Cordinates.msg"
  "mapping/Geometry.msg"
  "mapping/Feature.msg"
  "mapping/Propertie.msg"
  "mapping/GeoTiff.msg"
  "mapping/Band.msg"
  "mapping/Grid.msg"
  DEPENDENCIES nav_msgs std_msgs geometry_msgs sensor_msgs
)

if(BUILD_TESTING)
  find_package(ament_lint_auto REQUIRED)
  set(ament_cmake_copyright_FOUND TRUE)
  set(ament_cmake_cpplint_FOUND TRUE)
  ament_lint_auto_find_test_dependencies()
endif()

ament_package()
