SET(CWMDBIN_SRCS
	cwmd.h
	cwmd.cpp
	world_cwmd.h
	world_cwmd.cpp
	main.cpp
)


include_directories(
	./
	../common/
	../base/
	../cell/
)

add_executable(cwmd
    ${CWMDBIN_SRCS}
)

TARGET_LINK_LIBRARIES(cwmd "common")
TARGET_LINK_LIBRARIES(cwmd "ssl")
TARGET_LINK_LIBRARIES(cwmd "crypto")
TARGET_LINK_LIBRARIES(cwmd "lua.5.2.4")
TARGET_LINK_LIBRARIES(cwmd "boost_regex")
TARGET_LINK_LIBRARIES(cwmd "mysqlclient")


set_target_properties(cwmd PROPERTIES
    OUTPUT_NAME "cwmd"
    CLEAN_DIRECT_OUTPUT 1
    VERSION ${DARKSERVER_VERSION}
)

set_target_properties(cwmd PROPERTIES RUNTIME_OUTPUT_DIRECTORY ${CMAKE_SOURCE_DIR}/bin)
set_target_properties(cwmd PROPERTIES RUNTIME_OUTPUT_DIRECTORY_DEBUG ${CMAKE_SOURCE_DIR}/bin)
set_target_properties(cwmd PROPERTIES RUNTIME_OUTPUT_DIRECTORY_RELEASE ${CMAKE_SOURCE_DIR}/bin)