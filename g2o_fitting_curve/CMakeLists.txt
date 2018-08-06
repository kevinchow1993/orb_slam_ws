cmake_minimum_required(VERSION 2.8.3)
project(g2o_fitting_curve)
#set( CMAKE_BUILD_TYPE "Release" )
set( CMAKE_CXX_FLAGS "-std=c++11 -O3" )

set(CMAKE_MODULE_PATH ${PROJECT_SOURCE_DIR}/cmake_modules )
find_package(catkin REQUIRED)
find_package(G2O REQUIRED)
include_directories( 
    ${G2O_INCLUDE_DIRS}
    "/usr/include/eigen3"
)

find_package(catkin REQUIRED COMPONENTS
  roscpp
)

find_package( OpenCV REQUIRED )
include_directories( ${OpenCV_DIRS} )
catkin_package()
## Specify additional locations of header files
## Your package locations should be listed before other locations
include_directories(
  include ${catkin_INCLUDE_DIRS}
# include
# ${catkin_INCLUDE_DIRS}
)



add_executable(g2o_fitting_sub
  src/g2o_fitting_sub.cpp
)
add_dependencies(g2o_fitting_sub ${${PROJECT_NAME}_EXPORTED_TARGETS} ${catkin_EXPORTED_TARGETS})
target_link_libraries(g2o_fitting_sub
  ${catkin_LIBRARIES}
      ${OpenCV_LIBS}
    g2o_core g2o_stuff
)









