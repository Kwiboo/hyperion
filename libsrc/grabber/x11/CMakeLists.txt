# Define the current source locations
SET(CURRENT_HEADER_DIR ${CMAKE_SOURCE_DIR}/include/grabber)
SET(CURRENT_SOURCE_DIR ${CMAKE_SOURCE_DIR}/libsrc/grabber/x11)

# Find X11
find_package(X11 REQUIRED)

include_directories(
	${X11_INCLUDES}
)

SET(X11_QT_HEADERS
		${CURRENT_HEADER_DIR}/X11Grabber.h
)

SET(X11_HEADERS
	${CURRENT_HEADER_DIR}/X11Grabber.h
)

SET(X11_SOURCES
		${CURRENT_SOURCE_DIR}/X11Grabber.cpp
)

add_library(x11-grabber
		${X11_HEADERS}
		${X11_SOURCES}
		${X11_QT_HEADERS}
)

target_link_libraries(x11-grabber
	hyperion
	${QT_LIBRARIES}
)
