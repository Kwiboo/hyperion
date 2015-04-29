cmake_minimum_required(VERSION 2.8.11)

project(hyperion-v4l2)

include_directories(
	${CMAKE_CURRENT_BINARY_DIR}/../../libsrc/protoserver
	${PROTOBUF_INCLUDE_DIRS}
)

set(Hyperion_V4L2_QT_HEADERS
	ScreenshotHandler.h
)

set(Hyperion_V4L2_HEADERS
	VideoStandardParameter.h
	PixelFormatParameter.h
)

set(Hyperion_V4L2_SOURCES
	hyperion-v4l2.cpp
	ScreenshotHandler.cpp
)

add_executable(hyperion-v4l2
	${Hyperion_V4L2_HEADERS}
	${Hyperion_V4L2_SOURCES}
	${Hyperion_V4L2_QT_HEADERS}
)

target_link_libraries(hyperion-v4l2
	v4l2-grabber
	getoptPlusPlus
	blackborder
	hyperion-utils
	protoserver
	pthread
	${QT_LIBRARIES}
)
