cmake_minimum_required(VERSION 3.10)
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

project(IMU_MULTIPLEXER VERSION 1.0)

add_library(multiplexerlib STATIC lib/i2c_multiplexer.c)
target_include_directories(multiplexerlib PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}/lib/include)

add_library(imulib STATIC lib/i2c_bno055.c)
target_include_directories(imulib PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}/lib/include)

add_executable(imu_multiplexer main.cpp)
target_link_libraries(imu_multiplexer PUBLIC multiplexerlib imulib)



