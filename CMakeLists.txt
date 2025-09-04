cmake_minimum_required(VERSION 3.8)
project(aws_small_house_world)

find_package(ros_gz_sim REQUIRED)
find_package(ament_cmake_ros REQUIRED)

install(DIRECTORY
  launch
  models
  worlds
  photos
  DESTINATION share/${PROJECT_NAME}
)

ament_export_dependencies(ros_gz_sim)

if(BUILD_TESTING)
  find_package(ament_lint_auto REQUIRED)
  set(ament_cmake_copyright_FOUND TRUE)
  set(ament_cmake_cpplint_FOUND TRUE)
  ament_lint_auto_find_test_dependencies()
endif()

ament_environment_hooks("${CMAKE_CURRENT_SOURCE_DIR}/hooks/${PROJECT_NAME}.dsv.in")
ament_environment_hooks("${CMAKE_CURRENT_SOURCE_DIR}/hooks/${PROJECT_NAME}.sh.in")

ament_package()
