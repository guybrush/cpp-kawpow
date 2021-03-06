# ethash: C/C++ implementation of Ethash, the Ethereum Proof of Work algorithm.
# Copyright 2018-2019 Pawel Bylica.
# Licensed under the Apache License, Version 2.0.

hunter_add_package(GTest)
find_package(GTest CONFIG REQUIRED)

add_executable(
    ethash-test
    helpers.hpp
    test_bit_manipulation.cpp
    test_cases.hpp
    test_ethash.cpp
    test_keccak.cpp
    test_kiss.cpp
    test_managed.cpp
    test_primes.cpp
    test_progpow.cpp
    test_version.cpp
)

set_source_files_properties(test_version.cpp PROPERTIES COMPILE_DEFINITIONS TEST_PROJECT_VERSION="${PROJECT_VERSION}")

target_link_libraries(ethash-test PRIVATE ethash GTest::gtest_main)
target_include_directories(ethash-test PRIVATE ${ETHASH_PRIVATE_INCLUDE_DIR})
set_target_properties(ethash-test PROPERTIES RUNTIME_OUTPUT_DIRECTORY ..)
