cmake_minimum_required(VERSION 3.0.2)
project(flexbe_manipulation_states)

find_package(catkin REQUIRED)

catkin_python_setup()

catkin_package()

install(DIRECTORY tests
  DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}
  PATTERN "*.py" EXCLUDE # do not install scripts twice
)

# run tests
if(CATKIN_ENABLE_TESTING)
    find_package(rostest REQUIRED)
    add_rostest(tests/srdf_state_to_moveit/srdf_state_to_moveit.test)
    add_rostest(tests/srdf_state_to_moveit_execute_trajectory/srdf_state_to_moveit_execute_trajectory.test)
    add_rostest(tests/get_joints_from_srdf_state/get_joints_from_srdf_state.test)
    add_rostest(tests/get_joint_values_dyn_state/get_joint_values_dyn_state.test)
    add_rostest(tests/moveit_to_joints_state/moveit_to_joints_state.test)
    add_rostest(tests/moveit_to_joints_dyn_state/moveit_to_joints_dyn_state.test)
    add_rostest(tests/joint_state_to_moveit/joint_state_to_moveit.test)
    add_rostest(tests/get_joint_values_state/get_joint_values_state.test)
    add_rostest(tests/get_joints_from_srdf_group/get_joints_from_srdf_group.test)
endif()
