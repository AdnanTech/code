# Functions

* Function prototypes listed before main\(\)
* Function definitions after main\(\). 
* Every function definition should be preceded by a comment.

{% code title="houseAddresss.c" %}
```c
/***********************************************************************
* houseAddresss.c
* CLI application that outputs a name and an address to the console
* Adnan Quisar
* October 2020
***********************************************************************/

#include <stdio.h>

void myAddress(void);
void myName(void);

int main(void)
{
    /* Functions are called here */
    myName();
    myAddress();
    return 0;                    /* return an int was required */
}
/* Function definitions go after main() */

/* Display my name */
void myName(void)
{
    printf("Adnan Quisar\n");
}                                 /* no return statement required */

/* Display my address */
void myAddress(void)
{
    printf("123 A Road\n");
    printf("A town\n");
    printf("A county\n");
    printf("BN1 AAA");
}
```
{% endcode %}

* Functions can be passed as many parameters, but can only return one value

{% code title="squareCubeInput.c" %}
```c
/***********************************************************************
* squareCubeInput.c
* CLI application that outputs the squared and cubic value to 3 decimal 
  places of an input, to the console
* Adnan Quisar
* October 2020
***********************************************************************/

#include <stdio.h>

double square(double value);
double cube(double value);

int main(void)
{
    double num;
    
    /* Take input as double to be squared and cubed from user */
    printf("Enter the number to be sqaured: \n");
    scanf("%lf", &num);
    
    double numSquared = square(num);
    /* Output squared version of input to console */
    printf("%.3lf x %.3lf = %.3lf\n", num, num, numSquared);
    /* Output cubed version of input to console */
    printf("%.3lf x %.3lf x %.3lf = %.3lf\n", num, num, num,
    cube(num));
    return 0;
}

/* Return the square of the value passed to it */
double square(double value)
{
    return value * value;
}

/* Return the cube of the value passed to it */
double cube(double value)
{
    return value * value * value;
}
```
{% endcode %}

