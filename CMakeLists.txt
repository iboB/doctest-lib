# released in the public domain

option(DOCTEST_LIB_TREAT_CHAR_STAR_AS_STRING "Enable doctest char* comparisons with '=='" OFF)

mark_as_advanced(DOCTEST_LIB_TREAT_CHAR_STAR_AS_STRING)

# doctest
add_library(doctest STATIC doctest/parts/doctest.cpp)
target_compile_definitions(doctest PRIVATE -DDOCTEST_IMPLEMENT=1)
target_include_directories(doctest INTERFACE .)

if(DOCTEST_LIB_TREAT_CHAR_STAR_AS_STRING)
    target_compile_definitions(doctest PUBLIC -DDOCTEST_CONFIG_TREAT_CHAR_STAR_AS_STRING=1)
endif()

# doctest-main
add_library(doctest-main STATIC doctest/doctest-main.cpp)
target_link_libraries(doctest-main PUBLIC doctest)
