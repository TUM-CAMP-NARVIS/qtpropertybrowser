cmake_minimum_required(VERSION 3.10)

project(qtpropertybrowswer)

include(GNUInstallDirs)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTORCC ON)

find_package(Qt5 REQUIRED COMPONENTS Widgets)

set(APP_SRC 
    src/qtpropertybrowser.cpp
    src/qtpropertymanager.cpp
    src/qteditorfactory.cpp
    src/qtvariantproperty.cpp
    src/qttreepropertybrowser.cpp
    src/qtbuttonpropertybrowser.cpp
    src/qtgroupboxpropertybrowser.cpp
    src/qtpropertybrowserutils.cpp
)

set(APP_HDR
        include/qtpropertybrowser/qtpropertybrowser.h
        include/qtpropertybrowser/qtpropertymanager.h
        include/qtpropertybrowser/qteditorfactory.h
        include/qtpropertybrowser/qtvariantproperty.h
        include/qtpropertybrowser/qttreepropertybrowser.h
        include/qtpropertybrowser/qtbuttonpropertybrowser.h
        include/qtpropertybrowser/qtgroupboxpropertybrowser.h
        include/qtpropertybrowser/qtpropertybrowserutils_p.h
    )

set(APP_RSC
    src/qtpropertybrowser.qrc
)


add_library(qtpropertybrowser 
    ${APP_SRC}
    ${APP_HDR}
    ${APP_RSC}
)

set_property(TARGET qtpropertybrowser PROPERTY CXX_STANDARD 11)
set_target_properties(qtpropertybrowser PROPERTIES LINKER_LANGUAGE CXX)


target_link_libraries(qtpropertybrowser
    Qt5::Widgets
)

target_include_directories(qtpropertybrowser PUBLIC
        $<BUILD_INTERFACE:${CMAKE_SOURCE_DIR}>/include
        $<INSTALL_INTERFACE:include>
        PRIVATE
        ${PROJECT_SOURCE_DIR}/include/qtpropertybrowser
        ${PROJECT_BINARY_DIR}/src
        ${CMAKE_BINARY_DIR}/include
        )

install(TARGETS qtpropertybrowser EXPORT ringbufferConfig
    ARCHIVE  DESTINATION ${CMAKE_INSTALL_LIBDIR}
    LIBRARY  DESTINATION ${CMAKE_INSTALL_LIBDIR}
    RUNTIME  DESTINATION ${CMAKE_INSTALL_BINDIR})  # This is for Windows
install(DIRECTORY ${PROJECT_SOURCE_DIR}/include/qtpropertybrowser DESTINATION ${CMAKE_INSTALL_INCLUDEDIR})
