cmake_minimum_required(VERSION 3.10)

project(qtpropertybrowswer)

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
    src/qtpropertybrowser.h
    src/qtpropertymanager.h
    src/qteditorfactory.h
    src/qtvariantproperty.h
    src/qttreepropertybrowser.h
    src/qtbuttonpropertybrowser.h
    src/qtgroupboxpropertybrowser.h
    src/qtpropertybrowserutils_p.h
    )

set(APP_RSC
    src/qtpropertybrowser.qrc
)


add_library(qtpropertybrowser STATIC
    ${APP_SRC}
    ${APP_HDR}
    ${APP_RSC}
)

target_link_libraries(qtpropertybrowser
    Qt5::Widgets
)