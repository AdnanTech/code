# Arrays

An **array** is a collection of data items, all of the same type, accessed using a common name. Arrays are declared as a fixed length.

{% tabs %}
{% tab title="simpleArray" %}
{% code title="simpleArray.c" %}
```c
/***********************************************************************
* simpleArray.c
* CLI application that shows an example of arrays
* Adnan Quisar
* Version 1
* ********************************************************************/

#include <stdio.h>
 
int main ()
{
   int n[10]; /* n is an array of 10 integers */
   int i, j;
 
   /* initialize elements of array n to 0 */         
   for (i = 0; i < 10; i++ )
   {
      n[i] = i + 100; /* set element at location i to i + 100 */
   }
   
   /* output each array element's value */
   for (j = 0; j < 10; j++ )
   {
      printf("Element[%d] = %d\n", j, n[j] );
   }
 
   return 0;
}

/* Result
Element[0] = 100
Element[1] = 101
Element[2] = 102
Element[3] = 103
Element[4] = 104
Element[5] = 105
Element[6] = 106
Element[7] = 107
Element[8] = 108
Element[9] = 109
*/
```
{% endcode %}
{% endtab %}

{% tab title="avgTemperature" %}
{% code title="avgTemperature" %}
```c
/***********************************************************************
* avgTemperature.c
* CLI application that calculates the average temperature for a week
* Adnan Quisar
* Version 1
* ********************************************************************/

#include <stdio.h>
#define WEEK 7

void getTemperatures(int temps[]);

double calculateAverage(int temperature[]);

int main(void)
{
    int temper[WEEK];                /* Array declaration */
    getTemperatures(temper);        /* temper is a pointer to the array */
    printf("\nAverage is %.1f.\n\n", calculateAverage(temper));
    return 0;
}

/* Populates array of temperatures ie temper in main.
* Normal parameters are passed by value but array parameters are
* passed by reference */
void getTemperatures(int temps[])
{
    int day;
    for(day = 0; day < WEEK; day++)
    {
        printf("Enter temperature for day %d: ", day);
        scanf("%d",&temps[day]);
    }
}

/* calculates average temperature */
double calculateAverage(inttemperature[])
{
    int day;
    doublesum = 0;
    for(day = 0; day < WEEK; day++)
    {
        sum += temperature[day];
    }
    return sum / WEEK;
}
```
{% endcode %}
{% endtab %}

{% tab title="passingStrings" %}
{% code title="passingStrings" %}
```c
/***********************************************************************
* passingStrings.c
* CLI application that passes an array of characters (string) to a 
* function and prints it to the consoles
* Adnan Quisar
* Version 1
* ********************************************************************/

#include <stdio.h>
#include <string.h>
#include <ctype.h>

void sort(char *strings[], int n);

int main()
{
    char *string_database[4]={'\0'};
    string_database[0]="Florida";
    string_database[1]="Oregon";
    string_database[2]="California";
    string_database[3]="Georgia";
    sort(string_database, 4);
    return 0;
}

void sort(char *strings[], int n)
{
    int i;
    for (i = 0; i < n; i++)
    {
        printf("String %d: %s\n", i, strings[i]);
    }
}
```
{% endcode %}
{% endtab %}
{% endtabs %}

## Passing Array Examples

{% tabs %}
{% tab title="Passing some values from an array" %}
```c
#include <stdio.h>

int main()
{
    int ageArray[] = {2, 8, 4, 12};

    // Passing second and third elements to display()
    display(ageArray[1], ageArray[2]); 
    return 0;
}

void display(int age1, int age2)
{
    printf("%d\n", age1);
    printf("%d\n", age2);
}

```
{% endtab %}

{% tab title="Passing an Unsized Array" %}
```c
#include <stdio.h>
float calculateSum(float age[]);

int main() {
    float result, age[] = {23.4, 55, 22.6, 3, 40.5, 18};

    // age array is passed to calculateSum()
    result = calculateSum(age); 
    printf("Result = %.2f", result);
    return 0;
}

float calculateSum(float age[]) {

  float sum = 0.0;

  for (int i = 0; i < 6; ++i) {
		sum += age[i];
  }
```
{% endtab %}

{% tab title="Passing an Array with Pointers" %}
```c
#include <stdio.h>
#include <string.h>
#include <ctype.h>

void sort(char *strings[], int n);

int main()
{
    char *string_database[4]={'\0'};
    string_database[0]="Florida";
    string_database[1]="Oregon";
    string_database[2]="California";
    string_database[3]="Georgia";
    sort(string_database, 4);
    return 0;
}

void sort(char *strings[], int n)
{
    int i;
    for (i = 0; i < n; i++)
    {
        printf("String %d: %s\n", i, strings[i]);
    }
}
```
{% endtab %}
{% endtabs %}

