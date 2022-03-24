# doctest-lib

A wrapper of the awesome C++ unit-testing library **[doctest](https://github.com/doctest/doctest/)**.

It makes using the library as a submodule with CMake a bit easier.

It has a CMakeLists.txt which is nothing on its own. It's supposed to be added by `add_subdirectory`. It then defines two static library targets:

* `doctest` - which is a library with no main function, in case you want to write your own
* `doctest-main` - which defines a main function and is the common way of using doctest

To use doctest with this helper: `#include <doctest/doctest.h>`

With this you don't have to define your own file with a doctest implementation and it doesn't impose any compiler or linker settings whatsoever on the caller.

## Copying

The files in `doctest/parts` are copied from [doctest/doctest](https://github.com/doctest/doctest/) and are under the [MIT Software License](http://opensource.org/licenses/MIT). Copyright &copy;  2016-2021 Viktor Kirilov

Everything else is simple boilerplate which I release in the public domain.
