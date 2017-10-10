cmake_minimum_required(VERSION 3.8.2)


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
add_definitions("-std=c++1z")
add_definitions("-fcoroutines-ts")
add_definitions("-Wall -Wextra")

include_directories(${CMAKE_CURRENT_SOURCE_DIR}/include)

project("cppcoro")

set(SRC_FILES
lib/async_auto_reset_event.cpp
lib/async_manual_reset_event.cpp
lib/async_mutex.cpp
lib/cancellation_state.cpp
lib/cancellation_token.cpp
lib/cancellation_source.cpp
lib/cancellation_registration.cpp
lib/lightweight_manual_reset_event.cpp
)

add_library(${PROJECT_NAME} STATIC ${SRC_FILES})

add_subdirectory(test)

install(DIRECTORY include/cppcoro DESTINATION include)
install(TARGETS ${PROJECT_NAME}
        ARCHIVE DESTINATION lib)

#enable_testing()
