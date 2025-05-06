cmake_minimum_required(VERSION 3.8)
project(marine_sim)

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

# find dependencies
find_package(ament_cmake REQUIRED)
find_package(rclcpp REQUIRED)
find_package(gazebo_ros REQUIRED)

# If using gazebo-specific libraries or plugins, link them here
# e.g., find_package(gazebo REQUIRED)

if(BUILD_TESTING)
  find_package(ament_lint_auto REQUIRED)
  # Skipping linter checks for copyrights during development
  set(ament_cmake_copyright_FOUND TRUE)
  set(ament_cmake_cpplint_FOUND TRUE)
  ament_lint_auto_find_test_dependencies()
endif()

# Install directories
install(DIRECTORY launch models urdf worlds
  DESTINATION share/${PROJECT_NAME}/
)

# Install executables or libraries if needed
# If you have a custom executable, uncomment and modify:
# install(TARGETS my_node
#   DESTINATION lib/${PROJECT_NAME}
# )

ament_package()