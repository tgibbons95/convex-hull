cmake_minimum_required(VERSION 3.16)

# Set project name
project(DemoConvexHull)

# Gather all cpp files
file(GLOB_RECURSE SOURCES "*.cpp" "*h")

# Build static library from sources
add_library(${PROJECT_NAME} SHARED ${SOURCES})

# Add Options
enable_code_coverage(${PROJECT_NAME})

# Include header files
target_include_directories(${PROJECT_NAME} PUBLIC "${PROJECT_SOURCE_DIR}/include")

# Use C++17 features
set_property(TARGET ${PROJECT_NAME} PROPERTY CXX_STANDARD 17)

# Link libraries
target_link_libraries(${PROJECT_NAME} AlgorithmLib)
target_link_libraries(${PROJECT_NAME} glfw)

find_package(OpenGL REQUIRED)
target_link_libraries(${PROJECT_NAME} OpenGL::GL)

# Output destination for library
install(TARGETS ${PROJECT_NAME} DESTINATION bin)