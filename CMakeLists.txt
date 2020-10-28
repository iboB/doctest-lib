# released in the public domain

# doctest
add_library(doctest STATIC doctest/parts/doctest.cpp)
target_compile_definitions(doctest PRIVATE -DDOCTEST_IMPLEMENT=1)
target_include_directories(doctest INTERFACE .)

# doctest-main
add_library(doctest-main STATIC doctest/doctest-main.cpp)
target_link_libraries(doctest-main PUBLIC doctest)
