# CMake-template
This is guide that gives you a simple and easy to use CMake template for every small project you create. It is like the solution Visual Studio 2022 creates for every C# project.

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

## Building and Running the Project

### Prerequisites
- CMake (version 3.10 or higher)
- A C++ compiler (like MSVC, GCC, or Clang)
- Git (optional, for version control)

### Step 1: Generate the Build Files
First, create a build directory and generate the build files using CMake:

```console
# Create a build directory
mkdir build
cd build

# Generate build files for your system
cmake ..
```

### Step 2: Build the Project
Now build the project using the generated build system:

```console
# Build the project
cmake --build .
```

### Step 3: Run the Executable
After a successful build, you can run the executable:

```console
# Run the project (Debug build on Windows)
.\Debug\ProjectName.exe

# Alternative path (Release build on Windows)
.\Release\ProjectName.exe

# On Linux/macOS
./ProjectName
```

### Additional CMake Commands

#### Specify Build Type
```console
# Generate build files with specific build type
cmake -DCMAKE_BUILD_TYPE=Release ..
```

#### Clean and Rebuild
```console
# Clean the build directory
cmake --build . --target clean

# Rebuild
cmake --build .
```

#### Run Tests (if testing is enabled)
```console
# Run all tests
ctest
```
