cmake_minimum_required(VERSION 3.15 FATAL_ERROR)

project(release CXX)

if("${CMAKE_C_CLANG_TIDY}" STREQUAL "Debug")
  set(CMAKE_C_CLANG_TIDY clang-tidy -checks=*)
endif()

find_package(OpenCV REQUIRED objdetect highgui imgproc)

add_executable(${PROJECT_NAME} main.cpp)
set_target_properties(${PROJECT_NAME} PROPERTIES
        CXX_STANDARD 11
        CXX_STANDARD_REQUIRED YES
        CXX_EXTENSIONS NO)
target_link_libraries(${PROJECT_NAME} ${OpenCV_LIBS})
