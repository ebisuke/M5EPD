cmake_minimum_required(VERSION 3.5)


set(INCLUDEDIRS
        src
        )

file(GLOB_RECURSE SRCS "src/*.c*")


idf_component_register(INCLUDE_DIRS ${INCLUDEDIRS} SRCS ${SRCS} REQUIRES arduino)

target_compile_options(${COMPONENT_TARGET} PRIVATE
        -DCORE_DEBUG_LEVEL=5
        -Os
        -g0
        -Wno-error=all
        -Wno-missing-field-initializers
        -Wno-unused-variable
        -DBOARD_HAS_PSRAM
        -mfix-esp32-psram-cache-issue

        )

target_compile_features(${COMPONENT_TARGET} PRIVATE cxx_std_17)
