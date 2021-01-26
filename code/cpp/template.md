# Template



{% code title="\_\_\_\_.cpp" %}
```c
/***********************************************************************
* ____.cpp
* CLI application that ____
* Adnan Quisar
* January 2021
* *********************************************************************/

#include <iostream>            //Header file for input and output

class World {                  // Defines a class of objects
public:
        // A constructor used every time an object is created
        World() { std::cout << "Hello World!\n"; }
        
        // A destructor used when an object goes out of scope
        ~World(){std::cout << "Good bye World!\n"; }
};

World theWorld;        // Declares a global object of the class

int main()
{
        return 0;
}
```
{% endcode %}

