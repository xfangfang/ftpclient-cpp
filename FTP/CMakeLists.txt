
IF (MSVC OR NOT CMAKE_BUILD_TYPE MATCHES Coverage)

    set(CMAKE_POSITION_INDEPENDENT_CODE ON)

    #Locate libcURL
    find_package(CURL REQUIRED)

    file(GLOB_RECURSE source_files ./*)
    add_library(ftpclient STATIC ${source_files})
    target_include_directories(ftpclient PUBLIC "${CMAKE_CURRENT_SOURCE_DIR}")
    target_include_directories(ftpclient PRIVATE "${CURL_INCLUDE_DIRS}")

    install(TARGETS ftpclient)
ENDIF ()
