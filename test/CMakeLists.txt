
project(cppcoro_tests)

set(SRC_FILES 
        async_auto_reset_event_tests.cpp
        async_generator_tests.cpp
        async_latch_tests.cpp
        async_manual_reset_event_tests.cpp
        async_mutex_tests.cpp
        cancellation_token_tests.cpp
        counted.cpp
        # file_tests.cpp
        generator_tests.cpp
        # io_service_tests.cpp
        ip_address_tests.cpp
        ip_endpoint_tests.cpp
        ipv4_address_tests.cpp
        ipv4_endpoint_tests.cpp
        ipv6_address_tests.cpp
        ipv6_endpoint_tests.cpp
        main.cpp
        recursive_generator_tests.cpp
        # scheduling_operator_tests.cpp
        shared_task_tests.cpp
        single_consumer_async_auto_reset_event_tests.cpp
        # socket_tests.cpp
        static_thread_pool_tests.cpp
        sync_wait_tests.cpp
        task_tests.cpp
        when_all_ready_tests.cpp
        when_all_tests.cpp        
)

include_directories(${CMAKE_CURRENT_SOURCE_DIR}/doctest)

add_executable(${PROJECT_NAME} ${SRC_FILES})
target_link_libraries(${PROJECT_NAME} cppcoro)
