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
    nav_msgs
)

add_message_files(
    FILES
    # Message maintain by Korrawit Chaikangwan
    VisionQualification.msg
    # Message maintain by K.Supasan
    AUVState.msg
    HeaderFloat64.msg
    ControlCommand.msg
    # Message maintain by Natchanan Thongtem
    TelemetryStruct.msg
    # Message maintain by Natthaphat Wattanachansit
    VisionPath.msg
)

add_service_files(
    FILES
    # Service maintain by Korrawit Chaikangwan
    VisionSrvQualification.srv
    # Service maintain by K.Supasan
    GetAUVState.srv
    GetSensorImu.srv
    SendThrottle.srv
    SendControlCommand.srv
    GetGeometryVector3Stamped.srv
    # Service maintain by Natchanan Thongtem
    DepthCommand.srv
    Telemetry.srv
    SendUInt16Array.srv
    # Message maintain by Natthaphat Wattanachansit
    VisionSrvPath.srv
    # Message maintain by Phitchawat L.
    VisionGate.srv
)

generate_messages(
    DEPENDENCIES
    std_msgs
    sensor_msgs
    geometry_msgs
    nav_msgs
)

set( message_on_service
    std_msgs
    geometry_msgs
    sensor_msgs
    nav_msgs
)

catkin_package(
    CATKIN_DEPENDS message_runtime ${message_on_service}
)
