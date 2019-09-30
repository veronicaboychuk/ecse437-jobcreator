# Set the minimum version of CMake that will be supported by this build file
cmake_minimum_required(VERSION 2.6)

# Give the project a name
project(JobCreatorApp)
#set(CMAKE_BINARY_DIR ${CMAKE_SOURCE_DIR}/bin)
#set(EXECUTABLE_OUTPUT_PATH ${CMAKE_BINARY_DIR})
#set(LIBRARY_OUTPUT_PATH ${CMAKE_BINARY_DIR})


include_directories("${PROJECT_SOURCE_DIR}" "${PROJECT_BINARY_DIR}")

#Compile source files in utils and job into libraries
add_library(utils utils/input.c)
target_include_directories(utils PUBLIC include)
add_library(job job/job.c)
target_include_directories(job PUBLIC include)


# Add an executable that is made up of the three C source files
add_executable(jobcreator ${PROJECT_SOURCE_DIR}/main.c)

#link job and utils to it
target_link_libraries(jobcreator job utils)