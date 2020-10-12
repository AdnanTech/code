# Operators

### Operator Examples

* There are some cool built in functions
  * sizeof\(\) - returns the size of the element as number of bytes

{% code title="operatorsExamples.c" %}
```c
/***********************************************************************
* operatorsExamples.c
* CLI application that converts farenheit to degrees centigrade
* Adnan Quisar
* September 2020
***********************************************************************/

#include <stdio.h>

int main(void)
{
    printf("Enter temperature in degrees fahrenheit: ");
    scanf("%d", &ftemp);
    ctemp = (ftemp - 32) * 5 / 9;
    printf("Temperature in degrees centigrade: %d", ctemp);
    return 0;
}
```
{% endcode %}

{% code title="operatorsExamples.c" %}
```c
/***********************************************************************
* operatorsExamples.c
* CLI application that outputs an operator example to the console
* Adnan Quisar
* September 2020
***********************************************************************/

#include <stdio.h>

int main(void)
{
    int total = 0;
    int count = 10;
    printf("Total = %d\n", total); /* display total */
    total += count; /* add 10 to total */
    printf("Total = %d\n", total);
    total += count;
    printf("Total = %d\n", total);
    
    return 0;
}
```
{% endcode %}

{% code title="operatorsExamples.c" %}
```c
/***********************************************************************
* operatorsExamples.c
* CLI application that outputs an operator example to the console
* Adnan Quisar
* September 2020
***********************************************************************/

#include <stdio.h>

int main(void)
{
   int age;
   age = 15;
   printf("Is age %d less than 21? %d\n", age, age < 21);
   age = 45;
   printf("Is age %d less than 21? %d\n", age, age < 21);
   return 0;
}
```
{% endcode %}

