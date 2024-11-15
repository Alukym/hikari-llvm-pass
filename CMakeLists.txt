# ./CMakeLists.txt
cmake_minimum_required(VERSION 3.22)
project(Hikari-LLVM19)

set(CMAKE_OSX_ARCHITECTURES x86_64)

set(CMAKE_C_COMPILER /home/google-clang-prebuilt/bin/clang)
set(CMAKE_CXX_COMPILER /home/google-clang-prebuilt/bin/clang++)
set(ENV{LLVM_HOME} /home/google-clang-prebuilt)

if (NOT DEFINED ENV{LLVM_HOME})
    message(FATAL_ERROR "$LLVM_HOME is not defined")
else ()
    set(ENV{LLVM_DIR} $ENV{LLVM_HOME}/lib/cmake/llvm)
endif ()

find_package(LLVM REQUIRED CONFIG)
add_definitions(${LLVM_DEFINITIONS})
include_directories(${LLVM_INCLUDE_DIRS})
link_directories(${LLVM_LIBRARY_DIRS})

set(CMAKE_CXX_STANDARD 17)

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -stdlib=libc++")
set(CMAKE_SKIP_RPATH ON)

add_subdirectory(Hikari)
