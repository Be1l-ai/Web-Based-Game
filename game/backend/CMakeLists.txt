# auto generated file - do not edit

cmake_minimum_required(VERSION 3.15)
project(GameServer)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# Include Conan toolchain for Conan 2.x
include(${CMAKE_BINARY_DIR}/conan_toolchain.cmake)

# Add source files
set(SOURCES
    src/server.cpp
    src/GameState.cpp
    src/DatabaseManager.cpp
)

# Create executable
add_executable(server_app ${SOURCES})

# Link libraries (if any dependencies are added to conanfile.txt)
# target_link_libraries(server_app ${CONAN_LIBS})