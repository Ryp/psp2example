cmake_minimum_required(VERSION 2.8.11 FATAL_ERROR)
project(example)

# Make cmake search for FindPSP2SDK.cmake script in this directory
# This may be installed in your system by psp2sdk in the future
list(APPEND CMAKE_MODULE_PATH "${CMAKE_CURRENT_SOURCE_DIR}/cmake")

# Search for psp2sdk
find_package(PSP2SDK REQUIRED)

# Homebrew target name
set(HB_NAME myHomebrew)

# List sources
set(SRCS main.c draw.c font_data.c)

# Set additional compilation flags
set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -Wall -Wextra -nostdlib -specs=${PSP2SDK_PATH}/psp2.specs")

# Add main target
add_executable(${HB_NAME} ${SRCS})

# Use macro from PSP2SDK to fix elf target
add_elf_fixup_target(${HB_NAME})

# message(FATAL_ERROR ${PSP2SDK_INCLUDE_DIRS})
# message(FATAL_ERROR ${HB_NAME})
target_include_directories(${HB_NAME} PUBLIC
    ${PSP2SDK_INCLUDE_DIRS}
)

target_link_libraries(${HB_NAME}
    -lc_stub
    -lSceKernel_stub
    -lSceDisplay_stub
    -lSceGxm_stub
    -lSceCtrl_stub
    -lSceTouch_stub
)
