
file(GLOB ALL_GRID_TESTS grid/*.cpp)
file(GLOB ALL_FILE_TESTS file/*.cpp)
file(GLOB ALL_ALGORITHMS_TESTS algorithms/*.cpp)
set(ALL_SOURCES ${ALL_GRID_TESTS} ${ALL_FILE_TESTS} ${ALL_ALGORITHMS_TESTS})

add_definitions(-std=c++17 -Wall -pedantic -O1 -llapack -lblas -lgtest -larmadillo )

add_executable(
    unit_tests    
    ${ALL_SOURCES}
    )

target_link_libraries(
    unit_tests
    gtest_main
    wind_farm_model
    )

add_test(
  NAME
    Sensor_Home_AUTOMATION
  COMMAND
    ${CMAKE_BINARY_DIR}/${CMAKE_INSTALL_BINDIR}/unit_tests
  )
