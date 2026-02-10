cmake_minimum_required(VERSION 3.21)

project(fin_etude LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTOUIC ON)
set(CMAKE_AUTORCC ON)

set(CMAKE_WIN32_EXECUTABLE OFF)

find_package(Qt6 REQUIRED COMPONENTS Core Widgets Sql PrintSupport Network)

# chemins UI
set(CMAKE_AUTOUIC_SEARCH_PATHS
    ${CMAKE_SOURCE_DIR}/ui
)

include_directories(
    ${CMAKE_SOURCE_DIR}/views
    ${CMAKE_SOURCE_DIR}/models
    ${CMAKE_SOURCE_DIR}/core
    ${CMAKE_SOURCE_DIR}/ui
)

# fichiers .cpp
set(SRC_FILES
    src/main.cpp
    views/mainwindow.cpp
    views/productwindow.cpp
    views/cartwindow.cpp
    views/checkoutdialog.cpp
    views/smtpclient.cpp
    views/RegisterWindow.cpp
    ui/loginwindow.cpp
    models/productmodel.cpp
    resources/resources.qrc
)

# fichiers .h
set(HDR_FILES
    views/mainwindow.h
    views/productwindow.h
    views/cartwindow.h
    views/checkoutdialog.h
    views/smtpclient.h
    views/RegisterWindow.h
    ui/loginwindow.h
    models/productmodel.h
    core/database.h
)

# fichiers .ui
set(UI_FILES
    ui/mainwindow.ui
    ui/productwindow.ui
    ui/cartwindow.ui
    ui/checkoutdialog.ui
    ui/loginwindow.ui
    ui/RegisterWindow.ui
)

add_executable(fin_etude
    ${SRC_FILES}
    ${HDR_FILES}
    ${UI_FILES}
)

target_link_libraries(fin_etude PRIVATE
    Qt6::Core
    Qt6::Widgets
    Qt6::Sql
    Qt6::PrintSupport
    Qt6::Network
)
