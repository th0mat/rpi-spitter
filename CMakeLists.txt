cmake_minimum_required(VERSION 3.0)
project(spitter)

# not required if find_package is used
link_directories(/usr/local/lib/)

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++14 -Wall -I/usr/include/")

set(SOURCE_FILES macchina/spitter.cpp macchina/spitter.h mac2oui/lookup.cpp mac2oui/lookup.h
        main.cpp config.h config.cpp macchina/spitutils.cpp macchina/spitutils.h)

add_executable(spitter ${SOURCE_FILES})
target_link_libraries(spitter pthread pcap pqxx pq)

configure_file(mac2oui/oui_download.txt mac2oui/oui_download.txt COPYONLY)
configure_file(mac2oui/mac_config.txt mac2oui/mac_config.txt COPYONLY)
configure_file(config.json config.json COPYONLY)

