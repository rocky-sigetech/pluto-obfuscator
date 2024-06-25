cmake_minimum_required(VERSION 3.10)

project(HelloObfuscated C CXX)

# Use Clang as the compiler
set(CMAKE_C_COMPILER "clang")
#set(CMAKE_CXX_COMPILER "clang++")

# Set compilation flags with LLVM obfuscation options
set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -O2")
#set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -O2")

# Add the executable
add_executable(hello hello.c)

