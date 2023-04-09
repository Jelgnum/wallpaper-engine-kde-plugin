project(wescene-renderer)

find_package(PkgConfig REQUIRED)


include_directories(SYSTEM third_party)
add_subdirectory(third_party)
add_subdirectory(src)


if(BUILD_QML)
    find_package(Qt6 COMPONENTS REQUIRED Gui Quick Qml)


    add_library(${PROJECT_NAME}-qml
    STATIC
        qml_helper/SceneBackend.cpp
        qml_helper/glExtra.cpp
    )
    target_link_libraries(${PROJECT_NAME}-qml
    PUBLIC
        Qt6::Quick
        Qt6::Gui
        glad
        ${PROJECT_NAME}
    )
    target_include_directories(${PROJECT_NAME}-qml PUBLIC qml_helper third_party)

endif()
