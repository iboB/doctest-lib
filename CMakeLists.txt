# released in the public domain

option(DOCTEST_LIB_TREAT_CHAR_STAR_AS_STRING "Enable doctest char* comparisons with '=='" OFF)
option(DOCTEST_LIB_USE_STD_HEADERS "Include standard C++ headers with doctest (as opposed to emulating them)" ON)
mark_as_advanced(DOCTEST_LIB_TREAT_CHAR_STAR_AS_STRING DOCTEST_LIB_USE_STD_HEADERS)

# doctest-headers
add_library(doctest-headers INTERFACE)
target_include_directories(doctest-headers INTERFACE .)

if(DOCTEST_LIB_TREAT_CHAR_STAR_AS_STRING)
    target_compile_definitions(doctest-headers INTERFACE -DDOCTEST_CONFIG_TREAT_CHAR_STAR_AS_STRING=1)
endif()

if(DOCTEST_LIB_USE_STD_HEADERS)
    target_compile_definitions(doctest-headers INTERFACE -DDOCTEST_CONFIG_USE_STD_HEADERS=1)
endif()

# doctest lib
add_library(doctest STATIC doctest/parts/doctest.cpp)
target_compile_definitions(doctest PRIVATE -DDOCTEST_IMPLEMENT=1)
target_link_libraries(doctest PUBLIC doctest-headers)

# doctest-main
add_library(doctest-main STATIC doctest/doctest-main.cpp)
target_link_libraries(doctest-main PUBLIC doctest)
