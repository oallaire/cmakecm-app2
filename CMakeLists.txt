cmake_minimum_required(VERSION 3.24)
project(cmakecm-app2 LANGUAGES C)

include(FetchContent)
FetchContent_GetProperties(cmakecm-lib)
if (NOT cmakecm-lib_POPULATED)
    FetchContent_Declare(
            cmakecm-lib
            GIT_REPOSITORY https://github.com/oallaire/cmakecm-lib.git
            GIT_TAG        46d4ff8c80aaa50e323089dc035b6a4c3b65ae92
    )
    FetchContent_MakeAvailable(cmakecm-lib)
endif ()

add_executable(${PROJECT_NAME} main.c)
target_link_libraries(${PROJECT_NAME} cmakecm::lib)

install(TARGETS ${PROJECT_NAME} DESTINATION bin)
