cmake_minimum_required(VERSION 3.16)
set(CMAKE_CXX_STANDARD 17)

project(vulkan-tutorial)

list(APPEND CMAKE_MODULE_PATH "${PROJECT_SOURCE_DIR}/libs")

add_executable(${PROJECT_NAME} main.cpp)

find_package(Vulkan REQUIRED)
target_include_directories(${PROJECT_NAME} PUBLIC ${Vulkan_INCLUDE_DIRS})
target_link_libraries(${PROJECT_NAME} Vulkan::Vulkan)

#build from source
add_subdirectory(${CMAKE_MODULE_PATH}/glfw-3.3.2)
target_link_libraries(${PROJECT_NAME} glfw)

#find built binary
#find_package(glfw3 3.3.2 REQUIRED)
#include_directories(${GLFW_INCLUDE_DIRS})
#target_link_libraries(${PROJECT_NAME} ${GLFW_LIBRARIES})

add_subdirectory(${CMAKE_MODULE_PATH}/glm)
target_link_libraries(${PROJECT_NAME} glm)

#pkg_search_module(GLM REQUIRED glm)
#include_directories(${GLM_INCLUDE_DIRS})
#target_link_libraries(${PROJECT_NAME} ${GLM_LIBRARY_DIRS})
