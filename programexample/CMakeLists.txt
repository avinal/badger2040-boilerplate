# rename your project
project(programexample C CXX)

# Initialize the SDK
pico_sdk_init() 

# Add your source files
add_executable(${PROJECT_NAME}
    main.cpp # <-- Add source files here!
)

# set pico specific options
pico_set_program_name(${PROJECT_NAME} "${PROJECT_NAME}")
pico_set_program_version(${PROJECT_NAME} "0.1")

pico_enable_stdio_uart(${PROJECT_NAME} 0)
pico_enable_stdio_usb(${PROJECT_NAME} 0)


# Don't forget to link the libraries you need!
target_link_libraries(${PROJECT_NAME}
    pico_stdlib
    hardware_spi
    badger2040 # <-- List libraries here!
)


# create map/bin/hex file etc.
pico_enable_stdio_usb(${PROJECT_NAME} 1)
pico_add_extra_outputs(${PROJECT_NAME})

# include source directories if needed
include_directories(../pimoroni-pico)
