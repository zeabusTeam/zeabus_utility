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
    VisionStake.msg
    # Message maintain by Natthaphat Wattanachansit
    VisionBox.msg
    VisionPath.msg
    Int16Array.msg
    # Message maintain by K.Supasan
    AUVState.msg
    FuzzyParam.msg
    ControlFuzzy.msg
    HeaderFloat64.msg
    ControlCommand.msg
    # Message maintain by Natchanan Thongtem
    StructTelemetry.msg
    MessagePlannerSwitch.msg
)

add_service_files(
    FILES
    # Service maintain by Korrawit Chaikangwan
    VisionSrvQualification.srv
    VisionSrvStake.srv
    VisionSrvExposed.srv
    # Service maintain by K.Supasan
    SendBool.srv
    GetAUVState.srv
    GetSensorImu.srv
    SendThrottle.srv
    SendControlCommand.srv
    GetGeometryVector3Stamped.srv
    # Service maintain by Natchanan Thongtem
    ServiceDepth.srv
    ServiceGetTelemetry.srv
    # Message maintain by Natthaphat Wattanachansit
    VisionSrvDropGarlic.srv
    VisionSrvPath.srv
    # Message maintain by Phitchawat L.
    VisionGate.srv
    VisionBuoy.srv
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
