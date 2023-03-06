cmake_minimum_required(VERSION 3.13)

include(pico_sdk_import.cmake)

project(pico-helloworld C CXX ASM)
set(CMAKE_C_STANDARD 11)
set(CMAKE_CXX_STANDARD 17)

pico_sdk_init()

add_executable(pico_ws2812_network_interface
main.c)

file(MAKE_DIRECTORY ${CMAKE_CURRENT_LIST_DIR}/generated)

# generate the header file into the source tree as it is included in the RP2040 datasheet
pico_generate_pio_header(pico_ws2812_network_interface ${CMAKE_CURRENT_LIST_DIR}/ws2812.pio OUTPUT_DIR ${CMAKE_CURRENT_LIST_DIR}/generated)

target_link_libraries(pico_ws2812_network_interface pico_stdlib hardware_pio)


pico_enable_stdio_uart(pico_ws2812_network_interface 1)

pico_add_extra_outputs(pico_ws2812_network_interface)

