cmake_minimum_required(VERSION 3.8)
project(ck_ros2_msgs_node)

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

# find dependencies
find_package(ament_cmake REQUIRED)

file(GLOB_RECURSE message_sources CONFIGURE_DEPENDS
  RELATIVE "${PROJECT_SOURCE_DIR}" "${PROJECT_SOURCE_DIR}/msg/*.msg"
)

find_package(rosidl_default_generators REQUIRED)
rosidl_generate_interfaces(${PROJECT_NAME} ${message_sources})
ament_export_dependencies(rosidl_default_runtime)

ament_package()
