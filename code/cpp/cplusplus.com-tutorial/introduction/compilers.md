# Compilers



## Compilers

Like C, C++ is a compiled language, meaning that the source code is translated to machine code. This is because source code, is much easier to read than machine code, since machine code comprises of only 1s and 0s. Saying so, machines can only understand machine language.

### Console programs

Console programs use text channels to communicate with the user and the environment, these are your beginner, basic programs that might print out text to a console, or ask for input etc.

### IDEs

There are a few main IDEs for C++

| IDE | Platform | How to use the IDE |
| :--- | :--- | :--- |
| **Dev-C++** | Windows | [Guide](https://www.cplusplus.com/doc/tutorial/introduction/devcpp/) |
| **Visual Studio Express** | Windows | [Guide](https://www.cplusplus.com/doc/tutorial/introduction/visualstudio/) |
| **Code::blocks** | Windows/Linux/MacOS | [Guide](https://www.cplusplus.com/doc/tutorial/introduction/codeblocks/) |

### Compilers

There are 2 main compilers for C++, Clang and GCC, these compilers are built into Unix environments so that you can compile C++ files on the fly with the following command

| Compiler | Platform | Command |
| :--- | :--- | :--- |
| **GCC** | Linux | g++ -std=c++0x example.cpp -o example\_program |
| **Clang** | MacOS | clang++ -std=c++11 -stdlib=libc++ example.cpp -o example\_program |

