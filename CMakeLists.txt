cmake_minimum_required(VERSION 3.10)

project(main VERSION 1.0)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED True)

find_package(SFML 2.5 REQUIRED COMPONENTS graphics window system)

set(SOURCES
    src/main.cpp
    src/particle.cpp
    src/cell.cpp
    src/trail.cpp
    src/sensor.cpp
)

set(HEADERS
    include/const.hpp
    include/particle.hpp
    include/cell.hpp
    include/trail.hpp
    include/sensor.hpp
)

add_executable(${PROJECT_NAME} ${SOURCES})

target_include_directories(${PROJECT_NAME} PRIVATE ${SFML_INCLUDE_DIRS} include)

target_link_libraries(${PROJECT_NAME} sfml-graphics sfml-window sfml-system)

if (UNIX AND NOT APPLE)
    set(CMAKE_INSTALL_RPATH ${SFML_LIBRARIES})
elseif (APPLE)
    set(CMAKE_INSTALL_RPATH "@executable_path/../Frameworks")
endif()
