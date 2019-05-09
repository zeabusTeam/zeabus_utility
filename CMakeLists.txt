# This line will acquire and ensure version of cmake which you use 
# This version 2.8.3 we use this minimum because that is default of ROS distro MELODIC
cmake_minimum_required( VERSION 2.8.3 )

project( zeabus_utility ) # set name of your project

# Find package is importance key 
# It help you about beforedo this package that will ensure you have REQUIRED package
find_package( catkin REQUIRED COMPONENTS std_msgs 
    message_generation 
    geometry_msgs 
    sensor_msgs
)

add_message_files(
    FILES
    VisionQualification.msg
    HeaderFloat64.msg
)

add_service_files(
    FILES
    GetGeometryVector3Stamped.srv
    GetSensorImu.srv
    VisionSrvQualification.srv
    SendUInt16Array.srv
    DepthCommand.srv
)

generate_messages(
    DEPENDENCIES
    std_msgs
    sensor_msgs
    geometry_msgs
)

set( message_on_service
    std_msgs
    geometry_msgs
    sensor_msgs
)

catkin_package(
    CATKIN_DEPENDS message_runtime ${message_on_service}
)
