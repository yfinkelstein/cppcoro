cmake_minimum_required(VERSION 3.2.0)


#override via command line, for instance: cmake -DLLVM_HOME=/Library/Developer/CommandLineTools/usr
#set(LLVM_HOME /usr/local/opt/llvm CACHE PATH "path to LLVM distribution")
#set(CMAKE_CXX_COMPILER ${LLVM_HOME}/bin/clang++)
#set(CMAKE_C_COMPILER ${LLVM_HOME}/bin/clang)

set(CMAKE_DEBUG_TARGET_PROPERTIES
        INCLUDE_DIRECTORIES
        COMPILE_DEFINITIONS
        LIB_VERSION
        )

set( CMAKE_VERBOSE_MAKEFILE on )

set(CMAKE_DEBUG_POSTFIX "_d" CACHE STRING "postfix applied to debug build of libraries")
add_definitions("-std=c++17")
add_definitions("-fcoroutines-ts")
add_definitions("-Wall -Wextra")

include_directories(${CMAKE_CURRENT_SOURCE_DIR}/include)

project("cppcoro")

set(SRC_FILES
    lib/async_auto_reset_event.cpp
    lib/async_manual_reset_event.cpp
    lib/async_mutex.cpp
    lib/auto_reset_event.cpp
    lib/auto_reset_event.hpp
    lib/cancellation_registration.cpp
    lib/cancellation_source.cpp
    lib/cancellation_state.cpp
    lib/cancellation_state.hpp
    lib/cancellation_token.cpp
    # lib/file.cpp
    # lib/file_read_operation.cpp
    # lib/file_write_operation.cpp
    # lib/read_only_file.cpp
    # lib/read_write_file.cpp
    # lib/readable_file.cpp
    # lib/writable_file.cpp
    # lib/write_only_file.cpp
    # lib/io_service.cpp
    lib/ip_address.cpp
    lib/ip_endpoint.cpp
    lib/ipv4_address.cpp
    lib/ipv4_endpoint.cpp
    lib/ipv6_address.cpp
    lib/ipv6_endpoint.cpp
    lib/lightweight_manual_reset_event.cpp
    # lib/socket.cpp
    # lib/socket_accept_operation.cpp
    # lib/socket_connect_operation.cpp
    # lib/socket_disconnect_operation.cpp
    # lib/socket_helpers.cpp
    # lib/socket_helpers.hpp
    # lib/socket_recv_from_operation.cpp
    # lib/socket_recv_operation.cpp
    # lib/socket_send_operation.cpp
    # lib/socket_send_to_operation.cpp
    lib/spin_mutex.cpp
    lib/spin_mutex.hpp
    lib/spin_wait.cpp
    lib/spin_wait.hpp
    lib/static_thread_pool.cpp
)

add_library(${PROJECT_NAME} STATIC ${SRC_FILES})

add_subdirectory(test)

install(DIRECTORY include/cppcoro DESTINATION include)
install(TARGETS ${PROJECT_NAME}
        ARCHIVE DESTINATION lib)

#enable_testing()
