cmake_minimum_required(VERSION 3.10)

project(HelloObfuscated C CXX)

# Use Clang as the compiler
set(CMAKE_C_COMPILER "clang")
#set(CMAKE_CXX_COMPILER "clang++")

# Set compilation flags with LLVM obfuscation options
set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -O2")
#set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -O2")

# Add LLVM obfuscation flags (C and C++)
string(APPEND CMAKE_C_FLAGS " -mllvm -fla -mllvm -bcf -mllvm -sub -mllvm -gle -mllvm -mba -mllvm -mba-prob=100")
#string(APPEND CMAKE_CXX_FLAGS " -mllvm -fla -mllvm -bcf -mllvm -sub -mllvm -gle -mllvm -mba -mllvm -mba-prob=100")

# Add the executable
add_executable(hello_obf hello.c)

 Strip the executable during the Release build
if(CMAKE_BUILD_TYPE STREQUAL "Release")
    add_custom_command(
        TARGET hello_obf
        POST_BUILD
        COMMAND "${CMAKE_STRIP}" --strip-all $<TARGET_FILE:hello_obf>
    )
endif()

