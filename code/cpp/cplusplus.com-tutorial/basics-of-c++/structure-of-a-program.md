# Structure of a program

As with all programs, there is a general structure which helps legibility of code, as well as formatting. For C++, you include the headers at the top, then the header classes/methods, after that main functions and then the other functions below.

### Hello World

{% tabs %}
{% tab title="Input" %}
```cpp
// my first program in C++
#include <iostream>

int main()
{
  
  std::cout << "Hello World!"; // prints Hello World!
  std::cout << "I'm a C++ program"; // prints I'm a C++ program
}
```
{% endtab %}

{% tab title="Output" %}
```
Hello World! I'm a C++ program
```
{% endtab %}
{% endtabs %}

* `#include <iostream>` includes the header iostream, which is interpreted by the preprocessor
* `std:cout` is the **ST**andar**D C**haracter **OUT**put device \(the screen\)
* `<<` dictates that the string is inserted into the output, which dictates the displayed result

### Comments

There are 2 ways to comment in C++:

* /`/ line comment`
* `/* block comment */`

### Using namespace std

the `using namespace std;` declaration refers to the standard library, std, which can simplify the calling of the std namespace to make for shorter code, so the first program now becomes:

{% tabs %}
{% tab title="Input" %}
```cpp
// my second program in C++
#include <iostream>

using namespace std;

int main ()
{
  cout << "Hello World! ";
  cout << "I'm a C++ program";
}
```
{% endtab %}

{% tab title="Output" %}
```
Hello World! I'm a C++ program
```
{% endtab %}
{% endtabs %}

Note how the second program is the exact same as the first, just more clear to read.

