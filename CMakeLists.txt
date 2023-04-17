cmake_minimum_required(VERSION 3.22)
project(cmakecm-app2 LANGUAGES C)

include(FetchContent)
FetchContent_GetProperties(cmakecm-lib)
if (NOT cmakecm-lib_POPULATED)
    FetchContent_Declare(
            cmakecm-lib
            GIT_REPOSITORY https://github.com/oallaire/cmakecm-lib.git
            GIT_TAG        3d2d16bb24de73aedc052d971fb052d01e847027
    )
    FetchContent_MakeAvailable(cmakecm-lib)
else ()
#    get_target_property(cmakecm-lib_VERSION)
endif ()

get_target_property(cmakecm-lib_VERSION cmakecm-lib VERSION)

# Example of only supporting past versions
#set(cmakecm-lib_EXPECTED_VERSION 1.0.1)
#if (${cmakecm-lib_VERSION} VERSION_GREATER ${cmakecm-lib_EXPECTED_VERSION})
#    message(FATAL_ERROR "Version is ${cmakecm-lib_VERSION} but max supported version is ${cmakecm-lib_EXPECTED_VERSION}")
#endif ()

# Example of supporting all past versions and all current minor versions
#set(cmakecm-lib_CAP_VERSION 1.1)
#if (${cmakecm-lib_VERSION} VERSION_GREATER_EQUAL ${cmakecm-lib_CAP_VERSION})
#    message(FATAL_ERROR "Version is ${cmakecm-lib_VERSION} but supported version is  capped under ${cmakecm-lib_CAP_VERSION}")
#endif ()

add_executable(${PROJECT_NAME} main.c)
target_link_libraries(${PROJECT_NAME} cmakecm::lib)

install(TARGETS ${PROJECT_NAME} DESTINATION bin)
