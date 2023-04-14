cmake_minimum_required(VERSION 3.22)
project(cmakecm-app2 LANGUAGES C)

include(FetchContent)
FetchContent_GetProperties(cmakecm-lib)
if (NOT cmakecm-lib_POPULATED)
    FetchContent_Declare(
            cmakecm-lib
            GIT_REPOSITORY https://github.com/oallaire/cmakecm-lib.git
            GIT_TAG        e026562b7f8cc3e24a05d1aaf01f5a29f2329df0
    )
    FetchContent_MakeAvailable(cmakecm-lib)
endif ()

add_executable(${PROJECT_NAME} main.c)
target_link_libraries(${PROJECT_NAME} cmakecm::lib)

install(TARGETS ${PROJECT_NAME} DESTINATION bin)
