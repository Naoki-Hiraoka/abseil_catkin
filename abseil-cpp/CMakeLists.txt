cmake_minimum_required(VERSION 2.8.12)
project(abseil-cpp)

set(CMAKE_BUILD_TYPE Release)

find_package(catkin REQUIRED COMPONENTS
  )

include(ExternalProject)

## Find catkin macros and libraries
## if COMPONENTS list like find_package(catkin REQUIRED COMPONENTS xyz)
## is used, also find other catkin packages
execute_process(COMMAND
  git config --global http.sslVerify false)
## System dependencies are found with CMake's conventions
# find_package(Boost REQUIRED COMPONENTS system)
ExternalProject_Add(
  absl
  GIT_REPOSITORY https://github.com/abseil/abseil-cpp
  CMAKE_ARGS -DCMAKE_INSTALL_PREFIX=${CMAKE_INSTALL_PREFIX} -DCMAKE_BUILD_TYPE=Release -DABSL_ENABLE_INSTALL=ON -DBUILD_SHARED_LIBS=ON
  #INSTALL_COMMAND echo "install"
  )

#install(CODE "execute_process(COMMAND make install WORKING_DIRECTORY ${CMAKE_CURRENT_BINARY_DIR}/osqp-prefix/src/osqp-build)")
