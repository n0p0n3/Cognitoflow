cmake_minimum_required(VERSION 3.10) # Need at least 3.10 for C++17 target property

project(NeuralFlowCpp VERSION 1.0.0 LANGUAGES CXX)

# Require C++17 for std::any, std::optional
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED True)
set(CMAKE_CXX_EXTENSIONS OFF) # Prefer standard C++

# --- Library Definition (Optional, if you want to build a static/shared lib) ---
# add_library(neuralflow NeuralFlow.h) # Header-only doesn't need this directly
# target_include_directories(neuralflow PUBLIC ${CMAKE_CURRENT_SOURCE_DIR})
# target_compile_features(neuralflow PUBLIC cxx_std_17) # Ensure C++17

# --- Executable Example ---
add_executable(neuralflow_example main.cpp)

# Link executable to library if it were built separately:
# target_link_libraries(neuralflow_example PRIVATE neuralflow)

# If header-only, just need to ensure includes are found and C++17 is used
target_include_directories(neuralflow_example PUBLIC ${CMAKE_CURRENT_SOURCE_DIR})
target_compile_features(neuralflow_example PRIVATE cxx_std_17) # Ensure C++17 for the executable

# --- Testing (Example using GoogleTest - requires GTest setup) ---
# enable_testing()
# find_package(GTest REQUIRED)
# add_executable(neuralflow_tests NeuralFlow_test.cpp) # Your test file
# target_link_libraries(neuralflow_tests PRIVATE GTest::gtest GTest::gtest_main)
# target_include_directories(neuralflow_tests PUBLIC ${CMAKE_CURRENT_SOURCE_DIR})
# target_compile_features(neuralflow_tests PRIVATE cxx_std_17)
# include(GoogleTest)
# gtest_discover_tests(neuralflow_tests)
