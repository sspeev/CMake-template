# CMake-template
This is guide that gives you a simple and easy to use CMake template for every small project you create. It is like the solution Visual Studio 2022 creates for evert C# project.

## CMake Template Explanation

### Basic Configuration
- `cmake_minimum_required(VERSION 3.10)` - Sets the minimum CMake version required
- `project("ProjectName" VERSION 1.0)` - Sets your project name and version
- `set(CMAKE_CXX_STANDARD 17)` - Sets C++ standard (C++ 17 in this case)
- `set(CMAKE_CXX_STANDARD_REQUIRED ON)` - Makes the C++ standard required

### Include Directories
- `include_directories(${CMAKE_SOURCE_DIR})` - Includes the main source directory

### Creating Libraries
There are two approaches to define libraries:

1. Straightforward approach:
```cmake
add_library(libraryName
    pathTolibraryName.cpp
)
```

2. More specific approach (both do the same):
```cmake
add_library(libraryName) # Define the library name in settings
target_sources(
    libraryName 
    PRIVATE 
        "pathTolibraryName.cpp"
) 
```
The parameters for `target_sources` are:
- Library name (as defined in settings)
- Accessibility (PRIVATE, PUBLIC)
- Source files

### Testing
To add testing capabilities, uncomment:
```cmake
include(CTest)
enable_testing()
```

### Main Target
- `add_executable(ProjectName pathToMain.cpp)` - Creates the main executable
- Use `target_sources` to add the main.cpp and any additional files
- Use `target_link_libraries` to link libraries to your main executable
