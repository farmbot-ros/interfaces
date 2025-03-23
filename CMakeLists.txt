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
  "pathfinder/Waypoint.msg"
  "pathfinder/Waypoints.msg"
  "pathfinder/State.msg"
  "pathfinder/States.msg"
  "pathfinder/Segment.msg"
  "pathfinder/Segments.msg"

  "polestar/Datum.srv"
  "polestar/Gps2Ecef.srv"
  "polestar/Ecef2Gps.srv"
  "polestar/Ecef2Enu.srv"
  "polestar/Enu2Ecef.srv"
  "polestar/Gps2Enu.srv"
  "polestar/Enu2Gps.srv"

  "lighthouse/Float32Stamped.msg"
  "lighthouse/Float64Stamped.msg"
  "lighthouse/KeyValue.msg"
  "lighthouse/Value.srv"
  "lighthouse/Spawn.srv"
  "lighthouse/Trigger.srv"
  "lighthouse/Threshold.srv"
  "lighthouse/Reset.srv"
  "lighthouse/blockchain/Block.msg"
  "lighthouse/blockchain/Chain.msg"
  "lighthouse/blockchain/Transaction.msg"
  "lighthouse/blockchain/JoinChain.srv"
  "lighthouse/blockchain/VoteChain.srv"
  "lighthouse/blockchain/UpdateChain.srv"
  "lighthouse/agents/Agent.msg"
  "lighthouse/agents/Agents.msg"

  "taskforce/Job.msg"
  "taskforce/Auction.msg"
  "taskforce/Bid.msg"
  "taskforce/Job.srv"


  "trailblazer/Line.msg"
  "trailblazer/Lines.msg"
  "trailblazer/FieldGen.srv"

  "cartograph/GeoJson.msg"
  "cartograph/Cordinate.msg"
  "cartograph/Cordinates.msg"
  "cartograph/Geometry.msg"
  "cartograph/Feature.msg"
  "cartograph/Propertie.msg"
  "cartograph/GeoTiff.msg"
  "cartograph/Band.msg"
  "cartograph/Grid.msg"
  DEPENDENCIES nav_msgs std_msgs geometry_msgs sensor_msgs
)

if(BUILD_TESTING)
  find_package(ament_lint_auto REQUIRED)
  set(ament_cmake_copyright_FOUND TRUE)
  set(ament_cmake_cpplint_FOUND TRUE)
  ament_lint_auto_find_test_dependencies()
endif()

ament_package()
