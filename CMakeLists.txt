# Mindestversion von CMake
cmake_minimum_required(VERSION 3.12)

# Projektname und Version
project(MatrixLinAlgProject VERSION 1.0 LANGUAGES CXX)

# Setze den C++ Standard
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED True)

# Füge den Include-Ordner hinzu
# PROJECT_SOURCE_DIR ist eine variable, automatisch folder in der CMakelists liegt.
include_directories(${PROJECT_SOURCE_DIR}/include)

# Füge die Quell- und Header-Dateien hinzu
set(SOURCES
    src/helloworld.cpp
)

# Erstelle die ausführbare Datei
add_executable(execMat ${SOURCES})

# Falls gewünscht, füge AddressSanitizer hinzu
set(ENABLE_ASAN ON)

if (ENABLE_ASAN)
    message(STATUS "AddressSanitizer enabled")
    set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -fsanitize=address -fno-omit-frame-pointer -g")
    set(CMAKE_LINKER_FLAGS "${CMAKE_LINKER_FLAGS} -fsanitize=address")
endif()

