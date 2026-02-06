
# inih
add_library(inih STATIC inih/ini.c inih/cpp/INIReader.cpp)
target_include_directories(inih PUBLIC
    $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/inih>
    $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/inih/cpp>
    $<INSTALL_INTERFACE:${CMAKE_INSTALL_INCLUDEDIR}>)

# pugixml
add_subdirectory(pugixml)

# curlpp
find_package(CURL REQUIRED)
add_library(curlpp STATIC
    curlpp/src/curlpp/Easy.cpp
    curlpp/src/curlpp/Exception.cpp
    curlpp/src/curlpp/Form.cpp
    curlpp/src/curlpp/Multi.cpp
    curlpp/src/curlpp/OptionBase.cpp
    curlpp/src/curlpp/Options.cpp
    curlpp/src/curlpp/cURLpp.cpp
    curlpp/src/curlpp/internal/CurlHandle.cpp
    curlpp/src/curlpp/internal/OptionList.cpp
    curlpp/src/curlpp/internal/OptionSetter.cpp
    curlpp/src/curlpp/internal/SList.cpp)
target_include_directories(curlpp PUBLIC
    $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/curlpp/include>
    $<INSTALL_INTERFACE:${CMAKE_INSTALL_INCLUDEDIR}>)
target_link_libraries(curlpp PUBLIC CURL::libcurl)
