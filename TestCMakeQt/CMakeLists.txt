cmake_minimum_required(VERSION 3.10.0)

project(TestCMakeQt)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# CMake enables Qt specific behavior for .moc/.qrc/.ui file types
set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTORCC ON)
set(CMAKE_AUTOUIC ON)

# Ensures adding current source and build directory to the include path
set(CMAKE_INCLUDE_CURRENT_DIR ON)

# Qt dependencies required
find_package(Qt5 COMPONENTS Widgets REQUIRED)

# Add an executable target using different source file types
# This works thanks to CMAKE_AUTOxxx ON above
# We don't actually need to list the header files in an executable (CMake will figure it on its own)
add_executable(TestCMakeQt
	mainwindow.ui
	mainwindow.cpp
	main.cpp
	resources.qrc
			)

# Wrap up : link to the needed Qt libraries
target_link_libraries(TestCMakeQt Qt5::Widgets)
