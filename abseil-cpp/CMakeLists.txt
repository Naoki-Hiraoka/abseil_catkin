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


ExternalProject_Add(
  absl
  GIT_REPOSITORY https://github.com/abseil/abseil-cpp
  GIT_TAG lts_2024_01_16 # これ以降のバージョンはcmake3.16以上を要求するため、ubuntu18のデフォルトのcmakeではビルドできない.
  CMAKE_ARGS -DCMAKE_INSTALL_PREFIX=${CMAKE_INSTALL_PREFIX} -DCMAKE_BUILD_TYPE=Release -DABSL_ENABLE_INSTALL=ON -DBUILD_SHARED_LIBS=ON
  #INSTALL_COMMAND echo "install"
  )

# memo
#   202506時点のabseil-cppを使う場合、-DCMAKE_CXX_STANDARD=17 が必要.
#     こちらで17以上を指定しなければ https://github.com/abseil/abseil-cpp/blob/747f9c9fd244016e1d3da41f51b17aa03b96d6d3/CMake/AbseilDll.cmake#L727 でエラーになるため.
#     ただし、abslのヘッダファイルをincludeする全てのプログラムをc++17以上でビルドする必要があるので後方互換性注意.
