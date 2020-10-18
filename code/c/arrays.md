# Arrays

An **array** is a collection of data items, all of the same type, accessed using a common name. Arrays are declared as a fixed length.

{% tabs %}
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

