
TRIBITS_ADD_EXECUTABLE_AND_TEST(
  iallreduce
  SOURCES
    iallreduce
    ${TEUCHOS_STD_UNIT_TEST_MAIN}
  NUM_MPI_PROCS 1-4
  COMM serial mpi
  )

TRIBITS_ADD_EXECUTABLE_AND_TEST(
  extractMpiCommFromTeuchos
  SOURCES
    extractMpiCommFromTeuchos
    ${TEUCHOS_STD_UNIT_TEST_MAIN}
  NUM_MPI_PROCS 1-4
  COMM mpi
  )

# This test is best done with at least 2 MPI processes.
TRIBITS_ADD_EXECUTABLE_AND_TEST(
  isInterComm
  SOURCES
    isInterComm
    ${TEUCHOS_STD_UNIT_TEST_MAIN}
  NUM_MPI_PROCS 2-4
  COMM serial mpi
  )

TRIBITS_ADD_EXECUTABLE_AND_TEST(
  idot
  SOURCES
    idot
    ${TEUCHOS_STD_UNIT_TEST_MAIN}
  NUM_MPI_PROCS 1-4
  COMM serial mpi
  )

ASSERT_DEFINED (Tpetra_ENABLE_CUDA)
ASSERT_DEFINED (Tpetra_INST_CUDA)

# mfh 21 Aug 2017: The "CUDA-aware MPI" test still builds and runs if
# Tpetra_ASSUME_CUDA_AWARE_MPI is OFF, but it is a trivial run (doing
# nothing and passing) unless the TPETRA_ASSUME_CUDA_AWARE_MPI
# environment variable is set (to some "true" value, like "1", "ON",
# "YES", or "TRUE").  This makes the test useful for cross-compilation
# and other situations where the MPI implementation's CUDA-awareness
# cannot be known until run time.

IF (Tpetra_ENABLE_CUDA AND Tpetra_INST_CUDA)
  TRIBITS_ADD_EXECUTABLE_AND_TEST(
    cudaAwareMpi
    SOURCES
      cudaAwareMpi
      ${TEUCHOS_STD_UNIT_TEST_MAIN}
    NUM_MPI_PROCS 2
    COMM mpi
    )
ENDIF ()
