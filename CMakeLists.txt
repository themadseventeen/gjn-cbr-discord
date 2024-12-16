cmake_minimum_required(VERSION 2.8...3.14)

project(gjn-cbr-discord VERSION 1.0 LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED True)

include(FetchContent)

FetchContent_Declare(
  DPP
  GIT_REPOSITORY https://github.com/brainboxdotcc/DPP.git
  GIT_TAG v10.0.35
)

FetchContent_MakeAvailable(DPP)

# Fetch libpqxx
FetchContent_Declare(
  libpqxx
  GIT_REPOSITORY https://github.com/jtv/libpqxx.git
  GIT_TAG 7.9.2  # Replace with the desired version tag
)

# Make libpqxx available
FetchContent_MakeAvailable(libpqxx)

file(GLOB SOURCES "src/*.cpp")

add_executable(gjn-cbr-discord ${SOURCES})

target_link_libraries(gjn-cbr-discord PRIVATE dpp pqxx)

target_include_directories(gjn-cbr-discord PRIVATE "include/")
