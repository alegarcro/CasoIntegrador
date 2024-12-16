cmake_minimum_required(VERSION 3.29)
project(CasoIntegrador)

set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# Añade el directorio de json11 al path de inclusión
include_directories(${CMAKE_SOURCE_DIR}/json11)

# Añade json11 como subdirectorio si existe
if(EXISTS "${CMAKE_SOURCE_DIR}/json11/CMakeLists.txt")
    add_subdirectory(json11)
else()
    message(FATAL_ERROR "json11 directory not found. Please clone it into your project directory.")
endif()

# Añade los archivos fuente de tu proyecto
add_executable(CasoIntegrador
        main.cpp
        variant/variant.cpp
)

# Incluye los directorios necesarios
target_include_directories(CasoIntegrador PRIVATE
        ${CMAKE_SOURCE_DIR}/variant
        ${CMAKE_SOURCE_DIR}/json11
)

# Enlaza con la biblioteca json11
target_link_libraries(CasoIntegrador PRIVATE json11)