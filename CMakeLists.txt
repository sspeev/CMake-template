cmake_minimum_required(VERSION 3.10)
project("ProjectName" VERSION 1.0)

set(CMAKE_CXX_STANDARD 17) # cxx stands for cpp
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# Include directories
include_directories(${CMAKE_SOURCE_DIR})

# Create the libraryName library
#This approach is more straight forward
add_library(libraryName
    pathTolibraryName.cpp
)
# That is more specific but both do the same
# add_library(libraryName) # libName in settings

# target_sources(
#     libraryName 
#     PRIVATE 
#         "pathTolibraryName.cpp"
#) #parameters: libName in settings, Accessibility(PRIVATE, PUBLIC), libName 


#add testing
# include(CTest)
# enable_testing()

# Main target
add_executable(ProjectName pathToMain.cpp)

target_sources(
	ProjectName
	PRIVATE
		"pathTomain.cpp" # you can add path to main.cpp and additional files
)

target_link_libraries(
	ProjectName
	PRIVATE
		libraryName
)