

TRIBITS_ADD_EXECUTABLE_AND_TEST(
  OptimizationSolverStatusTestInput
  SOURCES test_01.cpp
  ARGS PrintItAll
  NUM_MPI_PROCS 1
  PASS_REGULAR_EXPRESSION "TEST PASSED"
  ADD_DIR_TO_NAME
  )

TRIBITS_COPY_FILES_TO_BINARY_DIR(
  AlgorithmTestDataCopy
  SOURCE_FILES
    input.xml
  SOURCE_DIR "${CMAKE_CURRENT_SOURCE_DIR}"
  DEST_DIR "${CMAKE_CURRENT_BINARY_DIR}"
)
