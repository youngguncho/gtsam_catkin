cmake_minimum_required(VERSION 2.8.3)
project(gtsam_test)

## Add support for C++11, supported in ROS Kinetic and newer
add_definitions(-std=c++11)

## Find catkin macros and libraries
## if COMPONENTS list like find_package(catkin REQUIRED COMPONENTS xyz)
## is used, also find other catkin packages
find_package(catkin REQUIRED COMPONENTS
    roscpp
)


## Include GTSAM CMake tools
#find_package(GTSAMCMakeTools)
##include(GtsamBuildTypes) # Load build type flags and default to Debug mode
##include(GtsamTesting)    # Easy functions for creating unit tests and scripts
##include(GtsamMatlabWrap) # Automatic MATLAB wrapper generation


## System dependencies are found with CMake's conventions
find_package(GTSAM REQUIRED)
find_package(Boost REQUIRED COMPONENTS system)


catkin_package(
#  INCLUDE_DIRS include
#  LIBRARIES gtsam_test
#  CATKIN_DEPENDS roscpp
#  DEPENDS system_lib
)

###########
## Build ##
###########

## Specify additional locations of header files
## Your package locations should be listed before other locations
# include_directories(include)
include_directories(
    ${catkin_INCLUDE_DIRS}
    ${GTSAM_INCLUDE_DIR}
)

set(GTSAM_LIBRARIES gtsam)   # TODO: automatic search libs

## Stereo VO sample code
add_executable(stero_vo
    src/StereoVO.cpp
)

target_link_libraries(stero_vo
    ${catkin_LIBRARIES}
    gtsam
)

## Pose2d SLAM sample code
add_executable(pose_2d
    src/Pose2SLAM.cpp
)

target_link_libraries(pose_2d
    ${catkin_LIBRARIES}
    gtsam
)

