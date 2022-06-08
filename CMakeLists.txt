# Original boilerplate: 
cmake_minimum_required(VERSION 3.20)

# Change your executable name to something creative!
set(NAME badger-project)

# include the dependencies
include(pimoroni_pico_import.cmake)
include(pico_sdk_import.cmake)
include(pico_extras_import.cmake)

# Gooey boilerplate
project(${NAME} C CXX ASM)
set(CMAKE_C_STANDARD 11)
set(CMAKE_CXX_STANDARD 17)

# add dependencies as subdirectory
add_subdirectory(pimoroni-pico)
# add_subdirectory(<dependency-directory-name>) # <- add more dependencies like this

# add the project as a subdirectory after bootstrapping
add_subdirectory(programexample)
# add_subdirectory(<program-directory-name>) # <- add more programs like this

