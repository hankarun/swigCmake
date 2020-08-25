cmake_minimum_required(VERSION 3.2)

project(igconnection)

add_library(igConnection 
IgConnection.h
    IgConnection.cpp)

target_include_directories(igConnection PUBLIC .)

set(SWIG_DIR "${CMAKE_CURRENT_SOURCE_DIR}/swigwin-4.0.2/lib")
set(SWIG_EXECUTABLE "${CMAKE_CURRENT_SOURCE_DIR}/swigwin-4.0.2/swig.exe")

find_package(SWIG REQUIRED)
include(UseSWIG)

set_property(SOURCE swig.i PROPERTY CPLUSPLUS ON)

swig_add_library(csharp
	TYPE SHARED
	LANGUAGE csharp
	SOURCES swig.i)

target_link_libraries(csharp igConnection)