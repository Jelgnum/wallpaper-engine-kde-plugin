project(mpvbackend)

find_package(Qt6 COMPONENTS REQUIRED Gui Quick X11Extras)
include_directories(${Qt6Gui_PRIVATE_INCLUDE_DIRS})

find_package(PkgConfig REQUIRED)
pkg_check_modules(MPV REQUIRED mpv)


add_library(${PROJECT_NAME}
	STATIC
	MpvBackend.cpp  
	qthelper.hpp
)
target_link_libraries(${PROJECT_NAME} 
	PRIVATE 
   	Qt6::Quick
	Qt6::Gui
	Qt6::X11Extras
	${MPV_LIBRARIES}
)
target_include_directories(${PROJECT_NAME} PUBLIC .) #${INCLUDE_DIRECTORIES})
