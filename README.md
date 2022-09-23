# doctest-lib

A wrapper of the awesome C++ unit-testing library **[doctest](https://github.com/doctest/doctest/)**.

It makes using the library as a submodule with CMake a bit easier.

It has a `CMakeLists.txt` which is supposed to be added by `add_subdirectory` and defines the following targets:

* `doctest::headers` or `doctest-headers` - a header-only interface library, in case you want to add the implementation in your own files
* `doctest::doctest` or `doctest` - a static library with no main function, in case you want to write your own
* `doctest::main` or `doctest-main` - a static library which defines a main function and is the common way of using doctest

To use doctest with this helper: `#include <doctest/doctest.h>`

For the header-only use include the implementation with `#include <doctest/impl.h>`

With this you don't have to define your own file with a doctest implementation and it doesn't impose any compiler or linker settings whatsoever on the caller.

## Copying

The files in `doctest/parts` are copied from [doctest/doctest](https://github.com/doctest/doctest/) and are under the [MIT Software License](http://opensource.org/licenses/MIT). Copyright &copy;  2016-2021 Viktor Kirilov

Everything else is simple boilerplate which I release in the public domain.
