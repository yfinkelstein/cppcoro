
project(cppcoro_tests)

get_target_property(parent_libs cppcoro LINK_LIBRARIES)

set(SRC_FILES main.cpp
        counted.cpp
        generator_tests.cpp
        recursive_generator_tests.cpp
        async_generator_tests.cpp
        async_auto_reset_event_tests.cpp
        async_manual_reset_event_tests.cpp
        async_mutex_tests.cpp
        cancellation_token_tests.cpp
        task_tests.cpp
        shared_task_tests.cpp
        sync_wait_tests.cpp
        when_all_tests.cpp
        when_all_ready_tests.cpp)

include_directories(${CMAKE_CURRENT_SOURCE_DIR}/doctest)

add_executable(${PROJECT_NAME} ${SRC_FILES})
target_link_libraries(${PROJECT_NAME} cppcoro ${parent_libs})
