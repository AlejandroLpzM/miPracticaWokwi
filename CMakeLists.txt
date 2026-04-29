cmake_minimum_required(VERSION 3.13)

# Documentation-oriented scaffold for Pico W projects.
# NOTE: The provided firmware uses Arduino APIs (setup/loop, Keypad library).
# Build with Arduino-Pico tooling for execution; this CMake file documents
# standard Pico SDK project layout for future migration.
project(pico_w_keypad_led C CXX ASM)
set(CMAKE_C_STANDARD 11)
set(CMAKE_CXX_STANDARD 17)

add_custom_target(info ALL
  COMMAND ${CMAKE_COMMAND} -E echo "Use Arduino-Pico (or PlatformIO) to build src/main.cpp with Keypad.h"
)
