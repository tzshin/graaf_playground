cmake_minimum_required(VERSION 3.14)
project(ReadGraph LANGUAGES CXX)

set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin)

set(CMAKE_CXX_STANDARD     20)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS    OFF)

include(FetchContent)
FetchContent_Declare(
  fmt
  GIT_REPOSITORY https://github.com/fmtlib/fmt.git
  GIT_TAG        master
)
FetchContent_MakeAvailable(fmt)

add_subdirectory(libs/graaf)

add_executable(my_app src/main.cpp)
target_link_libraries(my_app
  PRIVATE
    fmt::fmt
    Graaf::Graaf
)
