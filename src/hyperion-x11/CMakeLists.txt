# Configure minimum CMAKE version
cmake_minimum_required(VERSION 2.8.11)

# Set the project name
project(hyperion-x11)

# Find X11
find_package(X11 REQUIRED)

include_directories(
	${CMAKE_CURRENT_BINARY_DIR}/../../libsrc/protoserver
	${X11_INCLUDES}
	${PROTOBUF_INCLUDE_DIRS}
)

set(Hyperion_X11_QT_HEADERS
	X11Wrapper.h)

set(Hyperion_X11_HEADERS
)

set(Hyperion_X11_SOURCES
	hyperion-x11.cpp
	X11Wrapper.cpp
)

add_executable(hyperion-x11
	${Hyperion_X11_HEADERS}
	${Hyperion_X11_QT_HEADERS}
	${Hyperion_X11_SOURCES}
)

target_link_libraries(hyperion-x11
	getoptPlusPlus
	blackborder
	hyperion-utils
	protoserver
	x11-grabber
	${X11_LIBRARIES}
	pthread
	${QT_LIBRARIES}
)

