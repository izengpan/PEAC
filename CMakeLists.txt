cmake_minimum_required(VERSION 2.8 FATAL_ERROR)

project(PEAC)

set( CMAKE_CXX_COMPILER "g++" )
# set( CMAKE_BUILD_TYPE "Release" )
set( CMAKE_BUILD_TYPE "Debug" )
set( CMAKE_CXX_FLAGS "-std=c++11 -march=native -O3" )

find_package(OpenCV REQUIRED)
find_package(PCL REQUIRED)

include_directories("include")
include_directories(${PCL_INCLUDE_DIRS})
link_directories(${PCL_LIBRARY_DIRS})
add_definitions(${PCL_DEFINITIONS})

add_executable(plane_fitter cpp/plane_fitter.cpp)
target_link_libraries(plane_fitter ${PCL_LIBRARIES} ${OpenCV_LIBS})
# install(TARGETS plane_fitter DESTINATION bin)

add_executable(plane_fitter_pcd cpp/plane_fitter_pcd.cpp)
target_link_libraries(plane_fitter_pcd ${PCL_LIBRARIES} ${OpenCV_LIBS})
# install(TARGETS plane_fitter_pcd DESTINATION bin)
# install(FILES plane_fitter_pcd.ini DESTINATION bin)

add_executable(plane_fitter_png cpp/plane_fitter_png.cpp)
target_link_libraries(plane_fitter_png ${PCL_LIBRARIES} ${OpenCV_LIBS})