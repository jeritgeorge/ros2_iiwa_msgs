cmake_minimum_required(VERSION 3.5)
project(iiwa_msgs)

# Default to C++14
if(NOT CMAKE_CXX_STANDARD)
  set(CMAKE_CXX_STANDARD 17)
endif()

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra)
endif()



find_package(ament_cmake REQUIRED)
find_package(rosidl_default_generators REQUIRED)
find_package(builtin_interfaces REQUIRED)
find_package(std_msgs REQUIRED)
find_package(action_msgs REQUIRED)
find_package(geometry_msgs REQUIRED)

set(msg_deps
  "std_msgs"
  "geometry_msgs"
  "action_msgs"
)

set(msg_files
  "msg/CartesianControlModeLimits.msg"
  "msg/CartesianPose.msg"
  "msg/ControlMode.msg"
  "msg/CartesianEulerPose.msg"
  "msg/CartesianPlane.msg"
  "msg/CartesianQuantity.msg"
  "msg/CartesianImpedanceControlMode.msg"
  "msg/CartesianVelocity.msg"
  "msg/CartesianWrench.msg"
  "msg/DesiredForceControlMode.msg"
  "msg/DOF.msg"
  "msg/JointImpedanceControlMode.msg"
  "msg/JointPosition.msg"
  "msg/JointPositionVelocity.msg"
  "msg/JointDamping.msg"
  "msg/JointStiffness.msg"
  "msg/JointTorque.msg"
  "msg/JointVelocity.msg"
  "msg/JointQuantity.msg"
  "msg/JointSpline.msg"
  "msg/SinePatternControlMode.msg"
  "msg/Spline.msg"
  "msg/SplineSegment.msg"
  "msg/RedundancyInformation.msg"
)

set(srv_files
  "srv/ConfigureControlMode.srv"
  "srv/SetPTPCartesianSpeedLimits.srv"
  "srv/SetSmartServoJointSpeedLimits.srv"
  "srv/SetSpeedOverride.srv"
  "srv/SetEndpointFrame.srv"
  "srv/SetPTPJointSpeedLimits.srv"
  "srv/SetSmartServoLinSpeedLimits.srv"
  "srv/TimeToDestination.srv"
)

set(action_files
  "action/MoveAlongJointSpline.action"
  "action/MoveAlongSpline.action"
  "action/MoveToCartesianPose.action"
  "action/MoveToJointPosition.action"
)

rosidl_generate_interfaces(${PROJECT_NAME}
  ${msg_files}
  ${srv_files}
  ${action_files}
  DEPENDENCIES ${msg_deps}
)


ament_export_dependencies(rosidl_default_runtime)

ament_package()
