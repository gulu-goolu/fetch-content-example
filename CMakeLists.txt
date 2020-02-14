cmake_minimum_required(VERSION 3.11)

include(FetchContent)

FetchContent_Declare(
	gtest
	GIT_REPOSITORY https://github.com/google/googletest.git
	GIT_TAG release-1.8.0
)

FetchContent_GetProperties(gtest)
if (NOT gtest_POPULATED)
	FetchContent_Populate(gtest)
	set(BUILD_GTEST ON CACHE BOOL "" FORCE)
	set(BUILD_GMOCK OFF CACHE BOOL "" FORCE)
	add_subdirectory(${gtest_SOURCE_DIR} ${gtest_BINARY_DIR})
endif()

add_executable(test test.cpp)
target_link_libraries(test gtest_main)

