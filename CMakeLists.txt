project("test")
cmake_minimum_required(VERSION "3.10")
cmake_policy(SET CMP0003 NEW)
cmake_policy(SET CMP0048 NEW)
set(CMAKE_POLICY_DEFAULT_CMP0077 NEW)

# INCLUDE_DIRECTORIES(
# 	${CMAKE_SOURCE_DIR}/lib/Calibration/EMGSurrogates/Reflexes
# 	${CMAKE_SOURCE_DIR}/lib/Calibration/TorqueComputationModes
# 	${CMAKE_SOURCE_DIR}/lib/Calibration
# )

# ADD_LIBRARY("${PROJECT_NAME}" STATIC
# 	${CMAKE_CURRENT_SOURCE_DIR}/CalibrateReflexesMain.cpp
# 	${CMAKE_CURRENT_SOURCE_DIR}/TorqueComputation.cpp
# 	${CMAKE_CURRENT_SOURCE_DIR}/mapTools.cpp
# )

FIND_PACKAGE(Eigen3 3.3 REQUIRED NO_MODULE PATHS ${CMAKE_SOURCE_DIR}/Eigen3)
# find_package(OpenMP)

set (LIBCMAES_BUILD_SHARED_LIBS OFF) 
set (LIBCMAES_BUILD_PYTHON OFF) 
set (LIBCMAES_BUILD_TESTS OFF) 
set (LIBCMAES_USE_OPENMP ON) 
set (LIBCMAES_ENABLE_SURROG ON) 

add_subdirectory(libcmaes)

add_executable("${PROJECT_NAME}" main.cpp)
target_link_libraries("${PROJECT_NAME}" cmaes)