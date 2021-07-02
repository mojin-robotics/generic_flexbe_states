cmake_minimum_required(VERSION 3.0.2)
project(flexbe_utility_states)

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
    add_rostest(tests/start_record_logs_state/start_record_logs_state.test)
    add_rostest(tests/stop_record_logs_state/stop_record_logs_state.test)
    add_rostest(tests/publish_pose_state/publish_pose_state.test)
    add_rostest(tests/publish_twist_state/publish_twist_state.test)
endif()